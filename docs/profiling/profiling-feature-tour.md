---
title: Profil oluşturma araçları ile performans ölçümü
description: Visual Studio'da kullanılabilen farklı tanılama araçları kısa göz atın.
ms.custom: mvc
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f884b92d03027782eed27f4583e06b1141341db
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356801"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Hızlı Başlangıç: Profil oluşturma araçları ilk bakış

Visual Studio profil oluşturma araçları, farklı tür, uygulama türüne bağlı olarak performans sorunlarını tanılamanıza yardımcı olacak çeşitli sağlar.

Hata ayıklama oturumu sırasında erişebileceğiniz profil oluşturma araçları tanılama araçları penceresinde kullanılabilir. Bunu devre dışı bırakmış sürece tanılama araçları penceresi otomatik olarak görünür. Pencereyi ayarlayıp getirmek için tıklayın **hata ayıklama / Windows / tanılama araçlarını Göster**. Penceresi açıkken, veri toplamak istediğiniz Araçlar seçebilirsiniz.

![Tanılama araçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "tanılama araçları")

Hata ayıklarken, kullanabileceğiniz **tanılama araçları** penceresi CPU ve bellek kullanımı ve analiz etmek için performans ile ilgili bilgileri gösteren olayları görüntüleyebilir.

![Tanılama araçları özeti görünümünü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "tanılama araçları özeti")

**Tanılama araçları** penceresi, genellikle profili uygulamalar için tercih edilen yoludur, ancak sürüm derlemeleri için Ayrıca uygulamanızı son İnceleme analizini bunun yerine bunu yapabilirsiniz. Farklı yaklaşımlar hakkında daha fazla bilgi istiyorsanız bkz [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Farklı uygulama türleri için araç desteği görmek için bkz: [hangi aracın kullanmalıyım?](#which-tool-should-i-use).

> [!NOTE]
> Windows 7 ve daha sonra son İnceleme araçları kullanabilirsiniz. Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere).

## <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme

CPU kullanımı aracı, uygulamanızın performansını analiz etmeye başlamak için iyi bir yerdir. Bu, uygulamanızın kullandığı CPU kaynakları hakkında daha fazla bildirir. CPU kullanımı aracı hakkında daha ayrıntılı bilgi için bkz: [performans profili oluşturma Başlangıç Kılavuzu](../profiling/beginners-guide-to-performance-profiling.md).

Gelen **özeti** görüntülemek tanılama araçları öğesini **CPU profil oluşturmayı etkinleştir** (hata ayıklama oturumunda olmalıdır).

![Tanılama Araçları'nda CPU kullanımını etkinleştir](../profiling/media/prof-tour-enable-cpu-profiling.png "tanılama araçları CPU kullanımını etkinleştir")

Aracı en etkili bir şekilde kullanmak için kodunuzu, tek başına ve bir işlevin sonuna veya bölge kodu analiz etmek istediğiniz iki kesme noktalarını ayarlayın. İkinci bir kesme noktasında duraklatıldı, profil oluşturma verilerinin inceleyin.

**CPU kullanımı** görünüm işlevlerin üst uzun süre çalışan işleviyle en uzun çalışan göre sıralanmış bir listesini gösterir. Bu durum, performans sorunlarını gerçekleştiği işlevler Kılavuzu yardımcı olabilir.

![Tanılama araçları CPU Kullanımı görünümü](../profiling/media/prof-tour-cpu-usage.png "tanılama araçları CPU kullanımı")

İlgilendiğiniz, ve seçili işlev çağıran işlev sol taraftaki pencerede ortasında daha ayrıntılı bir "Kelebek" bölmesinde üç görünüm görürsünüz ve işlevleri sağ tarafta adlı bir işlev çift tıklayın. **İşlev gövdesi** süresi (ve zamanı yüzdesi) işlev gövdesinde harcanan süre hariç toplam miktarı harcanan içinde arama ve işlevlerin çağrılma bölümünde gösterilir. Bu veriler işlevi bir performans sorunu olup olmadığını değerlendirmeniz yardımcı olabilir.

![Tanılama araçları çağıran ve çağrılan "Kelebek" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "tanılama araçları arayan Aranan görünümü")

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

**Tanılama araçları** pencere ayrıca uygulamanızda bellek kullanımı değerlendirmek olanak tanır. Örneğin, sayı ve nesnelerin boyutunu yığında bakabilirsiniz. Daha ayrıntılı bellek analiz etmek için yönergeler için bkz. [bellek kullanımını analiz etme](../profiling/memory-usage.md).

Bellek kullanımı çözümlemek için hata ayıklama sırasında en az bir bellek anlık görüntüsünü almak gerekir. Genellikle, bellek analiz etmek için en iyi iki anlık görüntü almak için yoludur; ilk hemen bir tespit edildiğinde alınan önlemlerin bir bellek sorunu önce ve bir tespit edildiğinde alınan önlemlerin bir bellek sorunu gerçekleştikten sonra ikinci bir anlık görüntü sağ. Ardından bir iki anlık görüntü görüntüleyebilir ve tam olarak nelerin değiştiğini görmek.

![Tanılama araçları penceresindeki anlık](../profiling/media/prof-tour-take-snapshots.gif "tanılama araçları ele anlık görüntüleri")

Ok bağlantılardan birini seçtiğinizde, yığın farklı bir görünüm sunulur (kırmızı yukarı ok ![bellek artırmalarını](../profiling/media/prof-tour-mem-usage-up-arrow.png "bellek artırmalarını") (solda) artan bir nesne sayısı veya bir artırma gösterir yığın boyutu (sağdaki)). Doğru bağlantıya tıklarsanız, yığın boyutu en çok artırılmış nesneleri göre sıralanmış bir fark yığın görünümü açılır. Bu, bellek sorunlarını belirlemenize yardımcı olabilir. Örneğin, aşağıdaki çizimde, bayt tarafından kullanılan `ClassHandlersStore` 3,492 bayt ikinci anlık artış nesneleri.

![Tanılama araçları yığın fark görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "tanılama araçları yığın fark görünümü")

Sol taraftaki bağlantı yerine tıkladığınızda **bellek kullanımı** görünümü, yığın görünümü nesne sayısına göre düzenlenmiştir; en çok daha fazla belirli bir türdeki nesneler en üstünde gösterilir (sıralama ölçütü **sayısıfarkı** sütunu).

## <a name="examine-performance-events"></a>Performans olaylarını inceleyin

**Olayları** Görünümü'nde tanılama araçları size, bir kesme noktası veya bir kod adımlamaya işlemin ayarı gibi hata ayıklama sırasında gerçekleşen farklı olayları gösterir. (Hata ayıklayıcının en son ne zaman duraklatıldı ya da uygulama başladığında ölçülür) olay süresi gibi bilgileri kontrol edebilirsiniz. Örneğin, (F10, F11), kodunuz içinde adım adım **olayları** görünümü geçerli adım için önceki adımı işlemi uygulama çalışma zamanı süresi gösterilir.

![Tanılama araçları olayları görüntülemek](../profiling/media/prof-tour-events.png "tanılama araçları olaylarını görüntüle")

 > [!NOTE]
 > Visual Studio Enterprise yüklüyse, atabilirsiniz [IntelliTrace olayları](../debugger/intellitrace.md) bu sekmede.

Aynı olayları da PerfTips görüntüleyebileceğiniz Kod düzenleyicisinde gösterilir.

![Profil oluşturma turu PerfTips](../profiling/media/prof-tour-perf-tips.png "turu PerfTips profil oluşturma")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performansını ve erişilebilirliğini olayları (UWP) inceleyin

UWP uygulamalarınızda etkinleştirebilirsiniz **UI analizi** içinde **tanılama araçları** penceresi. Aracı için genel performans veya erişilebilirlik sorunları arar ve bunları görüntüler **olayları** ayıklarken görüntüleyin. Olay açıklamaları sorununu çözmeye yardımcı olan bilgiler sağlar.

![Tanılama araçları penceresindeki UI analizi olayları görüntülemek](../profiling/media/prof-tour-ui-analysis.png "tanılama araçları görünümü UI analizi olayları")

## <a name="post_mortem"></a> Hata Ayıklayıcı olmadan profil yayın derlemeleri

Profil oluşturma araçlarında CPU kullanımı ve bellek kullanımı hata ayıklayıcısı ile kullanılan gibi (önceki bölümlere göz atın) veya profil oluşturma araçları için analiz sağlamaya yönelik performans Profiler'ı kullanarak son İnceleme çalıştırabileceğiniz **yayın** oluşturur . Performans Profiler içinde uygulama çalışırken, tanılama bilgilerini toplamak ve uygulama durdurulduktan sonra toplanan bilgileri inceleyin. Bu farklı yaklaşımların hakkında daha fazla bilgi için bkz. [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Performans Profiler](../profiling/media/prof-tour-performance-profiler.png "performans Profiler")

Performans Profiler seçerek açın **hata ayıklama** > **performans Profiler**.

Pencerenin birden fazla profil oluşturma araçları, bazı senaryolarda seçmenize olanak sağlar. CPU kullanımı gibi araçlar, analizi yardımcı olmak için kullanabileceğiniz tamamlayıcı veriler sağlayabilir.

## <a name="analyze-resource-consumption-xaml"></a>(XAML) kaynak tüketimini analiz etme

Windows Masaüstü WPF uygulamaları ve UWP uygulamaları gibi XAML uygulamalarında, uygulama zaman çizelgesi Aracı'nı kullanarak kaynak tüketimini analiz edebilirsiniz. Örneğin, (Düzen ve işleme), UI çerçevelerinin hazırlanması ve ağ ve disk isteklerine hizmet, uygulama tarafından harcanan süre analiz edin ve uygulama başlatma gibi senaryolarda, sayfa yükleme ve pencereyi yeniden boyutlandırma. Aracı'nı kullanmayı tercih **uygulama zaman çizelgesi** performans Profiler içinde seçip **Başlat**. Uygulamanızda, şüpheli kaynak tüketimi sorunu senaryosuyla inceleyin ve ardından **koleksiyonu Durdur** raporu oluşturmak için.

Düşük içinde framerates **görsel üretilen iş** graf karşılık uygulamanızı çalışırken görmek için görsel sorunları. Benzer şekilde, içinde yüksek numaralar **UI iş parçacığı kullanımı** grafik kullanıcı Arabirimi yanıt hızı sorunlarını da karşılık. Raporda tespit edildiğinde alınan önlemlerin bir performans sorunu bir süre seçin ve zaman çizelgesi Ayrıntıları görünümünde (alt bölme) ayrıntılı kullanıcı Arabirimi iş parçacığı etkinliklerini inceleyin.

![Uygulama zaman çizelgesi aracı profil oluşturma](../profiling/media/prof-tour-application-timeline.gif "turu uygulama zaman çizelgesi profil oluşturma")

Zaman Çizelgesi Ayrıntıları görünümünde, etkinlik süresi birlikte activitiy türünü (veya UI öğesi dahil) gibi bilgileri bulabilirsiniz. Örneğin, şekildeki bir **Düzen** olay için bir kılavuz denetimi 57.53 ms alır.

Daha fazla bilgi için [uygulama zaman çizelgesi](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>(Direct3D) GPU kullanımını analiz etme

Direct3D uygulamalar (Direct3D bileşenleri c++'ta olması gerekir), GPU üzerinde etkinlik inceleyebilir ve performans sorunlarını analiz edin. Daha fazla bilgi için [GPU kullanımı](../debugger/gpu-usage.md). Aracı'nı kullanmayı tercih **GPU kullanımı** performans Profiler içinde seçip **Başlat**. Uygulamanızda, profil oluşturma ilginizi çeken senaryo inceleyin ve ardından **koleksiyonu Durdur** bir rapor oluşturabilirsiniz.

Ne zaman, bir zaman dönemi grafiklerde seçip **ayrıntıları görüntüle**, ayrıntılı bir görünüm alt bölmede görünür. Ayrıntılı görünümde, her CPU ve GPU üzerinde ne kadar etkinlik gerçekleştiği inceleyebilirsiniz. Açılan pencereler zaman çizelgesinde almak için en düşük bölmesinde olayları seçin. Örneğin, seçin **mevcut** görüntülemek için olay **mevcut** açılan pencereler çağırın. (Açık gri dikey Vsync çizgiler belirli olmadığını anlamak için referans olarak kullanılabilir **mevcut** çağrıları Vsync eksik. Olmalıdır **mevcut** gelinceye 60 FPS isabet her iki Vsyncs arasında uygulama için sırayla çağırın.)

![GPU kullanımı aracı profil oluşturma](../profiling/media/prof-tour-gpu-usage.png "Diag GPU kullanımı")

Grafikler, CPU'ya vardır veya performans sorunlarını GPU bağlı olup olmadığını belirlemek için de kullanabilirsiniz.

## <a name="analyze-performance-javascript-uwp"></a>(JavaScript UWP) performansını çözümleme

UWP uygulamaları için JavaScript bellek aracı ve HTML kullanıcı Arabirimi yanıt hızı Aracı'nı kullanabilirsiniz.

JavaScript bellek aracı diğer uygulama türleri için kullanılabilir bellek kullanımı aracı benzer. Bellek kullanımını anlamak ve uygulamanızda bellek sızıntılarını bulmak için bu aracı kullanabilirsiniz. Araç hakkında daha fazla ayrıntı için bkz. [JavaScript belleği](../profiling/javascript-memory.md).

![JavaScript bellek profil oluşturma aracı](../profiling/media/diagjsmemory.png "DiagJSMemory")

UI yanıtlama hızı, yükleme süresi ve yavaş görsel güncelleştirmeleri UWP uygulamalarında yavaş tanılamak için HTML kullanıcı Arabirimi yanıt hızı Aracı'nı kullanın. Kullanım, diğer uygulama türleri için uygulama zaman çizelgesi Aracı'nı benzerdir. Daha fazla bilgi için [HTML UI yanıtlama hızı](../profiling/html-ui-responsiveness.md).

![HTML kullanıcı Arabirimi yanıt hızı aracı profil oluşturma](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>(UWP) ağ kullanımını analiz etme

UWP uygulamalarında kullanılarak yapılan ağ işlemlerini çözümleyebilirsiniz `Windows.Web.Http` API. Bu araç, erişim ve kimlik doğrulaması ile ilgili sorunlar, yanlış önbellek kullanımı ve görüntü gibi sorunları çözmek ve indirme performansını size yardımcı olabilir. Aracı'nı kullanmayı tercih **ağ** performans Profiler içinde seçip **Başlat**. Uygulamanızda kullandığı senaryosuyla Git `Windows.Web.Http`ve ardından **koleksiyonu Durdur** raporu oluşturmak için.

![Ağ kullanımı aracı profil oluşturma](../profiling/media/prof-tour-network-usage.png "Diag ağ kullanımı")

Bir işlem içinde Özet görünümünü için daha fazla ayrıntı'ı seçin.

![Ayrıntılı bilgi ağ kullanımı aracında](../profiling/media/prof-tour-network-usage-details.png "Diag ağ kullanım ayrıntıları")

Daha fazla bilgi için [ağ kullanımını](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>(Eski araçları) performansını çözümleme

CPU kullanımı veya bellek kullanımı araçları şu anda mevcut olmayan özellikleri gibi araçları gerekir ve Masaüstü ya da ASP.NET uygulamaları çalıştırıyorsanız, profil oluşturma için performans Gezgini kullanabilirsiniz. (UWP uygulamalarında desteklenmez). Daha fazla bilgi için bkz. [performans Gezgini](../profiling/performance-explorer.md).

![Performans Gezgini aracını](../profiling/media/prof-tour-performance-explorer.png "performans Gezgini")

## <a name="which-tool-should-i-use"></a>Hangi aracı kullanmalıyım?  

Farklı araçlar sunan Visual Studio listeleyen bir tablo işte ve farklı proje türleri ile kullanabilirsiniz:
  
|Performans aracı|Windows Masaüstü|UWP|ASP.NET/ASP.NET çekirdek| 
|----------------------|---------------------|-------------|-------------|  
|[CPU Kullanımı](../profiling/cpu-usage.md)|Evet|Evet|Evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|Evet|Evet|Evet| 
|[GPU Kullanımı](../debugger/gpu-usage.md)|Evet|Evet|Yok| 
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|Evet|Evet|Yok|
|[PerfTips](../profiling/perftips.md)|Evet|XAML, HTML için Hayır için Evet|Evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|Evet|Yok|Evet|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise ile .NET|Yalnızca Visual Studio Enterprise ile .NET|Yalnızca Visual Studio Enterprise ile .NET|
|[Ağ Kullanımı](../profiling/network-usage.md)|Yok|Evet|Yok|
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|Yok|Evet, HTML için XAML için Hayır|Yok| 
|[JavaScript Belleği](../profiling/javascript-memory.md)|Yok|Evet, HTML için XAML için Hayır|Yok|

## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)
