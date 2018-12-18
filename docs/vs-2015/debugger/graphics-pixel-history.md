---
title: Grafik piksel geçmişi | Microsoft Docs
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
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20b33c987cf7e2b1ab57160b4f4917246d9030b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733160"
---
# <a name="graphics-pixel-history"></a>Grafik Piksel Geçmişi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio grafik Çözümleyicisi grafik piksel geçmişi penceresinde belirli bir pikseli oyunlarda veya uygulamalarda bir çerçevesinde gerçekleşen Direct3D olayları tarafından nasıl etkilendiğini anlamanıza yardımcı olur.  
  
 Piksel Geçmişi penceresini budur:  
  
 ![Üç Direct3D olayları geçmişinde bir piksel. ](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Piksel Geçmişi penceresini anlama  
 Piksel Geçmişi'ni kullanarak, belirli bir pikseli işleme hedefinin bir çerçevesinde Direct3D olayları tarafından nasıl etkilenir çözümleyebilirsiniz. Belirli bir Direct3D olay bile sonraki olayları işleme sorunuyla saptayabilirler — veya sonraki basit aynı olay — pikselin son rengini değerini değiştirmek devam edin. Örneğin, bir piksel yanlış işlenemiyor ve böylece renklerinin birlikte framebuffer içinde karışık sonra başka bir, yarı saydam piksel engellediği. Bu tür sorunlar, yalnızca son size yol göstermesi için işleme hedefinin içeriğini olsaydı tanı koymak güç olacaktır.  
  
 Piksel Geçmişi penceresini Seçilen çerçevenin boyunca bir piksel tam geçmişini görüntüler. **Son çerçeve arabelleği** penceresinin en üstünde geldiğini çerçeve ve ekranı gibi piksel hakkında ek bilgi ile birlikte bir çerçeve sonunda framebuffer yazılan rengini görüntüler. koordinatları. Bu alan da içerir **işleme alfa** onay kutusu. Bu onay kutusu işaretli olduğunda **son çerçeve arabelleği** renk ve Ara renk değerleri görüntülenir saydamlığı olan bir dama tahtası desenini. Onay kutusu işaretli değilse, renk değerlerinin alfa kanalı göz ardı edilir.  
  
 Pencerenin alt kısmında görüntüler şansınız ile birlikte piksel rengini etkileyen olayların **ilk** ve **son** ilk ve son renk değerlerini temsil eden sözde olayları framebuffer piksel. İlk renk değeri piksel rengi değişir ilk olay tarafından belirlenir (genellikle bir `Clear` olay). Olduğunda bile diğer olay etkilenen bir piksel geçmişini, bu iki sahte olay her zaman vardır. Diğer olayları piksel etkileyen şansınız olduğunda, bunlar arasında görüntülenir **ilk** ve **son** olayları. Olay ayrıntılarının gösterecek şekilde genişletilebilir. İşleme hedefi Temizle kullananlar gibi basit olaylar için bir renk değeri yalnızca olay etkisidir. Çizim çağrıları gibi daha karmaşık olayları piksel rengi için katkıda bulunan bir veya daha fazla temel oluşturur.  
  
 Olay tarafından çizilmiş temelleri, ilkel türü ve nesne için toplam ilkel sayısı ile birlikte dizini tarafından tanımlanır. Örneğin, bir tanımlayıcı gibi **(6214), üçgen (1456)** 1456th üçgeni 6214 üçgenler yapılan bir nesne için karşılık gelen temel anlamına gelir. Her temel tanımlayıcı solunda pikselini temel eleman olan etkisini özetleyen bir simge bulunur. Piksel rengi etkileyen temelleri sonucu renkle dolu bir Yuvarlatılmış Dikdörtgen gösterilir. Piksel renk üzerinde bir etkisi kalmamasını dışlanmaz temelleri piksel dışarıda bırakıldı nedenini gösteren simgeler tarafından temsil edilir. Bu simgeler bölümünde açıklanan [ilkel dışlama](../debugger/graphics-pixel-history.md#exclusion) bu makalenin ilerleyen bölümlerinde.  
  
 Piksel gölgelendirici çıkışı sonuç rengi üretmek için mevcut piksel rengi ile birleştirilmiş nasıl incelemek için her bir temel genişletebilirsiniz. Buradan ayrıca inceleyin veya temel ile ilişkili piksel gölgelendirici kodunda hata ayıklayın ve daha fazla giriş köşe gölgelendiricisi incelemek için köşe gölgelendirici düğümü genişletebilir.  
  
###  <a name="exclusion"></a> Temel dışlama  
 Basit bir tür piksel rengi etkilemesini çıkarılır, dışlama çeşitli nedenlerden dolayı ortaya çıkabilir. Her bir nedeni, bu tabloda açıklanan bir simgeyle gösterilir:  
  
|Simge|Dışlama nedeni|  
|----------|--------------------------|  
|![Derinlik test hatası simgesi. ](../debugger/media/vsg-hist-icon-failed-depth.png "vsg_hist_icon_failed_depth")|Derinlik testinde başarısız olduğu için piksel dışarıda bırakıldı.|  
|![Makas test hatası simgesi. ](../debugger/media/vsg-hist-icon-failed-scissor.png "vsg_hist_icon_failed_scissor")|Makas testinde başarısız olduğu için piksel dışarıda bırakıldı.|  
|![Şablon test hatası simgesi. ](../debugger/media/vsg-hist-icon-failed-stencil.png "vsg_hist_icon_failed_stencil")|Kalıp testinde başarısız olduğu için piksel dışarıda bırakıldı.|  
  
### <a name="draw-call-exclusion"></a>Çizim çağrısı dışlama  
 Tüm temel elemanlar bir çizim olarak çağırırsanız, çizim çağrısı genişletilemez ve dışlama nedeni karşılık gelen bir simge yanında görüntülenen sonra bir test başarısız olduğundan işleme hedefi etkileyen hariç tutulur. Temel dışlama nedeniyle çizim çağrısı dışlama nedenlerle benzer ve simgelerine benzerdir.  
  
### <a name="viewing-and-debugging-shader-code"></a>Görüntüleme ve gölgelendirici kodunda hata ayıklama  
 İnceleyebilir ve aşağıda gölgelendirici ile ilişkili temel denetimlerini kullanarak köşe, kabuk, etki alanı, geometri ve piksel gölgelendiricilerini kod hata ayıklama.  
  
##### <a name="to-view-a-shaders-source-code"></a>Gölgelendiricinin kaynak kodunu görüntülemek için  
  
1.  İçinde **grafik piksel geçmişi** penceresinde gölgelendirici için karşılık gelen bir çizim çağrısı bulun inceleyin ve genişletmek istiyor.  
  
2.  Çizim altında yalnızca genişletilmiş çağrı, ilgilendiğiniz sorunu gösteren basit bir tür seçin ve genişletin.  
  
3.  İlgilendiğiniz temel altında gölgelendirici başlık bağlantıyı — Örneğin, bağlantıyı **köşe gölgelendiricisi obj:30** köşe gölgelendirici kaynak kodunu görüntülemek için.  
  
    > [!TIP]
    >  Nesne sayısı **obj:30**, bu gölgelendirici grafik Çözümleyicisi arabirimi nesne tablosu ve ardışık düzen Aşamaları penceresinde olduğu gibi böyle boyunca tanımlar.  
  
##### <a name="to-debug-a-shader"></a>Gölgelendirici hata ayıklamak için  
  
1.  İçinde **grafik piksel geçmişi** penceresinde gölgelendirici için karşılık gelen bir çizim çağrısı bulun inceleyin ve genişletmek istiyor.  
  
2.  Ardından, çizim çağrısı altında yalnızca genişletilmiş, ilgileniyorsanız ve genişletmek sorunu gösteren basit bir tür seçin.  
  
3.  İlgilendiğiniz temel altında seçin **hata ayıklamayı Başlat**. Bu giriş noktası için karşılık gelen temel gölgelendirici ilk çağrısıysa HLSL hata ayıklayıcısı varsayılanlara içine — diğer bir deyişle, ilk piksel veya köşe gölgelendiricisi tarafından işlenen. Temel ile ilişkili yalnızca bir piksel yoktur ancak satırları ve bu üçgen için birden fazla köşe gölgelendirici çağrılarına yoktur.  
  
     Köşe gölgelendirici çağırma için belirli bir köşe hata ayıklama, VertexShader odkaz na nadpis genişletin ve ilgilendiğiniz köşe bulmak için ardından **hata ayıklamayı Başlat** yanında.  
  
### <a name="links-to-graphics-objects"></a>Grafik nesneleri bağlantılar  
 Grafik piksel geçmişi olayları anlamak için bir olay tarafından başvurulan Direct3D nesneleri veya etkinliğin zaman cihaz durumu hakkındaki bilgileri gerekebilir. Piksel geçmişi her olay için **grafik piksel geçmişi** durum ve için ilişkili nesnelerin geçerli cihaz bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Cihaz durumu nedeniyle nesnelerin eksikliği](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



