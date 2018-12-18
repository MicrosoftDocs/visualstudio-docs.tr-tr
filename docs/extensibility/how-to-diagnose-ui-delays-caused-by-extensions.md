---
title: Tanılama uzantısı UI, Visual Studio'da geciktirir | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1bf5dba23622c5dc3d964bdac19fec210aa60b1e
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639201"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Nasıl yapılır: UI tanılama uzantılardan kaynaklanan gecikme

Kullanıcı Arabirimi yanıt vermemeye başlıyor, Visual Studio kullanıcı Arabirimi iş parçacığı çağrı yığınını yaprak ile başlayan ve temel çalışma inceler. Visual Studio çağrı yığını çerçevesi uzantı yüklü ve etkin bir parçası olan bir modüle ait olduğunu belirlerse, bir bildirim gösterilir.

![Kullanıcı Arabirimi gecikmesi (sorununa) bildirim](media/ui-delay-notification-in-vs.png)

Kullanıcı Arabirimi gecikmesi (diğer bir deyişle, kullanıcı arabiriminde sorununa) bir uzantı koddan sonucu silinmiş olabilir, bildirim kullanıcıya bildirir. Ayrıca uzantı veya bu uzantı için gelecekteki bildirimleri devre dışı bırakma seçenekleri ile kullanıcı sağlar.

Bu belgede, nasıl uzantı kodunuza kullanıcı Arabirimi gecikmesi bildirimleri çözebilmeniz tanılayabilirsiniz açıklanmaktadır. 

> [!NOTE]
> Visual Studio deneysel örneğinde kullanıcı Arabirimi gecikmelerini tanılama için kullanmayın. Çağrı yığını analiz UI gecikmesi bildirimleri için gerekli bazı bölümlerini, kullanıcı Arabirimi gecikmesi bildirimleri gösterilmiyor yani Deneysel örneğini kullanırken kapalıdır.

Tanılama işlemine genel bakış aşağıdaki gibidir:
1. Tetikleyici senaryoyu belirleyin.
2. VS oturum açma etkinliği ile yeniden başlatın.
3. ETW İzleme başlatın.
4. Bildirim yeniden görünür tetikleyin.
5. ETW İzleme durdurun.
6. Gecikme Kimliği almak için Etkinlik günlüğünü inceleyin
7. 6. adım gecikmesi Kimliğinden kullanarak ETW İzleme analiz edin.

Aşağıdaki bölümlerde bu adımlar daha ayrıntılı ele alacağız.

## <a name="identify-the-trigger-scenario"></a>Tetikleyici senaryo belirleme

UI gecikmesi tanılamak için öncelikle hangi (bir dizi eylem) bildirim göstermek Visual Studio neden tanımlamak gerekir. Açık günlük kaydı ile daha sonra bildirim tetiklemek izinlere, sırayla budur.

## <a name="restart-vs-with-activity-logging-on"></a>VS oturum açma etkinliği ile yeniden başlatın

Visual Studio "etkinlik günlüğü" oluşturabileceği bir sorun hata ayıklama sırasında yararlı bilgiler sağlar. Etkinlik Visual Studio'da oturum açmak için Visual Studio ile hayat `/log` komut satırı seçeneği. Visual Studio başlatıldıktan sonra etkinlik günlüğü şu konumda depolanır:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

VS nasıl bulabileceğinizi hakkında daha fazla örnek kimliği bilgi edinmek için [algılama ve Visual Studio örneklerini yönetmek için Araçlar](../install/tools-for-managing-visual-studio-instances.md). Bu etkinlik günlüğü daha sonra UI gecikmesi yaşanır ve ilgili bildirimleri hakkında daha fazla bilgi edinmek için kullanacağız.

## <a name="starting-etw-tracing"></a>ETW İzleme başlatılıyor

Kullanabileceğiniz [PerfView](https://github.com/Microsoft/perfview/) bir ETW İzleme toplamak için. PerfView bir ETW İzleme toplama ve çözümleme için kullanımı kolay arabirim sağlar. Bir izleme toplamak için aşağıdaki komutu kullanın:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Bu, Visual Studio kullanıcı Arabirimi gecikmesi bildirimlerle ilgili olaylar için kullandığı sağlayıcıdır "Microsoft VisualStudio" Sağlayıcı sağlar. Anahtar sözcüğü için PerfView oluşturmak için kullanabileceğiniz çekirdek sağlayıcısı ayrıca belirtir **iş parçacığı zamanı yığınları** görünümü.

## <a name="trigger-the-notification-to-appear-again"></a>Tetikleyici bildirim yeniden görünür

Koleksiyon izleme PerfView başlatıldıktan sonra yeniden görüntülenmesini tetikleyici eylem dizisinden (1. adım) bildirim için kullanabilirsiniz. Bildirim gösterilen sonra izleme PerfView işleyebilir ve çıktı izleme dosyasını oluşturmak toplamalarında durdurabilirsiniz.

## <a name="stop-etw-tracing"></a>ETW İzleme Durdur

İzleme toplamasını durdurmak için sadece kullanın **koleksiyonu Durdur** PerfView penceresinde düğmesi. İzleme koleksiyonu durdurduktan sonra PerfView ETW olayları otomatik olarak işler ve bir çıkış izleme dosyası oluşturur.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Gecikme Kimliğini almak için Etkinlik günlüğünü inceleyin

Daha önce bahsedildiği gibi etkinlik günlüğüne bulabilirsiniz *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*. Visual Studio uzantı UI gecikmesi her algıladığında, bir düğüm ile etkinlik günlüğü Yazar `UIDelayNotifications` kaynağı olarak. Bu düğüm, dört adede kadar kullanıcı Arabirimi gecikmesi hakkında bilgi içerir:

- Kullanıcı Arabirimi gecikmesi kimliği, UI gecikmesi VS oturumunda tanıtan sıralı bir sayı
- Visual Studio oturumunuzu kapatmak için baştan tanımlamasının oturum kimliği
- Bildirim için kullanıcı Arabirimi gecikmesi olup olmadığını gösterildi
- Büyük olasılıkla UI gecikmesi nedeniyle uzantısı

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Tüm kullanıcı Arabirimi gecikmelerini sonucu bir bildirim. Bu nedenle, her zaman denetlemelisiniz **gösterilen bildirim?** doğru UI gecikmesi doğru bir şekilde tanımlamak için değeri.

Etkinlik günlüğü'nde doğru UI gecikmesi bulduktan sonra düğüm belirtilen kullanıcı Arabirimi gecikmesi kimliğini yazın. Sonraki adımda karşılık gelen ETW olayı aramak için kimliği kullanacaksınız.

## <a name="analyze-the-etw-trace"></a>ETW İzleme analiz

Ardından, izleme dosyasını açın. PerfView veya yeni bir örneğini başlatarak ve sol üst penceresinin izleme dosyasının konumu için geçerli bir klasör yolu ayarını aynı örneği kullanarak bunu yapabilirsiniz.

![Klasör yolu Perfview ayarlama](media/perfview-set-path.png)

Sonra sol bölmede izleme dosyasını seçin ve seçerek açın **açın** sağ tıklayın veya bağlam menüsünde.

> [!NOTE]
> Varsayılan olarak, bir ZIP arşivi PerfView çıkarır. Açtığınızda *trace.zip*, otomatik olarak arşiv açar ve izlemeyi açar. Kaldırarak bunu atlayabilirsiniz **Zip** izleme toplama sırasında kutusu. Aktarım ve izlemeler farklı makineler arasında planlıyorsanız, ancak işaretini karşı öneririz **Zip** kutusu. Bu seçenek olmadan Ngen derlemeler için gerekli pdb izleme eşlik değil ve bu nedenle Ngen derlemelerden sembolleri hedef makine üzerinde çözümlenmeyecek. (Bkz [bu blog gönderisini](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) Ngen derlemeler için pdb hakkında daha fazla bilgi için.) 

Bu, PerfView işlemek ve izlemeyi açmak birkaç dakika sürebilir. İzleme açıldıktan sonra çeşitli "görünümler" listesi altında görünür.

![PerfView izleme Özet görünümü](media/perfview-summary-view-events-selected.png)

İlk kullanacağız **olayları** UI gecikmesi süresi aralığının edinme görünümü:

1. Açık **olayları** görünümü seçerek `Events` izleme düğümünde seçip **açık** sağ tıklayın veya bağlam menüsünde.
2. Seçin "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" sol bölmesinde.
3. Enter tuşuna basın

Seçimi uygulanır ve tüm `ExtensionUIUnresponsiveness` olayları, sağ bölmede görüntülenir.

![Olaylar Görünümü'nde olayları seçme](media/perfview-event-selection.png)

Sağ bölmede her satır için bir kullanıcı Arabirimi gecikmesi karşılık gelir. Olay gecikme kimliği 6 adımdaki etkinlik günlüğünde eşleşen bir "Gecikme ID" değeri içerir. Bu yana `ExtensionUIUnresponsiveness` UI gecikme, olayın zaman damgası sonunda bitiş zamanı kullanıcı Arabirimi gecikmesi işaretleri (yaklaşık) tetiklenir. Olay, gecikme süresini de içerir. Biz, kullanıcı Arabirimi gecikmesi başladığı zaman damgası elde etmek için bitiş zaman damgası süresinden çıkarabilirsiniz.

![Kullanıcı Arabirimi gecikmesi zaman aralığı hesaplanıyor](media/ui-delay-time-range.png)

Önceki ekran görüntüsünde, örneğin, olayın zaman damgası 12,125.679 ve gecikme süresi (ms) 6,143.085. Bu nedenle,
* Başlangıç Gecikmesi 12,125.679 6,143.085 olduğu 5,982.594 =.
* Kullanıcı Arabirimi gecikmesi zaman aralığı için 5,982.594 12,125.679 ' dir.

Şu zaman aralığını aldıktan sonra biz tanesi kapatabilirsiniz **olayları** görüntüleyebilir ve açabilirsiniz **(StartStop etkinliklerle) zaman iş parçacığı yığınları** görünümü. Bu görünüm özellikle kullanışlı çünkü genellikle UI iş parçacığı engelleme uzantıları yalnızca diğer iş parçacıkları veya miyim/O-bağlama işlemi bekliyor. Bu nedenle, **CPU yığın** seçenektir çoğu durum için Görünüm, iş parçacığı için harcadığı bu süre boyunca CPU kullanmadığından engelleme zamanı değil yakalama. **İş parçacığı zamanı yığınları** düzgün bir şekilde gösteren engellenen zaman bu sorunu çözer.

![İş parçacığı (StartStop etkinliklerle) zamanı yığınları düğümünde PerfView Özet görünümü](media/perfview-thread-time-with-startstop-activities-stacks.png)

Açma sırasında **iş parçacığı zamanı yığınları** Görüntüle öğesini **devenv** analiz başlatılacak işlem.

![İş parçacığı UI gecikmesi analizi için zaman yığınlar görünümü](media/ui-delay-thread-time-stacks.png)

İçinde **iş parçacığı zamanı yığınları** görüntülemek için üst sol sayfasının, zaman aralığı biz hesaplanan değerler için önceki adımı ve ENTER tuşuna ayarlayabilirsiniz **Enter** yığınları, zaman aralığı için ayarlanır bu nedenle.

> [!NOTE]
> Kullanıcı arabirimini hangi iş parçacığının belirleme (Başlangıç) iş parçacığı zaten Visual Studio açıldıktan sonra izleme koleksiyonu başladıysa mantığa aykırı olabilir. Ancak, kullanıcı Arabirimi (Başlangıç) iş parçacığının yığınındaki ilk öğesini olasılıkla her zaman işletim sistemi DLL'lerdir (*ntdll.dll* ve *kernel32.dll*) ardından `devenv!?` ardından `msenv!?` . Bu sıra UI iş parçacığı belirlemenize yardımcı olabilir.

 ![Başlangıç iş parçacığı tanımlama](media/ui-delay-startup-thread.png)

Ayrıca, bu görünüm yalnızca modüllerden paketinizi içeren yığınları dahil ederek filtreleyebilirsiniz.

* Ayarlama **GroupPats** varsayılan olarak eklenen herhangi bir gruplama kaldırmak için boş metin.
* Ayarlama **IncPats** mevcut filtresi yanı sıra derleme adınız dahil edilecek. Bu durumda, olmalıdır **devenv; UIDelayR2**.

![İş parçacığı zaman yığınlar Görünümü'nde GroupPath ve IncPath ayarlama](media/perfview-tts-group-path-inc-path.png)

PerfView ayrıntılı kılavuz altında **yardımcı** kodunuzda performans sorunlarını tanımlamak için kullanabileceğiniz menü. Ayrıca, aşağıdaki bağlantılar, Visual Studio API kodunuzu iyileştirmek için iş parçacığı kullanma hakkında daha fazla bilgi sağlar:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

Yeni Visual Studio statik çözümleyici uzantıları için de kullanabilirsiniz (NuGet paketini [burada](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), sağlayan yönergeler en iyi yöntemler üzerinde verimli uzantıları yazmak için. Listesini [VS SDK'sı Çözümleyicileri](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) ve [Çözümleyicileri iş parçacığı](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Yanıt vermeyi durdurma sorununa bağımlılıklar nedeniyle adres ise (örneğin, uzantınızı UI iş parçacığı üzerinde eşzamanlı VS Hizmetleri çağıran gerekiyorsa) üzerinde denetiminiz olmayan, bunu bilmek istiyoruz. Visual Studio iş ortağı programımız üyesiyseniz, geliştirici destek talebi göndererek bize başvurabilirsiniz. Aksi takdirde, Geri bildiriminizi gönderin ve dahil etmek için 'Sorun bildir' Aracı'nı kullanın `"Extension UI Delay Notifications"` başlık. Lütfen analiz ayrıntılı bir açıklaması da içerir.
