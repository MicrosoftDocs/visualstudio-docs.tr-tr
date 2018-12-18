---
title: Bellek kullanımı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f62137fcbc71df87fb0569ed0516a7ae36d8a30a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746202"
---
# <a name="memory-usage"></a>Bellek kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklayıcıyla tümleştirilmiş ile hata ayıklarken bellek sızıntılarını ve verimsiz bellek Bul **bellek kullanımı** Tanılama aracı. Bir veya daha fazla atmanız bellek kullanımı aracı sağlar *anlık görüntüleri* yönetilen ve yerel bellek yığın. .NET, yerel veya karma mod (.NET ve yerel) uygulamaları, anlık toplayabilirsiniz.  
  
- Nesne türlerinin bellek kullanımı üzerindeki göreli etkisini anlamak ve uygulamanızda belleği verimsiz kullanan kodu bulmak için tek bir anlık görüntüyü anailz edebilirsiniz.  
  
- Zaman içinde bellek kullanımı neden (fark) iki anlık görüntüsünü uygulama kodunuzda alanlar bulmak için de karşılaştırabilirsiniz.  
  
  Aşağıdaki grafik gösterildiği **tanılama araçları** penceresi Visual Studio 2015 güncelleştirme 1'de:  
  
  ![DiagnosticTools&#45;güncelleştirme 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-güncelleştirme 1")  
  
  Her zaman bellek anlık görüntüleri toplama rağmen **bellek kullanımı** aracı, performans sorunlarını araştırma sırasında uygulamanızın nasıl yürütür denetlemek için Visual Studio hata ayıklayıcısını kullanabilirsiniz. Kesme noktaları, Adımlama, tümünü Kes ve diğer hata ayıklayıcı eylemlerini performans araştırmalarınıza en uygun olan kod yollarında odaklanmanıza yardımcı olabilir. Uygulamanız çalışırken bu eylemleri gerçekleştirmek ortadan kaldırır, bir sorunu tanılamak için gereken süreyi önemli ölçüde azaltabilir ve sizi ilgilendirmeyen kodu paraziti.  
  
  Hata ayıklayıcının dışında bellek Aracı'nı kullanabilirsiniz. Bkz: [hata ayıklama olmadan bellek kullanımı](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
>  **Özel ayırıcı desteği** yerel bellek profili Oluşturucu çalışır ayırma toplayarak [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) sırasında çalışma zamanı tarafından yayınlanan olay verileri.  Böylece ayırma verilerini yakalanabilir ayırıcılar CRT ve Windows SDK'sı kaynak düzeyinde ek açıklama eklenen.  Kendi ayırıcılar yazıyorsanız, yeni ayrılmış yığın için bir işaretçi döndüren tüm İşlevler'den bellek tasarlanabilir [__declspec](http://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(Bu örnekte myMalloc görüldüğü ayırıcı):  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Hata ayıklayıcısı ile bellek kullanımını analiz etme  
  
> [!NOTE]
>  Bellek anlık görüntüleri, veri, yerel veya karma mod uygulamaları hata ayıklama performansını etkileyebilir bellek toplamak için varsayılan olarak devre dışıdır. Anlık görüntüleri yerel veya karma mod uygulamaları etkinleştirmek için hata ayıklama oturumu başlatın (kısayol tuşu: **F5**). Zaman **tanılama araçları** penceresi görüntülenirse, bellek kullanımı sekmesini seçin ve ardından **anlık görüntüleri etkinleştir**.  
>   
>  ![Anlık görüntüleri etkinleştir](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
>  Durdur (kısayol tuşu: **Shift + F5 tuşlarına basarak**) ve hata ayıklamayı yeniden başlatın.  
  
 Bellek durumu yakalamak istediğinizde seçin **anlık görüntü Al** üzerinde **bellek kullanımı** özeti araç çubuğu.  
  
 ![Anlık Görüntü Al](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Bellek karşılaştırmaları için bir temel oluşturmak için bir anlık görüntü hata ayıklama oturumunuzu başlangıcında alma göz önünde bulundurun.  
>   -   Başlangıç ve bitiş istediğiniz işlemin veya tam bulma işlemi Adımlama, kesme noktaları belirleyin, uygulamanızı sık ayırır ve belleği serbest bırakır ilginizi çeken bir işlem bellek profilini yakalamak için bu zor olabilir çünkü noktası bellek değişti.  
  
## <a name="viewing-memory-snapshot-details"></a>Bellek anlık görüntü ayrıntılarını görüntüleme  
 Bellek kullanımı Özet tablonun satırlarını hata ayıklama oturumu sırasında yapılan anlık görüntüleri listelenmektedir.  
  
 Sütunları satır, seçtiğiniz proje özelliklerinde hata ayıklama modunu bağlıdır: .NET, yerel veya karma (.NET ve yerel).  
  
- **Yönetilen nesne**s ve **yerel ayırmaları** sütunları görüntülemek nesne sayısını .NET ve yerel bellek anlık görüntü alındığında.  
  
- **Yönetilen yığın boyutu** ve **yerel yığın boyutu** sütunlar, .NET ve yerel yığın bayt sayısını gösterir  
  
- Birden çok anlık görüntüleri gerçekleştirdiğinizden, Özet Tablo hücrelerinin değişiklik satır anlık görüntü ve önceki anlık görüntüye arasında bir değer ekleyin.  
  
   ![Bellek Özet Tablo hücresi](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Ayrıntı raporu görüntülemek için:**  
  
- Görüntülemek için seçilen anlık görüntü ayrıntılarını geçerli bağlantıyı seçin.  
  
- Geçerli anlık görüntü ve önceki anlık görüntü arasındaki fark görüntüsünün detaylarını görmeye değiştir bağlantısını seçin.  
  
  Rapor, ayrı bir pencerede görüntülenir.  
  
## <a name="memory-usage-details-reports"></a>Bellek Kullanım raporları ayrıntıları  
  
### <a name="managed-types-reports"></a>Yönetilen türler raporları  
 Geçerli bağlantıyı seçin bir **yönetilen nesneleri** veya **Yönetilen yığın boyutu** bellek kullanımı özeti tablodaki hücre.  
  
 ![Hata ayıklayıcı, yönetilen türü rapor &#45; kök yolları](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Üst bölme sayısı ve türleri boyutu türü tarafından başvurulan tüm nesnelerin boyutu da dahil olmak üzere anlık görüntünün gösterir (**kapsamlı boyut**).  
  
 **Kök yolları** alt bölme ağacında üst bölmede seçtiğiniz türüne başvuran nesneleri görüntüler. Yalnızca son türü başvurduğu yayınlandığında .NET Framework atık toplayıcı nesne için bellek temizler.  
  
 **Başvurulan türleri** üst bölmede seçilen tür tarafından tutulan başvuru ağacı görüntüler.  
  
 ![Yönetilen eferenced türleri rapor görünümü](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Seçili bir türün örneklerinin üst bölmede görüntülemek için seçin ![örneği simgesi](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") simgesi.  
  
 ![Örnekler görünümü](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Örnekleri** görünümü seçili nesnenin örneklerini üst bölmede anlık görüntüler. Kök ve başvurulan nesneleri bölmesinde yolları seçilen örnek ve seçili örneğin başvuruda türlerine başvuran nesneleri görüntüler. Hata ayıklayıcı burada anlık görüntünün alındığı noktadan durdurulduğunda bir araç ipucunda nesnenin değerlerini görüntülemek için Değer hücresini üzerine gelerek.  
  
### <a name="native-type-reports"></a>Yerel tür raporları  
 Geçerli bağlantıyı seçin bir **yerel ayırmaları** veya **yerel yığın boyutu** bellek kullanımı Özet tablosunu hücresinde **tanılama araçları** penceresi.  
  
 ![Yerel tür görünümü](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Türler görünümü** sayısı ve boyutu türleri anlık görüntüler.  
  
-   Örnekleri simgesini (![nesne türü sütununda örneği simgesi](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) anlık seçilen türe ait nesneleri hakkındaki bilgileri görüntülemek için seçilen bir tür.  
  
     **Örnekleri** Görünüm Seçili türünün her örneğinin görüntüler. Görüntüler oluşturma örneğinde sonuçlanan çağrı yığınını örneği seçerek **ayırma çağrı yığını** bölmesi.  
  
     ![Örnekler görünümü](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   Seçin **yığınlar görünümü** içinde **görünüm modu** seçili türü için ayırma yığını görmek için listenin.  
  
     ![Yığınlar görünümü](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Değiştir (fark) raporları  
  
- Özet tablosunu hücrede değiştir bağlantısını seçin **bellek kullanımı** sekmesinde **tanılama araçları** penceresi.  
  
   ![Bir değişiklik seçin &#40;DIF&#41;f rapor](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Anlık görüntüde seçin **Karşılaştırılacak** yönetilen veya yerel bir rapor listesi.  
  
   ![Bir anlık görüntüsünü karşılaştırmak için listeden seçin](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Değişiklik raporu sütunları ekler (ile işaretlenen **(fark)**) temel anlık görüntü değeri ile karşılaştırma anlık görüntü arasındaki fark gösteren temel bir rapor. Bir yerel tür View fark raporu nasıl görünebileceği aşağıda verilmiştir:  
  
  ![Yerel türler fark Veiw](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Bloglar ve videolar  
 [Visual Studio 2015'te tanılama araçları hata ayıklayıcı penceresi](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [Blog: Visual Studio 2015'te hata ayıklama bellek kullanımı aracı](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/13/memory-usage-tool-while-debugging-in-visual-studio-2015.aspx)  
  
 [Visual C++ blogu: VS2015 preview'da yerel Bellek Tanılama](http://blogs.msdn.com/b/vcblog/archive/2014/11/21/native-memory-diagnostics-in-vs2015-preview.aspx)  
  
 [Visual C++ blogu: Visual Studio 2015 CTP yerel Bellek Tanılama araçları](http://blogs.msdn.com/b/vcblog/archive/2014/06/04/native-memory-diagnostic-tools-for-visual-studio-14-ctp1.aspx)




