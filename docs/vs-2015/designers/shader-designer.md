---
title: Gölgelendirici Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac752d0b85a45193fe4aafb55e33ec23e26aed6a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942016"
---
# <a name="shader-designer"></a>Gölgelendirici Tasarımcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede ile nasıl çalışılacağı açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oluşturmak, değiştirmek ve olarak bilinen özel görsel efektler dışarı aktarmak için gölgelendirici Tasarımcısı *gölgelendiricileri*.  
  
 Oyunlarda veya uygulamalarda için özel görsel efektler HLSL programlama bilmeseniz bile oluşturmak için gölgelendirici Tasarımcısı'nı kullanabilirsiniz. Gölgelendirici Tasarımcısı'nda bir gölgelendirici oluşturmak için yalnızca teslim bir grafik oluşturun; diğer bir deyişle, tasarım yüzeyine eklediğiniz *düğümleri* verileri ve işlemleri temsil eder ve ardından verileri nasıl işlemlerini tanımlamak için bunlar arasında bağlantı kurun. Sonuç görselleştirebilir, böylece her işlem düğümünde o noktaya kadar etkili önizlemesi sağlanır. Veri düğümleri gölgelendirici çıkışı temsil eden bir son düğümü doğru akar.  
  
## <a name="supported-formats"></a>Desteklenen biçimler  
 Gölgelendirici Tasarımcısı bu gölgelendirici biçimlerini destekler:  
  
|Biçim Adı|Dosya Uzantısı|Desteklenen işlemler (görüntüleme, düzenleme, dışarı aktarma)|  
|-----------------|--------------------|-------------------------------------------------|  
|Yönlü graf gölgelendirici dili|.dgsl|Görüntüle, Düzenle|  
|HLSL gölgelendirici (kaynak kodu)|.hlsl|Dışarı aktarma|  
|HLSL gölgelendirici (bayt)|.CSO|Dışarı aktarma|  
|C++ üst bilgisi (HLSL bayt dizesi)|.h|Dışarı aktarma|  
  
## <a name="getting-started"></a>Başlarken  
 Bu bölüm için bir DGSL gölgelendirici ekleme işlemi açıklanmaktadır, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje ve başlamanıza yardımcı olmak için temel bilgiler sağlar.  
  
#### <a name="to-add-a-dgsl-shader-to-your-project"></a>Projenize DGSL gölgelendirici ekleme  
  
1.  İçinde **Çözüm Gezgini**, gölgelendiriciye ekleyin ve ardından istediğiniz projenin kısayol menüsünü **Ekle**, **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunun **yüklü**seçin **grafik**ve ardından **görsel gölgelendirici grafiği (.dgsl)**.  
  
3.  Belirtin **adı** gölgelendirici dosyası ve **konumu** sonra istediğiniz yere oluşturulacak.  
  
4.  Seçin **Ekle** düğmesi.  
  
### <a name="the-default-shader"></a>Varsayılan gölgelendiriciyi  
 İsteğe bağlı olarak bir DGSL gölgelendirici oluşturmak her zaman sadece sahip en az bir gölgelendirici başladığı bir **nokta rengi** bağlı düğüm **son rengini** düğümü. Bu gölgelendiriciyi tam ve işlevsel olsa da, çok yapmaz. Bu nedenle, çalışma gölgelendirici oluşturmanın ilk adımı genellikle silmektir **nokta rengi** düğümü veya bağlantısını kesmeniz **son rengini** diğer düğümler için yer açmak için düğümü.  
  
## <a name="working-with-the-shader-designer"></a>Gölgelendirici Tasarımcısı ile çalışma  
 Aşağıdaki bölümlerde, gölgelendirici Tasarımcısı özel gölgelendiricilerle çalışmak için nasıl kullanılacağını açıklanmaktadır.  
  
### <a name="shader-designer-toolbars"></a>Gölgelendirici Tasarımcısı araç çubukları  
 Gölgelendirici Tasarımcısı araç çubukları içeren DGSL gölgelendirici grafikler ile çalışmanıza yardımcı olan komutlar.  
  
 Gölgelendirici Tasarımcısı durumunu etkileyen komutlar bulunur **gölgelendirici Tasarımcısı modu** araç ana [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] penceresi. Tasarım araçları ve komutlar bulunur **gölgelendirici Tasarımcısı** gölgelendirici Tasarımcısı tasarım yüzeyinde araç çubuğu.  
  
 İşte **gölgelendirici Tasarımcısı modu** araç çubuğu:  
  
 ![Gölgelendirici Tasarımcısı kalıcı araç çubuğu. ](../designers/media/digit-dsd-modal-toolbar.png "DSD kalıcı araç basamak")  
  
 Bu tabloda öğeleri açıklar **gölgelendirici Tasarımcısı modu** araç çubuğu göründükleri soldan sağa doğru sırayla listelenir:  
  
|Araç Çubuğu Öğesi|Açıklama|  
|------------------|-----------------|  
|**Seçin**|Düğümler ve kenarlar graftaki etkileşimine olanak tanır. Bu modda, düğümleri seçin ve taşıyabilir veya silebilirsiniz ve kenarlar oluşturmak veya bunları bölün.|  
|**Pan**|Pencere çerçevesine göre bir gölgelendirici grafiği hareketini sağlar. Kaydırmak için bir tasarım yüzeyi noktasında seçin ve farklı yerlerinde taşıyın.<br /><br /> İçinde **seçin** modu basın ve basılı tutun etkinleştirmek için Ctrl **Pan** geçici olarak modu.|  
|**Yakınlaştırma**|Gölgelendirici grafiği ayrıntısı pencere çerçevesine göre daha az veya görüntülenmesini sağlar. İçinde **yakınlaştırma** modu, bir tasarım yüzeyi noktasında seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sola veya ettirin yetersiz.<br /><br /> İçinde **seçin** modu tuşuna basın ve yakınlaştırmak veya uzaklaştırmak fare tekerleğini kullanarak için Ctrl basılı tutun.|  
|**Sığacak kadar Yakınlaştır**|Tam gölgelendirici grafiği pencere çerçevesinde görüntüler.|  
|**Gerçek zamanlı işleme modu**|Gerçek zamanlı işleme etkin olduğunda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hiçbir kullanıcı eylemi gerçekleştirilmediğinde bile tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|  
|**Küre ile Önizleme**|Etkin olduğunda, bir model kürenin gölgelendiricinin önizlemesini görüntülemek için kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|  
|**Küp ile Önizleme**|Etkin olduğunda, bir küp modeli gölgelendiricinin önizlemesini görüntülemek için kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|  
|**Silindir ile Önizleme**|Etkin olduğunda, bir model silindir gölgelendiricinin önizlemesini görüntülemek için kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|  
|**Koni ile Önizleme**|Etkin olduğunda, bir model bir koni gölgelendiricinin önizlemesini görüntülemek için kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|  
|**Çaydanlık ile Önizleme**|Etkin olduğunda, bir çaydanlık modelinin gölgelendiricinin önizlemesini görüntülemek için kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|  
|**Düzlem ile Önizleme**|Etkin olduğunda, bir uçak modelinin gölgelendiricinin önizlemesini görüntülemek için kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|  
|**Araç Kutusu**|Alternatif olarak gösterir veya gizler **araç kutusu**.|  
|**Özellikler**|Alternatif olarak gösterir veya gizler **özellikleri** penceresi.|  
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Dışarı aktarma**: gölgelendiriciyi çeşitli biçimlerde verilmesini sağlar.<br /><br /> **Dışarı aktarma olarak**: Gölgelendirici ya da HLSL kaynak kodu veya derlenmiş gölgelendirici bytecode'una olarak dışarı aktarır. Gölgelendiricileri dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md).<br /><br /> **Grafik motorları**: tasarım yüzeyinde görüntülemek için kullanılan Oluşturucu seçimini etkinleştirir.<br /><br /> **D3d11 ile işle**: Gölgelendirici Tasarımcısı tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3d11warp ile işle**: kullanan Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (gölgelendirici Tasarımcısı tasarım yüzeyini işlemek için WARP).<br /><br /> **Görünüm**: Gölgelendirici Tasarımcısı hakkında ek bilgi sağlar.<br /><br /> **Kare hızı**: etkin olduğunda, tasarım yüzeyinin sağ üst köşesinde bulunan geçerli kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır.  Bu seçenek, etkinleştirdiğinizde kullanışlıdır **gerçek zamanlı işleme modu** seçeneği.|  
  
> [!TIP]
>  Seçebileceğiniz **Gelişmiş** düğmesine son komutu yeniden çalıştırın.  
  
### <a name="working-with-nodes-and-connections"></a>Düğümler ve bağlantılar ile çalışma  
 Kullanım **seçin** eklemek, kaldırmak, yeniden konumlandırma, bağlanma ve düğümleri yapılandırmak için modu. Bu temel işlemleri gerçekleştirmek nasıl aşağıda verilmiştir:  
  
##### <a name="to-perform-basic-operations-in-select-mode"></a>Seçim modunda temel işlemleri gerçekleştirmek için  
  
-   İşte nasıl:  
  
    -   Grafiğe bir düğüm eklemek, onu seçip **araç kutusu** ve ardından tasarım yüzeyine taşıyın.  
  
    -   Grafikten bir düğümü kaldırmak için onu seçin ve Sil'e basın.  
  
    -   Bir düğüme yeniden konumlandırmak için onu seçin ve ardından yeni bir konuma taşıyın.  
  
    -   İki düğüm bağlanmak için bir çıkış terminal düğümün diğer düğümü için bir giriş uç taşıyın. Uyumlu türleri olan terminaller bağlanabilir. Bir satır Terminaller arasında bağlantı gösterir.  
  
    -   Kısayol menüsünde herhangi birine bağlı terminaller yönelik bir bağlantı kaldırmak için **Bağlantıları Kes**.  
  
    -   Bir düğüm özelliklerini yapılandırmak için düğümü seçin ve ardından **özellikleri** penceresinde özellikleri için yeni değerler belirtin.  
  
### <a name="previewing-shaders"></a>Gölgelendiricileri Önizleme  
 Gölgelendirici uygulamanızda nasıl görüneceğini anlamanıza yardımcı olması için etkili nasıl önizlemesini görebilirsiniz yapılandırabilirsiniz. Uygulamanızı yaklaşık olarak belirlemenizi sağlayan, işleme, dokuları ve diğer malzeme parametreleri yapılandırmak, animasyon zaman tabanlı etkileri etkinleştirmek ve farklı açılardan Önizleme incelemek için birkaç şekil birini seçebilirsiniz.  
  
#### <a name="shapes"></a>Şekiller  
 Gölgelendirici Tasarımcısı altı şekiller içerir — bir küre, küp, silindir, bir koni, bir çaydanlık ve düzlem — gölgelendiricinizi önizlemek için kullanabilirsiniz. Gölgelendirici bağlı olarak belirli şekiller daha iyi önizleme verebilir.  
  
###### <a name="to-choose-a-preview-shape"></a>Bir önizleme şekli seçmek için  
  
-   Üzerinde **gölgelendirici Tasarımcısı modu** araç, istediğiniz şekli seçin.  
  
####  <a name="WWS_MaterialParameters"></a> Dokular ve malzeme parametreleri  
 Dokular ve malzeme özelliklerine nesne uygulamanızdaki her tür için benzersiz bir görünüm oluşturmak için birçok gölgelendirici dayanır. Gölgelendiricinizi, uygulamanızda nasıl görüneceğini görmek için dokular ve doku ve uygulamanızda kullanabileceğiniz parametreler eşleştirmek için Önizleme işlemek için kullanılan malzeme özellikleri ayarlayabilirsiniz.  
  
###### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>Bir doku kaydı için farklı bir doku bağlamak için veya diğer malzeme parametreleri değiştirmek için  
  
1. İçinde **seçin** modu, tasarım yüzeyinde boş bir alanı seçin. Bu neden **özellikleri** genel gölgelendirici özelliklerini görüntülemek için penceresi.  
  
2. İçinde **özellikleri** penceresinde değiştirmek istediğiniz doku ve parametre özellikleri için yeni değerler belirtin.  
  
   Değiştirebileceğiniz gölgelendirici Parametreler şunlardır:  
  
|Parametre|Özellikler|  
|---------------|----------------|  
|**Doku 1** – **doku 8**|**Erişim**: **genel** özelliğin Model Düzenleyicisi'nden Ayarla; tersi durumda, izin vermek için **özel**.<br /><br /> **Filename**: Bu doku kaydı ile ilişkili doku dosyasının tam yolu.|  
|**Malzeme ortam**|**Erişim**: **genel** özelliğin Model Düzenleyicisi'nden Ayarla; tersi durumda, izin vermek için **özel**.<br /><br /> **Değer**: dolaylı – veya ortam – aydınlatması nedeniyle geçerli pikselin yayınık rengi.|  
|**Malzeme Yayınık**|**Erişim**: **genel** özelliğin Model Düzenleyicisi'nden Ayarla; tersi durumda, izin vermek için **özel**.<br /><br /> **Değer**: geçerli pikselin doğrudan aydınlatmayı nasıl pürüzlü açıklayan bir renk.|  
|**Malzeme Yayımlatıcı**|**Erişim**: **genel** özelliğin Model Düzenleyicisi'nden Ayarla; tersi durumda, izin vermek için **özel**.<br /><br /> **Değer**: kendi kendine sağlanan aydınlatma nedeniyle geçerli pikselin renk katkısı.|  
|**Malzeme Yansımalı**|**Erişim**: **genel** özelliğin Model Düzenleyicisi'nden Ayarla; tersi durumda, izin vermek için **özel**.<br /><br /> **Değer**: geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|  
|**Malzeme Yansımalı güç**|**Erişim**: **genel** özelliğin Model Düzenleyicisi'nden Ayarla; tersi durumda, izin vermek için **özel**.<br /><br /> **Değer**: geçerli pikselin Yansımalı vurgular yoğunluğunu tanımlayan üs.|  
  
#### <a name="time-based-effects"></a>Zamana bağlı etkileri  
 Bazı gölgelendirici efekti canlandırır zamana bağlı bir bileşen var. Etkin uygulamada nasıl göründüğünü görmek için önizleme birkaç kez saniyede güncelleştirilmesi gerekir. Gölgelendirici değiştirildiğinde, varsayılan olarak, yalnızca önizleme güncelleştirilir; zamana bağlı etkileri görüntüleyebilmesi için bu davranışı değiştirmek için gerçek zamanlı işleme olanağı vardır.  
  
###### <a name="to-enable-real-time-rendering"></a>Gerçek zamanlı işleme olanağı  
  
-   Gölgelendirici Tasarımcısı araç çubuğunda **gerçek zamanlı işleme**.  
  
#### <a name="examining-the-effect"></a>Etkisi İnceleme  
 Birçok gölgelendirici açısını veya tek yönlü ışık görüntüleme gibi değişkenleri etkilenir. Bu değişkenler değiştikçe etkisi nasıl yanıt vereceğini incelemek için Önizleme şekle serbestçe döndürmek ve gölgelendirici nasıl davranacağını gözlemleyin.  
  
###### <a name="to-rotate-the-shape"></a>Şekil döndürmek için  
  
-   Tuşuna basın, Alt tuşunu basılı ve tasarım yüzeyinde herhangi bir noktasını seçin ve taşıyın.  
  
### <a name="exporting-shaders"></a>Gölgelendiricileri dışarı aktarma  
 Uygulamanızda bir gölgelendirici kullanmadan önce DirectX anlayan bir biçimde dışarı gerekir.  
  
 Gölgelendiricileri HLSL kaynak kodu veya derlenmiş gölgelendirici bytecode'una olarak dışarı aktarabilirsiniz. HLSL kaynak kodu .hlsl dosya adı uzantısına sahip bir metin dosyasına aktarılır. Gölgelendirici bytecode'una .cso dosya adı uzantısına sahip bir ham ikili dosyaya veya bir diziye gölgelendirici bytecode'una kodlayan bir C++ üstbilgi (.h) dosyasına dışarı aktarılabilir.  
  
 Gölgelendiricileri dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md).  
  
## <a name="keyboard-shortcuts"></a>Klavye kısayolları  
  
|Komut|Klavye kısayolları|  
|-------------|------------------------|  
|Geçiş **seçin** modu|Ctrl+G, Gtrl+Q<br /><br /> S|  
|Geçiş **yakınlaştırma** modu|Ctrl+G, Ctrl+Z<br /><br /> Z|  
|Geçiş **Pan** modu|Ctrl+G, Ctrl+P<br /><br /> K|  
|Tümünü seç|Ctrl+A|  
|Geçerli seçimi sil|Sil|  
|Geçerli seçimi iptal et|Esc|  
|Yakınlaştır|Ctrl+Fare tekerleği ileriye doğru<br /><br /> Artı İşareti (+)|  
|Uzaklaştır|CTRL-fare tekerleği geriye doğru<br /><br /> Eksi İşareti (-)|  
|Tasarım yüzeyine yukarı kaydır|Fare tekerleği geriye doğru<br /><br /> PageDown|  
|Tasarım yüzeyine aşağı kaydır|Fare tekerleği ileriye doğru<br /><br /> PageUp|  
|Tasarım yüzeyine sola kaydır|Shift+Fare tekerleği geriye doğru<br /><br /> Fare tekerleği sol<br /><br /> Shift + PageDown|  
|Tasarım yüzeyine sağa kaydır|Shift+Fare tekerleği ileriye doğru<br /><br /> Fare tekerleği sağ<br /><br /> Shift + PageUp|  
|Klavye odağı başka bir düğüme taşı|Ok tuşları|  
|Klavye odağı (düğümü seçimi gruba ekler) olan düğümü seçin|Shift + Ara çubuğu|  
|Klavye girintisine sahip düğümün Seçimi Değiştir|Ctrl+Ara Çubuğu|  
|Geçerli seçimi Değiştir (düğüm seçilirse, klavye girintisine sahip düğümü seçin)|Ara çubuğu|  
|Geçerli seçimi Yukarı Taşı|Shift+Yukarı Ok|  
|Geçerli seçimi aşağı taşı|Shift+Aşağı Ok|  
|Geçerli seçimi sola taşı|Shift+Sol Ok|  
|Geçerli seçimi sağa taşı|SHIFT + sağ ok.|  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Genel bir bakış sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokular ve resimler, 3B modeller ve gölgelendirici efektleri ile çalışmak için kullanabileceğiniz araçları.|  
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokularla ve görüntülerle çalışma için görüntü Düzenleyicisi.|  
|[Model Düzenleyicisi](../designers/model-editor.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 3B modellerle çalışmak için Model Düzenleyicisi.|



