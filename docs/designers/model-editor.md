---
title: Model Düzenleyicisi
ms.date: 04/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7e3da13240eb172e29676b990d1c23be71e4542
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855540"
---
# <a name="model-editor"></a>Model düzenleyicisi

Bu belge, Visual Studio ile çalışmaya açıklar **Model Düzenleyicisi** görüntülemek için oluşturma ve 3B modelleri değiştirin.

Kullanabileceğiniz **Model Düzenleyicisi** sıfırdan temel 3B model oluşturma veya görüntüleyebilir ve tam özellikli 3B modelleme araçları kullanılarak oluşturulmuş daha karmaşık 3B modelleri değiştirebilirsiniz.

## <a name="supported-formats"></a>Desteklenen biçimler

**Model Düzenleyicisi** DirectX uygulaması geliştirmede kullanılan çeşitli 3B model biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görüntüleme, Düzenleme, Oluşturma)|
|-----------------| - | - |
|AutoDesk FBX Değişim Dosyası|*.fbx*|Görüntüleme, Düzenleme, Oluşturma|
|Collada DAE Dosyası|*.DAE*|Görüntüleme, Düzenleme (Collada DAE dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|
|OBJ|*.obj*|Görüntüleme, Düzenleme (OBJ dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde, Visual Studio C++ projenize bir 3B model eklemeyi açıklar ve yardımcı olacak diğer temel bilgi başlama.

> [!NOTE]
> 3B Sahne (.fbx dosyaları) gibi grafik öğelerinin otomatik derleme tümleştirmesi yalnızca C++ projeleri için desteklenir.

### <a name="to-add-a-3d-model-to-your-project"></a>Projenize bir 3B model eklemek için

1. Grafiklerle gerektiğini bileşeni yüklü gerekli Visual Studio olduğundan emin olun. Bileşen çağrılır **görüntü ve 3B model düzenleyicileri**.

   Yüklemek için Visual Studio yükleyicisi seçerek açın **Araçları** > **araçları ve özellikleri Al** çubuğu ve ardından menüden **tek tek bileşenler**sekmesi. Seçin **görüntü ve 3B model düzenleyicileri** altındaki bileşen **oyunlar ve grafik** kategori tıklayın ve ardından **Değiştir**.

   ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

   Bileşeni yükleme başlar.

2. İçinde **Çözüm Gezgini**, görüntüye eklemek ve ardından istediğiniz C++ projesi için kısayol menüsünü açın **Ekle** > **yeni öğe**.

3. İçinde **Yeni Öğe Ekle** iletişim kutusunun **grafik** kategorisi, select **3B Sahne (.fbx)**.

   ![Seçili 3B Sahne ile yeni öğesi ekleme](media/add-new-3d-scene.png)

   > [!NOTE]
   > Görmüyorsanız **grafik** kategorisinde **Yeni Öğe Ekle** iletişim ve **görüntü ve 3B model düzenleyicileri** bileşeni yüklü, grafik öğeleri desteklenmez Proje türü için.

4. Girin **adı** model dosyasını ve ardından **Ekle**.

### <a name="axis-orientation"></a>Eksen yönlendirme

Visual Studio 3B ekseninin her yönlendirmesini destekler ve onu destekleyen model dosyası biçimlerinden eksen yönlendirmesi bilgilerini yükler. Hiçbir eksen yönlendirmesi belirtilmezse, Visual Studio varsayılan olarak sağ taraf yönelimli koordinat sistemini kullanır. **Eksen göstergesi** tasarım yüzeyinin sağ alt köşesinde geçerli eksen yönlendirmesini gösterir. Üzerinde **eksen göstergesi**, kırmızı x eksenini temsil eder, yeşil, y eksenini temsil eder ve mavi z ekseni temsil eder.

### <a name="begin-your-3d-model"></a>3B modelinize başlama

Model Düzenleyicisi'nde her yeni nesne her zaman temel 3B şekillerin biri olarak başlar — veya *Temelleri*; Model Düzenleyicisi içinde oluşturulur. Yeni ve benzersiz nesneler oluşturmak için, görünüme bir temel öğe ekler ve sonra da köşeleriyle oynayarak şeklini değiştirirsiniz. Karmaşık şekiller için, kalıp veya alt bölüm kullanarak ek köşeler ekler ve sonra bunlarda değişiklik yaparsınız. Görünümünüze temel öğe nesnesi ekleme hakkında daha fazla bilgi için bkz: [oluştur ve içeri aktarma 3B nesneleri](#Adding3DObjects). Bir nesne için daha fazla köşe ekleme hakkında daha fazla bilgi için bkz: [nesneleri değiştirme](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Model Düzenleyicisi ile çalışma

Aşağıdaki bölümlerde, 3B modellerle çalışmak için Model Düzenleyicisi'ni kullanma açıklanmaktadır.

### <a name="model-editor-toolbars"></a>Model Düzenleyicisi araç çubukları

Model Düzenleyicisi araç çubukları içeren, 3B modellerle çalışmanıza yardımcı olan komutlar.

Model Düzenleyicisi'nin durumunu etkileyen komutlar bulunur **Model Düzenleyicisi modu** ana Visual Studio penceresinde araç çubuğu. Modelleme araçlarını ve komut dosyalı komutlar bulunur **Model Düzenleyicisi** Model Düzenleyicisi tasarım yüzeyini araç.

İşte **Model Düzenleyicisi modu** araç çubuğu:

![Model Görüntüleyici kalıcı araç çubuğu.](../designers/media/digit-mre-modal-toolbar.png)

Bu tabloda öğeleri açıklar **Model Düzenleyicisi modu** araç çubuğu göründükleri soldan sağa doğru sırayla listelenir.

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seçin**|Etkin seçim moduna bağlı olarak görünümdeki noktaların, kenarların, yüzeylerin ya da nesnelerin seçimini etkinleştirir.|
|**Pan**|Pencere çerçevesine göre 3B Sahne hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> İçinde **seçin** modu basın ve basılı tutun **Ctrl** etkinleştirmek için **Pan** geçici olarak modu.|
|**Yakınlaştırma**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. İçinde **yakınlaştırma** modunda görünümde bir nokta seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sola veya yakınlaştırma en fazla giden.<br /><br /> İçinde **seçin** modu, sizin yakınlaştırabilir veya basılı durumdayken fare tekerleğini kullanarak **Ctrl**.|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Not:** Bu mod sahip olmayan etkisi yoktur **Ortografik** projeksiyon etkinleştirildiğinde.|
|**Dünya yerel**|Bu öğe etkin olduğunda, seçili nesne üzerindeki dönüştürmeler dünya uzayında oluşur. Aksi takdirde, seçilen nesne üzerinde dönüştürmeler yerel uzayda oluşur.|
|**Pivot modu**|Bu öğe etkinleştirildiğinde, dönüştürmeler konumunu ve yönlendirmesini etkiler *pivot noktası* seçili nesnenin (pivot noktası çeviri, ölçeklendirme ve döndürme işlemlerinin merkezini tanımlar.) Aksi takdirde dönüştürmeler, pivot noktasına göreli olarak, nesne geometrisinin konumunu ve yönlendirmesini etkiler.|
|**X eksenini Kilitle**|Nesne düzenlemesini x ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Y eksenini Kilitle**|Nesne düzenlemesini y ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**X eksenini Kilitle**|Nesne düzenlemesini z ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Çerçeve nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|
|**Görünümü**|Görünüm yönlendirmesini ayarlar. Kullanılabilir yönlendirmeler şunlardır:<br /><br /> **Ön**<br /> Görünümü sahnenin önüne yerleştirir.<br /><br /> **Geri**<br /> Görünümü sahnenin arkasına yerleştirir.<br /><br /> **Sol**<br /> Görünümü sahnenin soluna yerleştirir.<br /><br /> **sağ**<br /> Görünümü sahnenin sağına yerleştirir.<br /><br /> **Sayfanın Üstü**<br /> Görünümü sahnenin yukarısına yerleştirir.<br /><br /> **alt**<br /> Görünümü sahnenin aşağısına yerleştirir. **Not:** görünüm yönünü değiştirmenin tek yolu budur olduğunda **Ortografik** projeksiyon etkinleştirildiğinde.|
|**Projeksiyon**|Sahneyi çizmek için kullanılan projeksiyonun türünü ayarlar. Kullanılabilir projeksiyonlar şunlardır:<br /><br /> **Perspektif**<br /> Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.<br /><br /> **Ortografik**<br /> Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. Zaman **Ortografik** projeksiyon etkinleştirildiğinde kullanamaz **Yörünge** görünümü konumlandırmak için modu.|
|**Çizim Stili**|Sahnedeki nesnelerin işlenme yöntemini ayarlar. Kullanılabilir stiller şunlardır:<br /><br /> **Tel Çerçeve**<br /> Etkin olduğunda, nesneler tel çerçeve şeklinde işlenir.<br /><br /> **Overdraw**<br /> Etkin olduğunda, nesneler ek karıştırma kullanılarak işlenir. Görünümde, fazla çekme işleminin ne kadar yapıldığını görselleştirmek için bunu kullanabilirsiniz.<br /><br /> **Düz gölgelendirilmiş**<br /> Etkin olduğunda, nesneler temel ve düz gölgeli bir aydınlatma modeli kullanılarak işlenir. Bir nesnenin yüzeylerini daha kolay görmek için bunu kullanabilirsiniz.<br /><br /> Bu seçeneklerden hiçbiri etkin değilse, her nesne kendisine uygulanan malzeme kullanılarak işlenir.|
|**Gerçek zamanlı işleme modu**|Hiçbir kullanıcı eylemi gerçekleştirilmediğinde bile Visual Studio gerçek zamanlı işleme etkin olduğunda, tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Kılavuzu Aç/Kapat**|Bu öğe etkinleştirildiğinde bir kılavuz görüntülenir. Aksi takdirde kılavuz görüntülenmez.|
|**Araç Kutusu**|Alternatif olarak gösterir veya gizler **araç kutusu**.|
|**Belge Anahattı**|Alternatif olarak gösterir veya gizler **belge anahattı** penceresi.|
|**Özellikler**|Alternatif olarak gösterir veya gizler **özellikleri** penceresi.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Grafik motorları**<br /><br /> **D3d11 ile işle**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3d11warp ile işle**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır.<br /><br /> **Sahne Yönetimi**<br /><br /> **İçeri Aktar**<br /> Nesneleri başka bir 3B model dosyasındaki geçerli görünüme içeri aktarır.<br /><br /> **Üst öğeye Ekle**<br /> Çoklu seçilen nesnelerin ilkini, kalan seçili nesnelerin üst öğesi olarak ayarlar.<br /><br /> **Üst öğeden Ayır**<br /> Seçili nesneyi üst öğesinden ayırır. Seçilen nesne haline gelir bir *kök nesnesi* sahnedeki. Kök nesnenin bir üst nesnesi olmaz.<br /><br /> **Grup oluşturma**<br /> Seçili nesneleri eşdüzey nesneler olarak gruplandırır.<br /><br /> **Nesneleri Birleştir**<br /> Seçili nesneleri tek bir nesne halinde birleştirir.<br /><br /> **Çokgen seçiminden yeni nesne oluştur**<br /> Seçilen yüzeyleri geçerli nesneden kaldırır ve bu yüzeyleri içeren yeni bir nesneyi sahneye ekler.<br /><br /> **Araçlar**<br /><br /> **Ters poligon sargısı**<br /> Seçili çokgenleri çevirir ve böylece sargı sırasını ve yüzey normalini tersine çevirir.<br /><br /> **Tüm animasyonu Kaldır**<br /> Nesnelerden animasyon verilerini kaldırır.<br /><br /> **Üçgenlere bölmek**<br /> Seçili nesneyi üçgenlere dönüştürür.<br /><br /> **Görünümü**<br /><br /> Arkayüz Ayrılması<br /> Arka yüz ayırmayı etkinleştirir veya devre dışı bırakır.<br /><br /> **Kare hızı**<br /> Tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır.<br /><br /> Bu seçenek, etkinleştirdiğinizde kullanışlıdır **gerçek zamanlı işleme modu** seçeneği.<br /><br /> **Tümünü Göster**<br /> Sahnedeki tüm nesneleri gösterir. Bu sıfırlar **gizli** her bir nesnenin özellik **False**.<br /><br /> **Yüzey Normallerini Göster**<br /> Her bir yüzeyin normalini gösterir.<br /><br /> **Eksik malzemeleri Göster**<br /> Atanmış malzemeleri olmayan nesneler üzerinde özel bir doku gösterir.<br /><br /> **Pivot Göster**<br /> Etkinleştirir veya bir etkin seçimin pivot noktasında 3B Eksen işaretçisi görüntülenmesini devre dışı bırakır.<br /><br /> **Yer tutucu düğümlerini Göster**<br /> Yer tutucu düğümlerini gösterir. Nesneleri gruplandırdığınızda bir yer tutucu düğümü oluşturulur.<br /><br /> **Köşe için normal değerler Göster**<br /> Her köşenin normalini gösterir. **İpucu:** seçebileceğiniz **betikleri** düğmesine son betiğini yeniden çalıştırın.|

İşte **Model Düzenleyicisi** araç çubuğu:

![Model Görüntüleyici araç çubuğu](../designers/media/digit-mre-toolbar.png)

Sonraki tabloda öğeleri açıklar **Model Düzenleyicisi** araç çubuğu göründükleri üstten alta sırayla listelenir.

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Çevir**|Seçimi taşır.|
|**Ölçek**|Seçimin boyutunu değiştirir.|
|**Döndürme**|Seçimi döndürür.|
|**Nokta Seç**|Kümeleri **seçim modu** bir nesne üzerinde tek tek noktaları seçmek için.|
|**Kenar seç**|Kümeleri **seçim modu** bir nesne üzerinde kenar (iki köşe arasındaki çizgi) seçmek için.|
|**Yüz Seç**|Kümeleri **seçim modu** bir nesnede yüzey seçmek için.|
|**Nesne seçin**|Kümeleri **seçim modu** bir nesnenin tamamını seçmek için.|
|**Yükselt**|Ek bir yüzey oluşturur ve bunu seçili yüze bağlar.|
|**Alt bölümlere**|Seçilen her yüzeyi birden fazla yüzeye böler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir.|

### <a name="control-the-view"></a>Görünüm Denetimi

3B Sahne görünüme, bir konumu ve yönü olan sanal bir kamera düşünülebilir göre işlenir. Konumu veya yönü değiştirmek için görünüm denetimlerini kullanın **Model Düzenleyicisi modu** araç çubuğu.

Aşağıdaki tabloda birincil görünüm denetimleri açıklanmaktadır.

|Görünüm Denetimi|Açıklama|
|------------------|-----------------|
|**Pan**|Pencere çerçevesine göre 3B Sahne hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> İçinde **seçin** modu basın ve basılı tutun **Ctrl** etkinleştirmek için **Pan** geçici olarak modu.|
|**Yakınlaştırma**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. İçinde **yakınlaştırma** modunda görünümde bir nokta seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sola veya yakınlaştırma en fazla giden.<br /><br /> İçinde **seçin** modu, sizin yakınlaştırabilir veya basılı durumdayken fare tekerleğini kullanarak **Ctrl**.|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Not:** Bu mod sahip olmayan etkisi yoktur **Ortografik** projeksiyon etkinleştirildiğinde.|
|**Çerçeve nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|

Görünüm sanal kamera ile belirlenir, ancak aynı zamanda bir projeksiyon ile de tanımlanır. Projeksiyon, görünümdeki şekillerin ve nesnelerin tasarım yüzeyinde piksellere nasıl dönüştürüldüğünü tanımlar. Üzerinde **Model Düzenleyicisi** araç seçebilirsiniz **perspektif** veya **Ortografik** projeksiyon.

|Projeksiyon|Açıklama|
|----------------|-----------------|
|**Perspektif**|Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.|
|**Ortografik**|Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. Zaman **Ortografik** projeksiyon etkinleştirildiğinde kullanamaz **Yörünge** görünümü rastgele konumlandırmak için modu.|

3B Sahne bilinen konumu ve açısı, örneğin, iki benzer karşılaştırmak istediğinizde görüntülemek yararlı bulabilirsiniz. Bu senaryo için, Model Düzenleyicisi önceden tanımlı çeşitli görünümler sağlar. Önceden tanımlanmış bir görünüm kullanmak için **Model Düzenleyicisi modu** araç seçin **görünümü**, önceden tanımlanmış görünümü seçin — Ön, arka, sol, sağ, üst veya alt. Bu görünümlerde, sanal kamera doğrudan sahnenin başlangıç noktasına doğru bakar. Örneğin, seçtiğiniz **üstü görüntüle**, sanal kamera sahnenin başlangıç noktasına tam yukarıdan kaynağı bakar.

### <a name="view-additional-geometry-details"></a>Ek geometri ayrıntılarını görüntüle

Bir 3B nesneyi veya Sahneyi daha iyi anlamak için her köşe için normal değerler, her yüz için normal değerler, etkin seçimin pivot noktaları gibi ek geometri ayrıntılarını ve diğer ayrıntıları görüntüleyebilirsiniz. Etkinleştirmek veya bunları devre dışı bırakmak **Model Düzenleyicisi** araç seçin **betikleri** > **görünümü**, istediğinizi seçin.

### Oluşturma ve 3B nesne içeri aktarma <a name="Adding3DObjects"></a>

Sahneye önceden tanımlı bir 3B şekil eklemek için **araç kutusu**, seçmek istediğiniz ve ardından tasarım yüzeyine taşıyın. Yeni şekiller sahnenin başlangıcına yerleştirilir. Model Düzenleyicisi yedi şekil sağlar: **koni**, **küp**, **silindir**, **disk**, **düzlemi**,  **Küre**, ve **çaydanlık**.

Bir dosyadan 3B nesneyi almak için **Model Düzenleyicisi** araç seçin **Gelişmiş** > **Sahne Yönetimi** > **içeri aktarma**  > ve ardından içeri aktarmak istediğiniz dosyayı belirtin.

### <a name="transform-objects"></a>Dönüşüm nesneleri

Yapabilecekleriniz *dönüştürme* değiştirerek bir nesneyi kendi **döndürme**, **ölçek**, ve **çeviri** özellikleri. *Döndürme* x eksenini, y ekseni ve, pivot noktasıyla tanımlanan z ekseni etrafında art arda gelen dönüşümüne uygulayarak bir nesneyi yönlendirir. Her döndürme belirtiminin sırasıyla x, y ve z olmak üzere üç bileşeni vardır ve bu bileşenler derece olarak belirtilir. **Ölçeklendirme** nesneyi pivot noktasında ortalanmış bir veya daha fazla eksen boyunca belirtilen bir faktör olarak yayarak yeniden boyutlandırır. *Çeviri* nesneyi pivot noktası yerine üst öğesiyle ilişkili 3 boyutlu alanında bulur.

Modelleme araçlarını kullanarak veya özellikleri ayarlayarak bir nesneyi dönüştürebilirsiniz.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Modelleme araçlarını kullanarak bir nesne dönüştürme

1. İçinde **seçin** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. Üzerinde **Model Düzenleyicisi** araç seçin **çevir**, **ölçek**, veya **Döndür** aracı. Seçili nesne için bir çeviri, ölçeklendirme veya döndürme işleyicisi görüntülenir.

3. Dönüştürmeyi gerçekleştirmek için işleyiciyi kullanın. Çeviri ve ölçeklendirme dönüşümlerinde işleyici bir eksen göstergesidir. Bir kerede bir eksen değiştirebilir veya göstergenin ortasındaki beyaz küpü kullanarak aynı anda tüm eksenleri değiştirebilirsiniz. Döndürme için işleyici x eksenine (kırmızı), y eksenine (yeşil) ve z eksenine (mavi) karşılık gelen renk kodlu dairelerden oluşan bir küredir. İstediğiniz döndürmeyi oluşturmak için her ekseni tek tek değiştirmeniz gerekir.

#### <a name="transform-an-object-by-setting-its-properties"></a>Nesne özelliklerini ayarlayarak dönüştürme

1. İçinde **seçin** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. İçinde **özellikleri** penceresinde değerlerini belirtin **döndürme**, **ölçek**, ve **çeviri** özellikleri.

    > [!IMPORTANT]
    > İçin **döndürme** özelliği, her üç eksen birinin etrafındaki dönüş derecesini belirtin. Döndürmeler sırayla uygulandığından önce x ekseni, sonra y ekseni ve sonra da z ekseni açısından bir döndürme planladığınızdan emin olun.

Modelleme araçlarını kullanarak, dönüştürmeleri hızlı ancak kesin olmayan bir şekilde oluşturabilirsiniz. Nesne özelliklerini ayarlayarak, dönüştürmeleri kesin ancak hızlı olmayan bir şekilde belirtebilirsiniz. İstediğiniz dönüştürmelere "yeteri kadar" yaklaşmak için modelleme araçlarını kullanmanızı ve ardından özellik değerlerinde ince ayar yapmanızı öneririz.

İşleyicileri kullanmayı istemiyorsanız, serbest biçim modunu etkinleştirebilirsiniz. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Araçları** > **serbest biçim düzenleme** için Serbest Biçim modunu etkinleştirmek (veya devre dışı bırakın). Serbest biçim modunda, işleyici üzerindeki bir nokta yerine herhangi bir tasarım yüzeyi noktasında düzenleme yapmaya başlayabilirsiniz. Serbest biçim modunda, değiştirmek istemediklerinizi kilitleyerek bazı eksenlerde yapılacak değişiklikleri kısıtlayabilirsiniz. Üzerinde **Model Düzenleyicisi modu** araç, herhangi bir bileşimini seçin **Kilitle X**, **Kilitle Y**, ve **Kilitle Z** düğmeleri.

Kılavuza uydur işlevini kullanarak nesnelerle çalışmayı daha kullanışlı bulabilirsiniz. Üzerinde **Model Düzenleyicisi modu** araç seçin **Yasla** kılavuza etkinleştirmek (veya devre dışı bırakmak). Kılavuza uydur etkinleştirildiğinde, çeviri, döndürme ve ölçeklendirme dönüştürmeleri önceden tanımlı aralıklarla sınırlandırılır.

### <a name="work-with-the-pivot-point"></a>Pivot noktası ile çalışma

Pivot noktası nesnenin döndürme ve ölçeklendirme merkezini tanımlar. Döndürme ve ölçeklendirme dönüşümlerinden nasıl etkilendiğini değiştirmek için bir nesnenin özet noktasını değiştirebilirsiniz. Üzerinde **Model Düzenleyicisi modu** araç seçin **Pivot modu** pivot modunu etkinleştirmek (veya devre dışı). Pivot modu etkin olduğunda, seçili nesnenin pivot noktasında küçük bir eksen göstergesi görünür. Ardından **çeviri** ve **döndürme** pivot noktasını düzenlemek için Araçlar.

Pivot noktasının nasıl kullanıldığını gösteren bir örnek için bkz. [nasıl yapılır: 3B modelin pivot noktasını değiştirme](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Dünya ve yerel modları

Çeviri ve döndürme oluşabilir ya da yerel koordinat sisteminde (veya *yerel çerçeve başvuru*) nesnesinin ya da dünyanın koordinat sisteminde (veya *dünya çerçeve başvuru*). Dünya başvuru çerçevesi nesnenin dönüşünden bağımsızdır. Yerel mod varsayılandır. Etkinleştirmek (veya devre dışı bırakmak) için dünya modunu **Model Düzenleyicisi modu** araç seçin **dünya yerel** düğmesi.

### Nesneleri değiştirme <a name="ModifyingObjects"></a>

Taşıma veya kendi köşelerini, kenarlarını ve yüzeylerini silerek bir 3B nesnenin şeklini değiştirebilirsiniz. Varsayılan olarak, Model Düzenleyicisi bulunduğu *nesne modu*, böylece seçebilir ve tüm nesneleri dönüştürme. Noktaları, kenarları veya yüzeyleri seçmek için uygun seçim modunu seçin. Üzerinde **Model Düzenleyicisi modu** araç seçin **seçim modları**ve ardından istediğiniz modu seçin.

Çıkarmayla veya alt bölümlere ayırmayla ek köşeler oluşturabilirsiniz. Çıkarma bir yüzün köşelerini (aynı düzlemli bir yüzler kümesi) çoğaltır ve yüz çoğaltılmış köşelerle bağlı kalır. Alt bölümlere ayırma, önceden bir tane olan yüzeyden birçok yüzey oluşturmak için köşeler ekler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir. Her iki durumda da, nesnenin geometrisini değiştirmek için yeni köşeleri çevirebilir, döndürebilir ve ölçeklendirebilirsiniz.

#### <a name="to-extrude-a-face-from-an-object"></a>Bir nesneden bir yüzü çıkarmak için

1. Yüz seçimi modunda, çıkarmak istediğiniz yüzü seçin.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Araçları** > **Yükselt**.

#### <a name="to-subdivide-faces"></a>Yüzleri alt bölümlere ayırmak için

1. Yüz seçimi modunda, alt bölümlere ayırmak istediğiniz yüzleri seçin. Alt bölüm yeni kenar verileri oluşturduğundan, tüm yüzeyleri aynı anda alt bölümlere ayırmak yüzler bitişik olduğunda daha tutarlı sonuçlar verir.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Araçları** > **Ayır**.

Ayrıca yüzeyleri üçgenlere bölebilir, nesneleri birleştirebilir ve çokgen seçimlerini yeni nesnelere dönüştürebilirsiniz. Üçgenlere bölme, üçgen olmayan bir yüz, en uygun sayıda üçgene dönüştürülecek şekilde ek kenarlar oluşturur; ancak ek geometrik ayrıntı sağlamaz. Birleştirme işlemi, seçili nesneleri tek bir nesne halinde birleştirir. Yeni nesneler bir çokgen seçiminden oluşturulabilir.

#### <a name="triangulate-a-face"></a>Bir yüzü üçgenlere bölmek

1. Yüz seçimi modunda, üçgenlere bölmek istediğiniz yüzü seçin.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Araçları** > **üçgenlere**.

#### <a name="merge-objects"></a>Nesneleri Birleştir

1. Nesne seçimi modunda, birleştirmek istediğiniz nesneleri seçin.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Araçları** > **nesneleri Birleştir**.

#### <a name="create-an-object-from-a-polygon-selection"></a>Çokgen seçiminden bir nesne oluşturma

1. Yüz seçimi modunda yeni bir nesne oluşturmak istediğiniz yüzleri seçin.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Araçları** > **Çokgenseçimindenyeninesneoluştur**.

### <a name="work-with-materials-and-shaders"></a>Malzemeler ve gölgelendiriciler ile çalışma

Bir nesnenin görünümü, sahnedeki aydınlatma etkileşimi ve nesnenin malzemesi ile belirlenir. Malzemeler, yüzeyin farklı ışık türlerine nasıl tepki verdiğini açıklayan özelliklerle ve nesne yüzeyindeki her pikselin son rengini ışıklandırma bilgisine, doku eşlemelerine, normal eşlemelere ve diğer verilere göre hesaplayan bir gölgelendirici programla tanımlanır.

Model Düzenleyicisi şu varsayılan malzemeleri sağlar:

|Malzeme|Açıklama|
|--------------|-----------------|
|**Işıklandırılmamış**|Benzetimli aydınlatma olmadan bir yüzeyi işler.|
|**Lambert**|Benzetimli ortam aydınlatması ve yayınık aydınlatma ile bir yüzey işler.|
|**Phong**|Benzetimli ortam aydınlatması, yayınık aydınlatma ve yansımalı vurgular ile bir yüzeyi işler.|

Bu malzemelerin her biri nesnenin yüzeyine tek bir doku uygular. Malzemeyi kullanan her nesne için farklı bir doku ayarlayabilirsiniz.

Belirli bir nesnenin sahnedeki farklı ışık kaynaklarına verdiği tepkiyi değiştirmek için, malzemeyi kullanan diğer nesnelerden bağımsız olarak malzemenin aydınlatma özelliklerini değiştirebilirsiniz. Bu tabloda genel aydınlatma özellikleri açıklanmaktadır:

|Aydınlatma Özelliği|Açıklama|
| - |-----------------|
|**Ortam**|Yüzeyin ortam aydınlatmasından nasıl etkilendiğini açıklar.|
|**Yayınık**|Yüzeyin yönlü ve nokta ışıklardan nasıl etkilendiğini açıklar.|
|**Yayımlatıcı**|Yüzeyin, diğer aydınlatmalardan bağımsız olarak ışığı nasıl yaydığını açıklar.|
|**Yansımalı**|Yüzeyin yönlü ve nokta ışıkları nasıl yansıttığını açıklar.|
|**Yansımalı güç**|Yansımalı vurguların genişliğini ve yoğunluğunu açıklar.|

Bir malzemenin neyi desteklediğine bağlı olarak aydınlatma özelliklerini, dokuları ve diğer verileri değiştirebilirsiniz. İçinde **seçin** modu, malzeme değiştirmek istediğiniz nesneyi seçin ve ardından **özellikleri** penceresinde değişiklik **MaterialAmbient**,  **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**, veya diğer kullanılabilir özelliği. Malzeme özellikleri adlandırılmış sekiz dokular getirebilir **doku1** için **doku8**.

Bir nesneden tüm malzemeleri kaldırmak için **Model Düzenleyicisi** araç seçin **betikleri** > **malzemeleri** > **Kaldır Malzemeleri**.

Kullanabileceğiniz **gölgelendirici Tasarımcısı** , 3B Sahne nesnelere uygulayabileceğiniz özel gölgelendirici malzemeleri oluşturmak için. Özel gölgelendirici malzemelerin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [gölgelendirici Tasarımcısı](../designers/shader-designer.md). Özel bir gölgelendirici malzemeyi bir nesneye uygulama hakkında daha fazla bilgi için bkz: [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Sahne yönetimi

Sahneleri nesnelerin bir hiyerarşisi olarak yönetebilirsiniz. Birden fazla nesne hiyerarşik bir şekilde düzenlendiğinde, üst öğe düğümünün herhangi bir çeviri, ölçek veya döndürme işlemi alt öğelerini de etkiler. Bu, temel nesnelerden karmaşık nesneler veya sahneler oluşturmak istediğinizde kullanışlıdır.

Kullanabileceğiniz **belge anahattı** görünüm hiyerarşisini görüntülemek ve görünüm düğümlerini seçmek için pencere. Anahat içinde bir düğüm seçtiğinizde, kullanabileceğiniz **özellikleri** penceresinin özelliklerini değiştirin.

Gerek birini diğerlerinin üst öğesi yaparak, gerekse üst öğe gibi davranan bir yer tutucu düğümünün altında eşdüzeyler olarak birlikte gruplandırarak nesnelerin bir hiyerarşisini oluşturabilirsiniz.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Bir üst nesnenin sahip bir hiyerarşi oluşturun

1. İçinde **seçin** modu, iki veya daha fazla nesneleri seçebilir. İlk seçtiğiniz öğe üst nesne olur.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Sahne Yönetimi** > **eklemek için üst**.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Hiyerarşi eşdüzeyin nesneleri oluşturma

1. İçinde **seçin** modu, iki veya daha fazla nesneleri seçebilir. Bir yer tutucu nesne oluşturulur ve onların üst nesnesi haline gelir.

2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri** > **Sahne Yönetimi** > **Grup Oluştur**.

Model Düzenleyicisi, ilk seçilen nesneyi (üst öğe haline gelen) tanımlamak için beyaz tel çerçeve kullanır. Seçimdeki diğer nesneler mavi bir tel çerçeveye sahiptir. Varsayılan olarak, yer tutucu düğümleri görüntülenmez. Yer tutucu düğümlerini görüntülemek için **Model Düzenleyicisi** araç seçin **betikleri** > **Sahne Yönetimi** > **Göster Yer tutucu düğümlerini**. Yer tutucu düğümleriyle, yer tutucu olmayan nesnelerle çalıştığınız gibi çalışabilirsiniz.

İki nesne arasındaki üst-alt öğe ilişkilendirmesini kaldırmak için alt nesneyi seçin ve ardından **Model Düzenleyicisi** araç seçin **betikleri** > **SahneYönetimi**  >  **Üst öğeden Ayır**. Üst nesne ile alt nesneyi ayırdığınızda, alt nesne sahnede bir kök nesne olur.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|Geçiş **seçin** modu|**CTRL**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Geçiş **yakınlaştırma** modu|**CTRL**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Geçiş **Pan** modu|**CTRL**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Tümünü seç|**CTRL**+**A**|
|Geçerli seçimi sil|**Delete**|
|Geçerli seçimi iptal et|**Kaçış** (**Esc**)|
|Yakınlaştır|**Fare tekerleği ileriye doğru**<br /><br /> **CTRL**+**fare tekerleği ileriye doğru**<br /><br /> **Shift**+**fare tekerleği ileriye doğru**<br /><br /> **CTRL**+**PageUp**<br /><br /> Artı işareti (**+**)|
|Uzaklaştır|**Fare tekerleği geriye doğru**<br /><br /> **CTRL**+**fare tekerleği geriye doğru**<br /><br /> **Shift**+**fare tekerleği geriye doğru**<br /><br /> **CTRL**+**PageDown**<br /><br /> Eksi işareti (**-**)|
|Kamerayı yukarı kaydır|**PageDown**|
|Kamerayı aşağı kaydır|**PageUp**|
|Kamerayı sola kaydır|**Fare tekerleği sol**<br /><br /> **CTRL**+**PageDown**|
|Kamerayı sağa kaydır|**Fare tekerleği sağ**<br /><br /> **CTRL**+**PageDown**|
|Modelin üst kısmını görüntüle|**CTRL**+**L**, **Ctrl**+**T**<br /><br /> **T**|
|Modelin alt kısmını görüntüle|**CTRL**+**L**, **Ctrl**+**U**|
|Modelin sol tarafını görüntüle|**CTRL**+**L**, **Ctrl**+**m**|
|Modelin sağ tarafını görüntüle|**CTRL**+**L**, **Ctrl**+**R**|
|Modelin önünü görüntüle|**CTRL**+**L**, **Ctrl**+**F**|
|Modelin arkasını görüntüle|**CTRL**+**L**, **Ctrl**+**B**|
|Nesneyi pencere içinde çerçevele|**F**|
|Tel çerçeve modunu aç/kapat|**CTRL**+**L**, **Ctrl**+**W**|
|Kılavuza uydurmayı aç/kapat|**CTRL**+**G**, **Ctrl**+**N**|
|Pivot modunu aç/kapat|**CTRL**+**G**, **Ctrl**+**V**|
|X ekseni kısıtlamasını aç/kapat|**CTRL**+**L**, **Ctrl**+**X**|
|Y ekseni kısıtlamasını aç/kapat|**CTRL**+**L**, **Ctrl**+**Y**|
|Z ekseni kısıtlamasını aç/kapat|**CTRL**+**L**, **Ctrl**+**Z**|
|Çeviri moduna geçiş yap|**CTRL**+**G**, **Ctrl**+**W**<br /><br /> **W**|
|Ölçek moduna geçiş yap|**CTRL**+**G**, **Ctrl**+**E**<br /><br /> **E**|
|Döndürme moduna geçiş yap|**CTRL**+**G**, **Ctrl**+**R**<br /><br /> **R**|
|Nokta seçme moduna geçiş yap|**CTRL**+**L**, **Ctrl**+**1**|
|Kenar seçme moduna geçiş yap|**CTRL**+**L**, **Ctrl**+**2**|
|Yüz seçme moduna geçiş yap|**CTRL**+**L**, **Ctrl**+**3**|
|Nesne seçme moduna geçiş yap|**CTRL**+**L**, **Ctrl**+**4**|
|Yörünge (kamera) moduna geçiş yap|**CTRL**+**G**, **Ctrl**+**O**|
|Sahnede sonraki nesneyi seç|**sekmesi**|
|Sahnede önceki nesneyi seç|**Shift**+**sekmesi**|
|Geçerli araca bağlı olarak seçili nesneyi düzenle.|**Ok** anahtarları|
|Geçerli işleyiciyi devre dışı bırak|**Q**|
|Kamerayı döndür|**Alt**+**Sürükle** farenin sol düğmesi|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve resimler, 3B modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz Visual Studio Araçları'nın genel bir bakış sağlar.|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokularla ve görüntülerle çalışma için Visual Studio Resim Düzenleyici kullanmayı açıklar.|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Gölgelendiricilerle çalışmak için Visual Studio gölgelendirici Tasarımcısı kullanmayı açıklar.|