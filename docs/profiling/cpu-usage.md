---
title: CPU kullanımını analiz etme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b3d4d6a352d2ff1b71796d64c34992af493867a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063269"
---
# <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme 

Uygulamanızdaki performans sorunlarını araştırma başlatmak için en iyi yolu, CPU kullanımını öğrenmektir. **CPU kullanımı** performans aracını, CPU süresini gösterir ve yüzdesi, c++ kodu yürütürken harcanan C#/Visual Basic ve JavaScript uygulamaları. 

**CPU kullanımı** yüklü olan bir Microsoft Store uygulamasında açık bir Visual Studio projesini çalıştırın ya da çalışan bir uygulama veya işlem bağlı aracını kullanabilirsiniz. Yerel veya uzak makinelerde veya öykünücü veya simülatör aracı çalıştırabilirsiniz. Daha fazla bilgi için [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Çalıştırabileceğiniz **CPU kullanımı** aracı ile veya hata ayıklama olmadan. Hata ayıklayıcıda açıp kapatmak, CPU profili oluşturma ve işlev başına CPU kullanımı dökümünü görmek. Yürütme, örneğin bir kesme noktasında duraklatıldığında CPU kullanımı sonuçlarını görüntüleyebilirsiniz.  

Aşağıdaki yönergeler nasıl kullanılacağını göstermektedir **CPU kullanımı** aracını kullanarak Visual Studio hata ayıklayıcı olmadan **performans Profiler**. Örnekler, yerel makine üzerinde bir yayın yapısı kullanır. Yayın derlemeleri gerçek uygulama performansını en iyi görünümünü sağlar. Hata ayıklama yapıları ile CPU kullanımını analiz etme hakkında bilgi için bkz: [performans profili oluşturma Başlangıç Kılavuzu](../profiling/beginners-guide-to-performance-profiling.md).

Genellikle, yerel makine en iyi yüklü uygulama yürütme çoğaltır. Windows Phone uygulamaları için en doğru veriler doğrudan CİHAZDAN veri toplamayı sağlar. Uzak bir CİHAZDAN veri toplamak için Uzak Masaüstü Bağlantısı değil bir uygulamayı doğrudan cihazda çalıştırın. 

>[!NOTE]
>Windows 7 veya üzerini kullanmak için gerekli [performans Profiler](../profiling/profiling-feature-tour.md).
  
##  <a name="collect-cpu-usage-data"></a>CPU kullanım verileri toplama  
  
1. Visual Studio projesinde çözüm yapılandırması ayarlanmış **yayın** seçip **yerel makine** dağıtım hedefi olarak.  
  
    ![Yayın ve yerel makine seçin](../profiling/media/cpuuse_selectreleaselocalmachine.png "sürüm ve yerel makine seçin")  
  
1. Seçin **hata ayıklama** > **performans Profiler**.  
  
1. Altında **kullanılabilir Araçları**seçin **CPU kullanımı**ve ardından **Başlat**.  
  
    ![CPU kullanımı seçin](../profiling/media/cpuuse_lib_choosecpuusage.png "CPU kullanımı seçin")  
  
4. Uygulama başlatıldıktan sonra Tanılama oturumu başlatır ve CPU kullanım verilerini görüntüler. Veri toplamayı tamamladığınızda, seçin **toplamasını Durdur**.  
  
   ![CPU kullanım verilerini toplamayı Durdur](../profiling/media/cpu_use_wt_stopcollection.png "Durdur CPU kullanım verileri toplama")  
  
   CPU kullanımı aracı verileri çözümler ve rapor görüntüler.  
  
   ![CPU kullanım raporu](../profiling/media/cpu_use_wt_report.png "CPU kullanım raporu")  
  

## <a name="analyze-the-cpu-usage-report"></a>CPU kullanımı raporunu analiz etme  
  
Tanılama raporu kendisine göre sıralandığı **toplam CPU**, yüksekten en düşüğe. Sütun üst bilgilerini seçerek sıralama sütunu ve sıralama düzenini değiştirin. Kullanın **filtre** görüntülemek ve kullanmak için iş parçacığı seçimini kaldırın veya seçmek için açılan **arama** belirli iş parçacığı veya düğüm için arama kutusu. 

###  <a name="BKMK_Call_tree_data_columns"></a> CPU kullanımı veri sütunları  

|||  
|-|-|  
|**Toplam CPU [Birim, %]**|![Toplam % veri Denklem](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Milisaniye ve CPU yüzdesi işlev için çağrılar tarafından kullanılan ve seçili zaman aralığında işlev tarafından çağrılan işlevleri. Bu farklıdır **CPU kullanımı** karşılaştıran bir zaman aralığında bir toplam kullanılabilir CPU için toplam CPU etkinliği zaman çizelgesi grafiği.|  
|**İç CPU [Birim, %]**|![Kendi kendine % Denklem](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> CPU yüzdesi seçili zaman aralığındaki işlev tarafından çağrılan işlevler hariç işlev için çağrılar tarafından kullanılan ve milisaniye.|  
|**Module**|İşlevi içeren modül adı.   
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> CPU kullanımı çağrı ağacı 

Çağrı ağacı görüntülemek için raporun üst düğümü seçin. **CPU kullanımı** sayfası açılır **çağıran/çağrılan** görünümü. İçinde **Geçerli Görünüm** açılır menüsünde, select **çağrı ağacı**.  
  
####  <a name="BKMK_Call_tree_structure"></a> Çağrı ağacı yapısı  

 ![Ağaç yapısı çağrı](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "çağrı ağaç yapısı")  
  
|||  
|-|-|  
|![1. adım](../profiling/media/procguid_1.png "ProcGuid_1")|CPU kullanımı çağrı ağaçları en üst düzey düğüm sahte bir düğümdür.|  
|![2. adım](../profiling/media/procguid_2.png "ProcGuid_2")|Çoğu uygulama, zaman **harici kodu Göster** seçeneği devre dışıdır, ikinci düzey düğüm bir **[harici kod]** düğümü. Düğüm başlatır ve uygulamayı durdurur, UI çizer, iş parçacığı planlama denetler ve uygulamayı diğer alt düzey hizmetler sağlar sistem ve framework kodu içerir.|  
|![3. adım](../profiling/media/procguid_3.png "ProcGuid_3")|İkinci düzey düğümünün alt öğeleri, kullanıcı kodu yöntemleri ve çağrılan veya framework kodu ve ikinci düzey sistem tarafından oluşturulan zaman uyumsuz yordamlarını verilmiştir.|  
|![4. adım](../profiling/media/procguid_4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntem çağrıları için veri var. Zaman **harici kodu Göster** olduğundan devre dışı, uygulama yöntemlerini de içerebilir bir **[harici kod]** düğümü.|  
  
####  <a name="BKMK_External_Code"></a> Dış kod  

 Kodunuz tarafından çalıştırılan sistem ve çerçeve işlevlerinin çağrılır *dış kod*. Dış kod işlevleri başlatmak ve uygulamayı durdurun, UI çizme, iş parçacığı denetimi ve uygulamayı diğer alt düzey hizmetler sağlar. CPU kullanımı çağırmak için ağaç toplar harici işlevler kullanıcı yönteminin birine çoğu durumda, dış kod içinde ilginizi kullanmadığınız **[harici kod]** düğümü.  
  
 Dış kod, arama yollarını ana tanılama raporu sayfasında görüntülemek için seçin **harici kodu Göster** gelen **filtre** açılır listesinde ve ardından **Uygula**. **Çağrı ağacı** görünümünü **CPU kullanımı** sayfa sonra dış kod çağrıları genişletir.  
  
 ![Dış Kodu Göster](../profiling/media/cpu_use_wt_filterview.png "dış Kodu Göster")  
  
 Zincirinin genişliği görüntü genişliğini aşabilir için çok sayıda dış kod arama zincirleri, iç içe girmiş **işlev adı** sütun. İşlev adları olarak daha sonra görünür **...** .  
  
 ![Çağrı ağacında dış kod iç içe geçmiş](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "çağrı ağacında dış kod iç içe geçmiş")  
  
 Aradığınız bir işlev adı bulmak için arama kutusunu kullanın. Seçilen satırın üzerine gelin veya verileri görüntülemek için yatay kaydırma çubuğunu kullanın.  
  
 ![İç içe geçmiş bir dış kod arama](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "iç içe geçmiş bir dış kod arama")  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Zaman uyumsuz işlevleri CPU kullanımına çağrı ağacı  

 Derleyici, zaman uyumsuz bir yöntem karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, bir durum makinesindeki bir sınıftır. Sınıfı, derleyici tarafından oluşturulan ve özgün yöntemleri ve geri çağırmaları, Zamanlayıcı ve bunları çalıştırmak için gereken yineleyiciler zaman uyumsuz çağırma işlevleri vardır. Bir üst yöntemi özgün yöntemini çağırdığında, derleyici üst yürütme bağlamında yöntemi kaldırır ve gizli sınıf yöntemlerini uygulama yürütme denetimleri sistem ve framework kod bağlamında çalışır. Zaman uyumsuz yöntemler genellikle, ancak her zaman, bir veya daha fazla farklı iş parçacıkları üzerinde yürütülür. Bu kod görünür **CPU kullanımı** alt öğeleri olarak çağrı ağacını **[harici kod]** düğümünün üst ağaç düğümünü hemen altındaki.  

Aşağıdaki örnekte, ilk iki düğüm altında **[harici kod]** durum makine sınıfın derleyici tarafından oluşturulan yöntemler. Üçüncü çağrı özgün düğümüdür. 
  
![Zaman uyumsuz düğüm](media/cpu_use_wt_getmaxnumberasync_selected.png "zaman uyumsuz düğümü")  

Oluşturulan yöntemler neler olduğunu göstermek için genişletin:

![Zaman uyumsuz düğümün genişletilmiş](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "genişletilmiş zaman uyumsuz düğümü")  

- `MainPage::GetMaxNumberAsyncButton_Click` yalnızca görev değerlerin bir listesini yönetir, en fazla sonuçları hesaplar ve çıktıyı görüntüler.
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zamanlama ve çağrısını sarmalamak 48 görevleri başlatmak için gereken etkinlik gösterir `GetNumberAsync`.
  
- `MainPage::<GetNumberAsync>b__b` çağıran görevler etkinliğini gösterir `GetNumber`.
