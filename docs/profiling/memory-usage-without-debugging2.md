---
title: Hata ayıklama olmadan bellek kullanımını çözümleme | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/15/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dcc5c66998501044b04e4a8265d669927e3368a
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948939"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Hata Ayıklayıcı olmadan bellek kullanımını analiz etme

**Bellek kullanımı** aracı, uygulamanızın bellek kullanımını izler. Visual Studio'da etkin bir şekilde geliştirirken senaryoları gerçek zamanlı bellek etkilerini incelemek için Aracı'nı kullanabilirsiniz. Uygulamanın bellek durumlarını ayrıntılı anlık ve bellek sorunlarını kök nedenlerini bulmak için anlık görüntüleri karşılaştırın.  
  
**Bellek kullanımı** aracı ile veya hata ayıklayıcı olmadan çalıştırabilirsiniz. Aşağıdaki yönergeler nasıl kullanılacağını göstermektedir **bellek kullanımı** aracı Visual Studio hata ayıklayıcı olmadan **performans Profiler**. 

>[!NOTE]
>- .NET Core uygulaması için bellek kullanımını ölçmek için kullanmanız gerekir **bellek kullanımı** hata ayıklayıcısı ile aracı. Yönergeler için [Visual Studio'daki bellek kullanımı profil](memory-usage.md). 
>- JavaScript veya HTML UWP uygulamalarında bellek kullanımını analiz etmek için kullanın [JavaScript belleği](../profiling/javascript-memory.md) aracına **performans Profiler**.
  
## <a name="memory-usage-diagnostic-sessions"></a>Bellek kullanımı tanılama oturumları  

**Bellek kullanımı Tanılama oturumu başlatmak için:**

1. Açık bir C# Visual Studio'da Evrensel Windows (UWP) projesi.  
   
1. Menü çubuğunda, **hata ayıklama** > **performans Profiler**.  
   
1. Seçin **bellek kullanımı**ve ardından **Başlat**.  
   
   ![Bellek kullanımı Tanılama oturumu başlatmak](../profiling/media/memuse_start_diagnosticssession.png "bellek kullanımı Tanılama oturumu Başlat")  
  
### <a name="monitor-memory-use"></a>Bellek kullanımını izleme 

Tanılama oturumu başlattığınızda, uygulamanız başlar ve **tanılama araçları** penceresinde, uygulamanızın bellek kullanımını zaman çizelgesi grafiği görüntüler.  

![Bellek kullanımı genel bakış sayfasında](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")  

Zaman Çizelgesi grafiği uygulama çalışırken bellek dalgalanmaları gösterir. Graf artış genellikle bazı kod toplama veya veri oluşturma ve işlem bittiğinde atılıyor gösterir. Büyük depoları, en iyi duruma getirmek mümkün olabilir alanları gösterir. Daha fazla sorun bir artış döndürülmez, bellek tüketimi, çünkü verimsiz bellek kullanımını veya hatta bir bellek sızıntısı gösterebilir.  
  
### <a name="take-snapshots-of-app-memory-states"></a>Uygulama bellek durumları anlık 

Uygulama çok sayıda nesne kullanır ve bir senaryoya analizinizi odaklanmasına isteyebilirsiniz. Veya bellek sorunları araştırmak için fark edebilirsiniz. Bellek kullanımı belirli anlarda yakalamak için bir tanılama oturumu sırasında anlık görüntüsünü alabilirsiniz. Senaryo tekrar etmeniz durumunda, bir bellek sorunu, sorunu ilk geçtiği sonra başka bir anlık görüntü görünmeden önce bir uygulamanın bir temel anlık görüntü ve ek anlık görüntüleri almak için iyi bir fikirdir.  

Anlık görüntüleri toplamak için seçin **anlık görüntü Al** bellek verileri yakalamak istediğinizde.  

###  <a name="BKMK_Close_a_monitoring_session"></a> Tanılama oturumu kapat  

Rapor oluşturmadan bir izleme oturumunu durdurmak için tanılama pencereyi kapatmanız yeterlidir. İşiniz bittiğinde, rapor oluşturmak için seçim anlık görüntüler aldıysanız veya toplama **toplamasını Durdur**.  

![Toplamayı Durdur](../profiling/media/memuse__stopcollection.png "koleksiyonu Durdur")  

##  <a name="memory-usage-reports"></a>Bellek Kullanım raporları 

Veri toplamayı durdurduktan sonra **bellek kullanımı** aracı uygulamayı durdurur ve görüntüler **bellek kullanımı** genel bakış sayfası.  

![Bellek kullanımı genel bakış sayfasında](../profiling/media/memuse__reportoverview1.png "bellek kullanımı genel bakış sayfası")  

### <a name="BKMK_Memory_Usage_snapshot_views"></a> Bellek kullanımı anlık görüntüleri 

Sayıları **anlık görüntü** bölmeleri bayt ve her anlık görüntü alındığında bellekte nesneleri ve önceki bir anlık görüntü arasındaki farkı gösterir. 

Açık ayrıntılı bağlantılar sayılardır **bellek kullanımı** rapor görünümleri yeni Visual Studio Windows. A [anlık görüntü ayrıntılarını raporu](#snapshot-details-report) türlerinin ve örneklerinin bir anlık görüntüde gösterilmektedir. A [anlık görüntü raporu fark (fark)](#snapshot-difference-diff-reports) türleri ve iki anlık görüntü örnekleri karşılaştırır.  
  
  ![Anlık görüntü bağlantıları görüntüle](../profiling/media/memuse__snapshotview_numbered.png "anlık görüntü bağlantıları görüntüle")  
  
|||  
|-|-|  
|![1. adım](../profiling/media/procguid_1.png "ProcGuid_1")|Anlık Görüntü alındığında bellek bayt sayısı.<br /><br /> Tür örnekleri toplam boyutu tarafından sıralanan bir anlık görüntü ayrıntıları raporunu görüntülemek için bu bağlantıyı seçin.|  
|![2. adım](../profiling/media/procguid_2.png "ProcGuid_2")|Anlık Görüntü alındığında bellekteki nesnelerin toplam sayısı.<br /><br /> Tür örneklerine sayısına göre sıralanmış bir anlık görüntü ayrıntıları raporunu görüntülemek için bu bağlantıyı seçin.|  
|![3. adım](../profiling/media/procguid_3.png "ProcGuid_3")|Bu anlık görüntüdeki bellek nesnelerin toplam boyutu ve önceki anlık görüntü arasındaki farkı. <br /><br /> Bu anlık görüntüyü bellek boyutunu bir öncekinden daha büyük pozitif bir sayı anlamına gelir ve negatif bir sayı anlamına gelir boyutu küçüktür. **Taban çizgisi** bir anlık görüntü, bir tanılama oturumu ilk olduğu anlamına gelir. **Fark** fark sıfır olduğu anlamına gelir.<br /><br /> Türlerin örneklerinin toplam boyut farkı sıralama ölçütü bir anlık görüntü fark raporu görüntülemek için bu bağlantıyı seçin.|  
|![4. adım](../profiling/media/procguid_4.png "ProcGuid_4")|Bellek nesneleri bu anlık görüntüdeki toplam sayısı ve önceki anlık görüntü arasındaki farkı.<br /><br /> Türleri örneklerinin toplam sayısı farkı sıralama ölçütü bir anlık görüntü fark raporu görüntülemek için bu bağlantıyı seçin.|  
  
## <a name="memory-usage-snapshot-reports"></a>Bellek kullanımı anlık görüntü raporları 

<a name="BKMK_Snapshot_report_trees"></a> Seçtiğinizde, içinde anlık görüntü bağlantılardan birini **bellek kullanımı** genel bakış sayfasında, bir anlık görüntü raporu yeni bir sayfa açılır. 

![Bellek kullanımı anlık görüntü raporu](../profiling/media/memuse_snapshotreport_all.png "bellek kullanımı anlık görüntü raporu")  
  
Bir anlık görüntü raporu, genişletebilirsiniz **nesne türü** alt girişlerini görüntülemek için girdileri. Örneği, bellek kullanımı aracı tarafından oluşturulan benzersiz kimliklerinin adlarıdır. 

Varsa bir **nesne türü** olan mavi, bunu ayrı bir pencerede kaynak kod içindeki nesneye gitmek için seçebilirsiniz.  

Tanımlayan olamaz veya olan katılımı kodunuzda anlamadığınız büyük olasılıkla .NET Framework, işletim sistemi veya derleyici nesneleri türleridir. **Bellek kullanımı** aracı, nesnelerin sahipliği zincirde ilgili iseler bu nesneleri görüntüler.  

Anlık görüntü raporu: 

- **Yönetilen yığın** ağacı, raporda türleri ve örnekleri gösterir. Bir tür veya örnek seçerek görüntüler **kök yolları** ve **başvurulan nesneleri** ağaçları seçili öğe için.  
  
- **Kök yolları** zincirdeki bir tür veya örnek başvuru nesnelerinin ağacını gösterir. .NET Framework atık toplayıcı, yalnızca tüm başvuruları serbest bıraktığınızda bir nesne için bellek temizler.  
  
- **Başvurulan türleri** veya **başvurulan nesneleri** ağacı seçili türü veya örnek başvuru nesneleri gösterir.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Rapor ağaç filtreleri  

Uygulama geliştiricileri için ilgi çekici uygulamalarda birçok türü değil. Anlık görüntü raporu filtreleri bu türlerin çoğu gizleyebilirsiniz **Yönetilen yığın** ve **kök yolları** ağaçları.   

![Sıralama ve filtreleme seçenekleri](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")  

- <a name="BKMK_Filter"></a> Ağaç türü adına göre filtre uygulamak için adı girin. **filtre** kutusu. Filtre büyük küçük harfe duyarlı değildir ve herhangi bir tür adı bölümü içinde belirtilen dize tanır.  
  
- <a name="BKMK_Collapse_Small_Objects"></a> Seçin **küçük nesneleri Daralt** içinde **filtre** gizlemek için açılan türleri **boyutu (bayt)** 0,5 yüzde toplam belleğin küçüktür.  
  
- <a name="BKMK_Just_My_Code"></a> Seçin **yalnızca kendi kodum** içinde **filtre** dış kod tarafından oluşturulan çoğu örnekleri gizlemek için açılır. Dış türler belirli bir işletim sistemi veya framework bileşenlerini ait veya derleyici tarafından üretilen.  
  
## <a name="snapshot-details-reports"></a>Anlık görüntü raporları ayrıntıları  

 Anlık görüntü ayrıntılarını rapor bir anlık görüntüden bir tanılama oturumu açıklar. Raporu açmak için bir anlık görüntü bölmesinde boyutu veya nesneleri bağlantıyı seçin. 

 ![Anlık görüntü raporu bir anlık görüntü bölmesinde bağlantılar](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "anlık görüntü raporu bir anlık görüntü bölmesinde bağlantılar")  
  
Her iki bağlantı aynı raporu açın. Tek fark, başlangıç sıralama **Yönetilen yığın** ağaç. Rapor tarafından boyutu bağlantı sıralar **kapsamlı boyut (bayt)** sütun. Rapor tarafından nesneleri bağlantı sıralar **sayısı** sütun. Rapor açıldıktan sonra sıralama sütunu veya sırasını değiştirebilirsiniz.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Yönetilen yığın ağaç (anlık görüntü ayrıntılarını raporları)  
 **Yönetilen yığın** ağaç bellekte tutulan nesne türlerini listeler. On en büyük boyuta göre sıralayarak türü örneklerini görüntülemek için bir tür adı'nı genişletin. Bir türü veya örnek görüntülemek için seçin **kök yolları** ve **başvurulan nesneleri** ağaçları seçili öğe için.  
  
 ![Yönetilen yığın ağaç](../profiling/media/memuse__snapshotdetails_managedheaptree.png "yönetilen yığını ağacı")  
  
**Yönetilen yığın** anlık görüntü ayrıntılarını raporu ağacında aşağıdaki sütunlar vardır:

|||  
|-|-|  
|**Nesne türü**|Tür veya nesne örneğinin adı.|  
|**Sayısı**|Tür örnekleri nesne sayısı. **Sayısı** daima bir örneği için 1'dir.|  
|**Boyut (bayt)**|Bir tür örnekleri nesnelerinin boyutunu daha az anlık türünün tüm örneklerini boyutu.<br /><br /> Bir örneği boyutu örneğinde bulunan nesneler daha kısa bir nesnenin boyutu. |  
|**Kapsamlı boyut (bayt)**|Kapsanan nesneler boyutunu türdeki örneklerin boyutunu veya tek bir örnek boyutu dahil.|  
|**Module**|Nesne içeren modül.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Yolları (anlık görüntü raporları ayrıntıları) kök ağacı  
**Ağaç kök yolları** zincirini, bir tür veya örnek başvuru nesnelerin gösterir. .NET Framework atık toplayıcı, yalnızca tüm başvuruları serbest bıraktığınızda bir nesne için bellek temizler.  
  
Bir türü için **kök yolları** ağacı, bu türe yapılan başvuruları tutan nesne sayısını görünür **başvuru sayısını** sütun. 

![Kök yolları türleri için ağaç](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "kök yolları türleri için ağaç")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Başvurulan türler veya başvurulan nesneleri ağaç (anlık görüntü raporları ayrıntıları)  
**Başvurulan türleri** veya **başvurulan nesneleri** ağacı seçili türü veya örnek başvuru nesneleri gösterir.  
  
![Başvurulan nesne ağacının örnekler](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "için başvurulan nesneleri ağacı örnekleri")  
  
A **başvurulan türleri** anlık görüntü ayrıntılarını raporu ağacında aşağıdaki sütunlar vardır. A **başvurulan nesneleri** ağacı yok **başvuru sayısını** sütun.

|||  
|-|-|  
|**Nesne türü** veya **örneği**|Tür veya örnek adı.|  
|**Başvuru sayısı**|Türler için tür örnekleri nesne sayısı.|  
|**Boyut (bayt)**|Bir türü türün nesnelerinin boyutunu daha az türünün tüm örneklerini boyutu.<br /><br /> Bir örneği nesnede bulunan nesnelerin boyutunu daha az nesnenin boyutu.|  
|**Kapsamlı boyut (bayt)**|Türün örneklerini ya da kapsanan nesneleri boyutu da dahil olmak üzere, örnek boyutuna toplam boyutu.|  
|**Module**|Nesne içeren modül.|  
  
## <a name="snapshot-difference-diff-reports"></a>Anlık görüntü fark (fark) raporları  

Fark (fark) anlık görüntü raporu değişiklikler birincil bir anlık görüntü arasındaki önceki anlık görüntü olarak gösterilir. Fark raporu açmak için bir anlık görüntü bölmesinde fark bağlantılardan birini seçin. 

Her iki bağlantı aynı raporu açın. Tek fark, başlangıç sıralama **Yönetilen yığın** rapor ağacında. Rapor tarafından boyutu bağlantı sıralar **kapsamlı boyut farkı (bayt)** sütun. Rapor tarafından nesneleri bağlantı sıralar **sayısı farkı** sütun. Rapor açıldıktan sonra sıralama sütunu veya sırasını değiştirebilirsiniz.  
  
 ![Fark bağlanan bir anlık görüntü bölmesinde raporu](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "fark bağlanan bir anlık görüntü bölmesinde raporu")  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Yönetilen yığın ağaç (anlık görüntü fark raporları) 

 **Yönetilen yığın** ağaç bellekte tutulan nesne türlerini listeler. On en büyük boyuta göre sıralayarak türü örneklerini görüntülemek için bir tür adı genişletebilirsiniz. Bir türü veya örnek görüntülemek için seçin **kök yolları** ve **başvurulan nesneleri** ağaçları seçili öğe için.  
  
 ![Fark rapordaki bir tür için yönetilen yığını ağacı](../profiling/media/memuse_snapshotdiff_type_heap.png "fark rapordaki bir tür için yönetilen yığını ağacı")  
  
**Yönetilen yığın** diff anlık görüntü raporu ağacında aşağıdaki sütunlar vardır:

|||  
|-|-|  
|**Nesne türü**|Tür veya nesne örneğinin adı.|  
|**Sayısı**|Birincil anlık bir türün örneklerinin sayısı. **Sayısı** daima bir örneği için 1'dir.|  
|**Sayım farkı**|Bir tür türün örneklerinin sayısını birincil anlık görüntü ve önceki anlık görüntü arasındaki farkı. Alan bir örneği için boştur.|  
|**Boyut (bayt)**|Nesneleri nesnelerin boyutu daha az birincil anlık görüntüdeki nesnelerin boyutu. Bir tür için **boyutu (bayt)** ve **kapsamlı boyut (bayt)** toplamları boyutlarının türü örnekleri.|  
|**Toplam boyut farkı (bayt)**|Bir tür türün örneklerinin toplam boyutu birincil anlık görüntü ve örneklerinde nesnelerin boyutunu daha önceki bir anlık arasındaki farkı. Alan bir örneği için boştur.|  
|**Kapsamlı boyut (bayt)**|Nesnelerin boyutunu nesneler de dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|  
|**Kapsamlı boyut farkı (bayt)**|Bir tür, türün tüm örneklerin boyutunu birincil anlık görüntü ve önceki anlık görüntü arasındaki farkı için nesneleri nesnelerin boyutunu dahil olmak üzere. Alan bir örneği için boştur.|  
|**Module**|Nesne içeren modül.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Kök ağaç (anlık görüntü fark raporları) yolları  

**Ağaç kök yolları** zincirini, bir tür veya örnek başvuru nesnelerin gösterir. .NET Framework atık toplayıcı, yalnızca tüm başvuruları serbest bıraktığınızda bir nesne için bellek temizler. 

Bir türü için **kök yolları** ağacı, bu türe yapılan başvuruları tutan nesne sayısını görünür **başvuru sayısını** sütun. Önceki anlık görüntüden sayısı fark **başvuru fark** sütun. 

 ![Bir fark rapor yollar için kök ağacında](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "yollar için kök ağacında bir fark raporu")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Başvurulan türler veya başvurulan nesneleri ağaç (anlık görüntü fark raporları)  

**Başvurulan türleri** veya **başvurulan nesneleri** ağacı seçili türü veya örnek başvuru nesneleri gösterir.  

![Bir fark raporda türleri başvurulan](../profiling/media/memuse_snapshotdiff_referencedtypes.png "fark raporunda başvurulan türleri")  

A **başvurulan türleri** diff anlık görüntü raporu ağacında aşağıdaki sütunlar vardır. A **başvurulan nesneleri** ağacı içeriyor **örneği**, **boyutu (bayt)**, **kapsamlı boyut (bayt)**, ve **modülü** sütunları.

|||  
|-|-|  
|**Nesne türü** veya **örneği**|Tür veya nesne örneğinin adı.|  
|**Başvuru sayısı**|Birincil anlık bir türün örneklerinin sayısı.|  
|**Başvuru sayısı farkı**|Bir tür türün örneklerinin sayısını birincil anlık görüntü ve önceki anlık görüntü arasındaki farkı.|  
|**Boyut (bayt)**|Nesneleri nesnelerin boyutu daha az birincil anlık görüntüdeki nesnelerin boyutu. Bir tür için **boyutu (bayt)** ve **kapsamlı boyut (bayt)** toplamları boyutlarının türü örnekleri.|  
|**Toplam boyut farkı (bayt)**|Bir tür türün örneklerinin toplam boyutu birincil anlık görüntü ve örneklerinde nesnelerin boyutunu daha önceki bir anlık arasındaki farkı. |  
|**Kapsamlı boyut (bayt)**|Nesnelerin boyutunu nesneler de dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|  
|**Kapsamlı boyut farkı (bayt)**|Bir tür, türün tüm örneklerin boyutunu birincil anlık görüntü ve önceki anlık görüntü arasındaki farkı için nesneleri nesnelerin boyutunu dahil olmak üzere.|  
|**Module**|Nesne içeren modül.|  

## <a name="see-also"></a>Ayrıca bkz.  
 [JavaScript bellek](../profiling/javascript-memory.md)  
 [Visual Studio profil oluşturma](../profiling/index.md)  
 [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)  
 [C++, C# ve Visual Basic kullanarak UWP uygulamaları için en iyi performans](/previous-versions/windows/apps/hh750313\(v\=win.10\))   
 [Visual Studio'da yeni bellek kullanımı aracı ile bellek sorunlarını tanılama](http://go.microsoft.com/fwlink/p/?LinkId=394706)