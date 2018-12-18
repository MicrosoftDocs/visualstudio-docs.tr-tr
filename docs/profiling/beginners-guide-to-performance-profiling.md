---
title: Uygulamalarınızda ölçü CPU kullanımı
description: CPU hata ayıklayıcısıyla tümleştirilmiş tanılama araçları kullanarak uygulamanızdaki performans sorunlarını analiz edin.
ms.custom: seodec18
ms.date: 02/27/2017
ms.technology: vs-ide-debug
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46837bb68854f0f5dbb5c799d405c37431f6c379
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065768"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>CPU kullanımını analiz etme ölçü uygulama performansı
Visual Studio profil oluşturma araçları, uygulamanızdaki performans sorunlarını analiz etmek için kullanabilirsiniz. Bu yordam, nasıl kullanılacağını gösterir **CPU kullanımı** tanılama araçları, uygulamanız için performans verilerini almak için sekmesinde. Tanılama araçları, yerel/C++ geliştirme ve ASP.NET dahil olmak üzere Visual Studio .NET geliştirme için desteklenir.
  
Hata ayıklayıcı zaman duraklatır, **CPU kullanımı** aracı, uygulamanızda yürütülen işlevler hakkında bilgi toplar. Aracı işleri yapan işlevleri listeler ve örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

Tanılama hub'ı, çok sayıda çalıştırın ve tanılama oturumunuzu yönetmek için diğer bir seçenek sunar. Varsa **CPU kullanımı** duyduğunuz verileri sağlamazsa [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) farklı türde size yardımcı olabilecek bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorunu, CPU, bellek, işleme kullanıcı Arabirimi veya ağ isteği süresi gibi dışında bir şey tarafından kaynaklanabilir. Tanılama hub'ı, çok sayıda kaydedin ve bu tür verilerin analiz etmek için diğer bir seçenek sunar.

| | |
|---------|---------|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) CPU kullanımını analiz etme ve bellek kullanımını analiz etme gösteren tanılama araçlarını kullanma. |

Bu makalede, normal, hata ayıklama iş akışından çözümlenirken CPU kullanımının açıklayacağız. CPU kullanımı eklenmiş bir hata ayıklayıcı olmadan veya - daha fazla bilgi için çalışan bir uygulamanın hedefleyerek çözümleyebilirsiniz [hata ayıklama olmadan profil oluşturma verisi toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) içinde [profil oluşturma araçları ile veyaHataAyıklayıcıolmadançalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Windows 7 ve daha sonra hata ayıklayıcı olmadan profil oluşturma araçları kullanabilirsiniz. Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere).

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * CPU kullanım verileri toplama
> * CPU kullanım verilerini çözümleme
  
## <a name="step-1-collect-profiling-data"></a>1. adım: profil oluşturma verilerini topla 
  
1.  Visual Studio'da hata ayıklama ve CPU kullanımını incelemek için istediğiniz noktada uygulamanızda bir kesme noktası ayarlamak istediğiniz projeyi açın.

2.  İşlev veya bölge analiz etmek istediğiniz kodu sonunda ikinci bir kesme noktası ayarlayın.

    > [!TIP]
    > İki kesme noktaları ayarlayarak veri toplamayı çözümlemek istediğiniz kod parçalarını sınırlayabilirsiniz.
  
3.  **Tanılama araçları** penceresi görünür otomatik olarak, bunu devre dışı bırakmış sürece. Pencereyi ayarlayıp yeniden getirmek için tıklayın **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**.

4.  Görmek isteyip istemediğinizi seçebilirsiniz **CPU kullanımı**, [bellek kullanımı](../profiling/Memory-Usage.md), veya her ikisi de ile **seçtiğiniz Araçları** araç ayarlama. Visual Studio Enterprise çalıştırıyorsanız, ayrıca etkinleştirebilir veya IntelliTrace içinde devre dışı **Araçları** > **seçenekleri** > **IntelliTrace**.

     ![Tanılama araçlarını Göster](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     Biz esas olarak CPU kullanımı bakarak olması, bu nedenle emin olun **CPU kullanımı** etkin (varsayılan olarak etkindir).

5.  Tıklayın **hata ayıklama** > **hata ayıklamayı Başlat** (veya **Başlat** araç çubuğunda veya **F5**).

     Uygulamanın yüklenmesi tamamlandığında, Tanılama Araçları'nın Özet görünümü görüntülenir.

     ![Tanılama araçları Özet sekmesi](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     Olaylar hakkında daha fazla bilgi için bkz. [arama ve filtreleme tanılama araçları penceresinin olaylar sekmesinde](https://blogs.msdn.microsoft.com/devops/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6.  İlk kesme noktasına ulaşılmasına neden olacak senaryo çalıştırın.

7.  Hata Ayıklayıcı duraklatılmış durumdayken, CPU kullanım verileri toplamayı etkinleştirin ve ardından açın **CPU kullanımı** sekmesi.

     ![Tanılama araçları, CPU profili oluşturmayı etkinleştir](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     Seçeneğini belirlediğinizde **kayıt CPU profili**, Visual Studio, işlevlerinizin kaydı başlayacak ve aldıkları yürütmek için ne kadar süre. Uygulamanız bir kesme noktasında durdurulur, yalnızca bu toplanan verileri görüntüleyebilirsiniz.

8.  Uygulamayı, ikinci bir kesme noktasına kadar çalıştırmak için F5'e basın.

     Şimdi, artık performans verileri bölge için özellikle uygulamanız iki kesme noktaları arasında çalışan kod için var.

9.  CPU zaman çizelgesinde analiz ilgi bölgesi seçin (gösteren bir bölge olmalıdır profil oluşturma verilerini).

     ![Tanılama araçları zaman diliminin seçerek](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     Profil Oluşturucu, iş parçacığı veri hazırlama başlar. Bitmesini bekleyin.

     ![Tanılama araçları iş parçacıkları hazırlanıyor](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     CPU kullanımı aracı raporda görüntüler **CPU kullanımı** sekmesi.
  
     ![Tanılama araçları CPU kullanımı sekmesinde](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     Bu noktada, verileri çözümlemek başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. adım: CPU kullanım verilerini çözümleme

CPU kullanımı altında işlevler listesini inceleyerek, en fazla çalışmayı yapan işlevleri tanımlama ve ardından her birine daha yakından bakalım alma verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en fazla çalışmayı yapan işlevler inceleyin.

    ![Tanılama araçları CPU kullanımı işlev listesi](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > İşlevler, en fazla çalışmayı yapan olanlar başlayarak sırayla listelenir (çağrı sırayla olmadıklarını). Bu, uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde çok fazla iş yapıyor uygulama işlevlerinizi birine çift tıklayın.

    Bir işlev çift tıkladığınızda **çağıran/çağrılan** görünümü sol bölmede açılır. 

    ![Tanılama araçları arayan-Aranan görünümü](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    Bu görünümünde seçili işlev hem de başlığında gösterilir **geçerli işlevin** kutusunu (Bu örnekte, GetNumber). Geçerli işlevi çağıran işleve sol altında gösterilen **işlevi çağırma**, ve geçerli işlev tarafından çağrılan tüm işlevleri gösterilir **çağrılan işlevlerin** sağdaki kutuya. (Geçerli işlevin değiştirmek için ya da kutusunu seçebilirsiniz.)

    Bu görünüm, toplam süre (ms) ve genel uygulamayı işlevi tamamlamak için gerçekleştirdiği zaman yüzdesini gösterir.
    **İşlev gövdesi** ayrıca süresi (ve zamanı yüzdesi) işlev gövdesinde harcanan süre hariç toplam miktarı harcanan içinde arama ve işlevlerin çağrılma gösterilmektedir. (Bu örnekte, işlev gövdesinde 3713 tanesi 3729 ms harcanan ve kalan 16 ms, bu işlev tarafından çağırılan dış kodunda harcanan).

    > [!TIP]
    > Yüksek değerleri **işlev gövdesi** işlevin kendisi içinde bir performans engelini işaret edebilir.

3. Hangi işlevleri çağrılan, select sırayı gösteren bir üst düzey görmek istiyorsanız **çağrı ağacı** Bölmenin üst kısmındaki açılan listeden.
 
    Şekildeki her numaralı alan yordamdaki bir adımda ilgilidir.
  
    ![Tanılama araçları çağrı ağacı](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![1. adım](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU kullanımı çağrı ağaçları en üst düzey düğüm sözde düğümüdür|  
|![2. adım](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Çoğu uygulama, zaman [harici kodu Göster](#view-external-code) seçeneği devre dışıdır, ikinci düzey düğüm bir **[harici kod]** başlatır ve durdurur, uygulamanın sistem ve framework kodu içeren bir düğüm UI çizer iş parçacığı zamanlama denetler ve uygulamayı diğer alt düzey hizmetler sağlar.|  
|![3. adım](../profiling/media/ProcGuid_3.png "ProcGuid_3")|İkinci düzey düğümünün alt öğeleri, kullanıcı kodu yöntemleri ve çağrılan veya framework kodu ve ikinci düzey sistem tarafından oluşturulan zaman uyumsuz yordamlarını verilmiştir.|
|![4. adım](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntem çağrıları için veri içerir. Zaman **harici kodu Göster** olduğundan devre dışı, uygulama yöntemlerini de içerebilir bir **[harici kod]** düğümü.|

Sütun değerleri hakkında daha fazla bilgi aşağıda verilmiştir:

- **Toplam CPU** işlevi ve olarak adlandırılan her türlü işlev ne kadar iş yapıldığı gösterir. Toplam CPU yüksek, genel olarak en pahalı olduğunu işaret eder.
  
- **İç CPU** tarafından çağrılan işlevler tarafından yapılan iş hariç işlev gövdesindeki kod tarafından ne kadar iş yapıldığı gösterir. Yüksek **Self CPU** değerleri işlevin kendisi içinde bir performans sorunu olduğunu gösteriyor olabilir.

- **Modüller** işlev veya bir [harici kod] düğümünde işlevler içeren modül sayısı içeren modülünün adı.

## <a name="view-external-code"></a>Dış Kodu Göster

Dış kod yazdığınız kod tarafından yürütülen sistem ve framework bileşenlerinin işlevleri olan. Dış kod Başlat ve uygulamayı durdurun, UI çizme, iş parçacığı oluşturma denetleyen ve uygulama diğer alt düzey hizmetler sağlayan işlevler içerir. Çoğu durumda, dış kodda ilgilenen olmayacaktır, ve bu nedenle CPU kullanımı aracı toplayan harici işlevler kullanıcı yönteminin birine **[harici kod]** düğümü.
  
Dış kod arama yollarını görüntülemek istiyorsanız, seçin **harici kodu Göster** gelen **filtre görünümü** listeleyin ve ardından **Uygula**.  
  
![Filtre görünümü seçin, ardından dış Kodu Göster](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
Böylece işlev adı sütun genişliğini tüm bilgisayar monitörü en büyük görüntü genişliğini aşabilir birçok dış kod arama zincirleri iç içe girmiş olduğunu, unutmayın. Bu durumda, işlev adları olarak gösterilir **[...]** .
  
Aradığınız bir düğüm bulmak için arama kutusunu kullanın ve ardından verilerin görüntülenebilmesi için yatay kaydırma çubuğunu kullanın.

> [!TIP]
> Windows işlevlerini çağıran dış kod yazıyorsanız, en güncel olduğundan emin olun. *pdb* dosyaları. Bu dosyalar olmadan rapor görünümleriniz karmaşık ve anlaşılması zor olan Windows işlev adlarını listeler. Gereksinim duyduğunuz dosyaların bilgisayarınızda yüklü olduğundan emin olma hakkında daha fazla bilgi için bkz. [hata ayıklayıcıda sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, CPU kullanımı verilerini toplamanıza ve analiz öğrendiniz. Tamamladıysanız [araçları profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md), uygulamalarınızdaki bellek kullanımını analiz etme nasıl hızlı bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio’da bellek kullanımının profilini oluşturma](../profiling/memory-usage.md) 
