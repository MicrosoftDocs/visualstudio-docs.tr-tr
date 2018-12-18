---
title: Grafik piksel geçmişi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e0302e4b245a4fbf94d0eb49850101c404cd8a2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479961"
---
# <a name="graphics-pixel-history"></a>Grafik Piksel Geçmişi
Visual Studio grafik Çözümleyicisi grafik piksel geçmişi penceresinde, belirli bir piksel oyun veya uygulama bir çerçevesinde oluşan Direct3D olaylar tarafından nasıl etkilendiğini anlamanıza yardımcı olur.  
  
 Piksel Geçmişi penceresini şudur:  
  
 ![Piksel geçmişi üç Direct3D olayları ile. ](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Piksel Geçmişi penceresini anlama  
 Piksel geçmişi kullanarak, belirli bir piksel işleme hedef çerçevesi sırasındaki Direct3D olaylar tarafından nasıl etkilenir analiz edebilirsiniz. Belirli bir Direct3D olaya bile sonraki olayları işleme sorununu saptayabilirler — ya da aynı olayda sonraki temelleri — piksel son renk değeri değiştirmeye devam. Örneğin, bir piksel yanlış işlenemiyor ve böylece kendi renkleri birlikte framebuffer karıştırılan başka yarı saydam piksel getirilmemeli. Bu tür bir sorun yalnızca size yol göstermesi için işleme hedefi son içeriğini olsaydı tanılamak zor olurdu.  
  
 Piksel Geçmişi penceresini seçili çerçeve süresince piksel tam geçmişini görüntüler. **Son çerçeve arabelleği** nereden geldiğini çerçeve ve kendi ekran gibi piksel hakkında ek bilgi ile birlikte çerçeve sonunda framebuffer yazılır rengi penceresinin en üstünde görüntüler koordinatları. Bu alan ayrıca içerir **işlemek alfa** onay kutusu. Bu onay kutusu seçili olduğunda, **son çerçeve arabelleği** renk ve Ara renk değerleri görüntülenir saydamlığı olan Damalı bir desen. Onay kutusu işaretli değilse, renk değerleri alfa kanal göz ardı edilir.  
  
 Pencerenin alt bölümünde ile birlikte piksel rengi etkileyen şansınız olayları görüntüler **ilk** ve **son** ilk ve son renk değerlerini temsil eden sözde olayları framebuffer piksel. İlk renk değeri piksel rengini değiştirmiş ilk olay tarafından belirlenir (genellikle bir `Clear` olay). Hatta diğer bir olayları etkilenen bir piksel her zaman bu iki sözde olayları kendi geçmişinde bulunur. Diğer olayları piksel etkileyen şansınız, bunlar arasında görüntülenir **ilk** ve **son** olaylar. Olay ayrıntılarını görüntülemek için genişletilebilir. Bir işleme hedef temizleyin olanlar gibi basit olayları için olay etkisi yalnızca bir renk değeridir. Draw çağrıları gibi daha karmaşık olayları piksel rengini katkıda bulunabilir bir veya daha fazla temelleri oluşturur.  
  
 Olay tarafından çizilmiş temelleri, ilkel türü ve nesne için toplam ilkel sayısı yanı sıra dizin tarafından tanımlanır. Örneğin, bir tanımlayıcı gibi **üçgen (1456) (6214)** basit 1456th üçgen 6214 üçgenler yapılan bir nesne, karşılık gelen anlamına gelir. Her ilkel tanımlayıcı soluna pikselini basit olan etkisini özetleyen bir simgedir. Piksel rengini etkileyen temelleri sonuç renkle dolu bir yuvarlak dikdörtgen gösterilir. Piksel rengini üzerinde bir etkisi kalmaktan hariç tutulan temelleri piksel dışlandı nedenini gösterebilir simgelerle gösterilir. Bu simgeleri bölümünde açıklanan [ilkel dışlama](#exclusion) bu makalenin ilerisinde yer.  
  
 Piksel gölgelendirici çıktısı sonuç rengini oluşturmak için varolan piksel rengiyle nasıl birleştirildiği incelemek için her ilkel genişletebilirsiniz. Buradan inceleyin ya da ilkel ilişkili piksel gölgelendirici kodda hata ayıklama ve daha fazla giriş köşe gölgelendirici incelemek için köşe gölgelendirici düğümü genişletebilirsiniz.  
  
###  <a name="exclusion"></a> İlkel dışlama  
 Basit bir tür piksel rengini etkilemesini dışlanırsa, dışlama çeşitli nedenlerden dolayı meydana gelebilir. Her neden bu tabloda açıklanan bir simge ile temsil edilir:  
  
|Simge|Dışlama nedeni|  
|----------|--------------------------|  
|![Derinlik test hata simgesi. ](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Derinlik test başarısız olduğundan piksel hariç tutuldu.|  
|![Makaslı test hata simgesi. ](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Makaslı test başarısız olduğundan piksel hariç tutuldu.|  
|![Şablon test hata simgesi. ](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Şablon test başarısız olduğundan piksel hariç tutuldu.|  
  
### <a name="draw-call-exclusion"></a>Çağrı dışlama çizme  
 Tüm bir çizim elemanlar çağırırsanız, işleme hedef çizim çağrısı genişletilemiyor ve yanındaki dışlama nedeni karşılık gelen bir simge görüntülenir sonra bir test başarısız olduğundan etkileyen hariç tutulur. Draw çağrısı dışlama nedenlerle ilkel dışlama nedenlerle benzer ve simgelerine benzerdir.  
  
### <a name="viewing-and-debugging-shader-code"></a>Görüntüleme ve gölgelendirici kodda hata ayıklama  
 İnceleyin ve gölgelendirici ile ilişkili olan basit aşağıda denetimlerini kullanarak köşe hull, etki alanı, geometri ve piksel gölgelendiriciler kodda hata ayıklama.  
  
##### <a name="to-view-a-shaders-source-code"></a>Gölgelendirici'nın kaynak kodunu görüntülemek için  
  
1.  İçinde **grafik piksel geçmişi** penceresi, gölgelendirici karşılık gelen çizim çağrısı bulun inceleyin ve genişletmek istiyor.  
  
2.  Draw altında yalnızca genişletilmiş çağrısı, ilgilendiğiniz sorun gösteren bir temel seçin ve genişletin.  
  
3.  İlgilendiğiniz ilkel altında gölgelendirici başlık bağlantıyı — Örneğin, bağlantıyı izleyerek **köşe gölgelendirici obj:30** köşe gölgelendirici kaynak kodunu görüntülemek için.  
  
    > [!TIP]
    >  Nesne numarası **obj:30**, bu gölgelendirici nesne tablo ve ardışık düzen Aşamaları penceresi olduğu gibi böyle grafik Çözümleyicisi arabirimi boyunca tanımlar.  
  
##### <a name="to-debug-a-shader"></a>Gölgelendirici hata ayıklamak için  
  
1.  İçinde **grafik piksel geçmişi** penceresi, gölgelendirici karşılık gelen çizim çağrısı bulun inceleyin ve genişletmek istiyor.  
  
2.  Ardından, çizim çağrısı altında yalnızca genişletilmiş, ilgilendiğiniz ve genişletin sorunu gösteren bir temel seçin.  
  
3.  İlgilendiğiniz ilkel altında seçin **hata ayıklamayı Başlat**. Bu giriş noktasını karşılık gelen ilkel gölgelendirici ilk çalıştırılışı HLSL hata ayıklayıcısı varsayılanlara içine — diğer bir deyişle, ilk piksel veya gölgelendirici tarafından işlenen köşe. Basit ile ilişkili yalnızca bir piksel yoktur, ancak çizgilerin ve üçgenler için birden fazla köşe gölgelendirici çağrılarına yoktur.  
  
     Köşe gölgelendirici çağırma belirli köşe için hata ayıklama, VertexShader Başlık Bağlantısı'nı genişletin, ilgilendiğiniz köşe bulun, sonra seçin ve **hata ayıklamayı Başlat** yanında.  
  
### <a name="links-to-graphics-objects"></a>Grafik nesneleri bağlantılar  
 Piksel geçmişi grafik olayları anlamak için bir olay tarafından başvurulan Direct3D nesneleri veya olayın zaman cihaz durumu hakkında bilgi gerekebilir. Piksel geçmişi her olay için **grafik piksel geçmişi** durum ve için ilişkili nesnelerin geçerli cihaz bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Cihaz durumu nedeniyle nesnelerin eksikliği](walkthrough-missing-objects-due-to-device-state.md)   
 [İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)