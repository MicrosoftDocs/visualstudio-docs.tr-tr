---
title: Grafik nesne tablosu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba3ce8aa0727471ff4385792d85659fa2d208dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809096"
---
# <a name="graphics-object-table"></a>Grafik Nesnesi Tablosu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio grafik analizi grafik nesnesi tablosu oyunlarda veya uygulamalarda karesi destekleyen Direct3D nesneleri anlamanıza yardımcı olur.  
  
 Bu nesne tablosu.  
  
 ![Bir uygulama tarafından oluşturulan Direct3D nesneleri](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Grafik nesne tablosu anlama  
 Nesne tablosu kullanarak, belirli bir çerçevenin işleme desteği Direct3D nesneleri çözümleyebilirsiniz. Belirli bir nesnesi bir işleme sorunuyla özelliklerini ve verileri inceleyerek saptayabilirler (tanılama aşamasında daha önce diğer grafik tanılama araçlarını kullanarak, beklediğiniz olmayabilir nesne listesini daraltabilirsiniz.) Soruna neden olan nesne buldunuz, bunu incelemek için türü özel bir görselleştirmeyi kullanabilirsiniz — örneğin, dokuları ve görüntülemek için görüntü Düzenleyicisi kullanabilirsiniz veya *arabellek Görselleştirici* arabellek içeriği görüntülemek için.  
  
 Nesne tablosu Kopyala ve Yapıştır destekler böylece başka bir araç kullanabilirsiniz — örneğin, Microsoft Excel — içeriğini incelemek için.  
  
### <a name="graphics-object-table-format"></a>Grafik nesne tablosu biçimi  
 Direct3D nesneleri ve seçilen olayla ilişkili çerçevesini destekleyen kaynak nesne tablosu görüntüler — örneğin, nesneleri, arabellekler, gölgelendiricileri, dokuları ve diğer kaynakların durum. Önceki bir çerçeve içinde oluşturulmuş ancak sırasında yakalanan çerçeve kullanılmayan nesneleri nesne tablosundan göz ardı edilir. Önceki olayları tarafından yakalanan çerçevesinde edildikten sonra nesneleri sonraki olayları göz ardı edilir. D3D10Device veya D3D11DeviceContext ayarlanmamış nesneler gri renkte görüntülenir. Nesneler bir tablo biçiminde görüntülenir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**tanımlayıcı**|Nesne Kimliği|  
|**Ad**|Direct3D işlevini kullanarak bir nesnede ayarlanmış uygulamaya özgü bilgileri `SetPrivateData`— tipik bir nesneyle ilgili ek kimlik bilgileri sağlamak için.|  
|**Türü**|Nesne türü.|  
|**Etkin**|Görüntüler "*" D3D10Device veya D3D11DeviceContext sırasında yakalanan kare ayarlanmış bir nesne için.<br /><br /> Bu, gri renkte görüntülenir nesnelere karşılık gelen, ancak nesne tablosu sıralama yardımcı olmak için kullanabileceğiniz bir sütun girişi sağlar.|  
|**Boyutu**|Nesnenin bayt cinsinden boyutu.|  
|**Biçim**|Nesne biçimi. Örneğin, bir doku nesnesi veya bir gölgelendirici nesnesinin gölgelendirici modeli biçimi.|  
|**Genişlik**|Bir doku nesnesine genişliği. Diğer nesne türleri için geçerli değildir.|  
|**Yükseklik**|Bir doku nesnesine yüksekliği. Diğer nesne türleri için geçerli değildir.|  
|**Derinliği**|Bir 3B doku nesne derinliği. Doku 3B değilse, değeri 0'dır. Diğer nesne türleri için geçerli değildir.|  
|**MIPS**|Bir doku nesnesine sahip MIP düzeyi sayısı. Diğer nesne türleri için geçerli değildir.|  
|**Dizi boyutu**|Bir doku dizisi dokular sayısı. Aralık geçerli bir özellik düzeyi tarafından tanımlanan bir üst sınır 1'den sağlamaktır. Bir küp eşlemi için bu değer 6 kereye küp eşlemlerinin dizideki sayısıdır.|  
|**Örnekler**|Piksel başına multisamples sayısı.|  
  
## <a name="graphics-object-viewers"></a>Grafik nesne görüntüleyiciler  
 Bir nesne hakkındaki ayrıntıları görüntülemek için nesne tablosunda adını seçerek açın. Nesne ayrıntılarını, nesne türüne bağlı olarak farklı biçimlerde görüntülenir. Örneğin, dokular, doku Görüntüleyicisi'ni kullanarak görüntülenir ve D3D11 cihaz bağlamı gibi cihaz durumu biçimlendirilmiş bir liste görüntülenir. Direct3D'ün farklı sürümlerini olun farklı nesnelerin kullanın ve çoğunlukla her sürümün en önemli nesneler için özel görselleştiriciler vardır.  
  
 Çıkış Birleştiricisi ardışık düzen aşamasını içeriğini gösteren doku Görüntüleyicisi aşağıda verilmiştir.  
  
 ![Çıkış Birleştiricisi görüntüleme doku Önizleme](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>D3D12 komut listesi  
 Direct3D 12'deki komut listesi komutlar bir komut ayırıcısı kaydeder ve böylece tek bir istek olarak GPU için gönderilebilir bir nesnedir. Komut listeleri genellikle bir dizi bir ayar durumu gerçekleştirmek, çizme, Temizle ve komutları kopyalayın. Tercih edilen yöntem, oluşumunu Direct3D 12 yapıyorsanız ve performansı artırmaya yardımcı olmak için çerçeve arasında yeniden kullanılabilir olduğundan, bunlar özellikle önemlidir. Komut listesi ayrıntılarını kendi sekmede sunulan her bir ardışık düzen aşaması ile ilgili bilgileri içeren yeni bir belge penceresinde görüntülenir.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>D3D12 komut zinciri durumu nesnesi (PSO)  
 Direct3D 12'deki bir ardışık düzen durumu nesnesi şu anda tüm kümesi gölgelendiricileri ve belirli sabit işlevi durumu nesneleri dahil olmak üzere, bir GPU durumu önemli bir bölümünü temsil eder. İşlem hattı durum nesnesi oluşturulduktan sonra sabittir; bir uygulama yalnızca işlem hattının yapılandırmasını farklı bir işlem hattı durum nesnesi bağlayarak değiştirebilirsiniz. PSO ayrıntıları hiyerarşik olarak düzenlendiği ardışık düzen yapılandırma ayrıntılarını içeren yeni bir belge penceresi görüntülenir.  
  
### <a name="d3d12-root-signature"></a>D3D12 kök imzası  
 Direct3D 12'de, kök imzası bir grafik veya işlem ardışık düzenine bağlı olan tüm kaynakları tanımlar ve komut listeleri gölgelendiriciler gerektiren kaynaklara bağlar. Genellikle grafik için bir kök imza, diğeri de bir uygulamada bir işlem yoktur. Kök imza ayrıntıları hiyerarşik olarak düzenlendiği kök imzası ilgili ayrıntıları içeren yeni bir belge penceresi görüntülenir.  
  
### <a name="d3d12-resources"></a>D3D12 kaynakları  
 Direct3D 12'deki veri işleme ardışık düzenine sağlayan catch tüm nesneleri kaynaklardır; birçok belirli nesneler için farklı türleri ve boyutları kaynakların tanımlanan Direct3D11 aksine budur. Direct3D 12 kaynak doku veri, köşe verisi, gölgelendirici veri ve daha fazlasını içerebilir — derinlik arabelleği gibi işleme hedefleri bile temsil edebilir. Bir Direct3D 12 kaynağın ayrıntılarını yeni bir belge penceresi görüntülenir; Türünü belirlemek mümkün ise grafik analizi için kaynak nesnenin içeriğini uygun Görüntüleyicisi'ni kullanır. Örneğin, doku verileri içeren bir kaynak nesne doku Görüntüleyicisi'ni kullanarak görüntülenen yalnızca bir D3D11 Texture2D gibi nesnesidir.  
  
### <a name="device-context-object"></a>Cihaz bağlamı nesnesi  
 Direct3D 11 ve Direct3D 10, cihaz bağlam (**D3D11 cihaz bağlamı** veya **D3D10 cihazı**) nesnedir özellikle önemlidir çünkü en önemli durum bilgilerini tutar ve diğer bağlantılar şu anda ayarlanmış durum nesneleri. Cihaz bağlamı ayrıntıları yeni bir belge penceresi görüntülenir ve her bilgi kategorisi vardır, kendi sekmesinde sunulur. Yeni bir olay, geçerli cihaz durumunda yansıtacak şekilde seçildiğinde, cihaz bağlam değişiklikleri.  
  
### <a name="buffer-object"></a>Arabellek nesnesi  
 Arabellek nesne ayrıntıları (D3D11 arabellek veya D3D10 arabellek) bir tablodaki arabellek içeriği sunan ve arabellek içeriği nasıl görüntüleneceğini değiştirmek için bir arabirim sağlar. yeni bir belge penceresi görüntülenir. **Arabellek veri** Tablo kopyalama destekler ve yapıştırmak ve böylece başka bir araç kullanabilirsiniz — örneğin, Microsoft Excel — içeriğini incelemek için. Arabellek içeriği değerini göre yorumlanır **biçimi** yukarıda bulunan birleşik giriş kutusu **arabellek veri** tablo. Kutusunda aşağıdaki tabloda listelenen veri türlerinden oluşan bir bileşik veri biçimi girebilirsiniz. Örneğin, "int kaydırabilirsiniz", bir 32 bitlik işaretli tamsayı değer tarafından izlenen bir 32 bit kayan nokta değeri içeren yapılarını listesini görüntüler. Belirttiğiniz bileşik veri biçimleri daha sonra kullanmak için birleşik giriş kutusu eklenir.  
  
 Ayrıca geçiş yapabilirsiniz **Göster'e kaydırır** arabellek uzaklığı her öğenin görüntülemek veya gizlemek için onay kutusu.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|**float**|32 bit kayan nokta değeri.|  
|**float2**|İki 32-bit kayan nokta değerleri içeren vektör.|  
|**float3**|Üç 32-bit kayan nokta değerleri içeren vektör.|  
|**float4**|Dört 32-bit kayan nokta değerleri içeren vektör.|  
|**byte**|8-bit imzalı tamsayı değeri.|  
|**2 bayt**|Bir 16 bitlik işaretli tamsayı değeri.|  
|**4 bayt**|Bir 32 bitlik işaretli tamsayı değeri. Aynı **int**.|  
|**8 bayt**|Bir 64-bit imzalı bir tamsayı değeri. Aynı **Int64**.|  
|**xbyte kullanılıyor**|Bir 8 bit onaltılık değeri.|  
|**x2byte**|Bir 16 bitlik onaltılık değer.|  
|**x4byte**|Bir 32 bit onaltılık değer. Aynı **xint**.|  
|**x8byte**|Bir 64-bit onaltılık değer. Aynı **xint64**.|  
|**ubyte**|8 bitlik işaretsiz tamsayı değeri.|  
|**u2byte**|Bir 16 bitlik işaretsiz tamsayı değeri.|  
|**u4byte**|Bir 32-bit işaretsiz tamsayı değeri. Aynı **uint**.|  
|**u8byte**|Bir 64-bit işaretsiz tamsayı değeri. Aynı **uint64**.|  
|**Yarı**|16-bit kayan nokta değeri.|  
|**half2**|İki 16-bit kayan nokta değerleri içeren vektör.|  
|**half3**|Üç 16-bit kayan nokta değerleri içeren vektör.|  
|**half4**|Dört 16-bit kayan nokta değerleri içeren vektör.|  
|**double**|64-bit kayan nokta değeri.|  
|**int**|Bir 32 bitlik işaretli tamsayı değeri. Aynı **4 baytlık**.|  
|**int64**|Bir 64-bit imzalı bir tamsayı değeri. Aynı **8 baytlık**.|  
|**xint**|Bir 32 bit onaltılık değer. Aynı **x4byte**.|  
|**xint64**|Bir 64-bit onaltılık değer. Aynı **x8byte**.|  
|**uint**|Bir 32-bit işaretsiz tamsayı değeri. Aynı **u4byte**.|  
|**uint64**|Bir 64-bit işaretsiz tamsayı değeri. Aynı **u8byte**.|  
|**bool**|Bir Boole değeri (`true` veya `false`) değeri. Her bir Boole değeri bir 32-bit değeri tarafından temsil edilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik tanılama (DirectX grafik hata ayıklama)](../debugger/visual-studio-graphics-diagnostics.md)   
 [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](../debugger/walkthrough-missing-objects-due-to-device-state.md)



