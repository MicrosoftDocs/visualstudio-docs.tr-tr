---
title: Grafik olay listesi | Microsoft Docs
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
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 497ee3fe1c588c84195a544179d0d2955b1932b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766220"
---
# <a name="graphics-event-list"></a>Grafik Olay Listesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik olay listesi oyunlarda veya uygulamalarda karesi işlenirken kaydedilmiş Direct3D olayları keşfetmek için Visual Studio grafik Çözümleyicisi'nde kullanın.  
  
 Bu olay listesi.  
  
 ![Adında "Index" olan olaylar listesi. ](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Olay listesi kullanma  
 Olay listesi, bunu diğer grafik analizi araçları tarafından görüntülenen bilgileri yansıtılan bir olay seçtiğinizde, Bu diğer araçlar ile uyumlu bir şekilde olay listesi kullanılarak bir işleme sorunun nedenini belirlemek için ayrıntılı inceleyebilirsiniz. Olay listesi diğer grafik analizi araçları ile birlikte kullanarak işleme sorunları nasıl çözebileceğiniz hakkında daha fazla bilgi için bkz: [örnekler](../debugger/graphics-diagnostics-examples.md).  
  
 Olay listesi özelliklerinin etkili bir şekilde kullanarak, binlerce olayın içerebilir karmaşık çerçevelerinin çevresinde almak için önemlidir. Olay listesi verimli bir şekilde kullanma, görünüm sizin için en uygun seçin, arama olay listesini filtrelemek için bir olayla ilişkili olan Direct3D nesneleri hakkında daha fazla bilgi edinmek için bağlantıları izleyin ve oku çağrıları arasında taşımak için düğmeler hızla çizin.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12 renk kodlu olaylar  
 Direct3D 12 farklı donanım işlevselliği için karşılık gelen birden fazla kuyruk kullanıma sunar. Bir Direct3D 12 uygulama yakalama ile çalışırken, bir Direct3D 12 belirli grafik olay ile ilişkili kuyruk belirlemenize yardımcı olması için olayları Olay listesindeki kendi sıra göre renk kodludur.  
  
|Direct3D 12 sırası|Renk|  
|-----------------------|-----------|  
|Kuyruk oluştur|Yeşil|  
|Kuyruk işlem|Sarı|  
|Kopyalama kuyruğu|Turuncu|  
  
 Direct3D 11 birden fazla kuyruk kullanıma sunmak değil, Direct3D 11 uygulamasının bir yakalama ile çalışırken olayları renk kodlu kalmayacak bir olay listesi.  
  
### <a name="event-list-views"></a>Olay liste görünümleri  
 Olay listesi, grafik olaylarını düzenleme iş akışı ve tercihlerinizi desteklemek için farklı şekilde iki farklı görünümleri destekler. İlk görünümdür *çizim çağrıları Görünüm* hangi düzenler olayları ve durumlarını ilişkili hiyerarşik olarak. İkinci görünüm *zaman çizelgesi görünümü* hangi düzenler olayların kronolojik, düz bir liste.  
  
 **Çizim çağrıları'na** görüntüle  
 Görüntüler yakalanan olayları ve durumlarını bir hiyerarşide. Hiyerarşinin üst düzey olayları gibi çizim çağrıları, temizler, mevcut ve görünümler ile de oluşur. Olay listesi, çizim çağrılarını çizim çağrısı zaman güncel olan cihaz durumunu görüntülemek için genişletebilirsiniz; ve her tür değerlerini belirleyen olayları görüntülemek için durumları daha da genişletebilirsiniz. Bu düzey, önceki bir çerçeve içinde belirli bir duruma ayarlanmış olup olmadığını ya da son çizim çağrısı bu yana kereden fazla ayarlandı da görebilirsiniz.  
  
 **Zaman çizelgesi** görüntüle  
 Yakalanan her olay kronolojik sırayla görüntüler. Olay listesi düzenleme bu şekilde Visual Studio'nun önceki sürümlerinde olduğu gibi aynı olur.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Olay listesi görünümü modu değiştirmek için  
  
-   İçinde **grafik olay listesi** bulun, olayların listesinin üst penceresinde **görünümü** açılır ve seçeneğini **zaman çizelgesi** görünümü veya **çizim çağrıları** görünümü.  
  
### <a name="filtering-events"></a>Olayları filtreleme  
 Arama kutusunu kullanabilirsiniz — sağ üst köşesinde bulunan **grafik olay listesi** penceresi — yalnızca adında belirli anahtar sözcükler olayları dahil etmek için olayları listeyi filtrelemek için. İster tek anahtar sözcükleri belirtebilirsiniz `Vertex`— önceki resimde gösterildiği gibi — veya noktalı virgülle ayrılmış bir liste kullanarak birden çok anahtar sözcükleri `Draw;Primitive`— ya da sahip olayları eşleşen `Draw` veya `Primitive` adlarında. Aramalar için boşluk hassas — Örneğin, `VSSet` ve `VS Set` farklı aramalar — böylece form aramaları için dikkatli bir şekilde sağlayın.  
  
### <a name="moving-between-draw-calls"></a>Çizim çağrıları arasında taşıma  
 İnceleme çünkü `Draw` çağrıdır kullanabileceğiniz özellikle önemli **sonraki Git çizim çağrısı** ve **Git önceki çizim çağrısı** düğmeleri — solüstköşesindebulunan**Grafik olay listesi** penceresi — bulup çizim çağrıları arasında kolayca taşıyın.  
  
### <a name="links-to-graphics-objects"></a>Grafik nesneleri bağlantılar  
 Belirli grafik olaylarını anlamak için bir olay tarafından başvurulan Direct3D nesneleri veya Direct3D geçerli durumu hakkında ek bilgi gerekebilir. Çok sayıda olay daha fazla ayrıntı için izleyebileceğiniz bu bilgilere bağlantılar sağlar.  
  
## <a name="kinds-of-events-and-event-markers"></a>Olaylar ve olay işaretçileri tür  
 Liste düzenlenir olay dört kategoriye görüntülenen olayları: genel olaylar, olaylar, olay kullanıcı tanımlı grupları ve kullanıcı tanımlı olay işaretçileri çizin. Genel olaylar dışında her olay ait olduğu kategoriyi belirten bir simge ile birlikte görüntülenir.  
  
|Simge|Olay açıklaması|  
|----------|-----------------------|  
|(simge yok)|Genel olay<br /> Değil kullanıcı tanımlı olay, kullanıcı tanımlı olay grubu veya olay çizmek herhangi bir olay.|  
|![Çizim olay simgesi](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Çizim olayından<br /> Yakalanan karede bir çizim olayından işaretler.|  
|![Kullanıcı&#45;olay işaret simgesi tanımlanan](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay grubu<br /> Grupları, uygulama tarafından tanımlanan olayları, ilgili.|  
|![Kullanıcı&#45;olay işaret simgesi tanımlanan](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay işaretçisi<br /> Belirli bir konuma uygulama tarafından tanımlanan olarak işaretler.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Uygulamanızda işaretlenmesi kullanıcı tanımlı olayları  
 Kullanıcı tanımlı olaylar, uygulamanıza özgü niteliktedir. Grafik olay listesi olayları ile uygulamanızda gerçekleşen önemli olayları ilişkilendirmek için bunları kullanabilirsiniz. Örneğin, ilgili olaylar düzenlemek için kullanıcı tanımlı olay gruplar oluşturabilirsiniz — Bu, kullanıcı arabirimini oluşturmak gibi — olay listesi daha kolayca göz atabilir veya belirli bir türdeki nesneler, işaretçileri oluşturabilirsiniz böylece grupları veya Hiyerarşiler olan çizilen. böylece, grafik olaylarını Olay listesi kolayca bulabilirsiniz.  
  
 Gruplar ve işaretçileri, uygulamanızı oluşturmak için diğer Direct3D tarafından hata ayıklama araçları kullanmak için Direct3D sağlayan API'leri kullanın. Bu API'ler, bazen Direct3D sürümleri arasında değiştirmek, ancak temel işlevleri aynıdır.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Kullanıcı tanımlı olayları, Direct3D 12  
 Direct3D 12'deki gruplar ve işaretçileri oluşturmak için bu bölümde açıklanan API'leri kullanın. Aşağıdaki tabloda, bir komut kuyruğuna olaylar işaretleme veya liste komut bağlı olarak kullanabileceğiniz API'ler özetler.  
  
|API tanımı|[ID3D12CommandQueue](https://msdn.microsoft.com/library/dn788627.aspx)|[ID3D12GraphicsCommandList](https://msdn.microsoft.com/library/dn903537.aspx)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Kullanıcı tanımlı olay kullanılabilirliğini denetle|[PIXGetStatus](http://msdn.microsoft.com/en-us/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](http://msdn.microsoft.com/en-us/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Olay grubu başlayın|[PIXBeginEvent](http://msdn.microsoft.com/en-us/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](http://msdn.microsoft.com/en-us/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Son olay grubu|[PIXEndEvent](http://msdn.microsoft.com/en-us/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](http://msdn.microsoft.com/en-us/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Bir olay işaretçisi oluşturma|[PIXSetMarker](http://msdn.microsoft.com/en-us/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](http://msdn.microsoft.com/en-us/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11'de ve önceki kullanıcı tanımlı olayları  
 Grupları ve Direct3D 11 veya önceki işaretçileri oluşturmak için bu bölümde açıklanan API'leri kullanın. Aşağıdaki tabloda farklı sürümlerini Direct3D 11 ve Direct3D önceki sürümleri için kullanabileceğiniz API'ler özetler.  
  
|API tanımı|[ID3D11DeviceContext2](http://msdn.microsoft.com/library/windows/desktop/dn280498.aspx) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|D3DPerf_ API ailesi (Direct3D 11.0 ve daha önceki)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Olay grubu başlayın|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Son olay grubu|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Bir olay işaretçisi oluşturma|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Direct3D sürümünüz destekleyen bu API dilediğinizi kullanabilirsiniz — Direct3D 11.1 API hedefliyorsanız, örneğin, kullanabilirsiniz `SetMarker` veya `D3DPerf_SetMarker` bir olay işaretçisi değil oluşturmak için `SetMarkerInt` çünkü Direct3D, yalnızca kullanılabilir 11.2 — ve Direct3D'ün farklı sürümlerini birlikte aynı uygulamada destekleyen olanlar bile karıştırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](../debugger/walkthrough-missing-objects-due-to-device-state.md)



