---
title: Model Düzenleyicisi | Microsoft Docs
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
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e947793dff1f0068c1341ba6b70c21df07463f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844099"
---
# <a name="model-editor"></a>Model Düzenleyicisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede ile nasıl çalışılacağı açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görüntüleme, oluşturma ve 3B modeller değiştirmek için Model Düzenleyicisi.  
  
 Sıfırdan 3B modeller oluşturmak veya tam özellikli 3B modelleme araçları kullanılarak oluşturulmuş daha karmaşık 3B modelleri görüntülemek veya değiştirmek için Model Düzenleyicisi'ni kullanabilirsiniz. Model Düzenleyicisi, DirectX uygulaması geliştirmede kullanılan çeşitli 3B model biçimlerini destekler.  
  
## <a name="supported-formats"></a>Desteklenen biçimler  
 Model Düzenleyicisi şu model biçimlerini destekler:  
  
|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görüntüleme, Düzenleme, Oluşturma)|  
|-----------------|--------------------|-------------------------------------------------|  
|AutoDesk FBX Değişim Dosyası|.fbx|Görüntüleme, Düzenleme, Oluşturma|  
|Collada DAE Dosyası|.dae|Görüntüleme, Düzenleme (Collada DAE dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|  
|OBJ|.obj|Görüntüleme, Düzenleme (OBJ dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|  
  
## <a name="getting-started"></a>Başlarken  
 Bu bölümde, 3B modeline eklemeyi açıklar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje ve kullanmaya başlamak ihtiyacınız olan temel bilgileri sağlar.  
  
#### <a name="to-add-a-3-d-model-to-your-project"></a>Projenize 3B model eklemek için  
  
1.  İçinde **Çözüm Gezgini**, görüntüye eklemek ve ardından istediğiniz projenin kısayol menüsünü **Ekle**, **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunun **yüklü**seçin **grafik**ve ardından **3B Sahne (.fbx)**.  
  
3.  Belirtin **adı** model dosyasının ve **konumu** sonra istediğiniz yere oluşturulacak.  
  
4.  Seçin **Ekle** düğmesi.  
  
### <a name="axis-orientation"></a>Eksen yönlendirme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 3B ekseninin her yönlendirmesini destekler ve onu destekleyen model dosyası biçimlerinden eksen yönlendirmesi bilgilerini yükler. Hiçbir eksen yönlendirmesi belirtilmezse, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] varsayılan olarak sağ taraf yönelimli koordinat sistemini kullanır. **Eksen göstergesi** tasarım yüzeyinin sağ alt köşesinde geçerli eksen yönlendirmesini gösterir. Üzerinde **eksen göstergesi**, kırmızı x eksenini temsil eder, yeşil, y eksenini temsil eder ve mavi z ekseni temsil eder.  
  
### <a name="beginning-your-3-d-model"></a>3B modelinize başlama  
 Model Düzenleyicisi'nde her yeni nesne her zaman temel 3B şekillerden biri olarak başlar — veya *Temelleri*; Model Düzenleyicisi içinde oluşturulur. Yeni ve benzersiz nesneler oluşturmak için, görünüme bir temel öğe ekler ve sonra da köşeleriyle oynayarak şeklini değiştirirsiniz. Karmaşık şekiller için, kalıp veya alt bölüm kullanarak ek köşeler ekler ve sonra bunlarda değişiklik yaparsınız. Görünümünüze temel öğe nesnesi ekleme hakkında daha fazla bilgi için bkz: [oluşturma ve 3B nesneleri içeri aktarma](#Adding3DObjects). Bir nesne için daha fazla köşe ekleme hakkında daha fazla bilgi için bkz: [nesneleri değiştirme](#ModifyingObjects).  
  
## <a name="working-with-the-model-editor"></a>Model Düzenleyicisi ile çalışma  
 Aşağıdaki bölümlerde, 3B modellerle çalışmak için Model Düzenleyicisi'nin nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="model-editor-toolbars"></a>Model Düzenleyicisi araç çubukları  
 Model Düzenleyicisi araç çubukları, 3B modellerle çalışmanıza yardımcı olan komutlar içerir.  
  
 Model Düzenleyicisi'nin durumunu etkileyen komutlar bulunur **Model Düzenleyicisi modu** araç ana [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] penceresi. Modelleme araçlarını ve komut dosyalı komutlar bulunur **Model Düzenleyicisi** Model Düzenleyicisi tasarım yüzeyini araç.  
  
 İşte **Model Düzenleyicisi modu** araç çubuğu:  
  
 ![Model Görüntüleyici kalıcı araç çubuğu. ](../designers/media/digit-mre-modal-toolbar.png "MRE kalıcı araç basamak")  
  
 Bu tabloda öğeleri açıklar **Model Düzenleyicisi modu** araç çubuğu göründükleri soldan sağa doğru sırayla listelenir.  
  
|Araç Çubuğu Öğesi|Açıklama|  
|------------------|-----------------|  
|**Seçin**|Etkin seçim moduna bağlı olarak görünümdeki noktaların, kenarların, yüzeylerin ya da nesnelerin seçimini etkinleştirir.|  
|**Pan**|Pencere çerçevesine göre 3B görünümün hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> İçinde **seçin** modu basın ve basılı tutun etkinleştirmek için Ctrl **Pan** geçici olarak modu.|  
|**Yakınlaştırma**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. İçinde **yakınlaştırma** modunda görünümde bir nokta seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sola veya yakınlaştırma en fazla giden.<br /><br /> İçinde **seçin** modu, sizin yakınlaştırabilir veya Ctrl basılı durumdayken fare tekerleğini kullanarak.|  
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
|**Gerçek zamanlı işleme modu**|Gerçek zamanlı işleme etkin olduğunda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hiçbir kullanıcı eylemi gerçekleştirilmediğinde bile tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|  
|**Kılavuzu Aç/Kapat**|Bu öğe etkinleştirildiğinde bir kılavuz görüntülenir. Aksi takdirde kılavuz görüntülenmez.|  
|**Araç Kutusu**|Alternatif olarak gösterir veya gizler **araç kutusu**.|  
|**Belge Anahattı**|Alternatif olarak gösterir veya gizler **belge anahattı** penceresi.|  
|**Özellikler**|Alternatif olarak gösterir veya gizler **özellikleri** penceresi.|  
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Grafik motorları**<br /><br /> **D3d11 ile işle**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3d11warp ile işle**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır.<br /><br /> **Sahne Yönetimi**<br /><br /> **İçeri Aktar**<br /> Başka bir 3B model dosyasındaki nesneleri geçerli görünüme içeri aktarır.<br /><br /> **Üst öğeye Ekle**<br /> Çoklu seçilen nesnelerin ilkini, kalan seçili nesnelerin üst öğesi olarak ayarlar.<br /><br /> **Üst öğeden Ayır**<br /> Seçili nesneyi üst öğesinden ayırır. Seçilen nesne haline gelir bir *kök nesnesi* sahnedeki. Kök nesnenin bir üst nesnesi olmaz.<br /><br /> **Grup oluşturma**<br /> Seçili nesneleri eşdüzey nesneler olarak gruplandırır.<br /><br /> **Nesneleri Birleştir**<br /> Seçili nesneleri tek bir nesne halinde birleştirir.<br /><br /> **Çokgen seçiminden yeni nesne oluştur**<br /> Seçilen yüzeyleri geçerli nesneden kaldırır ve bu yüzeyleri içeren yeni bir nesneyi sahneye ekler.<br /><br /> **Araçlar**<br /><br /> **Ters poligon sargısı**<br /> Seçili çokgenleri çevirir ve böylece sargı sırasını ve yüzey normalini tersine çevirir.<br /><br /> **Tüm animasyonu Kaldır**<br /> Nesnelerden animasyon verilerini kaldırır.<br /><br /> **Üçgenlere bölmek**<br /> Seçili nesneyi üçgenlere dönüştürür.<br /><br /> **Görünümü**<br /><br /> Arkayüz Ayrılması<br /> Arka yüz ayırmayı etkinleştirir veya devre dışı bırakır.<br /><br /> **Kare hızı**<br /> Tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır.<br /><br /> Bu seçenek, etkinleştirdiğinizde kullanışlıdır **gerçek zamanlı işleme modu** seçeneği.<br /><br /> **Tümünü Göster**<br /> Sahnedeki tüm nesneleri gösterir. Bu sıfırlar **gizli** her bir nesnenin özellik **False**.<br /><br /> **Yüzey Normallerini Göster**<br /> Her bir yüzeyin normalini gösterir.<br /><br /> **Eksik malzemeleri Göster**<br /> Atanmış malzemeleri olmayan nesneler üzerinde özel bir doku gösterir.<br /><br /> **Pivot Göster**<br /> Etkin seçimin pivot noktasında 3B eksen işaretçisi görüntülenmesini etkinleştirir veya devre dışı bırakır.<br /><br /> **Yer tutucu düğümlerini Göster**<br /> Yer tutucu düğümlerini gösterir. Nesneleri gruplandırdığınızda bir yer tutucu düğümü oluşturulur.<br /><br /> **Köşe için normal değerler Göster**<br /> Her köşenin normalini gösterir. **İpucu:** seçebileceğiniz **betikleri** düğmesine son betiğini yeniden çalıştırın.|  
  
 İşte **Model Düzenleyicisi** araç çubuğu:  
  
 ![Model Görüntüleyici araç çubuğundaki](../designers/media/digit-mre-toolbar.png "basamak MRE araç")  
  
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
  
### <a name="controlling-the-view"></a>Görünümü denetleme  
 3B sahne görünüme göre işlenir; bu bir konumu ve yönü olan sanal bir kamera olarak düşünülebilir. Konumu veya yönü değiştirmek için görünüm denetimlerini kullanın **Model Düzenleyicisi modu** araç çubuğu.  
  
 Aşağıdaki tabloda birincil görünüm denetimleri açıklanmaktadır.  
  
|Görünüm Denetimi|Açıklama|  
|------------------|-----------------|  
|**Pan**|Pencere çerçevesine göre 3B görünümün hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> İçinde **seçin** modu basın ve basılı tutun etkinleştirmek için Ctrl **Pan** geçici olarak modu.|  
|**Yakınlaştırma**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. İçinde **yakınlaştırma** modunda görünümde bir nokta seçin ve ardından Sağa Taşı veya yakınlaştırmak için aşağı veya sola veya yakınlaştırma en fazla giden.<br /><br /> İçinde **seçin** modu, sizin yakınlaştırabilir veya Ctrl basılı durumdayken fare tekerleğini kullanarak.|  
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Not:** Bu mod sahip olmayan etkisi yoktur **Ortografik** projeksiyon etkinleştirildiğinde.|  
|**Çerçeve nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|  
  
 Görünüm sanal kamera ile belirlenir, ancak aynı zamanda bir projeksiyon ile de tanımlanır. Projeksiyon, görünümdeki şekillerin ve nesnelerin tasarım yüzeyinde piksellere nasıl dönüştürüldüğünü tanımlar. Üzerinde **Model Düzenleyicisi** araç seçebilirsiniz **perspektif** veya **Ortografik** projeksiyon.  
  
|Projeksiyon|Açıklama|  
|----------------|-----------------|  
|**Perspektif**|Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.|  
|**Ortografik**|Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. Zaman **Ortografik** projeksiyon etkinleştirildiğinde kullanamaz **Yörünge** görünümü rastgele konumlandırmak için modu.|  
  
 3 boyutlu bir görünümü bilinen bir konum ve açıdan görüntülemeyi (örneğin, iki benzer görünümü karşılaştırmak istediğinizde) kullanışlı bulabilirsiniz. Bu senaryo için, Model Düzenleyicisi önceden tanımlı çeşitli görünümler sağlar. Önceden tanımlanmış bir görünüm kullanmak için **Model Düzenleyicisi modu** araç seçin **görünümü**, önceden tanımlanmış görünümü seçin — Ön, arka, sol, sağ, üst veya alt. Bu görünümlerde, sanal kamera doğrudan sahnenin başlangıç noktasına doğru bakar. Örneğin, seçtiğiniz **üstü görüntüle**, sanal kamera sahnenin başlangıç noktasına tam yukarıdan kaynağı bakar.  
  
### <a name="viewing-additional-geometry-details"></a>Ek geometri ayrıntılarını görüntüleme  
 Bir 3B nesneyi veya sahneyi daha iyi anlamak için, her köşe için normal değerler, her yüz için normal değerler, etkin seçimin pivot noktaları ve diğer ayrıntılar gibi ek geometri ayrıntılarını görüntüleyebilirsiniz. Etkinleştirmek veya bunları devre dışı bırakmak **Model Düzenleyicisi** araç seçin **betikleri**, **görünümü**, istediğinizi seçin.  
  
###  <a name="Adding3DObjects"></a> Oluşturma ve 3B nesneleri içeri aktarma  
 Sahneye önceden tanımlı bir 3B şekil eklemek için **araç kutusu**, seçmek istediğiniz ve ardından tasarım yüzeyine taşıyın. Yeni şekiller sahnenin başlangıcına yerleştirilir. Model Düzenleyicisi yedi şekil sağlar: **koni**, **küp**, **silindir**, **disk**, **düzlemi**,  **Küre**, ve **çaydanlık**.  
  
 Bir dosyadan 3B nesnenin içeri aktarmak için **Model Düzenleyicisi** araç seçin **Gelişmiş**, **Sahne Yönetimi**, **alma**ve ardından belirtin içeri aktarmak istediğiniz dosya.  
  
### <a name="transforming-objects"></a>Nesneleri dönüştürme  
 Yapabilecekleriniz *dönüştürme* değiştirerek bir nesneyi kendi **döndürme**, **ölçek**, ve **çeviri** özellikleri. *Döndürme* x eksenini, y ekseni ve, pivot noktasıyla tanımlanan z ekseni etrafında art arda gelen dönüşümüne uygulayarak bir nesneyi yönlendirir. Her döndürme belirtiminin sırasıyla x, y ve z olmak üzere üç bileşeni vardır ve bu bileşenler derece olarak belirtilir. **Ölçeklendirme** nesneyi pivot noktasında ortalanmış bir veya daha fazla eksen boyunca belirtilen bir faktör olarak yayarak yeniden boyutlandırır. *Çeviri* nesneyi pivot noktası yerine üst öğesiyle ilişkili 3 boyutlu alanında bulur.  
  
 Modelleme araçlarını kullanarak veya özellikleri ayarlayarak bir nesneyi dönüştürebilirsiniz.  
  
##### <a name="to-transform-an-object-by-using-modeling-tools"></a>Modelleme araçlarını kullanarak bir nesneyi dönüştürmek için  
  
1.  İçinde **seçin** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.  
  
2.  Üzerinde **Model Düzenleyicisi** araç seçin **çevir**, **ölçek**, veya **Döndür** aracı. Seçili nesne için bir çeviri, ölçeklendirme veya döndürme işleyicisi görüntülenir.  
  
3.  Dönüştürmeyi gerçekleştirmek için işleyiciyi kullanın. Çeviri ve ölçeklendirme dönüşümlerinde işleyici bir eksen göstergesidir. Bir kerede bir eksen değiştirebilir veya göstergenin ortasındaki beyaz küpü kullanarak aynı anda tüm eksenleri değiştirebilirsiniz. Döndürme için işleyici x eksenine (kırmızı), y eksenine (yeşil) ve z eksenine (mavi) karşılık gelen renk kodlu dairelerden oluşan bir küredir. İstediğiniz döndürmeyi oluşturmak için her ekseni tek tek değiştirmeniz gerekir.  
  
##### <a name="to-transform-an-object-by-setting-its-properties"></a>Özelliklerini ayarlayarak bir nesneyi dönüştürmek için  
  
1. İçinde **seçin** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.  
  
2. İçinde **özellikleri** penceresinde değerlerini belirtin **döndürme**, **ölçek**, ve **çeviri** özellikleri.  
  
   > [!IMPORTANT]
   >  İçin **döndürme** özelliği, her üç eksen birinin etrafındaki dönüş derecesini belirtin. Döndürmeler sırayla uygulandığından önce x ekseni, sonra y ekseni ve sonra da z ekseni açısından bir döndürme planladığınızdan emin olun.  
  
   Modelleme araçlarını kullanarak, dönüştürmeleri hızlı ancak kesin olmayan bir şekilde oluşturabilirsiniz. Nesne özelliklerini ayarlayarak, dönüştürmeleri kesin ancak hızlı olmayan bir şekilde belirtebilirsiniz. İstediğiniz dönüştürmelere "yeteri kadar" yaklaşmak için modelleme araçlarını kullanmanızı ve ardından özellik değerlerinde ince ayar yapmanızı öneririz.  
  
   İşleyicileri kullanmayı istemiyorsanız, serbest biçim modunu etkinleştirebilirsiniz. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Araçları**, **serbest biçim düzenleme** serbest biçim modunu etkinleştirmek (veya devre dışı bırakmak). Serbest biçim modunda, işleyici üzerindeki bir nokta yerine herhangi bir tasarım yüzeyi noktasında düzenleme yapmaya başlayabilirsiniz. Serbest biçim modunda, değiştirmek istemediklerinizi kilitleyerek bazı eksenlerde yapılacak değişiklikleri kısıtlayabilirsiniz. Üzerinde **Model Düzenleyicisi modu** araç, herhangi bir bileşimini seçin **Kilitle X**, **Kilitle Y**, ve **Kilitle Z** düğmeleri.  
  
   Kılavuza uydur işlevini kullanarak nesnelerle çalışmayı daha kullanışlı bulabilirsiniz. Üzerinde **Model Düzenleyicisi modu** araç seçin **Yasla** kılavuza etkinleştirmek (veya devre dışı bırakmak). Kılavuza uydur etkinleştirildiğinde, çeviri, döndürme ve ölçeklendirme dönüştürmeleri önceden tanımlı aralıklarla sınırlandırılır.  
  
### <a name="working-with-the-pivot-point"></a>Pivot noktası ile çalışma  
 Pivot noktası nesnenin döndürme ve ölçeklendirme merkezini tanımlar. Döndürme ve ölçeklendirme dönüşümlerinden nasıl etkilendiğini değiştirmek için bir nesnenin özet noktasını değiştirebilirsiniz. Üzerinde **Model Düzenleyicisi modu** araç seçin **Pivot modu** pivot modunu etkinleştirmek (veya devre dışı). Pivot modu etkin olduğunda, seçili nesnenin pivot noktasında küçük bir eksen göstergesi görünür. Ardından **çeviri** ve **döndürme** pivot noktasını düzenlemek için Araçlar.  
  
 Pivot noktasının nasıl kullanıldığını gösteren bir örnek için bkz. [nasıl yapılır: 3B modelin Pivot noktasını değiştirme](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).  
  
### <a name="world-and-local-modes"></a>Dünya ve yerel modları  
 Çeviri ve döndürme oluşabilir ya da yerel koordinat sisteminde (veya *yerel çerçeve başvuru*) nesnesinin ya da dünyanın koordinat sisteminde (veya *dünya çerçeve başvuru*). Dünya başvuru çerçevesi nesnenin dönüşünden bağımsızdır. Yerel mod varsayılandır. Etkinleştirmek (veya devre dışı bırakmak) için dünya modunu **Model Düzenleyicisi modu** araç seçin **dünya yerel** düğmesi.  
  
###  <a name="ModifyingObjects"></a> Nesneleri değiştirme  
 Köşelerini, kenarlarını ve yüzeylerini taşıyarak veya silerek bir 3B nesnenin şeklini değiştirebilirsiniz. Varsayılan olarak, Model Düzenleyicisi bulunduğu *nesne modu*, böylece seçebilir ve tüm nesneleri dönüştürme. Noktaları, kenarları veya yüzeyleri seçmek için uygun seçim modunu seçin. Üzerinde **Model Düzenleyicisi modu** araç seçin **seçim modları**ve ardından istediğiniz modu seçin.  
  
 Çıkarmayla veya alt bölümlere ayırmayla ek köşeler oluşturabilirsiniz. Çıkarma bir yüzün köşelerini (aynı düzlemli bir yüzler kümesi) çoğaltır ve yüz çoğaltılmış köşelerle bağlı kalır. Alt bölümlere ayırma, önceden bir tane olan yüzeyden birçok yüzey oluşturmak için köşeler ekler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir. Her iki durumda da, nesnenin geometrisini değiştirmek için yeni köşeleri çevirebilir, döndürebilir ve ölçeklendirebilirsiniz.  
  
##### <a name="to-extrude-a-face-from-an-object"></a>Bir nesneden bir yüzü çıkarmak için  
  
1.  Yüz seçimi modunda, çıkarmak istediğiniz yüzü seçin.  
  
2.  Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Araçları**, **Yükselt**.  
  
##### <a name="to-subdivide-faces"></a>Yüzleri alt bölümlere ayırmak için  
  
1. Yüz seçimi modunda, alt bölümlere ayırmak istediğiniz yüzleri seçin. Alt bölüm yeni kenar verileri oluşturduğundan, tüm yüzeyleri aynı anda alt bölümlere ayırmak yüzler bitişik olduğunda daha tutarlı sonuçlar verir.  
  
2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Araçları**, **Ayır**.  
  
   Ayrıca yüzeyleri üçgenlere bölebilir, nesneleri birleştirebilir ve çokgen seçimlerini yeni nesnelere dönüştürebilirsiniz. Üçgenlere bölme, üçgen olmayan bir yüz, en uygun sayıda üçgene dönüştürülecek şekilde ek kenarlar oluşturur; ancak ek geometrik ayrıntı sağlamaz. Birleştirme işlemi, seçili nesneleri tek bir nesne halinde birleştirir. Yeni nesneler bir çokgen seçiminden oluşturulabilir.  
  
##### <a name="to-triangulate-a-face"></a>Bir yüzü üçgenlere bölmek için  
  
1.  Yüz seçimi modunda, üçgenlere bölmek istediğiniz yüzü seçin.  
  
2.  Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Araçları**, **üçgenlere**.  
  
##### <a name="to-merge-objects"></a>Nesneleri birleştirmek için  
  
1.  Nesne seçimi modunda, birleştirmek istediğiniz nesneleri seçin.  
  
2.  Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Araçları**, **nesneleri Birleştir**.  
  
##### <a name="to-create-an-object-from-a-polygon-selection"></a>Çokgen seçiminden bir nesne oluşturmak için  
  
1.  Yüz seçimi modunda yeni bir nesne oluşturmak istediğiniz yüzleri seçin.  
  
2.  Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Araçları**, **Çokgen seçiminden yeni nesne oluştur**.  
  
### <a name="working-with-materials-and-shaders"></a>Malzemeler ve gölgelendiriciler ile çalışma  
 Bir nesnenin görünümü, sahnedeki aydınlatma etkileşimi ve nesnenin malzemesi ile belirlenir. Malzemeler, yüzeyin farklı ışık türlerine nasıl tepki verdiğini açıklayan özelliklerle ve nesne yüzeyindeki her pikselin son rengini ışıklandırma bilgisine, doku eşlemelerine, normal eşlemelere ve diğer verilere göre hesaplayan bir gölgelendirici programla tanımlanır.  
  
 Model Düzenleyicisi şu varsayılan malzemeleri sağlar:  
  
|Malzeme|Açıklama|  
|--------------|-----------------|  
|Işıklandırılmamış|Benzetimli aydınlatma olmadan bir yüzeyi işler.|  
|Lambert|Benzetimli ortam aydınlatması ve yayınık aydınlatma ile bir yüzey işler.|  
|Phong|Benzetimli ortam aydınlatması, yayınık aydınlatma ve yansımalı vurgular ile bir yüzeyi işler.|  
  
 Bu malzemelerin her biri nesnenin yüzeyine tek bir doku uygular. Malzemeyi kullanan her nesne için farklı bir doku ayarlayabilirsiniz.  
  
 Belirli bir nesnenin sahnedeki farklı ışık kaynaklarına verdiği tepkiyi değiştirmek için, malzemeyi kullanan diğer nesnelerden bağımsız olarak malzemenin aydınlatma özelliklerini değiştirebilirsiniz. Bu tabloda genel aydınlatma özellikleri açıklanmaktadır:  
  
|Aydınlatma Özelliği|Açıklama|  
|-----------------------|-----------------|  
|Ortam|Yüzeyin ortam aydınlatmasından nasıl etkilendiğini açıklar.|  
|Yayınık|Yüzeyin yönlü ve nokta ışıklardan nasıl etkilendiğini açıklar.|  
|Yayımlatıcı|Yüzeyin, diğer aydınlatmalardan bağımsız olarak ışığı nasıl yaydığını açıklar.|  
|Yansımalı|Yüzeyin yönlü ve nokta ışıkları nasıl yansıttığını açıklar.|  
|Yansımalı Güç|Yansımalı vurguların genişliğini ve yoğunluğunu açıklar.|  
  
 Bir malzemenin neyi desteklediğine bağlı olarak aydınlatma özelliklerini, dokuları ve diğer verileri değiştirebilirsiniz. İçinde **seçin** modu, malzeme değiştirmek istediğiniz nesneyi seçin ve ardından **özellikleri** penceresinde değişiklik **MaterialAmbient**,  **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**, veya diğer kullanılabilir özelliği. Malzeme özellikleri adlandırılmış sekiz dokular getirebilir **doku1** için **doku8**.  
  
 Bir nesneden tüm malzemeleri kaldırmak için **Model Düzenleyicisi** araç seçin **betikleri**, **malzemeleri**, **malzemeleri Kaldır**.  
  
 Kullanabileceğiniz **gölgelendirici Tasarımcısı** 3B görünümlerinizdeki nesnelere uygulayabileceğiniz özel gölgelendirici malzemeleri oluşturmak için. Özel gölgelendirici malzemelerin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [gölgelendirici Tasarımcısı](../designers/shader-designer.md). Özel bir gölgelendirici malzemeyi bir nesneye uygulama hakkında daha fazla bilgi için bkz: [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
### <a name="scene-management"></a>Sahne yönetimi  
 Sahneleri nesnelerin bir hiyerarşisi olarak yönetebilirsiniz. Birden fazla nesne hiyerarşik bir şekilde düzenlendiğinde, üst öğe düğümünün herhangi bir çeviri, ölçek veya döndürme işlemi alt öğelerini de etkiler. Bu, temel nesnelerden karmaşık nesneler veya sahneler oluşturmak istediğinizde kullanışlıdır.  
  
 Kullanabileceğiniz **belge anahattı** görünüm hiyerarşisini görüntülemek ve görünüm düğümlerini seçmek için pencere. Anahat içinde bir düğüm seçtiğinizde, kullanabileceğiniz **özellikleri** penceresinin özelliklerini değiştirin.  
  
 Gerek birini diğerlerinin üst öğesi yaparak, gerekse üst öğe gibi davranan bir yer tutucu düğümünün altında eşdüzeyler olarak birlikte gruplandırarak nesnelerin bir hiyerarşisini oluşturabilirsiniz.  
  
##### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Üst nesnesi olan bir hiyerarşi oluşturmak için  
  
1.  İçinde **seçin** modu, iki veya daha fazla nesneleri seçebilir. İlk seçtiğiniz öğe üst nesne olur.  
  
2.  Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Sahne Yönetimi**, **eklemek için üst**.  
  
##### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Eşdüzeyli nesnelerin hiyerarşisini oluşturmak için  
  
1. İçinde **seçin** modu, iki veya daha fazla nesneleri seçebilir. Bir yer tutucu nesne oluşturulur ve onların üst nesnesi haline gelir.  
  
2. Üzerinde **Model Düzenleyicisi** araç seçin **betikleri**, **Sahne Yönetimi**, **Grup Oluştur**.  
  
   Model Düzenleyicisi, ilk seçilen nesneyi (üst öğe haline gelen) tanımlamak için beyaz tel çerçeve kullanır. Seçimdeki diğer nesneler mavi bir tel çerçeveye sahiptir. Varsayılan olarak, yer tutucu düğümleri görüntülenmez. Yer tutucu düğümlerini görüntülemek için **Model Düzenleyicisi** araç seçin **betikleri**, **Sahne Yönetimi**, **yer tutucu düğümlerini Göster**. Yer tutucu düğümleriyle, yer tutucu olmayan nesnelerle çalıştığınız gibi çalışabilirsiniz.  
  
   İki nesne arasındaki üst-alt öğe ilişkilendirmesini kaldırmak için alt nesneyi seçin ve ardından **Model Düzenleyicisi** araç seçin **betikleri**, **Sahne Yönetimi**, **Üst öğeden Ayır**. Üst nesne ile alt nesneyi ayırdığınızda, alt nesne sahnede bir kök nesne olur.  
  
## <a name="keyboard-shortcuts"></a>Klavye kısayolları  
  
|Komut|Klavye kısayolları|  
|-------------|------------------------|  
|Geçiş **seçin** modu|Ctrl+G, Gtrl+Q<br /><br /> S|  
|Geçiş **yakınlaştırma** modu|Ctrl+G, Ctrl+Z<br /><br /> Z|  
|Geçiş **Pan** modu|Ctrl+G, Ctrl+P<br /><br /> K|  
|Tümünü seç|Ctrl+A|  
|Geçerli seçimi sil|Sil|  
|Geçerli seçimi iptal et|Esc|  
|Yakınlaştır|Fare tekerleği ileriye doğru<br /><br /> Ctrl+Fare tekerleği ileriye doğru<br /><br /> Shift+Fare tekerleği ileriye doğru<br /><br /> Ctrl+PageUp<br /><br /> Artı İşareti (+)|  
|Uzaklaştır|Fare tekerleği geriye doğru<br /><br /> Ctrl+Fare tekerleği geriye doğru<br /><br /> Shift+Fare tekerleği geriye doğru<br /><br /> Ctrl+PageDown<br /><br /> Eksi İşareti (-)|  
|Kamerayı yukarı kaydır|PageDown|  
|Kamerayı aşağı kaydır|PageUp|  
|Kamerayı sola kaydır|Fare tekerleği sol<br /><br /> Ctrl+PageDown|  
|Kamerayı sağa kaydır|Fare tekerleği sağ<br /><br /> Ctrl+PageDown|  
|Modelin üst kısmını görüntüle|Ctrl+L, Ctrl+T<br /><br /> T|  
|Modelin alt kısmını görüntüle|Ctrl+L, Ctrl+U|  
|Modelin sol tarafını görüntüle|Ctrl+L, Ctrl+L|  
|Modelin sağ tarafını görüntüle|Ctrl+L, Ctrl+R|  
|Modelin önünü görüntüle|Ctrl+L, Ctrl+F|  
|Modelin arkasını görüntüle|Ctrl+L, Ctrl+B|  
|Nesneyi pencere içinde çerçevele|F|  
|Tel çerçeve modunu aç/kapat|Ctrl+L, Ctrl+W|  
|Kılavuza uydurmayı aç/kapat|Ctrl+G, Ctrl+N|  
|Pivot modunu aç/kapat|Ctrl+G, Ctrl+V|  
|X ekseni kısıtlamasını aç/kapat|Ctrl+L, Ctrl+X|  
|Y ekseni kısıtlamasını aç/kapat|Ctrl+L, Ctrl+Y|  
|Z ekseni kısıtlamasını aç/kapat|Ctrl+L, Ctrl+Z|  
|Çeviri moduna geçiş yap|Ctrl+G, Ctrl+W<br /><br /> W|  
|Ölçek moduna geçiş yap|Ctrl+G, Ctrl+E<br /><br /> E|  
|Döndürme moduna geçiş yap|Ctrl+G, Ctrl+R<br /><br /> R|  
|Nokta seçme moduna geçiş yap|Ctrl+L, Ctrl+1|  
|Kenar seçme moduna geçiş yap|Ctrl+L, Ctrl+2|  
|Yüz seçme moduna geçiş yap|Ctrl+L, Ctrl+3|  
|Nesne seçme moduna geçiş yap|Ctrl+L, Ctrl+4|  
|Yörünge (kamera) moduna geçiş yap|Ctrl+G, Ctrl+O|  
|Sahnede sonraki nesneyi seç|Tab|  
|Sahnede önceki nesneyi seç|Shift+Sekme Tuşu|  
|Geçerli araca bağlı olarak seçili nesneyi düzenle.|Ok tuşları|  
|Geçerli işleyiciyi devre dışı bırak|Q|  
|Kamerayı döndür|Alt + Farenin sol düğmesiyle sürükleme|  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Genel bir bakış sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokular ve resimler, 3B modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz araçları.|  
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokularla ve görüntülerle çalışma için görüntü Düzenleyicisi.|  
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gölgelendiricilerle çalışmak için gölgelendirici Tasarımcısı.|



