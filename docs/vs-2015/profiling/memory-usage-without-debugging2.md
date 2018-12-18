---
title: Bellek kullanımı Debugging2 olmadan | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ebd4dd187f2b976ca7861f95609dd6ce8d8d318f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808589"
---
# <a name="memory-usage-without-debugging"></a>Hata ayıklama olmadan bellek kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz **bellek kullanımı** aşağıdakileri yapmak için hata ayıklama olmadan aracı  
  
- Uygulamanızın izleme bellek kullanım hakkı Visual Studio'da bir senaryo geliştirirken.  
  
- Uygulamanızın bellek durumunun ayrıntılı anlık görüntüler oluşturun.  
  
- Bellek sorunlarının temel nedenini bulmak için anlık görüntüleri karşılaştırın.  
  
  Bu konu açıklar nasıl bir Windows Evrensel XAML uygulaması çözümlemek için bellek kullanımı aracı kullanın. JavaScript ve HTML kullanmak, bkz. Evrensel Windows uygulamalarında bellek kullanımını analiz etmek istiyorsanız [(JavaScript) bellek kullanımını analiz etme](http://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
##  <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> Bir bellek kullanımı Tanılama oturumu başlatın  
  
1.  Bir C# Evrensel Windows projesi, Visual Studio'da açın.  
  
2.  Menü çubuğunda, **hata ayıklama / performans Profiler...** .  
  
3.  Seçin **bellek kullanımı** seçip **Başlat** sayfanın alt kısmındaki düğmesi.  
  
     ![Bellek kullanımı Tanılama oturumu başlatmak](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
##  <a name="BKMK_Monitor_memory_use"></a> Bellek kullanımını izleme  
 Hizmetini kullanıyor olsanız da **bellek kullanımı** aracını bulun ve sorunları gidermek için kullanabileceğiniz ayrıntılı raporlar oluşturmak için de bunu gerçek zamanlı bellek etkilerini etkin olarak geliştirme bir senaryo incelemek için kullanabilirsiniz.  
  
 Tanılama oturumu başlattığınızda, uygulamanız başlar ve **tanılama araçları** penceresinde, uygulamanızın bellek kullanımını zaman çizelgesi grafiği görüntüler.  
  
 ![Bellek kullanımı genel bakış sayfasında](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Zaman Çizelgesi grafiği, çalışırken uygulamanızın bellek dalgalanmaların gösterir. Graf artış genellikle bazı kod toplama veya veri oluşturma ve işlem bittiğinde atılıyor olduğunu gösterir. Büyük depoları, en iyi duruma getirmek mümkün olabilir alanları gösterir. Daha fazla verimsiz bellek kullanımını veya hatta bir bellek sızıntısı işaret edebilir çünkü döndürülmez bellek tüketimi artış konusudur.  
  
###  <a name="BKMK_Close_a_monitoring_session"></a> Bir izleme oturumu kapat  
 ![Toplamayı Durdur](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Rapor oluşturmadan bir izleme oturumunu durdurmak için tanılama pencereyi kapatmanız yeterlidir. Bellek anlık görüntüleri gerçekleştirdiğinizden, rapor oluşturmak için Seç **Durdur**.  
  
##  <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Uygulamanızın bellek durumunun anlık görüntüsünü  
 İncelemek istediğiniz bir bellek sorunu bulursanız, belirli bir süre nesneleri bellekte yakalamak için tanılama oturumu sırasında anlık görüntüsünü alabilirsiniz. Uygulama çok sayıda nesne türlerini kullandığından analiz bir senaryoya odaklanmasına isteyebilirsiniz. Senaryo tekrar etmeniz durumunda da bir bellek sorunu, sorunu ilk geçtiği sonra başka bir anlık görüntü görünmeden önce uygulamanın temel anlık görüntüsünü almak için iyi bir fikir ve bir veya daha fazla ek anlık görüntüleri sağlar.  
  
 Anlık görüntüleri toplamak için yeni bir tanılama oturumu başlatın. Seçin **anlık görüntüsünü Al** bellek verileri yakalamak istediğinizde. Bir rapor oluşturmak için Seç **Durdur**.  
  
##  <a name="BKMK_Memory_Usage_overview_page"></a> Bellek kullanım genel bakış sayfası  
 Veri toplamayı durdurduktan sonra bellek kullanımı aracı uygulamayı durdurur ve genel bakış raporu görüntüler.  
  
 ![Bellek kullanımı genel bakış sayfasında](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
###  <a name="BKMK_Memory_Usage_snapshot_views"></a> Bellek kullanımı anlık görüntü görünümleri  
 Ayrıntılı raporlar Visual Studio'nun yeni bir pencerede açmak için anlık görüntü görünümleri kullanın. Anlık görüntü görünümleri iki tür vardır:  
  
- A [anlık görüntü raporları ayrıntıları](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) türlerinin ve örneklerinin bir anlık görüntüde gösterilmektedir.  
  
- A [anlık görüntü fark (fark) raporları](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) türleri ve iki anlık görüntü örnekleri karşılaştırır.  
  
  ![Anlık görüntü bağlantıları görüntüle](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Anlık görüntü görünümü bir resimde numaralı öğeler bellek kullanım raporu görünümlerini açmak bağlantılardır.  
  
|||  
|-|-|  
|![1. adım](../profiling/media/procguid-1.png "ProcGuid_1")|Anlık Görüntü alındığında bağlantı metni bellekte toplam bayt sayısını gösterir.<br /><br /> Tür örnekleri toplam boyutu tarafından sıralanan bir anlık görüntü ayrıntıları raporunu görüntülemek için bu bağlantıyı seçin.|  
|![2. adım](../profiling/media/procguid-2.png "ProcGuid_2")|Bağlantı metni, anlık görüntü alındığında bellekte toplam nesne sayısı gösterilmektedir.<br /><br /> Tür örneklerine sayısına göre sıralanmış bir anlık görüntü ayrıntıları raporunu görüntülemek için bu bağlantıyı seçin.|  
|![3. adım](../profiling/media/procguid-3.png "ProcGuid_3")|Bağlantı metni, önceki anlık görüntüye toplam boyutu ve bu anlık görüntü şu anda bellekteki nesnelerin toplam boyutu arasındaki farkı gösterir.<br /><br /> Boyutu daha küçük olduğunda bu anlık görüntüyü bellek boyutunu Öncekine ve negatif bir sayı büyük olduğunda, bağlantı metnini pozitif bir sayıdır. Bağlantı metni **temel** bu anlık görüntüyü Tanılama oturumu; ilk olduğunu gösterir **Hayır fark** fark sıfır olduğunu gösterir.<br /><br /> Türlerin örneklerinin toplam boyut farkı göre sıralanmış bir anlık görüntü fark raporu görüntülemek için bu bağlantıyı seçin.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bağlantı metni, bellek nesneleri bu anlık görüntüdeki toplam sayısı ve önceki anlık görüntüsündeki nesne sayısı arasındaki farkı gösterir.<br /><br /> Türleri örneklerinin toplam sayısı farkı göre sıralanmış bir anlık görüntü fark raporu görüntülemek için bu bağlantıyı seçin.|  
  
##  <a name="BKMK_Snapshot_reports"></a> Anlık görüntü raporları  
 ![Bellek kullanımı anlık görüntü raporu](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
###  <a name="BKMK_Snapshot_report_trees"></a> Anlık görüntü raporu ağaçları  
  
####  <a name="BKMK_Managed_Heap"></a> Yönetilen yığın  
 Yönetilen yığın ağaç [Yönetilen yığın ağaç (anlık görüntü ayrıntılarını)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) ve [Yönetilen yığın ağaç (anlık görüntü fark)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) raporda türleri ve örnekleri gösterir. Bir tür veya örnek seçerek görüntüler **kök yolları** ve **başvurulan nesneleri** ağaçları seçili öğe için.  
  
####  <a name="BKMK_Paths_to_Root"></a> Kök yolları  
 [Kök ağaç (anlık görüntü ayrıntılarını) yollara](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) ve [kök ağaç (anlık görüntü fark) yollara](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) nesnelerin türü veya örnek başvuru zinciri göster. .NET Framework atık toplayıcı, yalnızca tüm başvuruları serbest bıraktığınızda bir nesne için bellek temizler.  
  
####  <a name="BKMK_Referenced_Objects"></a> Başvurulan nesneler  
 [Başvurulan nesneleri ağaç (anlık görüntü ayrıntılarını)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) ve [başvurulan nesneleri ağaç (anlık görüntü fark)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) seçili türü veya örnek başvuru nesnelerini gösterir.  
  
###  <a name="BKMK_Object_Type_and_Instance_fields"></a> Nesne türü ve örneği alanları  
 Olduğunda bir **nesne türü** girişi alt girişler vardır, bunları görüntülemek için ok simgesini de seçebilirsiniz. Varsa rengini **nesne türü** metin mavi, kaynak kodu dosyası nesnesinde gitmek için seçebilirsiniz. Kaynak dosyayı ayrı bir pencerede açılır.  
  
 Örneği, bellek kullanımı aracı tarafından oluşturulan benzersiz kimliklerinin adlarıdır.  
  
 Bir kolayca belirleyemez tür fark ederseniz veya kodunuzda nasıl dahil bilmiyorsanız, .NET Framework, işletim sistemi ya da derleyici bellek kullanımı aracı sahipliği zincirleri söz konusu olduğu için görüntüleyen bir nesne olabilir nesnelerinizi.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Rapor ağaç filtreleri  
 Çoğu uygulama, çoğu uygulama geliştiricisine çok ilgi çekici olmayan türleri, oyununuzun çok sayıda içerir. **Bellek kullanımı** aracı tanımlar bu türlerin çoğu gizlemek için kullanabileceğiniz iki filtre **Yönetilen yığın** ve **kök yolları** ağaçları. Ayrıca, bir ağaç türü adına göre filtreleyebilirsiniz.  
  
 ![Sıralama ve filtreleme seçenekleri](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
####  <a name="BKMK_Filter"></a> Filtre  
 Bir dize girin **filtre** ağaç kısıtlamak için kutusu belirtilen metni içeren türleri için görüntüler. Filtre büyük küçük harfe duyarlı değildir ve herhangi bir bölümünü tür adları belirtilen dizenin tanır.  
  
####  <a name="BKMK_Collapse_Small_Objects"></a> Küçük nesneleri Daralt  
 Bu filtre uygulandığında ayarlanmış türleri **boyutu (bayt)** anlık bellek toplam boyutunun yüzde 0,5'den az gizli olarak **Yönetilen yığın** listesi.  
  
####  <a name="BKMK_Just_My_Code"></a> Yalnızca kendi kodum  
 **Yalnızca kendi kodum** filtre dış kod tarafından oluşturulan çoğu örnekleri gizler. Dış türler Framework bileşenleri veya işletim sistemi tarafından sahip olunan veya derleyici tarafından üretilen.  
  
##  <a name="BKMK_Snapshot_details_reports"></a> Anlık görüntü raporları ayrıntıları  
 Bir anlık görüntüden bir tanılama oturumu odaklanmak için anlık görüntü ayrıntıları raporunu kullanın. Ayrıntıları raporu açmak için bağlantılardan birini bir anlık görüntü Görünümü'nde aşağıdaki resimde gösterildiği gibi seçin. Her iki bağlantı aynı raporu açın; tek fark, başlangıç sıralama **Yönetilen yığın** rapor ağacında. Her iki durumda da, rapor açıldıktan sonra sıralama düzenini değiştirebilirsiniz.  
  
 ![Anlık görüntü raporu bir anlık görüntü Görünümü'nde bağlantılar](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
-   **MB** bağlantı sıralar raporun **kapsamlı boyut (bayt)** sütun.  
  
-   **Nesneleri** bağlantı sıralar raporun **sayısı** sütun.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Yönetilen yığın ağaç (anlık görüntü ayrıntılarını)  
 **Yönetilen yığın** ağaç bellekte tutulan nesne türlerini listeler. On en büyük boyuta göre sıralayarak türü örneklerini görüntülemek için bir tür adı genişletebilirsiniz. Bir tür veya örnek seçerek görüntüler **kök yolları** ve **başvurulan nesneleri** ağaçları seçili öğe için.  
  
 ![Yönetilen yığın ağaç](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Nesne türü**|Tür veya nesne örneğinin adı.|  
|**Sayısı**|Tür örnekleri nesne sayısı. Her zaman bir örneği için 1 sayısıdır.|  
|**Boyut (bayt)**|Bir tür nesnelerinin örneklerini boyutunu hariç tür bellek anlık görüntüsündeki tüm örneklerini boyutu.<br /><br /> Bir örneği, türü, boyutu örneğinde bulunan nesneler hariç nesnenin boyutu için. örnekleri.|  
|**Kapsamlı boyut (bayt)**|Tür örnekleri ya da kapsanan nesneleri boyutu da dahil olmak üzere tek bir örnek boyutu boyutu.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Yollar için kök ağaç (anlık görüntü ayrıntılarını)  
 **Ağaç kök yolları** türü veya örnek başvuran nesnelerin zincirini gösterir. .NET Framework atık toplayıcı, yalnızca tüm başvuruları serbest bıraktığınızda bir nesne için bellek temizler.  
  
 ![Kök yolları türleri için ağaç](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Bir tür içinde görüntülediğinizde **kök yolları** ağacı, bu türe yapılan başvuruları tutmak türlerindeki nesneler, sayısını görüntülenir **başvuru sayısını** sütun. Bir örneği çözümlediğinizde sütun görünmüyor.  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Başvurulan nesneler ağaç (anlık görüntü ayrıntılarını)  
 **Başvurulan nesneleri** ağacı seçili türü veya örnek başvuru nesneleri gösterir.  
  
 ![Örnekler için başvurulan Objjects ağacı](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Nesne türü / örnek**|Tür veya nesne örneğinin adı.|  
|**Boyut (bayt)**|Bir türü türün nesnelerinin boyutunu hariç türünün tüm örneklerini boyutu.<br /><br /> Bir örneği nesnede bulunan nesnelerin boyutunu hariç, nesnenin boyutu.|  
|**Kapsamlı boyut (bayt)**|Türün örneklerini ya da kapsanan nesneleri boyutu da dahil olmak üzere, örnek boyutuna toplam boyutu.|  
  
##  <a name="BKMK_Snapshot_difference__diff__reports"></a> Anlık görüntü fark (fark) raporları  
 Fark (fark) anlık görüntü raporu, birincil bir anlık görüntü ve hemen daha önce alınmış bir anlık görüntü arasındaki değişiklikleri gösterir. Bir fark raporu açmak için bağlantılardan birini bir anlık görüntü Görünümü'nde aşağıdaki resimde gösterildiği gibi seçin. Her iki bağlantı aynı raporu açın; tek fark, başlangıç sıralama **Yönetilen yığın** rapor ağacında. Rapor açıldıktan sonra sıralama düzenini değiştirebilirsiniz.  
  
 ![Fark bağlantılarını rapor bir anlık görüntü Görünümü'nde](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
-   **MB** bağlantı sıralar raporun **kapsamlı boyut (bayt)** sütun.  
  
-   **Nesneleri** bağlantı sıralar raporun **sayısı** sütun.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Yönetilen yığın ağaç (anlık görüntü fark)  
 **Yönetilen yığın** ağaç bellekte tutulan nesne türlerini listeler. On en büyük boyuta göre sıralayarak türü örneklerini görüntülemek için bir tür adı genişletebilirsiniz. Bir tür veya örnek seçerek görüntüler **kök yolları** ve **başvurulan nesneleri** ağaçları seçili öğe için.  
  
 ![Fark rapordaki bir tür için yönetilen yığını ağacı](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Dikkat **sayısı**, **boyutu (bayt)**, ve **kapsamlı boyut (bayt)** sütunları, resim daraltılmış.  
  
|||  
|-|-|  
|**Nesne türü**|Tür veya nesne örneğinin adı.|  
|**Sayısı**|Birincil anlık bir türün örneklerinin sayısı. **Sayısı** daima bir örneği için 1'dir.|  
|**Sayım farkı**|Bir tür türün örneklerinin sayısını birincil anlık görüntü ve önceki anlık görüntü arasındaki farkı. Alan bir örneği için boştur.|  
|**Boyut (bayt)**|Nesnelerin içindeki nesnelerin boyutunu hariç birincil anlık görüntüdeki nesnelerin boyutu. Bir tür için **boyutu (bayt)** ve **kapsamlı boyut (bayt)** toplamları boyutlarının türü örnekleri.|  
|**Toplam boyut farkı (bayt)**|Nesnelerinin örneklerini boyutunu dışında bir tür için türün örneklerinin toplam boyutu birincil anlık görüntü ve önceki anlık görüntü arasındaki farkı. Alan bir örneği için boştur.|  
|**Kapsamlı boyut (bayt)**|Nesnelerin içindeki nesnelerin boyutunu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|  
|**Kapsamlı boyut farkı (bayt)**|Bir tür türünün tüm örneklerini boyutunu birincil anlık görüntü nesnelerin içindeki nesnelerin boyutunu da dahil olmak üzere önceki anlık görüntü arasındaki farkı. Alan bir örneği için boştur.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Yollar için kök ağaç (anlık görüntü fark)  
 **Ağaç kök yolları** türü veya örnek başvuran nesnelerin zincirini gösterir. .NET Framework atık toplayıcı, yalnızca tüm başvuruları serbest bıraktığınızda bir nesne için bellek temizler.  
  
 ![Yollar için kök ağacı örnekler fark görünümünde](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Başvurulan nesneler ağaç (anlık görüntü fark)  
 **Başvurulan nesneleri** ağacı, başvuru birincil türü veya örnek nesneleri gösterir.  
  
 ![Örnekler için başvurulan Objjects ağacı](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Nesne türü / örnek**|Tür veya nesne örneğinin adı.|  
|**Boyut (bayt)**|Bir örneği boyutu örneğinde bulunan nesneler dışlama birincil anlık görüntüsündeki nesne boyutu.<br /><br /> Bir türü örneğinde bulunan nesnelerin boyutunu hariç türün örneklerinin birincil anlık görüntüdeki toplam boyutu.|  
|**Kapsamlı boyut (bayt)**|Nesnelerin içindeki nesnelerin boyutunu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript bellek](../profiling/javascript-memory.md)   
 [Uygulama performansını analiz edin](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [Performans ve tanı araçlarını çalıştırma](http://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [C++, C# ve Visual Basic kullanan Windows Store uygulamaları için en iyi performans](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Visual Studio'da yeni bellek kullanımı aracı ile bellek sorunlarını tanılama](http://go.microsoft.com/fwlink/p/?LinkId=394706)



