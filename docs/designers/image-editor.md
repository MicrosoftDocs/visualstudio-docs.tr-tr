---
title: Görüntü Düzenleyici
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2149410782587d8472faff678cbc20bf1ea577c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878382"
---
# <a name="image-editor"></a>Görüntü düzenleyicisi

Bu makalede Visual Studio ile çalışmaya nasıl **Resim Düzenleyicisi** doku ve resim kaynakları görüntülemek ve değiştirmek için.

Kullanabileceğiniz **Resim Düzenleyicisi** DirectX uygulaması geliştirmede kullanılan zengin doku ve resim biçimleri türleri ile çalışmak için. Bu popüler görüntü dosyası biçimlerini ve renk Kodlamalar, alfa kanalları ve MIP eşleştirme gibi özellikler için destek içerir ve DirectX destekleyen yüksek oranda sıkıştırılmış, Donanım hızlandırmalı doku birçoğu biçimlendirir.

## <a name="supported-formats"></a>Desteklenen biçimler

**Resim Düzenleyicisi** aşağıdaki görüntü biçimlerini destekler:

|Biçim adı|Dosya Adı Uzantısı|
|-----------------| - |
|Taşınabilir Ağ Grafikleri|*.PNG*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Doğrudan çizim yüzeyi|*.DDS*|
|Grafik Değişim Biçimi|*.gif*|
|Bit eşlem|*.bmp*, *.dib*|
|Etiketli Resim dosyası biçimi|*.tif*, *.tiff*|
|TGA (Targa)|*.TGA*|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde, Visual Studio projenize bir görüntü ekleyin ve gereksinimleriniz için yapılandırma açıklanmaktadır.

### <a name="add-an-image-to-your-project"></a>Projenize bir görüntü ekleme

1. İçinde **Çözüm Gezgini**, görüntüye eklemek ve ardından istediğiniz projenin kısayol menüsünü **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunun **yüklü**seçin **grafik**ve ardından bir görüntü için uygun dosya biçimini seçin.

   > [!NOTE]
   > Görmüyorsanız **grafik** kategorisinde **Yeni Öğe Ekle** iletişim kutusunda, yüklemeniz gerekebilir **görüntü ve 3B model düzenleyicileri** bileşeni. İletişim kutusunu kapatın ve ardından **Araçları** > **araçları ve özellikleri Al** açmak için menü çubuğundan **Visual Studio yükleyicisi**. Seçin **tek tek bileşenler** sekmesine tıklayın ve ardından **görüntü ve 3B model düzenleyicileri** altındaki bileşen **oyunlar ve grafik** kategorisi. Seçin **değiştirme**.
   >
   > ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

   Gereksinimlerinize göre bir dosya biçimini seçme konusunda daha fazla bilgi için bkz: [görüntü biçimi seçin](#choose-the-image-format).

3. Belirtin **adı** görüntü dosyasının ve **konumu** sonra istediğiniz yere oluşturulacak.

4. Seçin **Ekle** düğmesi.

### <a name="choose-the-image-format"></a>Görüntü biçimi seçin

Nasıl görüntü kullanmayı planladığınız bağlı olarak, belirli dosya biçimlerine diğerlerine göre daha uygun olabilir. Örneğin, bazı biçimler örneğin gereken bir özellik, saydam veya belirli renk biçimi desteklemiyor olabilir. Bazı biçimler planladığınız görüntü içerik türü için uygun sıkıştırma sağlamayabilir.

Aşağıdaki bilgiler ihtiyaçlarınıza uygun bir görüntü biçimi seçmenize yardımcı olabilir:

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

### <a name="configure-the-image"></a>Yapılandırma resmi

Oluşturduğunuz görüntüyle çalışmaya başlamadan önce varsayılan yapılandırmasını değiştirebilirsiniz. Örneğin, Boyutlar veya kullandığı renk biçimi değiştirebilirsiniz. Bunlar ve diğer görüntü özelliklerini nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [görüntü özellikleri](#image-properties).

> [!NOTE]
> İş kaydetmeden önce ayarladığınızdan emin olun **renk biçimi** belirli renk biçimi kullanmak istiyorsanız özelliği. Dosya biçimi, sıkıştırmayı destekliyorsa, ilk kez veya seçtiğiniz dosyayı kaydettiğinizde sıkıştırma ayarlarını ayarlayabilirsiniz **Kaydet**.

## <a name="work-with-the-image-editor"></a>Resim Düzenleyicisi ile çalışma

Bu bölümde, nasıl kullanılacağını açıklar **Resim Düzenleyicisi** dokularla ve görüntülerle değiştirilecek.

Durumunu etkileyen komutlar **Resim Düzenleyicisi** bulunan **resim düzenleyici modu** Gelişmiş komutları birlikte araç çubuğu. Araç çubuğunun üst kenarı boyunca bulunan **Resim Düzenleyicisi** tasarım yüzeyi. Çizim araçları bulunur **Resim Düzenleyicisi** araç sol kenarı boyunca **Resim Düzenleyicisi** tasarım yüzeyi.

### <a name="image-editor-mode-toolbar"></a>Resim Düzenleyici modu araç çubuğu

![Visual Studio Resim Düzenleyici modu araç](../designers/media/digit-tre-modal-toolbar.png)

Öğeler aşağıdaki tabloda açıklanmaktadır **resim düzenleyici modu** araç çubuğu göründükleri soldan sağa doğru sırayla listelenir:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seçin**|Görüntünün dikdörtgen bir bölge seçimini etkinleştirir. Bir bölge seçin, sonra Kes, kopyalayabilir, taşıma, ölçeklendirme, döndürme, çevirme veya silin. Çizim Araçları, yalnızca etkin bir seçim olduğunda, seçili bölgeye etkiler.|
|**Düzensiz seçim**|Görüntünün düzensiz bir bölge seçimini etkinleştirir. Bir bölge seçin, sonra Kes, kopyalayabilir, taşıma, ölçeklendirme, döndürme, çevirme veya silin. Çizim Araçları, yalnızca etkin bir seçim olduğunda, seçili bölgeye etkiler.|
|**Değnek seçimi**|Benzer şekilde renkli bir bölge görüntü seçimini etkinleştirir. *Dayanıklılık*— diğer bir deyişle, bitişik renkleri içinde değerlendirilir benzer arasındaki en büyük fark — benzer renkleri daha küçük ya da daha geniş bir aralığını içerecek şekilde yapılandırılabilir. Bir bölge seçin, sonra Kes, kopyalayabilir, taşıma, ölçeklendirme, döndürme, çevirme veya silin. Çizim Araçları, yalnızca etkin bir seçim olduğunda, seçili bölgeye etkiler.|
|**Pan**|Görüntünün pencere çerçevesine göre hareket sağlar. İçinde **Pan** modu, bir noktadaki bir görüntü seçin ve ardından gezinebilirsiniz.<br /><br /> Geçici olarak etkinleştirebilirsiniz **Pan** tuşuna basarak ve bulunduran modu **Ctrl** anahtarı.|
|**Yakınlaştırma**|Görüntü ayrıntıları pencere çerçevesine göre daha az veya görüntülenmesini sağlar. İçinde **yakınlaştırma** modu, resimdeki bir nokta seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sol ettirin veya yetersiz.<br /><br /> Yakınlaştırmak veya uzaklaştırmak tuşuna basın ve basılı tarafından **Ctrl** fare tekerleğini kullanın veya artı işaretine basın (**+**) ya da eksi işareti (**-**) .|
|**Gerçek boyutuna Yakınlaştır**|Görüntü, görüntünün ve ekranın pikseller arasında 1:1 ilişki kullanarak görüntüler.|
|**Sığacak kadar Yakınlaştır**|Tam görüntü pencere çerçevesinde görüntüler.|
|**Genişliğe göre Yakınlaştır**|Tam görüntü genişliğini pencere çerçevesinde görüntüler.|
|**Kılavuz**|Etkinleştirir veya piksel sınırları gösteren Kılavuzu devre dışı bırakır. Görüntüye yakınlaştırma kadar kılavuz görünmeyebilir.|
|**Sonraki MIP düzeyini görüntüle**|MIP harita zincirindeki büyük sonraki MIP düzeyine etkinleştirir. Tasarım yüzeyinde etkin MIP düzeyi görüntülenir. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|
|**Önceki MIP düzeyini görüntüle**|MIP harita zincirdeki sonraki daha küçük MIP düzeyine etkinleştirir. Tasarım yüzeyinde etkin MIP düzeyi görüntülenir. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|
|**Kırmızı kanal**<br /><br /> **Yeşil kanal**<br /><br /> **Mavi kanal**<br /><br /> **Alfa kanalı**|Etkinleştirir veya belirli renk kanal devre dışı bırakır. **Not:** sistematik olarak etkinleştirme veya renk kanallarını devre dışı bırakarak, bir veya daha fazlası için ilgili sorunları ayırabilirsiniz. Örneğin, yanlış Alfa Saydamlığı tanımlayabilirsiniz.|
|**Arka plan**|Etkinleştirir veya arka plan resmi saydam kısımları aracılığıyla görüntülenmesini devre dışı bırakır. Aşağıdaki seçeneklerden birini seçerek arka planı nasıl görüntüleneceğini yapılandırabilirsiniz:<br /><br /> **Dama Tahtası**<br /> Belirtilen arka plan rengi ile birlikte yeşil renk, arka planda bir dama tahtası desenini görüntülemek için kullanır. Resmin saydam kısımları daha belirgin hale getirmek için bu seçeneği kullanabilirsiniz.<br /><br /> Beyaz arka plan<br /> Rengi beyaz arkaplan görüntülenmesi için kullanır.<br /><br /> Siyah arka plan<br /> Arka plan görüntülemek için siyah renk kullanır.<br /><br /> Arka plana animasyon ekle<br /> Dama Tahtası desenini yavaş yatay kaydırır. Resmin saydam kısımları daha belirgin hale getirmek için bu seçeneği kullanabilirsiniz.|
|**Özellikler**|Alternatif olarak, açar veya kapatır **özellikleri** penceresi.|
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Birçok ortak görüntü filtreler sağlar: **siyah beyaz**, **bulanıklaştıran**, **Brighten**, **Koyulaştır**, **Kenaralgılama**, **Kabartma**, **renkleri ters çevir**, **Ripple**, **sepya**, ve **keskinleştirin**.<br /><br /> **Grafik motorları**<br /><br /> **D3d11 ile işle**<br /> İşlemek için Direct3D 11 kullanır **Resim Düzenleyicisi** tasarım yüzeyi.<br /><br /> **D3d11warp ile işle**<br /> İşlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır **Resim Düzenleyicisi** tasarım yüzeyi.<br /><br /> **Araçlar**<br /><br /> **Yatay Çevir**<br /> Görüntü, yatay ya da x ekseni etrafında kendisini veya sırasını değiştirir.<br /><br /> **Dikey Çevir**<br /> Görüntü, dikey ya da y ekseni etrafında kendisini veya sırasını değiştirir.<br /><br /> **Mips üret**<br /> MIP düzeyleri görüntü oluşturur. MIP düzeyleri zaten varsa, en büyük MIP düzeyini yeniden oluşturulur. Daha küçük MIP düzeylerine yapılan tüm değişiklikler kaybolur. Ürettiğiniz MIP düzeylerini kaydetmek için kullanmanız gerekir *.dds* görüntüsünü kaydetmek için kullanılan biçim.<br /><br /> **Görünümü**<br /><br /> **Kare hızı**<br /> Etkin olduğunda, tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:** seçebileceğiniz **Gelişmiş** düğmesine son komutu yeniden çalıştırın.|

### <a name="image-editor-toolbar"></a>Resim Düzenleyicisi araç çubuğu

![Resim Düzenleyicisi araç çubuğu](../designers/media/digit-tre-toolbar.png)

Öğeler aşağıdaki tabloda açıklanmaktadır **Resim Düzenleyicisi** araç çubuğu göründükleri üstten alta sırayla listelenir:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Kalem**|Diğer adlı vuruş çizmek için etkin bir renk seçimi kullanır. İçinde kontur kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.|
|**Fırça**|Etkin bir renk seçimi yumuşatılmış vuruş çizmek için kullanır. İçinde kontur kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.|
|**Püskürtme kabı**|Görüntünün birlikte karıştırır ve bir zaman işlevi daha doygun olur yumuşatılmış vuruş çizmek için etkin bir renk seçimi kullanır. İçinde kontur kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.|
|**Renk damlalığı**|Seçilen piksel rengi için etkin bir renk seçimi ayarlar.|
|**Dolgu**|Görüntü bölgesi doldurmak için etkin bir renk seçimi kullanır. Etkilenen bölge dolgu, her piksel, kendisine aynı rengin piksel bağlı ve aynı renge birlikte uygulandığı piksel olarak tanımlanır. Dolgu içinde etkin bir seçim uygulanırsa, etkilenen bölgeyi seçerek kısıtlanmış.<br /><br /> Varsayılan olarak, görüntü, alfa bileşeni göre etkilenen bölgesi ile birlikte active renk seçimi karışık. Etkilenen bölge üzerine yazmak için etkin bir renk seçimi kullanmak için basılı **Shift** anahtar dolgu Aracı'nı kullandığınızda.|
|**Silgi**|Görüntünün bir alfa kanalı destekleyip desteklemediğini piksel için tamamen saydam rengini ayarlar. Aksi takdirde, piksel etkin arka plan rengine ayarlar.|
|**Satır**, **dikdörtgen**, **Yuvarlatılmış Dikdörtgen**, **elipsin**|Yansımaya bir şekil çizer. Anahat kalınlığı ve rengini ayarlayabilirsiniz **özellikleri** penceresi.<br /><br /> Eşit genişlik ve yüksekliğe sahip basit bir tür çizmek için basılı **Shift** çizin.|
|**Metin**|Ön plan renk seçimi, metin çizmek için kullanır. Arka plan rengi, arka plan rengi seçime göre belirlenir. Saydam arka plan, arka plan renk seçimi alfa değeri 0 olmalıdır. Metin bölge etkin durumdayken metni bir yumuşatılmış vuruşu çizilen ve metin ayarlayabilirsiniz ayarlayabilirsiniz **değer**, **yazı tipi**, **boyutu**ve stil —**Kalın**, **italik**, veya **altı çizili**— içinde **özellikleri** penceresi. İçerik ve metin görünümünü tümü metin bölge artık etkin olduğunda.|
|**Döndürme**|Görüntüyü saat yönünde 90 derece döndürür.|
|**Kırpma**|Etkin seçimin görüntüye kırpar.|

### <a name="work-with-mip-levels"></a>MIP düzeyleri ile çalışma

Bazı görüntü biçimleri, örneğin, DirectDraw Surface (*.dds*), doku alanı düzeyi ayrıntı düzeyi için (LOD) MIP düzeylerini destekler. Oluşturma ve MIP düzeyleri ile çalışma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Saydamlık ile çalışma

Bazı görüntü biçimleri, örneğin, DirectDraw Surface (*.dds*), saydamlık destekler. Saydamlık, kullanmakta olduğunuz aracı bağlı olarak kullanabileceğiniz birçok yöntem vardır. Bir renk seçimi için saydamlık düzeyini belirtmek için **özellikleri** penceresinde **A** renk seçimi bileşeninin (alfa).

Aşağıdaki tabloda, saydamlık nasıl uygulanacağını araçları denetimi nasıl farklı türleri açıklanmaktadır:

|Aracı|Açıklama|
|----------|-----------------|
|**Kalem**, **fırça**, **kabı**, **satırı**, **dikdörtgen**, **Yuvarlatılmış Dikdörtgen** , **Elipsin**, **metin**|Görüntü ile birlikte etkin renk seçimi içinde karıştırmak için **özellikleri** penceresinde genişletin **kanalları** özellik grubu ve küme **çizmek** onaykutusuna **Alfa** kanal ve bu normalde çizin.<br /><br /> Etkin bir renk seçimi kullanarak çizme ve alfa değeri görüntünün yerinde bırakmak için işareti kaldırın **çizmek** , onay kutusu **alfa** kanal ve bu normalde çizin.|
|**Dolgu**|Görüntü ile birlikte etkin renk seçimi karıştırmak için yalnızca doldurmak için alanı seçin.<br /><br /> Etkin renk seçimi kullanılacak — alfa kanalı değerini de dahil olmak üzere — görüntünün üzerine yazmak için basılı **Shift** doldurmak için alanı seçin.|

### <a name="image-properties"></a>Görüntü Özellikleri

Kullanabileceğiniz **özellikleri** penceresi görüntüyü çeşitli özelliklerini belirtmek için. Örneğin, genişlik ve yükseklik özellikleriyle görüntüyü yeniden boyutlandırmak için ayarlayabilirsiniz.

Aşağıdaki tablo, görüntü özellikleri açıklar:

|Özellik|Açıklama|
|--------------|-----------------|
|Genişlik|Görüntü genişliği.|
|Yükseklik|Resim yüksekliği.|
|Piksel başına bit|Her piksel gösteren bit sayısı. Bu özelliğin değeri bağımlı **renk biçimi** görüntüsü.|
|Saydam seçim|**Doğru** karıştırmak için ana birlikte seçimi katman görüntü, göre seçim katman alfa değeri; Aksi takdirde **False**. Bu öğe yalnızca alfa destekleyen görüntüler için kullanılabilir.|
|Biçimi|Görüntü renk biçimi. Renk biçimleri, resim biçimi bağlı olarak çeşitli belirtebilirsiniz. Renk biçimi sayısı ve tür yansıma ve boyutu dahil ve çeşitli kanal kodlama renk kanallarını tanımlar.|
|Mip düzeyi|Etkin MIP düzeyi. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|
|Mip düzeyi sayısı|MIP düzeyleri görüntüdeki toplam sayısı. Bu öğe yalnızca MIP düzeyleri dokular için kullanılabilir.|
|Çerçeve sayısı|Çerçeve görüntüdeki toplam sayısı. Bu öğe, yalnızca doku diziler destekleyen görüntüler için kullanılabilir.|
|Çerçeve|Geçerli çerçeve. Yalnızca ilk çerçeve görüntülenebilir; diğer tüm çerçeveleri, görüntünün kaydedildiğinde kaybolur.|
|Derinlik dilimi sayısı|Derinlik dilimleri görüntüdeki toplam sayısı. Bu öğe yalnızca birim dokular destekleyen görüntüler için kullanılabilir.|
|Derinlik dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görüntülenebilir; görüntüyü kaydederken diğer dilimleri kaybolur.|

> [!NOTE]
> Çünkü **Döndür** özelliğinin uygulanması tüm araçları ve seçili bölgeler, sonunda her zaman görünür **özellikleri** birlikte diğer araç özellikleri penceresi. **Döndürme tarafından** diğer seçimi veya etkin araç olduğunda görüntünün tamamını örtük olarak seçili olduğundan her zaman görüntülenir. Hakkında daha fazla bilgi için **Döndür** özelliğine bakın [aracı özellikleri](#tool -properties).

### <a name="resize-images"></a>Görüntüleri yeniden boyutlandırma

Bir görüntüyü yeniden boyutlandırmak için iki yolu vardır. Her iki durumda da **Resim Düzenleyicisi** çift doğrusal enterpolasyon görüntü yeniden örneklemek için kullanır.

- İçinde **özellikleri** penceresi için yeni değerler belirtin **genişliği** ve **yükseklik** özellikleri.

- Görüntünün tamamını seçin ve kenarlık işaretlerinin görüntüsünü yeniden boyutlandırma için kullanın.

### <a name="selected-regions"></a>Seçili bölge

Seçimleri **Resim Düzenleyicisi** etkin olan bölgeleri görüntünün tanımlayın. Etkin bölgeler, araçları ve dönüştürmeler tarafından etkilenir. Etkin bir seçim olduğunda, seçili bölge dışında alanları araçları ve dönüştürmeler tarafından etkilenmez. Etkin bir seçim yoksa, görüntünün etkin değil.

Çoğu araç (**kalem**, **fırça**, **kabı**, **dolgu**, **Silgi**ve 2B ilkel) ve Dönüşümler (**Döndür**, **Trim**, **renkleri**, **Yatay Çevir**, ve **Dikey Çevir** ) sınırlandırılmış ya da etkin seçimin tarafından tanımlanır. Ancak, bazı araçlar (**damlalığı** ve **metin**) ve dönüştürmeler (**Mips üret**) herhangi bir etkin seçimin tarafından etkilenmez. Bu araçlar, her zaman görüntünün etkin seçimin grubundaymış gibi davranır.

Bir bölge seçeneğini belirliyoruz ancak tutun tuşuna basın ve **Shift** orantılı (kare) seçim yapmak için. Aksi takdirde seçimi sınırlı değildir.

#### <a name="resize-selections"></a>Seçimleri yeniden boyutlandırma

Bir bölge seçin, sonra seçimi işaretin boyutunu değiştirerek veya görüntü içeriğini boyutlandırabilirsiniz. Seçili bölge yeniden boyutlandırma sırasında yeniden boyutlandırma sırasında seçilen bölge davranışını değiştirmek için aşağıdaki değiştirici tuşları kullanabilirsiniz:

**CTRL** -yeniden önce seçilen bölge içeriğini kopyalar. Kopyalama yeniden boyutlandırıldığını ancak orijinal görüntünün olduğu gibi bırakır.

**Shift** -özgün boyutuna derlemekten seçili bölgeye göre yeniden boyutlandırır.

**Alt** -seçimi bölgesi boyutunu değiştirir. Bu, üzerinde değişiklik yapılmadan görüntü bırakır.

Aşağıdaki tablo, geçerli değiştirici tuş birleşimlerini açıklar:

|CTRL|Kaydırma|Alt|Açıklama|
|----------|-----------|---------|-----------------|
||||Seçili bölge içeriğini yeniden boyutlandırır.|
||**Kaydırma**||Orantılı olarak seçili bölge içeriğini yeniden boyutlandırır.|
|||**Alt**|Seçili bölgeye göre yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
||**Kaydırma**|**Alt**|Orantılı olarak seçili bölgeye göre yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
|**CTRL**|||Kopyalar ve ardından seçili bölgeye içeriğini yeniden boyutlandırır.|
|**CTRL**|**Kaydırma**||Kopyalar ve seçili bölgeye içeriğini orantılı olarak yeniden boyutlandırır.|

### <a name="tool-properties"></a>Araç Özellikleri

Bir araç seçiliyken, kullanabileceğiniz **özellikleri** penceresinin görüntüsünü nasıl etkilediği hakkında ayrıntıları belirtin. Örneğin, kalınlığı ayarlayabilirsiniz **kalem** aracını veya rengini **fırça** aracı.

Hem ön plan rengini ve arka plan rengi ayarlayabilirsiniz. Her ikisi de, kullanıcı tanımlı saydamlık sağlamak için bir alfa kanalı destekler. Tüm Araçlar ayarlar uygulanır. Fare kullanıyorsanız, farenin sol düğmesi için ön plan rengini karşılık gelir ve sağ fare düğmesine karşılık gelen arka plan rengi.

Aşağıdaki tabloda, araç özellikleri açıklanmaktadır:

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
|-------------| - |
|Geçiş **seçin** modu|**S**|
|Geçiş **yakınlaştırma** modu|**Z**|
|Geçiş **Pan** modu|**K**|
|Tümünü seç|**CTRL**+**A**|
|Geçerli seçimi sil|**Delete**|
|Geçerli seçimi iptal et|**ESC** (çıkış)|
|Yakınlaştır|**CTRL**+**fare tekerleği ileriye doğru**<br /><br /> **CTRL**+**PageUp**<br /><br /> Artı işareti (**+**)|
|Uzaklaştır|**CTRL**-**fare tekerleği geriye doğru**<br /><br /> **CTRL**-**PageDown**<br /><br /> Eksi işareti (**-**)|
|Görüntü yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Görüntüyü aşağı kaydır|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Görüntünün sola kaydır|**Shift**+**fare tekerleği geriye doğru**<br /><br /> **Fare tekerleği sol**<br /><br /> **Shift**+**PageDown**|
|Görüntü sağa kaydır|**Shift**+**fare tekerleği ileriye doğru**<br /><br /> **Fare tekerleği sağ**<br /><br /> **Shift**+**PageUp**|
|Gerçek boyutuna Yakınlaştır|**CTRL**+**0** (sıfır)|
|Resmi pencereye sığdır|**CTRL**+**G**, **Ctrl**+**F**|
|Pencere genişliği Sığdır görüntüye|**CTRL**+**G**, **Ctrl**+**ediyorum**|
|Kılavuzu Aç/Kapat|**CTRL**+**G**, **Ctrl**+**G**|
|Geçerli seçimi görüntüsünü Kırp|**CTRL**+**G**, **Ctrl**+**C**|
|Görünümü İleri (daha ayrıntılı) MIP düzeyi|**CTRL**+**G**, **Ctrl**+**6**|
|Görüntüleme önceki (alt ayrıntılı) MIP düzeyi|**CTRL**+**G**, **Ctrl**+**7**|
|İki durumlu kırmızı renk kanalı|**CTRL**+**G**, **Ctrl**+**1**|
|İki durumlu yeşil renk kanalı|**CTRL**+**G**, **Ctrl**+**2**|
|İki durumlu mavi renk kanalı|**CTRL**+**G**, **Ctrl**+**3**|
|İki durumlu (saydam) alfa kanalı|**CTRL**+**G**, **Ctrl**+**4**|
|Alfa dama tahtası desenini Aç/Kapat|**CTRL**+**G**, **Ctrl**+**B**|
|Düzensiz seçim aracı arasında geçiş|**L**|
|Değnek seçim aracını geçiş|**M**|
|Kalem aracı geç|**P**|
|Fırça aracı geç|**B**|
|Dolgu aracı geç|**F**|
|Silgi aracına geçme|**E**|
|Metin aracı arasında geçiş|**T**|
|Renk Seç (renk damlalığı) aracı arasında geçiş|**I**|
|Etkin seçimin ve içeriği taşıyın.|**OK** anahtarları.|
|Etkin seçimin ve içeriği yeniden boyutlandırın.|**CTRL**+**ok** anahtarları|
|Etkin seçimin ancak içeriğini değil taşıyın.|**Shift**+**ok** anahtarları|
|Etkin seçimin, ancak kendi içeriklerini yeniden boyutlandırın.|**Shift**+**Ctrl**+**ok** anahtarları|
|Geçerli katmanını işle|**döndürülecek**|
|Azaltma aracının kalınlığı|**[**|
|Aracının kalınlığı artırın|**]**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Visual Studio'da dokular ve resimler, 3B modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz araçları genel bir bakış sağlar.|
|[Model düzenleyicisi](../designers/model-editor.md)|3B modellerle çalışmak için Visual Studio Model Düzenleyicisi'ni kullanmayı açıklar.|
|[Gölgelendirici tasarımcısı](../designers/shader-designer.md)|Gölgelendiricilerle çalışmak için Visual Studio gölgelendirici Tasarımcısı kullanmayı açıklar.|