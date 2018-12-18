---
title: Menüler ve Komutlar
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f892c96a40f9edfc01ea0c6a8de15e59b20fb067
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061277"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menüler ve komutlar için Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="command-usage"></a>Komut kullanımı

### <a name="overview"></a>Genel Bakış
 Birçok ayrı ürünü oluşturan paketidir, Microsoft Office farklı olarak, Visual Studio her genel Visual Studio IDE, komut kümelerini katkıda pek çok ürünlerin içerir. IDE, bağlama göre kullanıcının işlevselliğini filtreleyerek komutları binlerce karmaşıklığını yönetir.

 Bir kullanıcının bağlamını değiştirir – bir tasarım penceresinde kod düzenleme penceresini değiştirme gibi – işlevselliği için ilgisi olmayan yeni bir bağlam kaybolur. Aynı anda, özellikleri ve araç seçenekleri gibi ilgili dinamik bilgileriyle birlikte yeni işlevsellik yüzeyleri. Kullanıcı kullanılabilen komut kümesi takas fark etmişsinizdir değil. Kullanıcı dikkatinizin veya görünmesini veya kaybolmasını komutları kafanız ise, kullanıcı Arabirimi tasarımı ayarlaması gerekir. Kullanıcının geçerli bağlam her zaman bir veya daha fazla yollarla gibi IDE başlık çubuğu, Özellikler penceresinde veya özellik sayfaları iletişim kutusu gösterilir.

 Komut çubukları kullanıcı arabiriminde esneklik sağlar. Yalnızca komut ortam: ana menü ve hem de özelleştirilebilir ve hatta gizli ana komut çubuğu, Visual Studio devralınan yapıları. Diğer komut çubukları görünür ve uygulama durumuna göre kaybolur. Araç pencereleri ve belge Düzenleyicisi penceresi kenarlarına içinde gömülü araç çubukları de içerebilir.

#### <a name="basic-guidelines"></a>Temel yönergeler

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Mevcut paylaşılan komutların, komut grupları ve menüler mümkün olduğunca kullanın.
 Komutları genellikle içeriğine göre gösterilen olduğundan, mevcut paylaşılan menü ve komut gruplarını kullanımı, komut yapısını bağlamında değişiklikler arasında göreceli olarak tutarlı kalmasını sağlar. Paylaşılan komutları yeniden kullanma ve yeni komutlar ilgili paylaşılan komutları yakın yerleştirme ayrıca IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur. Yeni bir komut tanımlanmış olması gerekiyorsa, mevcut bir paylaşılan komut grubunda yerleştirmeyi deneyin. Yeni bir grup tanımlanmış olması gerekiyorsa, ilgili komut grubu yakın var olan bir paylaşılan menüsünden Yeni bir üst düzey menü oluşturmadan önce yerleştirin.

##### <a name="do-not-create-icons-for-every-command"></a>Her komut için simgeler oluşturmayın.
 Komut simgesinin oluşturmadan önce dikkatlice düşünün. Simgeler yalnızca komutları için oluşturulması:

-   Varsayılan araç çubuğunda görünür.

-   kullanıcılar tarafından bir araç çubuğu eklenmesi olasılığı **Özelleştir...** iletişim kutusu.

-   başka bir Microsoft ürünü aynı eylemi ile ilişkili bir simgesi vardır.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Klavye kısayolları eklenmesini sınırla
 Kullanıcılar büyük çoğunluğu, tüm kullanılabilir kısayolları küçük bir bölümünü kullanın. Şüpheye düştüğünüzde özelliğinizi bir klavye kısayolu bağlamayın. Kullanıcı iş kısayollar eklemeden önce takım karşılaşırsınız.

##### <a name="give-commands-a-default-menu-placement"></a>Komutları varsayılan menü yerleşimi sağlar.
 Komutlarınızın başkaları tarafından özelleştirilmiş ve buna göre tasarlayın unutmayın. Gizli komut de yoktur. Görünen tüm Visual Studio komutları **araçları > Özelleştir** iletişim kutusunda komut penceresinde otomatik tamamlama **Araçlar > Seçenekler > klavye** iletişim ve geliştirme araçları ortam (DTE). Kullanıcıların bunları kolayca bulabilmesi için bir ad ve araç ipucu .ctc dosyanızdaki komutlarınızı koyduğunuzdan emin olun.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Paylaşılan bir gömülü araç komutları yinelenen değil.
 Komutları yakınında kullanıcının odak alanına yerleştirmek kullanışlıdır. Bunu yapmanın bir yolu, Düzenleyicisi araç penceresi ya da belgenin üst kısmında bir gömülü araç oluşturmaktır. Araç çubuğunda yer komutları belirli içerik bölgeye penceresi içinde olmalıdır. Bu araç çubuklarında paylaşılan komutları yinelenen değil. Örneğin, hiçbir zaman içinde bir gömülü araç bir "Kaydet" simgesi yerleştirin.

### <a name="content-and-command-visibility"></a>İçerik ve komut görünürlük
 Komutları mevcut aşağıdaki kapsamlar: **ortam**, **hiyerarşi**, ve **belge**. Güvenle komut yerleşimden sahip olmak için her kapsam bildirin.

 İçindeki komutlar **ortam** kapsam birincil bağlam'kurmak ve birden çok bağlamları arasında paylaşılır. Bunlar, belge ve araç pencereleri düzenleme ve görünürlük değiştirir. Ortamdaki komutları yanı sıra kapsamı olan **yeni proje**, **sunucuya Bağlan**, **iliştirme işlemi**, **Kes**,  **Kopyalama**, **Yapıştır**, **Bul**, **seçenekleri**, **özelleştirme**, **yeni pencere**, ve **Yardım görüntülemek**.

 İçindeki komutlar **hiyerarşi** kapsamını Visual Studio da dahil olmak üzere, hiyerarşileri Yönet **proje**, **takım**, ve **veri**. Bir projenin üzere için – örneğin teklifiyle **hata ayıklama**, **derleme**, **Test**, **mimarisi**, veya **Çözümle** . Kapsama hiyerarşisi komutlar arasındadır **Yeni Öğe Ekle**, **yeni sorgu**, **proje ayarları**, **yeni veri kaynağı Ekle**, **Başlatma performansı Sihirbazı**, ve **yeni diyagram**.

 İçindeki komutlar **belge** kodu, tasarım veya bir iş öğesi sorgusu (WIQ) gibi bir belge içeriklerini kapsam eylemidir. Bunlar ayrıca bir araç penceresinin görünümünde işlem veya aksi takdirde, araç penceresine özgü. Belge kapsamı komutları da hareket kendileri gibi hiyerarşi özgü dosya nesnelerde **projeden Kaldır**. Belgedeki komutları yanı sıra kapsamı olan **yeniden düzenleyin > Yeniden Adlandır**, **iş öğesi kopyası oluştur**, **Tümünü Genişlet**, **Tümünü Daralt**, ve **Kullanıcı Görevi Oluştur**.

### <a name="command-placement-decisions"></a>Komut yerleştirme kararları
 Bir komut oluşturmaya karar verdiyseniz, uygun yerleşimi ve klavye kısayolu oluşturulup oluşturulmayacağını belirleyen gerekecektir. Komut yerleştirileceği yeri kurmak için bu kararı yolu izleyin:

 ![Komut yerleştirme karar grafiği](../../extensibility/ux-guidelines/media/0501-a-commandplacement.png "a_CommandPlacement 0501")

 **Visual Studio komut yerleştirme için karar yolu**

### <a name="command-placement-in-menus"></a>Menülerde komut yerleştirme

#### <a name="main-menu-bar"></a>Ana menü çubuğu
 Ana menü çubuğu kullanıcı Arabirimi için katkıda bulunan herhangi bir özel bağlam menüsü paket komutları için standart konumun olması gerekir. İsteğe bağlı olarak ortam hangi komutların görülebilir denetimine kullanması yönüyle diğer komut yapıları ana menü çubuğu ayrılır. Tüm diğer komut çubukları yalnızca bağlam dışında olan komutları devre dışı bir menü veya araç çubuğunda yer alır.

 Ortamı, tüm IDE ve birden çok görev etki alanları arasında ortak olan ana menü çubuğuna yerleşik komut kümesini tanımlar. Bu komutların her zaman bakılmaksızın VSPackages ortamına yüklendi görülebilir. VSPackages bu komut kümesini genişletebilirsiniz olsa da, her ürün ve bunların komutları yerleşimini Ayarla komutu her takım sorumluluğundadır.

 Visual Studio ana menü yapısı aşağıdaki menü kategoriye ayrılabilir:

##### <a name="core-menus"></a>Ana menü

-   Dosya

-   Düzenle

-   Görüntüle

-   Araçlar

-   Pencere

-   Yardım

##### <a name="project-specific-menus"></a>Projeye özgü menüleri

-   Proje

-   Derleme

-   Hata ayıklama

##### <a name="context-specific-menus"></a>Özel bağlam menüleri

-   Takım

-   Veri

-   Test

-   Mimari

-   Çözümle

##### <a name="document-specific-menus"></a>Belgeye özgü menüleri

-   Biçimi

-   Tablo

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Ana menü tasarlarken, bu kurallar için uyar:

-   Belirli bir bağlamda 25 en üst düzey öğe aşamaz.

-   Menüleri, hiçbir zaman 600 piksel cinsinden yükseklik aşmalıdır.

-   Ultimate SKU ve genel profil gibi birden fazla bağlamı, ana menüde değerlendirin.

-   Açılır menüleri kabul edilir.

-   Açılır menüleri, en az üç öğe ve en fazla yedi içermelidir.

-   Açılır menüleri tek düzey derinlikte gitmesi gereken – basamaklı alt menüler bazı Visual Studio menü öğeleri var ancak bu deseni değil teşvik edilir.

-   Altıdan fazla ayırıcı kullanın. Aşağıdaki çizime gruplandırmaları uymalıdır:

     ![Ana menü gruplandırma için yönergeler](../../extensibility/ux-guidelines/media/0501-b-mainmenus.png "b_MainMenus 0501")

-   Şekilde, her grup için gerekli olmasa da, ek ekleme sınırlıdır.

-   Her gruplandırma, iki yedi menü öğelerine sahip olmalıdır.

#### <a name="main-menu-ordering"></a>Ana menü sıralama
 Yeni bir üst düzey öğe eklemeden önce var olan bir üst düzey menü komutu yerleştirmeyi göz önünde bulundurun. Yeni bir üst düzey menü eklerken, doğru konuma yerleştirmek emin olun. Menü proje bağlamı veya belgeye özgü olup olmadığına karar verin. Üst düzey menü adını kısa tutun ve yalnızca bir Word'ü kullanın.

 Çekirdek menüleri bağlayıcının komutları geri kalanını gerekir. Dosya, düzenleme ve görüntüleme her zaman sola ve araçları, penceresinde olmalıdır ve Yardım her zaman sağa doğru olması gerekir.

#### <a name="context-menus"></a>Bağlam menüleri
 Bağlam menüleri içinde çok fazla işlevselliği yerleştirme öğrenin zor bir arabirimde sonuçlanır. Tüm ana işlevleri ana menü çubuğu aracılığıyla kullanılabilir olması gerekir. Komut yerleştirme yinelenen komutları önlemek için mevcut komutları ile aynı olmalıdır. Bağlam menüleri için kabuk bağlam menüsünden çözüm, bir proje düğümü veya bir proje öğesi olduğuna bağlı olarak dahil edilmesi gereken standart menü grupları tanımlar.

 Bağlam menüleri tasarlarken, ana menüden için ve ayrıca aynı kurallara uyar:

-   25 üst düzey menü öğeleri geçmeyin.

-   Açılır menüleri kabul edilebilir ancak gerekir derin bir düzey aşmayacak – hiçbir zaman basamaklı çıkarmalar kullanın.

-   Altıdan fazla ayırıcı kullanın.

### <a name="command-placement-in-toolbars"></a>Araç çubuğundaki komutu yerleştirme

#### <a name="general-toolbars"></a>Genel araç çubukları
 Ne zaman tasarlama ve araç çubuklarını, düzenleme, bu standartlar uygulayın:

-   Düğme başına birden fazla fiili kullanmayın. Bir düğmeyi bir eylem =.

-   Yalnızca bu etiketi ile güçlendirilmiş gerekiyorsa, metin simgesi ile birlikte kullanın.

-   Birleşik giriş kutusu yalnızca tek bir oturumda birden çok kez da geçirilecek özellikler için kullanın. Aksi takdirde, başka bir yerde özelliğini kullanıma sunar.

-   Bir açılan kutunun genişliği kutusu + % 30 içinde uzun öğenin genişliğini eşit olmalıdır. Örneğin, en uzun öğe 200 piksel ise, birleşik giriş kutusu 260 piksel genişliğinde olmalıdır.

-   Ayırıcılar kullanımını sınırlayın. Yanındaki açılan bir menüde bir ayırıcı kullanımına açılan şeklin görsel ayırıcı olarak davranan önleyici bir desen olmasıdır.

-   Üç altı simge için simge grubu içermelidir.

-   Birden çok yararlı komutlar niteleyicileri yol açarsa son ayarı depolayan bir Bölünmüş düğme kullanın:

     ![Visual Studio'da düğmeleri bölme](../../extensibility/ux-guidelines/media/0501-c-splitbuttons.png "c_SplitButtons 0501")

     **Bölünmüş düğme örneği. Sol taraftaki altı komutları bunun yerine tek bir düğme sığacak.**

#### <a name="product-specific-toolbars"></a>Ürüne özel araç çubukları
 Her ürünün ürün yüklendikten sonra Visual Studio ilk başlatıldığında sık kullanılan içeren bir varsayılan araç ve önemli komutlar her ürünün varsayılan araç çubuğu görüntülenmelidir sağlayabilir.

 Ürünleri de paylaşılan komut gruplarını ve menüler IDE tarafından sağlanan hizmetlerden yararlanır. Her paylaşılan komut grubuyla ilgili komutları kullanıcı için anlamlı bir şekilde düzenlemek için gereken paylaşılan bir menü yerleştirilir. Karmaşıklığını azaltmak için bu paylaşılan komut yapısını yararlanmak önemlidir.

#### <a name="global-toolbars"></a>Genel araç çubukları
 Genel araç çubukları, yepyeni bir satır sağdaki sığdırmak için gereklidir. Yeni bir genel araç çubuğu oluştururken, bu araç çubuğu türü için yönergeleri izleyin.

 **Genel araç yönergeleri:**

- Her araç 24 piksel ortak denetimleri (kavrayıcı, taşma) sahiptir.

- Her araç çubuğu düğmesi 22 doldurma dahil olmak üzere geniş pikseldir. Bölünmüş düğme simgesi yapma, başka bir 11 piksel genişliği ekler.

- Çoğaltma komut araç çubukları arasında izin verilir.

  **Belge özel araç çubukları** belirli bir dosya türü etkin olduğunda görünür ve farklı bir dosya türü etkin olduğunda kaybolur.

- Belge özel araç çubukları 12'den fazla düğmeleri olmayabilir.

- Araç toplam genişliği 300 piksel aşamaz.

- Her dosya türü, bir gömülü araç veya belge özgü bir genel araç ancak ikisini birden sahip olabilir.

  **Bağlama özel araç çubukları** belirli bir içerik görünmez kümesidir ve uzun süre etkin kalır eğilimindedir.

- Tüm bağlama özel araç çubukları için düğme 18 sınırdır.

- Ardından bağlam etkin olduğunda kullanıcıların çoğu bu araç çubuğunun komutları tutarlı bir şekilde görevlendirmek olmaz, bu araç bir bağlamı ile ilişkilendirme.

- Araç içerik çıkarken kaybolur emin olun. Bu araç çubukları hiçbiri, başlangıçta görüntülenmesi gerekir.

  **Hiçbir bağlam çubuklarıyla** hiçbir zaman otomatik olarak görünür. Bu, yalnızca, kullanıcı bunları etkinleştirir gösterir. Maksimum genişliğini 200 piksel altında tutun.

### <a name="general-organization-and-shell-defined-groups"></a>Genel kuruluş ve Kabuk tanımlı grupları
 Mevcut paylaşılan komutları ve komut gruplarını menüleri kullanın. Yeni bir komut tanımlanmış olması gerekiyorsa, mevcut bir paylaşılan komut grubunda yerleştirmeyi deneyin. Yeni bir grup tanımlanmış olması gerekiyorsa, ilgili komut grubu yakın var olan bir paylaşılan menüsündeki yeni bir üst düzey menü oluşturmadan önce yerleştirmeyi deneyin. Bu, IDE'de tutarlı komut yerleştirme sağlarken komut karmaşıklığı azaltır.

 Paylaşılan **biçimi** Menü Tasarımcısı stili belge pencereleri bağlamında genellikle gösterilen, aşağıdaki görüntüde gösterilmiştir:

 ![Visual Studio biçim menüsüne çağrılar ile](../../extensibility/ux-guidelines/media/0501-d-formatmenu.png "d_FormatMenu 0501")

 **Visual Studio'da menü grupları**

### <a name="reducing-and-reusing-commands"></a>Azaltma ve komutlar yeniden kullanma
 Komutları genellikle bağlam üzerinde herhangi bir zamanda kullanıcının gördüğü komut sayısını azaltmak için temel gösterilmektedir. Ancak, mevcut paylaşılan menülerini de yeniden kullanmamalısınız ve bağlamda değişiklikleri arasındaki komut yapısını göreceli olarak kalmasını sağlamak için komut gruplarını kararlı.

 Paylaşılan komutları yeniden kullanmak ve ilgili paylaşılan komutları yakın yeni komutlar yerleştirme IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur.

## <a name="naming-commands"></a>Adlandırma komutları

### <a name="naming-conventions"></a>Adlandırma kuralları
 Kullanıcıların bulun ve komutlar, komut satırını kullanarak veya bir klavye kısayolu bağlama yürütme komut tutarlı adlandırma kritik öneme sahiptir. Komut adlarını, araç çubuğundaki veya geçişli veya bağlam menüsünde görüntülendiğinde komut işlevi görür. hangi amacını kullanıcı da yardımcı olur.

#### <a name="when-naming-commands"></a>Ne zaman adlandırma komutları:

-   Böylece kolayca yerelleştirilebilir metin oluşturmak. Metin yerelleştirme hakkında daha fazla bilgi için bkz. [Visual Studio için dünyanın hazırlık](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).

-   Kısa olmalıdır. Komutlar, en fazla üç sözcük kullanmanız gerekir.

-   İlk harfler büyük harf kullanın: her sözcüğün ilk harfini büyük harfe. Visual Studio'da biçimlendirme metin hakkında daha fazla bilgi için bkz: [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

-   Komut nereye yerleştirileceğini dikkate alın. Bu, üst düzey bir menü veya bir açılır öğesi mi? Örneğin, "Hizala" ve çıkma komutları gruplandırma hizalama komutları açılır öğesi, üst düzey komutu ne zaman olmalıdır "Sol" "Hak", "Orta" "Yasla" olması ve benzeri. Açılan menüyü komutları "Sola Hizala" veya "Sağa Hizala." adı olarak yedekli

     ![Visual Studio biçim menüsüne](../../extensibility/ux-guidelines/media/0502-a-formatmenu.png "a_FormatMenu 0502")

### <a name="using-icons-with-commands"></a>Simgeler komutları ile kullanma
 Komutları ile eşleştirme simgesi kullanımında sparing olabilir. Kullanıcının yeteneğini komut tanımlamak için benzersiz bir görüntü komutu ile ilişkilendirme hastens olsa da visual karmaşasından ve verimsizlik görüntü aşırı kullanıma karşı oluşur. Aşağıdaki kurallar, bir komut simge oluşturulmaya karar verirken yardımcı olur.

#### <a name="use-an-icon-with-a-command-only-if"></a>Bir simge ile yalnızca bir komut durumlarda kullanın:

-   Aynı komutu, Microsoft Office uygulamalarından birini gibi başka bir belirgin Microsoft ürününün kendisiyle ilişkili bir simgesi vardır.

-   Komut, varsayılan araç çubuğunda yer alır.

-   Kullanıcılar için bir araç kullanarak eklemek büyük olasılıkla bir özel komut komuttur **"Özelleştir..."** iletişim kutusu.

## <a name="access-and-shortcut-keys"></a>Erişim ve kısayol tuşları

### <a name="overview"></a>Genel Bakış
 Klavye atamalarının iki tür vardır:

-   **Erişim anahtarları** (Hızlandırıcıları olarak da bilinir) kullanıcı Arabirimi iletişim kutusunda komut vermeye genel ve her etiket için menüleri aracılığıyla klavye erişime izin verin. Erişim anahtarları çoğunlukla erişilebilmesi için olan tüm menüleri ve çoğu iletişim kutusu denetimlerine atanan değildir belleğe alınan bölümü, yalnızca geçerli pencere etkiler ve yerelleştirilmiş olduğunu.

-   **Kısayol tuşları** çoğunlukla denetimi (Ctrl) ve anahtar dizileri işlevi (Fn) kullanın. Daha ileri düzey kullanıcılara ve Yardım için üretkenlik tasarlanan. Bunlar yalnızca en sık kullanılan komutlar için atanan ve ana menüye atlayarak sırasında hızlı erişim izni. Kısayol tuşları belleğe alınan bölümü amaçlanmıştır ve için neden Profil şeması ile tutarlı atanması gerekir. Kısayol tuş düzenleri profili profili farklılık gösterebilir. Bir kullanıcı üzerinden kısayol tuşları özelleştirebilir **Araçlar > Seçenekler > klavye**.

### <a name="assigning-access-keys"></a>Erişim tuşları atama
 Erişim anahtarları Alt artı alfasayısal anahtarları oluşur. Özel durum olmadan her bir menü öğesi için bir erişim anahtarı atayın. Windows ve erişim tuşları atama için genel kurallar izleyin. Örneğin, erişim anahtarı **Dosya > Yeni** her zaman olmalıdır **Alt, F, N**.

 Değil 'i' (büyük veya küçük harf) ya da küçük 'l' gibi tek piksel genişliği harf kullanın ve bunları ayırt etmek zor olduğu gibi karakterler çıkıntılarını (g, j, p, soru ve y) kullanmaktan kaçının.

 Mümkün olduğunda yinelenen anahtarlar kullanmaktan kaçının. Çoğaltma kaçınılmaz olduğu durumlarda, menü sistemi anahtarını kullanan tüm komutları dönüşüm tarafından çakışmaları işler. Örneğin, "Sayı" komut "N" erişim tuşu yineleme dosyası menüsünün altında bir kuramsal için **Alt, F, N** yeni bir dosya oluşturur ve **Alt, F, N, N** "Number" komutu gerçekleştirmelisiniz.

### <a name="assigning-shortcut-keys"></a>Kısayol tuşları atama
 Yeni kısayol tuşları atama her komut için gerekli değildir ve sistem (ve kullanıcı bellek) aşırı kullanılmasına varsa vergi kaçının. Veri alanından Müşteri Deneyimi Geliştirme Programı'nı (CEIP), Visual Studio kullanıcılarına tümleşik kısayollar yalnızca küçük bir kısmı kullanacağını belirtir.

 Kısayolları tanımlarken bu kuralları izleyin:

- **Denetim (Ctrl) ve anahtar dizileri işlevi (Fn) kullanın.**

- **Sık kullanılan kısayollarını koruma.** En popüler kısayolları korur.

- **Düzenleyici kısayolları yazmak kolay hale getirir.** Geliştiricilerin çoğu kod yazarken gereken komutları türü kolay kısayolları bağlayın. Örneğin, **Edit.InvokeSmartTag** Ctrl gibi hızlı kısayol tuşu gerek duyduğu +/ ve olmayan Alt + Shift + F10.

- **Tutarlı bir şekilde temalı kısayolları çaba harcar.**

- **Uygulamaları hangi değiştirici tuşları belirlemek için Windows yönergeleri izleyin.** Belgenin tamamına Uygula komutlar gibi büyük ölçekli etkileri komutları için CTRL tuş birleşimlerini kullanın. Shift tuş birleşimleri genişletin veya standart bir kısayol tuşu eylemlerini tamamlamak için komutları kullanın. Ctrl + Alt birleşimleri kullanmayın.

- **Fazlalık kısayolları kaldırın.** Eski bir özellik varsa, bir erişim anahtarı aynı komutu hızlı erişim sağlıyorsa, aşırı infrequency (az 10 kez gelen CEIP verilerini) veya Orta infrequency (daha az 100 kat daha CEIP verileri) ile kullanılan kısayollar kaldırılıyor göz önünde bulundurun. Örneğin: Alt H, C, Yardım/Contents açılır.

  Kısayol kullanılabilirliğini denetlemek için basit bir yol değil. Bir kısayol eklemek istiyorsanız, şu adımları izleyin:

1.  Listesini kontrol edin [Visual Studio 2013 kısayolları](http://visualstudioshortcuts.com/2013/) türlerinizle gruplandırmak için benzer komutları olup olmadığını belirlemek için.

2.  Git **Araçlar > Seçenekler > ortam > klavye** ve kısayolu test. "Aşağıdaki ek klavye eşleme şemasını Uygula" her klavye eşleme şemasını altında listelenen denetleyin Bu benzersiz kısayollarını paylaşma gibi genel, C#, VB ve C++ profilleri denetleyin. Kısayolu bu yerlerin hiçbirinde eşlenmemiş kullanılabilir.
