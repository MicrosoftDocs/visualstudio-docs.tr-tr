---
title: Uygulamalarınızda ölçü bellek kullanımı
description: Hata ayıklayıcıyla tümleştirilmiş Tanılama Aracı ile hata ayıklarken bellek sızıntılarını ve verimsiz bellek bulun.
ms.custom: seodec18
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 622f35ccbe29130dea3b35b96373da0c8b39e0b7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052083"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Visual Studio'da ölçü bellek kullanımı
Hata ayıklayıcıyla tümleştirilmiş ile hata ayıklarken bellek sızıntılarını ve verimsiz bellek Bul **bellek kullanımı** Tanılama aracı. Bir veya daha fazla atmanız bellek kullanımı aracı sağlar *anlık görüntüleri* nesne türlerinin bellek kullanımı etkilerini anlamanıza yardımcı olmak üzere yönetilen ve yerel bellek yığın. .NET, yerel veya karma mod (.NET ve yerel) uygulamaları, anlık toplayabilirsiniz.  
  
 Aşağıdaki grafik gösterildiği **tanılama araçları** penceresi (Visual Studio 2015 güncelleştirme 1 ve sonraki sürümlerinde kullanılabilir):  
  
 ![DiagnosticTools&#45;güncelleştirme 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-güncelleştirme 1")  
  
 Her zaman bellek anlık görüntüleri toplama rağmen **bellek kullanımı** aracı, performans sorunlarını araştırma sırasında uygulamanızın nasıl yürütür denetlemek için Visual Studio hata ayıklayıcısını kullanabilirsiniz. Kesme noktaları, Adımlama, tümünü Kes ve diğer hata ayıklayıcı eylemlerini performans araştırmalarınıza en uygun olan kod yollarında odaklanmanıza yardımcı olabilir. Uygulamanız çalışırken, bu eylemleri gerçekleştirerek, sorunu tanılamak için gereken süreyi önemli ölçüde azaltabilir ve sizi ilgilendirmeyen kodu paraziti ortadan kaldırabilir.  
  
 Hata ayıklayıcının dışında bellek Aracı'nı kullanabilirsiniz. Bkz: [hata ayıklama olmadan bellek kullanımı](../profiling/memory-usage-without-debugging2.md). Windows 7 ve daha sonra bağlı hiçbir hata ayıklayıcısı ile profil oluşturma araçları kullanabilirsiniz. Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere).
  
> [!NOTE]
>  **Özel ayırıcı desteği** yerel bellek profili Oluşturucu çalışır ayırma toplayarak [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) sırasında çalışma zamanı tarafından yayınlanan olay verileri.  Böylece ayırma verilerini yakalanabilir ayırıcılar CRT ve Windows SDK'sı kaynak düzeyinde ek açıklama eklenen.  Kendi ayırıcılar yazıyorsanız sonra yeni ayrılmış yığın bellek için bir işaretçi döndüren herhangi işlevleri ile donatılmış [__declspec](/cpp/cpp/declspec)(Bu örnekte myMalloc görüldüğü ayırıcı):  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)` 

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Bellek anlık
> * Bellek kullanım verilerini çözümleme

## <a name="collect-memory-usage-data"></a>Bellek kullanım verilerini toplama

1.  Visual Studio'da hata ayıklama ve bellek kullanımı İnceleme başlamak istediğiniz noktada uygulamanızda bir kesme noktası ayarlamak istediğiniz projeyi açın.

    Burada, bir bellek sorunu şüphelendiğiniz bir alan varsa, bellek sorunu gerçekleşmeden önce ilk kesme noktası ayarlayın.

    > [!TIP]
    >  Uygulamanız sıklıkla ayırır ve belleği serbest bırakır ilginizi çeken bir işlem bellek profilini yakalamak için bu zor olabilir çünkü başlangıç ve bitiş tam noktası bulmak için işlemi (veya adım işlemi aracılığıyla) kesme noktaları ayarlayın bellek değişti. 

2.  İşlev veya bölge analiz etmek istediğiniz kodu sonunda ikinci bir kesme noktası ayarlayın (veya bir tespit edildiğinde alınan önlemlerin bir bellek sorunu gerçekleştikten sonra).
  
3.  **Tanılama araçları** penceresi görünür otomatik olarak, bunu devre dışı bırakmış sürece. Pencereyi ayarlayıp yeniden getirmek için tıklayın **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**.

4.  Seçin **bellek kullanımı** ile **seçtiğiniz Araçları** araç ayarlama.

     ![Tanılama araçlarını Göster](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

5.  Tıklayın **hata ayıklama / hata ayıklamayı Başlat** (veya **Başlat** araç çubuğunda veya **F5**).

     Uygulamanın yüklenmesi tamamlandığında, Tanılama Araçları'nın Özet görünümü görüntülenir.

     ![Tanılama araçları Özet sekmesi](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     > [!NOTE]
     >  Bellek anlık görüntüleri, veri, yerel veya karma mod uygulamaları hata ayıklama performansını etkileyebilir bellek toplamak için varsayılan olarak devre dışıdır. Anlık görüntüleri yerel veya karma mod uygulamalarında etkinleştirmek için hata ayıklama oturumu başlatın (kısayol tuşu: **F5**). Zaman **tanılama araçları** penceresi görüntülenirse, seçin **bellek kullanımı** sekmesine ve ardından **yığın profili oluşturmayı**.  
     >   
     >  ![Anlık görüntüleri etkinleştir](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
     >   
     >  Durdur (kısayol tuşu: **Shift**+**F5**) ve hata ayıklamayı yeniden başlatın.  

6.  Hata ayıklama oturumunuzu başlangıcında bir anlık görüntüsünü almak için seçin **anlık görüntü Al** üzerinde **bellek kullanımı** özeti araç çubuğu. (Bu da bir kesme noktası Burada ayarlanan yardımcı olabilir.)

    ![Anlık Görüntü Al](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot") 
     
     > [!TIP]
     >  Bellek karşılaştırmaları için bir temel oluşturmak için bir anlık görüntü hata ayıklama oturumunuzu başlangıcında alma göz önünde bulundurun.  

6.  İlk kesme noktasına ulaşılmasına neden olacak senaryo çalıştırın.

7.  Hata ayıklayıcıyı ilk kesme noktasında duraklatılmış durumdayken seçin **anlık görüntü Al** üzerinde **bellek kullanımı** özeti araç çubuğu.  

8.  Tuşuna **F5** , ikinci bir kesme noktasına uygulamayı çalıştırmak için.

9.  Artık, başka bir anlık görüntüsünü alın.

     Bu noktada, verileri çözümlemek başlayabilirsiniz.    
  
## <a name="analyze-memory-usage-data"></a>Bellek kullanım verilerini çözümleme
Bellek kullanımı Özet tablonun satırlarını, hata ayıklama oturumu sırasında yapılan anlık görüntülerini listeler ve bağlantılar ayrıntılı görünümler sağlar.

![Bellek Özet Tablo](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Sütun adı, seçtiğiniz proje özelliklerinde hata ayıklama modunu bağlıdır: .NET, yerel veya karma (.NET ve yerel).  
  
-   **Nesneler (fark)** ve **ayırmalar (fark)** sütunları görüntülemek nesne sayısını .NET ve yerel bellek anlık görüntü alındığında.  
  
-   **Yığın boyutu (fark)** sütunu, .NET ve yerel yığın bayt sayısını gösterir 

Birden çok anlık görüntüleri gerçekleştirdiğinizden, Özet Tablo hücrelerinin değişiklik satır anlık görüntü ve önceki anlık görüntüye arasında bir değer ekleyin.  

Bellek kullanımını analiz etme için bellek kullanımının ayrıntılı bir rapor açılır bağlantılardan birine tıklayın:  

- Geçerli anlık görüntü ve önceki anlık görüntü arasındaki fark görüntüsünün detaylarını görmeye değiştir bağlantısını sol tarafındaki oku seçin (![bellek artırmalarını](../profiling/media/prof-tour-mem-usage-up-arrow.png "bellek artırmalarını")). Kırmızı bir ok, bellek kullanımı ve düzenli bir Azalış gösterir için yeşil bir ok artış gösterir.

  > [!TIP]
  >  Bellek sorunlarını daha hızlı bir şekilde belirlemenize yardımcı olmak için fark raporları en genel numarasını artırılmış nesne türlerine göre sıralanır (değişiklik bağlantıya tıklayın **nesneler (fark)** sütun) veya en genel yığın boyutunu (tıklayın artar değişiklik bağlantıya **yığın boyutu (fark)** sütunu).

- Yalnızca seçilen anlık görüntüsünün detaylarını görmeye olmayan değiştir bağlantısını tıklayın. 
  
  Rapor, ayrı bir pencerede görüntülenir.   
  
### <a name="managed-types-reports"></a>Yönetilen türler raporları  
 Geçerli bağlantıyı seçin bir **nesneler (fark)** veya **ayırmalar (fark)** bellek kullanımı özeti tablodaki hücre.  
  
 ![Hata ayıklayıcı, yönetilen türü rapor &#45; kök yolları](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Üst bölme sayısı ve türleri boyutu türü tarafından başvurulan tüm nesnelerin boyutu da dahil olmak üzere anlık görüntünün gösterir (**kapsamlı boyut**).  
  
 **Kök yolları** alt bölme ağacında üst bölmede seçtiğiniz türüne başvuran nesneleri görüntüler. Yalnızca son türü başvurduğu yayınlandığında .NET Framework atık toplayıcı nesne için bellek temizler.  
  
 **Başvurulan türleri** üst bölmede seçilen tür tarafından tutulan başvuru ağacı görüntüler.  
  
 ![Yönetilen eferenced türleri rapor görünümü](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Seçili bir türün örneklerinin üst bölmede görüntülemek için seçin ![örneği simgesi](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") simgesi.  
  
 ![Örnekler görünümü](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Örnekleri** görünümü seçili nesnenin örneklerini üst bölmede anlık görüntüler. **Kök yolları** ve **başvurulan nesneleri** bölmesi, seçilen örnek ve seçili örneğin başvuruda türlerine başvuran nesneleri görüntüler. Hata ayıklayıcı burada anlık görüntünün alındığı noktadan durdurulduğunda üzerine gelerek **değer** hücre bir araç ipucunda nesnenin değerlerini görüntülemek için.  
  
### <a name="native-type-reports"></a>Yerel tür raporları  
 Geçerli bağlantıyı seçin bir **ayırmalar (fark)** veya **yığın boyutu (fark)** bellek kullanımı Özet tablosunu hücresinde **tanılama araçları** penceresi.  
  
 ![Yerel tür görünümü](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Türler görünümü** sayısı ve boyutu türleri anlık görüntüler.  
  
-   Örnekleri simgesini (![nesne türü sütununda örneği simgesi](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) anlık seçilen türe ait nesneleri hakkındaki bilgileri görüntülemek için seçilen bir tür.  
  
     **Örnekleri** Görünüm Seçili türünün her örneğinin görüntüler. Görüntüler oluşturma örneğinde sonuçlanan çağrı yığınını örneği seçerek **ayırma çağrı yığını** bölmesi.  
  
     ![Örnekler görünümü](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   Seçin **yığınlar görünümü** içinde **görünüm modu** seçili türü için ayırma yığını görmek için listenin.  
  
     ![Yığınlar görünümü](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Değiştir (fark) raporları  
  
- Özet tablosunu hücrede değiştir bağlantısını seçin **bellek kullanımı** sekmesinde **tanılama araçları** penceresi.  
  
   ![Bir değişiklik seçin &#40;DIF&#41;f rapor](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Anlık görüntüde seçin **Karşılaştırılacak** yönetilen veya yerel bir rapor listesi.  
  
   ![Bir anlık görüntüsünü karşılaştırmak için listeden seçin](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Değişiklik raporu sütunları ekler (ile işaretlenen **(fark)**) temel anlık görüntü değeri ile karşılaştırma anlık görüntü arasındaki fark gösteren temel bir rapor. Bir yerel tür View fark raporu nasıl görünebileceği aşağıda verilmiştir:  
  
  ![Yerel türler fark Veiw](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Bloglar ve videolar  

| | |
|---------|---------|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) bellek kullanımı ve Visual Studio 2017'de CPU kullanımını analiz etme gösteren tanılama araçlarını kullanma. |

 [Hata ayıklama sırasında CPU ve bellek çözümleme](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ blogu: Bellek, Visual C++ 2015'te profil oluşturma](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bellek kullanımı verileri toplayıp analiz öğrendiniz. Tamamladıysanız [profil oluşturucu Turu](../profiling/profiling-feature-tour.md), uygulamalarınızda CPU kullanımını analiz etme nasıl hızlı bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [CPU kullanımını analiz etme](../profiling/beginners-guide-to-performance-profiling.md) 