---
title: CPU kullanımı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af6d58ac5cd87523124d567e36559a82d69ddfc6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810539"
---
# <a name="cpu-usage"></a>CPU kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki performans sorunlarını araştırmak gerektiğinde başlatmak için iyi bir yerdir, CPU kullanma anlamaktır. **CPU kullanımı** aracı gösterir, burada CPU, Visual C++, Visual C# ' ı yürütürken zaman harcadığı yerleri / Visual Basic ve JavaScript kodu.  
  
 Visual Studio 2015 güncelleştirme 1'de başlayarak, hata ayıklayıcı çıkmadan bir işlev başına kırılımını CPU kullanımının görebilirsiniz. Hata ayıklama sırasında CPU açıp profil açın ve yürütme, örneğin bir kesme noktasında kesildiğinde sonuçları görüntüleyin. Daha fazla bilgi için [Visual Studio 2015'te Hata Ayıklayıcısı'nda CPU profilinizi](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/profile-your-cpu-in-the-debugger-in-visual-studio-2015.aspx).  
  
 Bir Windows Store uygulaması performansını analiz eden bir kılavuz için bkz. [Store uygulamalarında CPU kullanımını analiz](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Performans ve tanılama hub'ı bu, çok sayıda çalıştırın ve tanılama oturumunuzu yönetmek için diğer bir seçenek başına sunar. Örneğin, çalıştırabileceğiniz **CPU kullanımı** aracı yerel veya uzak makinelerde veya açık bir simülatörü veya öykünücü. Visual Studio, çalışan bir uygulama için bağlı açık bir projedeymiş performansını analiz veya Windows Store ' yüklü olduğu bir uygulamayı başlatın. Daha fazla bilgi için [hata ayıklama olmadan profil oluşturma araçları çalıştırma](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> CPU kullanım verileri toplama  
  
1. Visual Studio'da çözüm yapılandırması ayarlanmış **yayın** ve dağıtım hedefini seçin.  
  
    ![Yayın ve yerel makine seçin](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   -   Uygulamayı çalışır durumda **yayın** modu gerçek uygulamanızın performansını daha iyi bir görünümünü sağlar.  
  
   -   Uygulamayı yerel makinede en iyi çalışan yüklü uygulama yürütülmesini çoğaltır.  
  
   -   Uzak bir CİHAZDAN veri topluyorsanız, uygulamayı doğrudan cihazda ve Uzak Masaüstü bağlantısı kullanarak değil çalıştırın.  
  
   -   Windows Phone uygulamaları için doğrudan veri toplama **cihaz** en doğru veriler sağlar.  
  
2. Üzerinde **hata ayıklama** menüsünde seçin **performans Profiler...** .  
  
3. Seçin **CPU kullanımı** seçip **Başlat**.  
  
    ![CPU kullanımı seçin](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. Uygulama başlatıldığında tıklayın **alma sınırı**. Çıkış görüntülendikten sonra ikinci bir bekleyin ve ardından **alma en fazla sayı Async**. Düğme tıklamaları yapar bekleyen düğme yalıtmak daha kolay tıklayın tanılama raporu yordamları.  
  
5. İkinci çıktı satırı göründükten sonra seçin **toplamasını Durdur** performans ve tanılama hub'ında.  
  
   ![CpuUsage veri toplamayı Durdur](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   CPU kullanımı aracı verileri çözümler ve rapor görüntüler.  
  
   ![CpuUsage rapor](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>CPU kullanımı raporunu analiz etme  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> CPU kullanımı çağrı ağacı  
 Çağrı ağacı bilgileri anlama kullanmaya başlamak için yeniden `GetMaxNumberButton_Click` segmentlere ayırın ve çağrı ağacı ayrıntılarını inceleyin.  
  
####  <a name="BKMK_Call_tree_structure"></a> Çağrı ağacı yapısı  
 ![GetMaxNumberButton&#95;tıklayın çağrı ağacı](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![1. adım](../profiling/media/procguid-1.png "ProcGuid_1")|CPU kullanımı çağrı ağaçları en üst düzey düğüm sözde düğümüdür|  
|![2. adım](../profiling/media/procguid-2.png "ProcGuid_2")|Çoğu uygulama, zaman **harici kodu Göster** seçeneği devre dışıdır, ikinci düzey düğüm bir **[harici kod]** başlatır ve durdurur, uygulamanın sistem ve framework kodu içeren bir düğüm UI çizer iş parçacığı zamanlama denetler ve uygulamayı diğer alt düzey hizmetler sağlar.|  
|![3. adım](../profiling/media/procguid-3.png "ProcGuid_3")|İkinci düzey düğümünün alt öğeleri, kullanıcı kodu yöntemleri ve çağrılan veya framework kodu ve ikinci düzey sistem tarafından oluşturulan zaman uyumsuz yordamlarını verilmiştir.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntem çağrıları için veri içerir. Zaman **harici kodu Göster** olduğundan devre dışı, uygulama yöntemlerini de içerebilir bir **[harici kod]** düğümü.|  
  
####  <a name="BKMK_External_Code"></a> Dış kod  
 Dış kod olan sistem ve framework bileşenleri işlevlerde yazdığınız kod tarafından yürütülür. Dış kod Başlat ve uygulamayı durdurun, UI çizme, iş parçacığı oluşturma denetleyen ve uygulama diğer alt düzey hizmetler sağlayan işlevler içerir. Çoğu durumda, dış kod içinde olacak ve bu nedenle CPU kullanımı çağırma ağacı toplar harici işlevler kullanıcı yöntemi birine **[harici kod]** düğümü.  
  
 Dış kod arama yollarını görüntülemek istediğinizde seçin **harici kodu Göster** gelen **filtre görünümü** listeleyin ve ardından **Uygula**.  
  
 ![Filtre görünümü seçin, ardından dış Kodu Göster](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Böylece işlev adı sütun genişliğini tüm bilgisayar monitörü en büyük görüntü genişliğini aşabilir birçok dış kod arama zincirleri iç içe girmiş olduğunu, unutmayın. Bu durumda, işlev adları olarak gösterilir **[...]** :  
  
 ![Çağrı ağacında dış kod iç içe geçmiş](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Aradığınız bir düğüm bulmak için arama kutusunu kullanın ve ardından verilerin görüntülenebilmesi için yatay kaydırma çubuğunu kullanın:  
  
 ![İç içe geçmiş bir dış kod arama](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Ağaç veri sütunları arayın  
  
|||  
|-|-|  
|**Toplam CPU (%)**|![Toplam % veri Denklem](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Seçili zaman aralığındaki işlevi ve işlev tarafından çağırılan işlevlerde yapılan çağrılar tarafından kullanılan uygulamanın CPU etkinliği yüzdesi. Bu farklı olduğunu unutmayın **CPU kullanımı** toplam etkinlik uygulamanın toplam kullanılabilir CPU kapasitesi için bir zaman aralığında karşılaştıran zaman çizelgesi grafiği.|  
|**Kendi kendine CPU (%)**|![Kendi kendine % Denklem](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağırılan işlevlerdeki etkinlik hariç bu işleve yapılan çağrılar tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliği yüzdesi.|  
|**Toplam CPU (ms)**|Seçili zaman aralığındaki işlevi ve işlev tarafından çağrılan işlevler çağrılarında harcanan milisaniye sayısı.|  
|**Kendi kendine CPU (ms)**|Seçili zaman aralığındaki işlevi ve işlev tarafından çağrılan işlevler çağrılarında harcanan milisaniye sayısı.|  
|**Module**|İşlev veya bir [harici kod] düğümünde işlevler içeren modül sayısı içeren modül adı.|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Zaman uyumsuz işlevleri CPU kullanımına çağrı ağacı  
 Derleyici, zaman uyumsuz bir yöntem karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, derleyicinin ürettiği işlevleri, özgün metodun işlemlerini zaman uyumsuz olarak çağırın ve geri çağırmaları, Zamanlayıcı ve bunları doğru gerekli yineleyiciler listesini içeren bir durum makinesindeki bir sınıftır. Özgün yöntemi tarafından bir üst yöntem çağrıldığında, çalışma zamanı üst yürütme bağlamında yöntemi kaldırır ve gizli sınıfı yöntemleri uygulamanın yürütmesini denetlemek sistem ve framework kod bağlamında çalışır. Zaman uyumsuz yöntemler genellikle, ancak her zaman, bir veya daha fazla farklı iş parçacıkları üzerinde yürütülür. Bu kod CPU kullanımı çağrı ağacında altı olarak gösterilen **[harici kod]** düğümünün üst ağaç düğümünü hemen altındaki.  
  
 Bu örneğimizde görmek için yeniden seçin `GetMaxNumberAsyncButton_Click` zaman çizelgesi segmenti.  
  
 ![GetMaxNumberAsyncButton&#95;tıklayın rapor seçim](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 İlk iki düğüm altında **[harici kod]** durum makine sınıfın derleyici tarafından oluşturulan yöntemler. Üçüncü özgün yöntem çağrısı var. Oluşturulan yöntemler genişletme neler olduğunu gösterir.  
  
 ![GetMaxNumberAsyncButton Genişletilmiş&#95;tıklayın çağrı ağacı](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` çok az yapar; Görev değerlerin bir listesini yönetir, en fazla sonuçları hesaplar ve çıktıyı görüntüler.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zamanlama ve çağrısını sarmalamak 48 görevleri başlatmak için gereken etkinlik gösterir `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` çağıran görevler etkinliğini gösterir `GetNumber`.



