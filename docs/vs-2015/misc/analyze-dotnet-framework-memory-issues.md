---
title: .NET Framework bellek sorunlarını çözümleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: douge
ms.openlocfilehash: 5b5b79e351f828f443e133f40c322ffba3f1a8b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810487"
---
# <a name="analyze-net-framework-memory-issues"></a>.NET Framework bellek sorunlarını çözümleme
Visual Studio tarafından yönetilen bellek çözümleyicisini kullanarak .NET Framework kodu içindeki bellek sızıntılarını ve verimsiz bellek kullanımını bulun. En düşük .NET Framework sürümü hedef kodun .NET Framework 4. 5 ' dir.  
  
 Bellek analizi aracı bilgileri analiz eder *düküm dosyalarında yığın verisine sahip* , bir uygulamanın belleğindeki nesnelerin bir kopyasını. Döküm (.dmp) dosyalarını Visual Studio IDE'den veya diğer sistem araçlarını kullanarak toplayabilirsiniz.  
  
- Nesne türlerinin bellek kullanımı üzerindeki göreli etkisini anlamak ve uygulamanızda belleği verimsiz kullanan kodu bulmak için tek bir anlık görüntüyü anailz edebilirsiniz.  
  
- Ayrıca karşılaştırabilirsiniz (*fark*) zaman içinde bellek neden iki anlık görüntü alanlar kodunuzda bulmak için bir uygulamanın kullanın.  
  
  Yönetilen bellek çözümleyicisinin bir kılavuz için bkz. [üretimde .NET bellek sorunlarını tanılamak için Visual Studio 2013 kullanarak](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) Visual Studio ALM + Team Foundation Server blog'daki.  
  
##  <a name="BKMK_Contents"></a> İçeriği  
 [.NET Framework uygulamalarında bellek kullanımı](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Bir uygulamada bir bellek sorunu tanımlama](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Bellek anlık görüntüleri toplama](#BKMK_Collect_memory_snapshots)  
  
 [Bellek kullanımını analiz etme](#BKMK_Analyze_memory_use)  
  
##  <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> .NET Framework uygulamalarında bellek kullanımı  
 .NET Framework, atık toplama yapılan bir çalışma zamanıdır, böylelikle çoğu uygulamada bellek kullanımı bir sorun değildir. Ancak web servisleri ve uygulamaları gibi uzun süre çalışan uygulamalarda ve sınırlı miktarda belleğe sahip aygıtlarda, bellekte nesnelerin birikmesi, uygulamanın ve üzerinde çalıştığı aygıtın performansını etkileyebilir. Atık toplayıcı çok sık çalışıyorsa veya işletim sistemi, RAM ve disk arasında bellek taşımak zorunda kalıyorsa, aşırı bellek kullanımı, uygulamaya veya makineye yeterli kaynak kalmamasına neden olabilir. En kötü durumda, bir uygulama bir "Yetersiz bellek" özel durumuyla çökebilir.  
  
 .NET *Yönetilen yığın* bir uygulama tarafından oluşturulan başvuru nesnelerinin depolandığı bir sanal bellek bölgesidir. Nesnelerin kullanım ömrü atık toplayıcı (GC) tarafından yönetilir. Atık toplayıcı, bellek bloklarını kaplayan nesneleri izlemek için başvurular kullanır. Bir başvuru, bir nesne oluşturulduğunda ve bir değişkene atandığında oluşturulur. Tek bir nesne birden çok başvuruya sahip olabilir. Örneğin, nesneyi bir sınıfa, koleksiyona ve başka veri yapısına ekleyerek veya nesneyi ikinci bir değişkene atayarak ek başvurular oluşturulabilir. Bir başvuru oluşturmanın daha az belirgin bir yolu, bir nesnenin, başka bir nesnenin olayına bir işleyici eklemesidir. Bu durumda, işleyici açıkça kaldırılana veya ikinci nesne yok edilene kadar ikinci nesne ilk nesnenin başvurusunu tutar.  
  
 Her uygulama için, atık toplayıcı, uygulama tarafından başvurulan nesneleri izleyen bir başvuru ağacı tutar. *Başvuru ağacı* genel ve statik nesneler, ilgili iş parçacığı yığınlarını yanı sıra ve dinamik olarak içeren bir kök kümesine örneklenen nesneleri. Ona başvurusu olan en az bir üst nesneye sahipse bir nesnenin kökü belirtilir. Atık toplayıcı, yalnızca uygulamada başka hiçbir nesnenin veya değişkenin başvurmadığı bir nesnenin belleğini geri kazanabilir.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Bir uygulamada bir bellek sorunu tanımlama  
 Bellek sorunlarının en çok görünen belirtisi uygulamanızın performansıdır, özellikle performans zamanla düşüyorsa. Uygulamanız çalışırken diğer uygulamaların performansının düşmesi de bir bellek sorunu olduğunu belirtebilir. Bir bellek sorunu olduğundan şüpheleniyorsanız, Görev Yöneticisi'gibi bir araç kullanın veya [Windows Performans İzleyicisi'ni](http://technet.microsoft.com/library/cc749249.aspx) daha fazla araştırmak için. Örneğin, toplam bellek büyüklüğünde, olası bellek sızıntılarının kaynağı olarak açıklayamadığınız bir artış olup olmadığına bakın:  
  
 ![Kaynak İzleyicisi tutarlı bellek büyüme](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Ayrıca, bir yordamda verimsiz bellek kullanımına işaret edecek şekilde, kodun önereceğini beklediğiniz miktarı aşan anlık bellek artışlarına bakın:  
  
 ![Kaynak Yöneticisi'nde bellekte ani](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
##  <a name="BKMK_Collect_memory_snapshots"></a> Bellek anlık görüntüleri toplama  
 Bellek analizi aracı bilgileri analiz eder *düküm dosyalarında* yığın bilgileri içerir. Visual Studio'da döküm dosyaları oluşturabilir veya gibi bir araç kullanabilirsiniz [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) gelen [Windows SysInternals](http://technet.microsoft.com/sysinternals). Bkz: [döküm nedir ve biri nasıl oluşturabilirim?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) Visual Studio Debugger Team blogunda.  
  
> [!NOTE]
>  Çoğu araç, döküm bilgisini, tam yığın belleği verilerini içerecek veya içermeyecek şekilde toplayabilir. Visual Studio bellek çözümleyicisi tam yığın bilgisi gerektirir.  
  
 **Visual Studio'dan bir döküm toplamak için**  
  
1. Visual Studio projesinden başlatılan bir işlem için bir döküm dosyası oluşturabilirsiniz, veya hata ayıklayıcıyı çalışan bir işleme ekleyebilirsiniz. Bkz: [çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Yürütmeyi durdurun. Hata ayıklayıcıyı durdurur seçtiğinizde **tümünü Kes** üzerinde **hata ayıklama** menüsünden veya bir özel durumda veya bir kesme noktası  
  
3. Üzerinde **hata ayıklama** menüsünde seçin **dökümü Farklı Kaydet**. İçinde **dökümü Farklı Kaydet** iletişim kutusunda bir konum belirtin ve emin **yığınlı** (varsayılan) seçili olduğundan **farklı kaydetme türü** listesi.  
  
   **İki bellek anlık görüntüsünü karşılaştırmak için**  
  
   Bir uygulamanın bellek kullanımındaki artışı analiz etmek için, uygulamanın tek bir örneğinden iki döküm dosyası toplayın.  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Analyze_memory_use"></a> Bellek kullanımını analiz etme  
 [Nesne listesini filtreleme](#BKMK_Filter_the_list_of_objects) **&#124;** [tek bir anlık görüntüden bellek verileri analiz etme](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [iki bellek karşılaştırın anlık görüntüleri](#BKMK_Compare_two_memory_snapshots)  
  
 Bellek kullanımı sorunları için bir döküm dosyasını analiz etmek amacıyla:  
  
1. Visual Studio'da **dosya**, **açık** ve döküm dosyasını belirtin.  
  
2. Üzerinde **mini döküm dosya özeti** sayfasında **yönetilen bellekte Hata Ayıkla**.  
  
    ![Bilgi döküm Özet sayfası dosya](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Bellek çözümleyicisi, dosyayı analiz etmek için bir hata ayıklama oturumu başlatır ve sonuçları Yığın Görünümü sayfasında görüntüler:  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Filter_the_list_of_objects"></a> Nesne listesini filtreleme  
 Varsayılan olarak, bellek çözümleyicisi, bir bellek anlık görüntüsündeki nesne listesini yalnızca kullanıcı kodundaki türleri ve örnekleri gösterecek şekilde ve yalnızca toplam kapsamalı boyutu toplam yığın boyutunun bir eşik yüzdesini geçen türleri gösterecek şekilde filtreler. Bu seçenekleri değiştirebilirsiniz **görünüm ayarlarını** listesi:  
  
|||  
|-|-|  
|**Yalnızca kendi kodumu etkinleştir**|Yalnızca Kendi Kodum, en genel sistem nesnelerini gizler, böylelikle listede yalnızca sizin oluşturduğunuz türler görüntülenir.<br /><br /> Visual Studio'da yalnızca kendi kodum seçeneğini de ayarlayabilirsiniz **seçenekleri** iletişim kutusu. Üzerinde **hata ayıklama** menüsünde seçin **seçenekler ve ayarlar**. İçinde **hata ayıklama**/**genel** sekmesinde seçin veya temizleyin **yalnızca kendi kodum**.|  
|**Küçük nesneleri Daralt**|**Küçük nesneleri Daralt** toplam kapsamalı boyutu toplam yığın boyutunun yüzde 0,5'den az olan tüm türleri gizler.|  
  
 Tür listesini bir dize girerek de filtreleyebilirsiniz **arama** kutusu. Listede yalnızca, adları dizeyi içeren türler görüntülenir.  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
###  <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Tek bir anlık görüntüden bellek verileri analiz etme  
 Visual Studio dosyayı analiz etmek için yeni bir hata ayıklama oturumu başlatır ve bellek verileri bir yığın Görünümü penceresinde görüntüler.  
  
 ![Nesne türü listesinde](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Nesne türü tablosu  
 Üstteki tabloda, bellekte tutulan nesne türleri listelenir.  
  
- **Sayısı** anlık görüntüde türün örneklerinin sayısını gösterir.  
  
- **Boyut (bayt)** başvurularını tuttuğu nesnelerin boyutunu hariç, türünün tüm örneklerini boyutudur. Bu  
  
- **Kapsamlı boyut (bayt)** başvurulan nesnelerin boyutunu içerir.  
  
  Örnekler simgesi seçebilirsiniz (![nesne türü sütun örneği simgeye](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) içinde **nesne türü** örneklerinin listesini görüntülemek için sütun yazın.  
  
#### <a name="instance-table"></a>Örneği tablosu  
 ![Örnek tablo](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Örnek** nesnesinin nesne tanımlayıcısı görev yapan nesnenin bellek konumu  
  
- **Değer** değer türlerinin gerçek değeri gösterir. Veri değerlerini bir veri ipucunda görüntülemek için bir başvuru türü adının üzerine gelebilirsiniz.  
  
   ![Örnek bir veri ipucunda değerleri](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Boyut (bayt)** başvurularını tuttuğu nesnelerin boyutunu hariç nesnenin boyutu. Bu  
  
- **Kapsamlı boyut (bayt)** başvurulan nesnelerin boyutunu içerir.  
  
  Varsayılan olarak, göre sıralanır türlerinin ve örneklerinin **kapsamlı boyut (bayt)**. Sıralama düzenini değiştirmek için listede bir sütun başlığı seçin.  
  
#### <a name="paths-to-root"></a>Kök yolları  
  
-   Bir tür seçildiği için **nesne türü** tablo **kök yolları** tablo dönüşen başvuru sayısını türdeki tüm nesneler için kök nesnelere giden benzersiz tür hiyerarşileri gösterir hiyerarşide olduğu türü.  
  
-   Bir nesne türünün örneğinden seçili için **kök yolları** örneğe bir başvuru tutan gerçek nesnelerin bir grafiğini gösterir. Veri değerlerini bir veri ipucunda görüntülemek için nesne adının üzerine gelebilirsiniz.  
  
#### <a name="referenced-types--referenced-objects"></a>Başvurulan türleri / başvurulan nesneler  
  
- Bir tür seçildiği için **nesne türü** tablo **başvurulan türleri** sekmesi seçili türdeki tüm nesneler tarafından tutulan başvurulan türlerin sayısı ve boyutu gösterir.  
  
- Bir türün seçili bir örneği için **başvurulan nesneleri** seçilen örnek tarafından tutulan nesneleri gösterir. Veri değerlerini bir veri ipucunda görüntülemek için ada üzerine getirin.  
  
  **Döngüsel başvurular**  
  
  Bir nesne, ilk nesneye doğrudan veya dolaylı olarak bir başvuru tutan ikinci bir nesneye başvurabilir. Bellek Çözümleyicisi bu durumla karşılaştığında başvuru yolunu genişletmeyi durdurur ve ekler bir **[döngü algılandı]** döküm ek açıklama ilk nesne ve durur.  
  
  **Kök türleri**  
  
  Bellek çözümleyicisi, kök nesnelerine, tutulmakta olan başvuru türünü açıklayan ek açıklamalar ekler:  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**Statik değişken** `VariableName`|Bir statik değişken. `VariableName`, değişkenin adıdır.|  
|**Sonlandırma işleyicisi**|Sonlandırma sırasından bir başvuru.|  
|**Yerel değişken**|Yerel bir değişken.|  
|**Güçlü işleyici**|Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.|  
|**Zaman uyumsuz. Sabitlenmiş işleyici**|Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.|  
|**Bağımlı işleyici**|Nesne işleyicisi tablosundan bir bağımlı nesne.|  
|**Sabitlenmiş işleyici**|Nesne işleyicisi tablosundan bir sabitlenmiş güçlü başvuru.|  
|**RefCount işleyicisi**|Nesne işleyicisi tablosundan bir başvurusu sayılan nesne.|  
|**SizedRef işleyicisi**|Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.|  
|**Sabitlenmiş yerel değişken**|Sabitlenmiş bir yerel değişken.|  
  
###  <a name="BKMK_Compare_two_memory_snapshots"></a> İki bellek anlık görüntüsünü karşılaştırma  
 Bellek sızıntılarının kaynağı olabilecek nesneler bulmak üzere bir işlemin iki döküm dosyasını karşılaştırabilirsiniz. İlk (önceki) ve ikinci (sonraki) dosyanın toplanması arasındaki aralık, sızan nesne sayısı artışı kolayca görülebilecek kadar büyük olmalıdır. İki dosyayı karşılaştırmak için:  
  
1. İkinci döküm dosyasını açın ve ardından **yönetilen bellekte Hata Ayıkla** üzerinde **mini döküm dosya özeti** sayfası.  
  
2. Bellek analizi raporu sayfasında açın **Select temel** listeleyin ve ardından **Gözat** ilk döküm dosyasını belirtin.  
  
   Çözümleyici sütunları arasındaki farkı görüntüler raporun üst bölmesine ekler **sayısı**, **boyutu**, ve **kapsamlı boyut** bu değerlere türleri Önceki anlık görüntü.  
  
   ![Fark sütun türü listesinde](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **başvuru sayısı farkı** sütunu da eklenir **kök yolları** tablo.  
  
   ![Başa dön](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VS ALM TFS Blog: Üretimde .NET bellek sorunlarını tanılamak için Visual Studio 2013 kullanarak.](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; yönetilen bellek analizi](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio araç kutusu &#124; yönetilen bellek analizi Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)