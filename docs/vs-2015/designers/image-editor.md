---
title: Görüntü Düzenleyicisi | Microsoft Docs
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
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 748d58ec8446841242fdf7b5b990eebe90df5ba1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185776"
---
# <a name="image-editor"></a>Görüntü Düzenleyici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede ile nasıl çalışılacağı açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doku ve resim kaynakları görüntülemek ve değiştirmek için görüntü Düzenleyicisi.  
  
 Resim Düzenleyicisi, DirectX uygulaması geliştirmede kullanılan zengin doku ve resim biçimleri türleri ile çalışmak için kullanabileceğiniz — Bu popüler görüntü dosyası biçimlerini ve renk Kodlamalar, alfa kanalları ve MIP eşleştirme gibi özellikler için destek ve birçoğunu içerir yüksek oranda sıkıştırılmış, Donanım hızlandırmalı doku DirectX destekleyen biçimlendirir.  
  
## <a name="supported-formats"></a>Desteklenen biçimler  
 Resim Düzenleyicisi bu görüntü biçimlerini destekler:  
  
|Biçim adı|Dosya Adı Uzantısı|  
|-----------------|-------------------------|  
|Taşınabilir Ağ Grafikleri|.PNG|  
|JPEG|.jpg, .jpeg, .jpe, .jfif|  
|Doğrudan çizim yüzeyi|.DDS|  
|Grafik Değişim Biçimi|.gif|  
|Bit eşlem|.bmp, .dib|  
|Etiketli Resim dosyası biçimi|.tif, .tiff|  
|TGA (Targa)|.TGA|  
  
## <a name="getting-started"></a>Başlarken  
 Bu bölümde, görüntüye eklemeyi açıklar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje ve gereksinimleriniz için yapılandırın.  
  
#### <a name="to-add-an-image-to-your-project"></a>Projenize bir görüntü eklemek için  
  
1.  İçinde **Çözüm Gezgini**, görüntüye eklemek ve ardından istediğiniz projenin kısayol menüsünü **Ekle**, **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunun **yüklü**seçin **grafik**ve ardından bir görüntü için uygun dosya biçimini seçin. Gereksinimlerinize göre bir dosya biçimini seçme konusunda daha fazla bilgi için aşağıdaki bölüme bakın.  
  
3.  Belirtin **adı** görüntü dosyasının ve **konumu** sonra istediğiniz yere oluşturulacak.  
  
4.  Seçin **Ekle** düğmesi.  
  
### <a name="choosing-the-image-format"></a>Görüntü biçimini seçme  
 Nasıl görüntü kullanmayı planladığınız bağlı olarak, belirli dosya biçimlerine diğerlerine göre daha uygun olabilir. Örneğin, bazı biçimler gereken bir özelliği desteklemiyor olabilir — saydamlık veya belirli renk biçimi gibi — veya gerçekleştirmeyi planladığınız görüntü içerik türü için uygun sıkıştırma sağlamayabilir.  
  
 Aşağıdaki bilgiler, ihtiyaçlarınıza uygun bir görüntü biçimi seçmenize yardımcı olabilir.  
  
 **Bit eşlem resmi (.bmp)**  
 Bit eşlem resim biçimi. 24 bit renk destekleyen bir sıkıştırılmamış görüntü biçimi. Bit eşlem biçimi saydamlık desteklemiyor.  
  
 **GIF resmi (.gif)**  
 Grafik Değişim Biçimi (GIF) görüntü biçimi. 256 renk destekler LZW sıkıştırılmış, kayıpsız bir görüntü biçimi. Uygun fotoğraflar ve renk ayrıntısını önemli miktarda var, ancak yüksek düzeyde bir renk modellenmiş sahip düşük-color görüntüler için iyi sıkıştırma oranları sağlar görüntüler.  
  
 **JPG Resmi (.jpg)**  
 Birleşik Fotoğraf Experts grubu (JPEG) görüntü biçimi. 24 bit renk destekleyen ve renk modellenmiş yüksek derecede sahip görüntülerin genel amaçlı sıkıştırma için uygun bir yüksek oranda sıkıştırılmış, kayıplı görüntü biçimi.  
  
 **PNG resmi (.png)**  
 Taşınabilir Ağ Grafikleri (PNG) görüntü biçimi. 24 bit renk ve saydamlık alfa destekleyen bir orta sıkıştırılmış, kayıpsız görüntü biçimi. Doğal ve yapay görüntüler için uygundur, ancak sıkıştırma oranı, JPG veya GIF gibi kadar iyi kayıplı biçimleri sağlamaz.  
  
 **TIFF resmi (.tif)**  
 Etiketli Resim dosyası biçimi (TIFF veya TIF) görüntü biçimi. Birkaç sıkıştırma düzenleri destekleyen esnek görüntü biçimi.  
  
 **DDS dokusu (.dds)**  
 DirectDraw Surface (DDS) doku biçimi. 24 bit renk ve saydamlık alfa destekleyen bir yüksek oranda sıkıştırılmış, kayıplı doku biçimi. Kendi sıkıştırma oranları 8:1 olarak yüksek olabilir. Grafik donanımda sıkıştırmasının açılması S3 doku sıkıştırma, temel alır.  
  
 **TGA resmi (.tga)**  
 Truevision grafik bağdaştırıcısının (TGA) görüntü biçimi (Targa olarak da bilinir). Kayıpsız, RLE'yi sıkıştırılmış görüntüyü biçimlendirme renk eşlenen her ikisini de destekler (renk paletinin) veya en fazla 24 bit renk ve saydamlık alfa doğrudan Renk görüntülerini. Uygun fotoğraflar ve renk ayrıntısını önemli ölçüde, ancak görüntüler için iyi sıkıştırma oranları sağlayan görüntüleri için aynı renkleri uzun yayılma vardır.  
  
### <a name="configuring-the-image"></a>Görüntü yapılandırma  
 Yeni oluşturduğunuz görüntüyle çalışmaya başlamadan önce varsayılan yapılandırmasını değiştirebilirsiniz. Örneğin, Boyutlar veya kullandığı renk biçimi değiştirebilirsiniz. Bunlar ve diğer görüntü özelliklerini nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [görüntü özellikleri](#ImageProperties).  
  
> [!NOTE]
>  İş kaydetmeden önce ayarladığınızdan emin olun **renk biçimi** belirli renk biçimi kullanmak istiyorsanız özelliği. Dosya biçimi, sıkıştırmayı destekliyorsa, ilk kez veya seçtiğiniz dosyayı kaydettiğinizde sıkıştırma ayarlarını ayarlayabilirsiniz **Kaydet**.  
  
## <a name="working-with-the-image-editor"></a>Resim Düzenleyicisi ile çalışma  
 Bu bölümde, dokuları ve görüntüleri değiştirmek için görüntü Düzenleyicisi kullanmayı açıklar.  
  
### <a name="image-editor-toolbars"></a>Görüntü Düzenleyicisi araç çubukları  
 Resim Düzenleyicisi araç çubukları içeren görüntülerle çalışmanıza yardımcı olan komutlar.  
  
 Resim Düzenleyicisi'nin durumunu etkileyen komutlar bulunur **resim düzenleyici modu** Gelişmiş komutları birlikte araç çubuğu. Araç çubuğunda en üstteki görüntü Düzenleyicisi tasarım yüzeyini kenarına bulunur. Çizim araçları bulunur **Resim Düzenleyicisi** Resim Düzenleyicisi tasarım yüzeyini sol kenarında araç çubuğu.  
  
 İşte **resim düzenleyici modu** araç çubuğu:  
  
 ![Resim Düzenleyicisi kalıcı araç çubuğu. ](../designers/media/digit-tre-modal-toolbar.png "TRE kalıcı araç basamak")  
  
 Bu tabloda öğeleri açıklar **resim düzenleyici modu** araç çubuğu göründükleri soldan sağa doğru sırayla listelenir.  
  
|Araç Çubuğu Öğesi|Açıklama|  
|------------------|-----------------|  
|**Seçin**|Görüntünün dikdörtgen bir bölge seçimini etkinleştirir. Bir bölge seçin, sonra Kes, kopyalayabilir, taşıma, ölçeklendirme, döndürme, çevirme veya silin. Çizim Araçları, yalnızca etkin bir seçim olduğunda, seçili bölgeye etkiler.|  
|**Düzensiz seçim**|Görüntünün düzensiz bir bölge seçimini etkinleştirir. Bir bölge seçin, sonra Kes, kopyalayabilir, taşıma, ölçeklendirme, döndürme, çevirme veya silin. Çizim Araçları, yalnızca etkin bir seçim olduğunda, seçili bölgeye etkiler.|  
|**Değnek seçimi**|Görüntünün bir benzer şekilde renkli bölge seçimini etkinleştirir. *Dayanıklılık*— diğer bir deyişle, bitişik renkleri içinde değerlendirilir benzer arasındaki en büyük fark — benzer renkleri daha küçük ya da daha geniş bir aralığını içerecek şekilde yapılandırılabilir. Bir bölge seçin, sonra Kes, kopyalayabilir, taşıma, ölçeklendirme, döndürme, çevirme veya silin. Çizim Araçları, yalnızca etkin bir seçim olduğunda, seçili bölgeye etkiler.|  
|**Pan**|Görüntünün pencere çerçevesine göre hareket sağlar. İçinde **Pan** modu, bir noktadaki bir görüntü seçin ve ardından gezinebilirsiniz.<br /><br /> Geçici olarak etkinleştirebilirsiniz **Pan** tuşuna basarak ve Ctrl tuşunu basılı tutarak modu.|  
|**Yakınlaştırma**|Görüntü ayrıntıları pencere çerçevesine göre daha az veya görüntülenmesini sağlar. İçinde **yakınlaştırma** modu, resimdeki bir nokta seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sol ettirin veya yetersiz.<br /><br /> Tuşuna basarak ve fare tekerleğini kullanabilir veya (+) artı işaretine basın Ctrl tutarken veya eksi işareti (-) yakınlaştırma veya uzaklaştırma.|  
|**Gerçek boyutuna Yakınlaştır**|Görüntü, görüntünün ve ekranın pikseller arasında 1:1 ilişki kullanarak görüntüler.|  
|**Sığacak kadar Yakınlaştır**|Tam görüntü pencere çerçevesinde görüntüler.|  
|**Genişliğe göre Yakınlaştır**|Tam görüntü genişliğini pencere çerçevesinde görüntüler.|  
|**Kılavuz**|Etkinleştirir veya piksel sınırları gösteren Kılavuzu devre dışı bırakır. Görüntüye yakınlaştırma kadar kılavuz görünmeyebilir.|  
|**Sonraki MIP düzeyini görüntüle**|MIP harita zincirindeki büyük sonraki MIP düzeyine etkinleştirir. Tasarım yüzeyinde etkin MIP düzeyi görüntülenir. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|  
|**Önceki MIP düzeyini görüntüle**|MIP harita zincirdeki sonraki daha küçük MIP düzeyine etkinleştirir. Tasarım yüzeyinde etkin MIP düzeyi görüntülenir. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|  
|**Kırmızı kanal**<br /><br /> **Yeşil kanal**<br /><br /> **Mavi kanal**<br /><br /> **Alfa kanalı**|Etkinleştirir veya belirli renk kanal devre dışı bırakır. **Not:** sistematik olarak etkinleştirme veya renk kanallarını devre dışı bırakarak, bir veya daha fazlası için ilgili sorunları ayırabilirsiniz. Örneğin, yanlış Alfa Saydamlığı tanımlayabilirsiniz.|  
|**Arka plan**|Etkinleştirir veya arka plan resmi saydam kısımları aracılığıyla görüntülenmesini devre dışı bırakır. Aşağıdaki seçeneklerden birini seçerek arka planı nasıl görüntüleneceğini yapılandırabilirsiniz:<br /><br /> **Dama Tahtası**<br /> Belirtilen arka plan rengi ile birlikte yeşil renk, arka planda bir dama tahtası desenini görüntülemek için kullanır. Resmin saydam kısımları daha belirgin hale getirmek için bu seçeneği kullanabilirsiniz.<br /><br /> Beyaz arka plan<br /> Rengi beyaz arkaplan görüntülenmesi için kullanır.<br /><br /> Siyah arka plan<br /> Arka plan görüntülemek için siyah renk kullanır.<br /><br /> Arka plana animasyon ekle<br /> Dama Tahtası desenini yavaş yatay kaydırır. Resmin saydam kısımları daha belirgin hale getirmek için bu seçeneği kullanabilirsiniz.|  
|**Özellikler**|Alternatif olarak, açar veya kapatır **özellikleri** penceresi.|  
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Birçok ortak görüntü filtreler sağlar: **siyah beyaz**, **bulanıklaştıran**, **Brighten**, **Koyulaştır**, **Kenaralgılama**, **Kabartma**, **renkleri ters çevir**, **Ripple**, **sepya**, ve **keskinleştirin**.<br /><br /> **Grafik motorları**<br /><br /> **D3d11 ile işle**<br /> Görüntü Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3d11warp ile işle**<br /> Görüntü Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır.<br /><br /> **Araçlar**<br /><br /> **Yatay Çevir**<br /> Görüntü, yatay ya da x ekseni etrafında kendisini veya sırasını değiştirir.<br /><br /> **Dikey Çevir**<br /> Görüntü, dikey ya da y ekseni etrafında kendisini veya sırasını değiştirir.<br /><br /> **Mips üret**<br /> MIP düzeyleri görüntü oluşturur. MIP düzeyleri zaten varsa, en büyük MIP düzeyini yeniden oluşturulur. Daha küçük MIP düzeylerine yapılan tüm değişiklikler kaybolur. Ürettiğiniz MIP düzeylerini kaydetmek için görüntüsünü kaydetmek için .dds biçimi kullanmanız gerekir.<br /><br /> **Görünümü**<br /><br /> **Kare hızı**<br /> Etkin olduğunda, tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:** seçebileceğiniz **Gelişmiş** düğmesine son komutu yeniden çalıştırın.|  
  
 İşte **Resim Düzenleyicisi** araç çubuğu.  
  
 ![Resim Düzenleyicisi araç çubuğu](../designers/media/digit-tre-toolbar.png "basamak TRE araç")  
  
 Öğeler aşağıdaki tabloda açıklanmaktadır **Resim Düzenleyicisi** araç çubuğu göründükleri üstten alta sırayla listelenir.  
  
|Araç Çubuğu Öğesi|Açıklama|  
|------------------|-----------------|  
|**Kalem**|Diğer adlı vuruş çizmek için etkin bir renk seçimi kullanır. İçinde kontur kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.|  
|**Fırça**|Etkin bir renk seçimi yumuşatılmış vuruş çizmek için kullanır. İçinde kontur kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.|  
|**Püskürtme kabı**|Görüntünün birlikte karıştırır ve bir zaman işlevi daha doygun olur yumuşatılmış vuruş çizmek için etkin bir renk seçimi kullanır. İçinde kontur kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.|  
|**Renk damlalığı**|Seçilen piksel rengi için etkin bir renk seçimi ayarlar.|  
|**Dolgu**|Görüntü bölgesi doldurmak için etkin bir renk seçimi kullanır. Etkilenen bölge dolgu, her piksel, kendisine aynı rengin piksel bağlı ve aynı renge birlikte uygulandığı piksel olarak tanımlanır. Dolgu içinde etkin bir seçim uygulanırsa, etkilenen bölgeyi seçerek kısıtlanmış.<br /><br /> Varsayılan olarak, görüntü, alfa bileşeni göre etkilenen bölgesi ile birlikte active renk seçimi karışık. Etkilenen bölge üzerine yazmak için etkin bir renk seçimi kullanmak için tuşuna basın ve dolgu Aracı'nı kullandığınızda Shift tuşunu basılı tutun.|  
|**Silgi**|Görüntünün bir alfa kanalı destekleyip desteklemediğini piksel için tamamen saydam rengini ayarlar. Aksi takdirde, piksel etkin arka plan rengine ayarlar.|  
|**Satır**, **dikdörtgen**, **Yuvarlatılmış Dikdörtgen**, **elipsin**|Yansımaya bir şekil çizer. Anahat kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.<br /><br /> Eşit genişlik ve yüksekliğe sahip basit bir tür çizmek için tuşuna basın ve çizerken Shift tuşunu basılı tutun.|  
|**Metin**|Ön plan renk seçimi, metin çizmek için kullanır. Arka plan rengi, arka plan rengi seçime göre belirlenir. Saydam arka plan, arka plan renk seçimi alfa değeri 0 olmalıdır. Metin bölge etkin durumdayken metni bir yumuşatılmış vuruşu çizilen ve metin ayarlayabilirsiniz ayarlayabilirsiniz **değer**, **yazı tipi**, **boyutu**ve stil —**Kalın**, **italik**, veya **altı çizili**— içinde **özellikleri** penceresi. İçerik ve metin görünümünü tümü metin bölge artık etkin olduğunda.|  
|**Döndürme**|Görüntüyü saat yönünde 90 derece döndürür.|  
|**Kırpma**|Etkin seçimin görüntüye kırpar.|  
  
### <a name="working-with-mip-levels"></a>MIP düzeyleri ile çalışma  
 Bazı görüntü biçimleri — Örneğin, doğrudan çizim yüzeyi (.dds) — MIP düzeyleri doku alanı düzeyi ayrıntı düzeyi için (LOD) destekler. Oluşturma ve MIP düzeyleri ile çalışma hakkında daha fazla bilgi için bkz [nasıl yapılır: oluşturma ve değiştirme MIP düzeyleri](../designers/how-to-create-and-modify-mip-levels.md)  
  
### <a name="working-with-transparency"></a>Saydamlık ile çalışma  
 Bazı görüntü biçimleri — Örneğin, doğrudan çizim yüzeyi (.dds) — saydamlık destekler. Saydamlık, kullandığınız araç bağlı olarak kullanılabileceğini birkaç yolu vardır. Bir renk seçimi için saydamlık düzeyini belirtmek için **özellikleri** penceresinde **A** renk seçimi bileşeninin (alfa). Saydamlık nasıl uygulanacağını araçları denetimi nasıl farklı tür aşağıda verilmiştir:  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|**Kalem**, **fırça**, **kabı**, **satırı**, **dikdörtgen**, **Yuvarlatılmış Dikdörtgen** , **Elipsin**, **metin**|Görüntü ile birlikte etkin renk seçimi içinde karıştırmak için **özellikleri** penceresinde genişletin **kanalları** özellik grubu ve küme **çizmek** onaykutusuna **Alfa** kanal ve bu normalde çizin.<br /><br /> Etkin bir renk seçimi kullanarak çizme ve alfa değeri görüntünün yerinde bırakmak için işareti kaldırın **çizmek** , onay kutusu **alfa** kanal ve bu normalde çizin.|  
|**Dolgu**|Görüntü ile birlikte etkin renk seçimi karıştırmak için yalnızca doldurmak için alanı seçin.<br /><br /> Etkin renk seçimi kullanılacak — alfa kanalı değerini de dahil olmak üzere — görüntünün üzerine yazmak için tuşuna basın ve Shift tuşunu basılı tutun ve doldurmak için alanı seçin.|  
  
###  <a name="ImageProperties"></a> Görüntü Özellikleri  
 Kullanabileceğiniz **özellikleri** penceresi görüntüyü çeşitli özelliklerini belirtmek için. Örneğin, genişlik ve yükseklik özellikleriyle görüntüyü yeniden boyutlandırmak için ayarlayabilirsiniz.  
  
 Aşağıdaki tablo, görüntü özelliklerini açıklar.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|Genişlik|Görüntü genişliği.|  
|Yükseklik|Resim yüksekliği.|  
|Piksel başına bit|Her piksel gösteren bit sayısı. Bu özelliğin değeri bağımlı **renk biçimi** görüntüsü.|  
|Saydam seçim|**Doğru** karıştırmak için ana birlikte seçimi katman görüntü, göre seçim katman alfa değeri; Aksi takdirde **False**. Bu öğe yalnızca alfa destekleyen görüntüler için kullanılabilir.|  
|Biçimi|Görüntü renk biçimi. Görüntü biçimi bağlı olarak çeşitli biçimlerde renk belirtilebilir. Renk biçimi sayısı ve tür yansıma ve boyutu dahil ve çeşitli kanal kodlama renk kanallarını tanımlar.|  
|Mip düzeyi|Etkin MIP düzeyi. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|  
|Mip düzeyi sayısı|MIP düzeyleri görüntüdeki toplam sayısı. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|  
|Çerçeve sayısı|Çerçeve görüntüdeki toplam sayısı. Bu öğe, yalnızca doku diziler destekleyen görüntüler için kullanılabilir.|  
|Çerçeve|Geçerli çerçeve. Yalnızca ilk çerçeve görüntülenebilir; diğer tüm çerçeveleri, görüntünün kaydedildiğinde kaybolur.|  
|Derinlik dilimi sayısı|Derinlik dilimleri görüntüdeki toplam sayısı. Bu öğe yalnızca birim dokular destekleyen görüntüler için kullanılabilir.|  
|Derinlik dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görüntülenebilir; görüntüyü kaydederken diğer dilimleri kaybolur.|  
  
> [!NOTE]
>  Çünkü **Döndür** özelliğinin uygulanması tüm araçları ve seçili bölgeler, sonunda her zaman görünür **özellikleri** birlikte diğer araç özellikleri penceresi. **Döndürme tarafından** diğer seçimi veya etkin araç olduğunda görüntünün tamamını örtük olarak seçili olduğundan her zaman görüntülenir. Hakkında daha fazla bilgi için **Döndür** özelliğine bakın [araç özellikleri](#ToolProperties).  
  
#### <a name="resizing-images"></a>Görüntüleri yeniden boyutlandırma  
 Bir görüntüyü yeniden boyutlandırmak için iki yolu vardır. Her iki durumda da, görüntü yeniden örneklemek için BI doğrusal enterpolasyon Resim Düzenleyicisi'ni kullanır.  
  
-   İçinde **özellikleri** penceresi için yeni değerler belirtin **genişliği** ve **yükseklik** özellikleri.  
  
-   Görüntünün tamamını seçin ve kenarlık işaretlerinin görüntüsünü yeniden boyutlandırma için kullanın.  
  
### <a name="working-with-tools"></a>Araçlar ile çalışma  
  
#### <a name="selected-regions"></a>Seçili bölge  
 Seçimleri Resim Düzenleyicisi'nde etkin olan bölgeleri görüntünün tanımlayın; araçları ve dönüştürmeler tarafından bölge diğer bir deyişle, etkilenecek. Etkin bir seçim olduğunda, seçili bölge dışında alanları araçları ve dönüştürmeler tarafından etkilenmez. Etkin bir seçim yoksa, görüntünün etkin değil.  
  
 Çoğu araç —**kalem**, **fırça**, **kabı**, **dolgu**, **Silgi**ve 2B temelleri — ve Dönüşümler —**Döndür**, **Trim**, **renkleri**, **Yatay Çevir**, ve **Dikey Çevir** : sınırlandırılmış ya da etkin seçimin tarafından tanımlanır. Ancak, bazı araçları —**renk damlalığı** ve **metin**— ve dönüştürmeler —**Mips üret**— tüm etkin seçimin tarafından; etkilenmez her zaman bu araçlar davranır gibi tüm Etkin seçimin görüntüsüdür.  
  
 Bir bölge seçerken, ancak tuşuna basın ve orantılı (kare) seçim yapmak için Shift tuşunu basılı tutun; Aksi takdirde seçimi sınırlı değildir.  
  
##### <a name="resizing-selections"></a>Seçimleri yeniden boyutlandırma  
 Bir bölge seçin, sonra seçimi işaretin boyutunu değiştirerek veya görüntü içeriğini boyutlandırabilirsiniz. Seçili bölge yeniden boyutlandırdığınız olsa da, aşağıdaki değiştirici tuşları (basılı yeniden boyutlandırma anahtar, olarak) yeniden boyutlandırma sırasında seçilen bölge davranışını değiştirmek için kullanabilirsiniz.  
  
 CTRL  
 Bu yeniden boyutlandırıldığı önce seçilen bölge içeriğini kopyalar. Kopyalama yeniden boyutlandırıldığını ancak orijinal görüntünün olduğu gibi bırakır.  
  
 Kaydırma  
 Seçili bölge derlemekten özgün boyutuna göre yeniden boyutlandırır.  
  
 Alt  
 Seçimi bölgesi boyutunu değiştirir. Bu, üzerinde değişiklik yapılmadan görüntü bırakır.  
  
 Geçerli değiştirici tuş bileşimlerini şunlardır:  
  
|CTRL|Kaydırma|Alt|Açıklama|  
|----------|-----------|---------|-----------------|  
||||Seçili bölge içeriğini yeniden boyutlandırır.|  
||Kaydırma||Orantılı olarak seçili bölge içeriğini yeniden boyutlandırır.|  
|||Alt|Seçili bölgeye göre yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|  
||Kaydırma|Alt|Orantılı olarak seçili bölgeye göre yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|  
|CTRL|||Kopyalar ve ardından seçili bölgeye içeriğini yeniden boyutlandırır.|  
|CTRL|Kaydırma||Kopyalar ve seçili bölgeye içeriğini orantılı olarak yeniden boyutlandırır.|  
  
####  <a name="ToolProperties"></a> Araç Özellikleri  
 Bir araç seçiliyken, kullanabileceğiniz **özellikleri** penceresinin görüntüsünü nasıl etkilediği hakkında ayrıntıları belirtin. Örneğin, kalınlığı ayarlayabilirsiniz **kalem** aracını veya rengini **fırça** aracı.  
  
 Hem ön plan rengini ve arka plan rengi ayarlayabilirsiniz. Her ikisi de, kullanıcı tanımlı saydamlık sağlamak için bir alfa kanalı destekler. Tüm Araçlar ayarlar uygulanır. Fare kullanıyorsanız, farenin sol düğmesi için ön plan rengini karşılık gelir ve sağ fare düğmesine karşılık gelen arka plan rengi.  
  
 Aşağıdaki tabloda, araç özellikleri açıklanmaktadır.  
  
|Aracı|Özellikler|  
|----------|----------------|  
|Tüm araçlar ve seçimleri|**Döndür:**<br /> Seçimi veya aracı etkisi saat yönünde döndürüldüğüne derece miktarı tanımlar.|  
|**Kalem**, **fırça**, **kabı**, **Silgi**|**Kalınlığı**<br /> Araç tarafından etkilenen alanının boyutunu tanımlar.|  
|**Metin**|**Yumuşatma**<br /> Yumuşatılmış kenarları metin çizer. Bu metin daha sorunsuz bir görünümünü sağlar.<br /><br /> **Değer**<br /> Çizilecek metin.<br /><br /> **Yazı tipi**<br /> Metin çizmek için kullanılan yazıtipi.<br /><br /> **Boyutu**<br /> Metin boyutu.<br /><br /> **Kalın**<br /> Yazı tipinin kalın yapar.<br /><br /> **İtalik**<br /> İtalik yazı yapar.<br /><br /> **Altı çizili**<br /> Altı çizili yazı tipi yapar.|  
|**2B temel**|**Yumuşatma**<br /> Yumuşatılmış kenarları sahip temelleri çizer. Bu onları daha sorunsuz bir görünümünü sağlar.<br /><br /> **Kalınlığı**<br /> Sınırları temel forms çizginin kalınlığını tanımlar.<br /><br /> **Yarıçap X**<br /> (Yalnızca Yuvarlatılmış dikdörtgen) Yuvarlama RADIUS temel üst ve alt kenarları için tanımlar.<br /><br /> **Yarıçap Y**<br /> (Yalnızca Yuvarlatılmış dikdörtgen) Yuvarlama RADIUS temel sol ve sağ kenarları için tanımlar.|  
|**Kalem**, **fırça**, **kabı**, **2B temel**|**Kanallar**<br /> Etkinleştirir veya belirli renk kanallarını görüntüleme ve çizim için devre dışı bırakır. Varsa **görünümü** kanal için bir belirli renk kanal olarak ayarlı, görüntüde görünür; Aksi takdirde, görünür değil. Varsa **çizmek** ayarlanmış belirli renk kanal için kanal işlemleri çizim tarafından etkilenen; Aksi takdirde, bu değildir.|  
|**Değnek seçimi**, **doldurun**|**Dayanıklılık**<br /> Bitişik renkleri, böylece daha az veya fazla benzer renkleri etkilenen ya da seçili bölgeye bir parçası olarak yapılır içinde benzer olarak kabul edilir arasındaki en büyük fark tanımlar. Varsayılan olarak, 32 bitişik piksel özgün renk, 32 gri (açık veya koyu) içinde bölgesinin bir parçası olarak değerlendirilir anlamına gelir değerdir.|  
  
## <a name="keyboard-shortcuts"></a>Klavye kısayolları  
  
|Komut|Klavye kısayolları|  
|-------------|------------------------|  
|Geçiş **seçin** modu|S|  
|Geçiş **yakınlaştırma** modu|Z|  
|Geçiş **Pan** modu|K|  
|Tümünü seç|Ctrl+A|  
|Geçerli seçimi sil|Sil|  
|Geçerli seçimi iptal et|Esc|  
|Yakınlaştır|Ctrl+Fare tekerleği ileriye doğru<br /><br /> Ctrl+PageUp<br /><br /> Artı İşareti (+)|  
|Uzaklaştır|CTRL-fare tekerleği geriye doğru<br /><br /> CTRL-PageDown<br /><br /> Eksi İşareti (-)|  
|Görüntü yukarı kaydır|Fare tekerleği geriye doğru<br /><br /> PageDown|  
|Görüntüyü aşağı kaydır|Fare tekerleği ileriye doğru<br /><br /> PageUp|  
|Görüntünün sola kaydır|Shift+Fare tekerleği geriye doğru<br /><br /> Fare tekerleği sol<br /><br /> Shift + PageDown|  
|Görüntü sağa kaydır|Shift+Fare tekerleği ileriye doğru<br /><br /> Fare tekerleği sağ<br /><br /> Shift + PageUp|  
|Gerçek boyutuna Yakınlaştır|CTRL + 0 (sıfır)|  
|Resmi pencereye sığdır|CTRL + G, Ctrl + F|  
|Pencere genişliği Sığdır görüntüye|CTRL + G, Ctrl + ı|  
|Kılavuzu Aç/Kapat|CTRL + G, Ctrl + G|  
|Geçerli seçimi görüntüsünü Kırp|CTRL + G, Ctrl + C|  
|Görünümü İleri (daha ayrıntılı) MIP düzeyi|CTRL + G, Ctrl + 6|  
|Görüntüleme önceki (alt ayrıntılı) MIP düzeyi|CTRL + G, Ctrl + 7|  
|İki durumlu kırmızı renk kanalı|CTRL + G, Ctrl + 1|  
|İki durumlu yeşil renk kanalı|CTRL + G, Ctrl + 2|  
|İki durumlu mavi renk kanalı|CTRL + G, Ctrl + 3|  
|İki durumlu (saydam) alfa kanalı|CTRL + G, Ctrl + 4|  
|Alfa dama tahtası desenini Aç/Kapat|CTRL + G, Ctrl + B|  
|Düzensiz seçim aracı arasında geçiş|L|  
|Değnek seçim aracını geçiş|M|  
|Kalem aracı geç|P|  
|Fırça aracı geç|B|  
|Dolgu aracı geç|F|  
|Silgi aracına geçme|E|  
|Metin aracı arasında geçiş|T|  
|Renk Seç (renk damlalığı) aracı arasında geçiş|I|  
|Etkin seçimin ve içeriği taşıyın.|Ok tuşları.|  
|Etkin seçimin ve içeriği yeniden boyutlandırın.|CTRL + ok tuşları|  
|Etkin seçimin ancak içeriğini değil taşıyın.|SHIFT + ok tuşları|  
|Etkin seçimin, ancak kendi içeriklerini yeniden boyutlandırın.|Shift + Ctrl + ok tuşları|  
|Geçerli katmanını işle|döndürülecek|  
|Azaltma aracının kalınlığı|[|  
|Aracının kalınlığı artırın|]|  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Kullanabileceğiniz araçları genel bakışını sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokular ve resimler, 3B modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için.|  
|[Model Düzenleyicisi](../designers/model-editor.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 3B modellerle çalışmak için Model Düzenleyicisi.|  
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gölgelendiricilerle çalışmak için gölgelendirici Tasarımcısı.|



