---
title: Grafik nesnesi tablosu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d58c219069efcc98fccaa52dff5bd156212ea64d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477771"
---
# <a name="graphics-object-table"></a>Grafik Nesnesi Tablosu
Visual Studio grafik analizi grafik nesnesi tablosu çerçeve oyun veya uygulama desteği Direct3D nesneleri anlamanıza yardımcı olur.  
  
 Bu nesne tablo.  
  
 ![Uygulama tarafından oluşturulan Direct3D nesneleri](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Grafik nesnesi tablosu anlama  
 Nesne tabloyu kullanarak, belirli bir çerçeve işlemeyi destekleyen Direct3D nesneleri analiz edebilirsiniz. Bir işleme sorun belirli bir nesnenin özelliklerini ve veri inceleyerek saptayabilirler (daha önce tanılama aşamasında diğer grafik tanılama araçlarını kullanarak, beklediğiniz olmayabilir nesnelerin listesini daraltabilirsiniz.) Soruna neden olan nesne buldunuz, onu incelemek için kendi türüne özgü bir görsel öğe kullanabilirsiniz — örneğin, doku, görüntülemek için görüntü Düzenleyicisi kullanabilirsiniz veya *arabellek Görselleştirici* arabellek içeriğini görüntülemek için.  
  
 Başka bir araç kullanabilmesi için Kopyala ve Yapıştır nesnesi tablosu destekler — Örneğin, Microsoft Excel — içeriğini incelemek için.

 Ayrıca, kullanabileceğiniz **türü** açılır üst sol köşe görüntüleme nesne türü geçiş yapmak için **arabellekleri**, **gölgelendiriciler** veya **dokuları**, veya bunların tümü öğeleri aynı anda.  Ayrıca, tüm sunulan veri belirli satırları bulmak için sağ üst köşedeki arama kutusunu kullanabilirsiniz.  Örneğin, için araması yapabilirsiniz *D32_FLOAT* bu biçimi nesnelerin tüm örnekleri listesinde bulunamadı.
  
### <a name="graphics-object-table-format"></a>Grafik nesnesi tablosu biçimi  
 Nesne tablosu Direct3D nesneleri ve seçili olayla ilişkili çerçeve desteği kaynakları görüntüler — örneğin, nesneler, arabellek, gölgelendiriciler, doku ve diğer kaynakları belirtin. Önceki bir çerçevede oluşturulmuş ancak yakalanan çerçevesinde kullanılmayan nesneleri nesneyi tablosundan göz ardı edilir. Önceki olaylar tarafından yakalanan çerçevesinde yok edildi nesneleri sonraki olaylarda göz ardı edilir. D3D10Device veya D3D11DeviceContext ayarlı değil nesneler gri renkte görüntülenir. Nesneler bir tablo biçiminde görüntülenir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Tanımlayıcı**|Nesne Kimliği|  
|**Ad**|Bir nesne üzerinde Direct3D işlevini kullanarak ayarlandı uygulamaya özgü bilgileri `SetPrivateData`— tipik bir nesne hakkındaki ek tanımlayıcı bilgileri sağlamak için.|  
|**Türü**|Nesne türü.|  
|**Etkin**|Görüntüler "*" D3D10Device veya D3D11DeviceContext yakalanan çerçevesinde ayarlandı bir nesne için.<br /><br /> Bu gri renkte görüntülenir nesneleri karşılık gelir, ancak nesnesi tablosu sıralama yardımcı olmak için kullanabileceğiniz bir sütun girişi sağlar.|  
|**Boyutu**|Nesnenin bayt cinsinden boyutu.|  
|**Biçimi**|Nesne biçimi. Örneğin, bir doku nesnesi veya bir gölgelendirici nesnesinin gölgelendirici modeli biçimi.|  
|**Genişlik**|Bir doku nesnesi genişliği. Diğer nesne türleri için geçerli değildir.|  
|**Yükseklik**|Bir doku nesnesi yüksekliği. Diğer nesne türleri için geçerli değildir.|  
|**Derinliği**|Bir 3B doku nesnesi derinliği. Bir doku 3-b değilse, değeri 0'dır. Diğer nesne türleri için geçerli değildir.|  
|**MIPS**|Bir doku nesnesi MIP düzey sayısı. Diğer nesne türleri için geçerli değildir.|  
|**ArraySize**|Dokular doku dizisindeki sayısı. Geçerli özellik düzeyi tarafından tanımlanan bir üst sınırı için 1'den aralığıdır. Bir küp eşleme için bu değer 6 kereye dizideki küp haritalarının sayıdır.|  
|**Örnekler**|Multisamples / piksel sayısı.|  
  
## <a name="graphics-object-viewers"></a>Grafik nesne görüntüleyiciler  
 Bir nesne hakkındaki ayrıntıları görüntülemek için nesne tablosundaki adını seçerek açın. Nesne ayrıntılarını nesne türüne bağlı olarak farklı biçimlerde görüntülenir. Örneğin, doku doku Görüntüleyicisi'ni kullanarak görüntülenir ve Aygıt durumu D3D11 cihaz bağlamı gibi biçimlendirilmiş bir liste olarak görüntülenir. Direct3D farklı sürümlerini olun farklı nesnelerin kullanın ve çoğunlukla her sürümün en önemli nesneler için belirli görselleştiriciler vardır.  
  
 Çıktı birleşme ardışık düzen aşaması içeriğini gösteren doku Görüntüleyicisi'ni aşağıda verilmiştir.  
  
 ![Çıktı birleşme görüntüleme doku Önizleme](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>D3D12 komut listesi  
 Direct3D 12'de komut listesini komutları Komut ayırıcısı kaydeder ve böylece tek bir istek olarak GPU için gönderilebilir bir nesnedir. Komut listeleri genellikle durumu ayarı, bir dizi gerçekleştirmek, çizim, temizleyin ve komutları kopyalayın. Direct3D 12 işlemede tercih edilen yöntemi olduğunuz ve performansını artırmaya yardımcı olmak için çerçeveler arasında yeniden kullanılabilir çünkü bunlar özellikle önemlidir. Komut listesi ayrıntılarını kendi sekmesinde sunulan her ardışık düzen aşaması ilgili bilgiler içeren yeni bir belge penceresinde görüntülenir.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>D3D12 ardışık düzen durum nesnesi (PSO)  
 Direct3D 12'de bir ardışık düzen durumu nesnesi şu anda tüm kümesi gölgelendiriciler ve belirli sabit işlevi durum nesneleri dahil olmak üzere GPU durumu önemli bir kısmını temsil eder. Oluşturduktan sonra bir ardışık düzen durumu nesnesi sabittir — bir uygulamayı yalnızca ardışık düzen yapılandırma farklı ardışık düzen durum nesnesi bağlayarak değiştirebilirsiniz. PSO ayrıntıları hiyerarşik olarak düzenlendiği ardışık düzen yapılandırma ayrıntılarını ile yeni bir belge penceresi görüntülenir.  
  
### <a name="d3d12-root-signature"></a>D3D12 kök imza  
 Direct3D 12, grafik veya işlem bir ardışık düzene bağlı olan tüm kaynakları kök imza tanımlar ve komut listeleri gölgelendiriciler gerektiren kaynaklara bağlar. Genellikle bir kök imza grafikler ve işlem bir uygulama için bir tane yoktur. Kök imzası ayrıntıları hiyerarşik olarak düzenlendiği kök imzasının ayrıntılarını ile yeni bir belge penceresi görüntülenir.  
  
### <a name="d3d12-resources"></a>D3D12 kaynakları  
 Direct3D 12'de, veri işleme ardışık düzenine sağlayan catch tüm nesneleri kaynaklardır; birçok belirli nesneler için değişik ve kaynakların boyutları tanımlanan Direct3D11 aksine budur. Direct3D 12 kaynak doku veri, köşe veri, gölgelendirici verilerini ve daha fazlasını içerebilir: render hedefleri derinliği arabellek gibi bile temsil edebilir. Direct3D 12 kaynak ayrıntılarını yeni bir belge penceresinde görüntülenir; Türü belirlemek mümkün ise grafik analiz kaynak nesnesi içeriği için uygun Görüntüleyicisi'ni kullanın. Örneğin, doku verileri içeren bir kaynak nesnesi doku Görüntüleyicisi'ni kullanarak görüntülenen yalnızca bir D3D11 Texture2D gibi nesnesidir.  
  
### <a name="device-context-object"></a>Aygıt bağlam nesnesi  
 Direct3D 11 ve Direct3D 10, cihaz bağlamı (**D3D11 cihaz bağlamı** veya **D3D10 aygıt**) nesnesidir özellikle önemlidir çünkü en önemli durum bilgilerini tutar ve diğer bağlantılar şu anda ayarlanmış durum nesneleri. Cihaz bağlamı ayrıntıları yeni bir belge penceresinde görüntülenir ve her kategori bilgilerinin var. kendi sekmesinde sunulur. Yeni bir olay geçerli aygıt durumunu yansıtacak şekilde seçildiğinde cihaz bağlam değişiklikleri.  
  
### <a name="buffer-object"></a>Arabellek nesnesi  
 Arabellek nesne ayrıntıları (D3D11 arabellek veya D3D10 arabellek) bir tabloda arabellek içeriği sunan ve arabellek içeriği görüntülenme biçimini değiştirmek için bir arabirim sağlar. yeni bir belge penceresi görüntülenir. **Arabellek veri** tablo destekler Kopyala ve başka bir araç kullanabilmesi için Yapıştır — Örneğin, Microsoft Excel — içeriğini incelemek için. Arabellek içeriğini değeri göre yorumlanır **biçimi** üzerinde bulunan birleşik giriş kutusu **arabellek veri** tablo. Kutusunda aşağıdaki tabloda listelenen veri türlerinin yapılan bir bileşik veri biçimi girebilirsiniz. Örneğin, "int float" bir 32 bit işaretli tamsayıyı değeri tarafından izlenen bir 32 bit kayan nokta değeri içeren yapılarını listesini görüntüler. Açılan kutu daha sonra kullanmak için belirttiğiniz bileşik veri biçimleri eklenir.  
  
 Ayrıca Değiştir **Göster kaydırır** arabellek uzaklığı her öğenin görüntülemek veya gizlemek için onay kutusunu.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|**float**|Bir 32 bit kayan nokta değeri.|  
|**float2**|İki 32-bit kayan nokta değerlerini içeren bir vektör.|  
|**float3**|Üç 32 bit kayan nokta değerlerini içeren bir vektör.|  
|**float4**|Dört 32 bit kayan nokta değerlerini içeren bir vektör.|  
|**byte**|Bir 8 bit işaretli tamsayıyı değeri.|  
|**2 bayt**|Bir 16 bit işaretli tamsayıyı değer.|  
|**4 bayt**|Bir 32 bit işaretli tamsayıyı değer. Aynı **int**.|  
|**8 bayt**|Bir 64 bit işaretli tamsayıyı değer. Aynı **Int64**.|  
|**xbyte**|Bir 8 bit onaltılık değeri.|  
|**x2byte**|Bir 16 bit onaltılık değer.|  
|**x4byte**|32 bit onaltılık değeri. Aynı **xint**.|  
|**x8byte**|64-bit bir onaltılık değer. Aynı **xint64**.|  
|**ubyte**|Bir 8 bit işaretsiz tamsayı değeri.|  
|**u2byte**|Bir 16 bit işaretsiz tamsayı değeri.|  
|**u4byte**|Bir 32 bit işaretsiz tamsayı değeri. Aynı **uint**.|  
|**u8byte**|Bir 64-bit işaretsiz tamsayı değeri. Aynı **uint64**.|  
|**yarısı**|Bir 16 bit kayan nokta değeri.|  
|**half2**|İki 16 bit kayan nokta değerlerini içeren bir vektör.|  
|**half3**|Üç 16 bit kayan nokta değerlerini içeren bir vektör.|  
|**half4**|Dört 16 bit kayan nokta değerlerini içeren bir vektör.|  
|**double**|Bir 64-bit kayan nokta değeri.|  
|**int**|Bir 32 bit işaretli tamsayıyı değer. Aynı **4 bayt**.|  
|**int64**|Bir 64 bit işaretli tamsayıyı değer. Aynı **8 bayt**.|  
|**xint**|32 bit onaltılık değeri. Aynı **x4byte**.|  
|**xint64**|64-bit bir onaltılık değer. Aynı **x8byte**.|  
|**uint**|Bir 32 bit işaretsiz tamsayı değeri. Aynı **u4byte**.|  
|**uint64**|Bir 64-bit işaretsiz tamsayı değeri. Aynı **u8byte**.|  
|**bool**|Bir Boole değeri (`true` veya `false`) değeri. Her bir Boole değeri 32-bit değeri ile temsil edilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik tanılama (hata ayıklama DirectX grafik)](visual-studio-graphics-diagnostics.md)   
 [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](walkthrough-missing-objects-due-to-device-state.md)