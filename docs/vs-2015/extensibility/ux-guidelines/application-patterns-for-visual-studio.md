---
title: Uygulama Desenleri
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0deaad86e5b14bfd0dee4d73c9ceb51916231ff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060400"
---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio için uygulama desenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_WindowInteractions"></a> Pencere etkileşimleri

### <a name="overview"></a>Genel Bakış
 Visual Studio'da kullanılan iki ana pencere belge düzenleyiciler ve araç pencerelerini türleridir. Rare ancak mümkün olan büyük geçici kutularıdır. Bunlar Kabuğu'nda tüm geçici olsa da, bunların şekillerine tamamen farklı. Bu konuda belge pencerelerini, araç pencereleri ve kalıcı olmayan iletişim kutuları arasındaki farkı kapsar. Kalıcı iletişim kutusu desenleri içinde ele alınmıştır [iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Pencere kullanım desenleri karşılaştırma
 **Windows belge** neredeyse her zaman belge içinde de görüntülenir. Bu belge Düzenleyicisi sağlar bir "merkezi aşama" ek araç pencereleri geçici bir çözüm için.

 A **araç penceresi** – hangi görünür, gizli veya otomatik olarak gizli olabilir – ayrı, daha küçük bir pencere IDE kenarında karşı daraltılmış gibi en sık görüntülenir. Ancak, bazen Geçmiş olsun, belgenin içinde kaldırarak verildikleri **penceresi/Docking** penceresinde özelliği. Bu daha fazla Emlak olur, ancak aynı zamanda ortak bir tasarım kararı: Visual Studio ile tümleştirmek çalışırken, araç penceresi ya da belge penceresini özelliğinizi görüntüleyip görüntülemeyeceğini karar vermelisiniz.

 **Kalıcı olmayan iletişim kutuları** Visual Studio'daki önerilir değil. Büyük ölçüde için tanımına göre – araç pencereleri kayan ve bu nedenle uygulanmalıdır. Kalıcı olmayan iletişim kutuları, burada Kabuk tarafına yerleştirilmiş normal araç penceresi boyutu çok kısıtlayıcı olabilecek durumlarda izin verilir. Bunlar ayrıca ise kullanıcı iletişim ikincil bir monitöre taşıyabilirsiniz olasılığı olacağı durumlarda izin verilir.

 Dikkatli bir şekilde hangi kapsayıcı türü hakkında ihtiyacınız düşünün. Genel kullanım deseni için kullanıcı Arabirimi tasarımı aşağıdaki tabloda faktörlerdir.

||Belge penceresi|Araç penceresi|Kalıcı olmayan iletişim|
|-|---------------------|-----------------|---------------------|
|**Konumu**|Her zaman belge içinde iyi konumlandırılmış ve IDE kenarlarına dock değil. "Böylece ayrı ayrı bir ana kabuğundan gezinen da çekilebilir".|Genel sekmesi-yerleştirilmiş IDE köşelerindeki ancak (Temizle) kayan için özelleştirilmiş, otomatik olarak gizli olabilir ya da belge içinde iyi yuvaya.|IDE içinden ayrı büyük kayan pencere.|
|**Model yürütme**|*Gecikmeli işleme*<br /><br /> Kullanıcı bir belgedeki verileri kaydetmek için dosya/kaydetme, Farklı Kaydet veya Tümünü Kaydet komut yayımlamanız gerekir. Bir belge penceresi kaydetme birine kaydedilen verileri "kirlenmiş" kavramını sahip komutları. Bir belge penceresi kapatıldığında tüm içeriğini diske kaydedilmiş veya kaybolur.|*Hemen yürütme*<br /><br /> Kaydet mevcuttur modeli. Bir dosya düzenlenmesine yardımcı olmak denetçisi araç pencereleri, dosyanın aktif Düzenleyici ya da Tasarımcısı açık olması gerekir ve düzenleyici veya tasarımcı kaydetme sahip.|*Geciken ya da hemen yürütme*<br /><br /> Çoğunlukla, büyük bir kalıcı olmayan iletişim değişiklikleri kaydetmek için bir eylem gerektirir ve iletişim oturumunda yapılan tüm değişiklikler geri alınır "İptal" işlemi için sağlar.  Araç pencereleri her zaman bir anında yürütme modeline sahiptir, bu araç penceresinden modelsiz bir iletişim kutusu ayırır.|
|**Görünürlük**|*Açık (dosya) / oluşturun ve Kapat*<br /><br /> Bir belge pencerelerini açmak, var olan bir belgeyi açmak veya yeni bir belge oluşturmak için bir şablon kullanarak aracılığıyla gerçekleştirilir. Yok yok "açık \<belirli bir düzenleyici >" komutu.|*Gizleme ve gösterme*<br /><br /> Tek Örnekli araç pencereleri gizli veya gösterilen. İçeriği ve araç penceresi iller kalıcı olup, görünüm veya gizli. Çok örnekli araç pencereleri kapatıldığında gizli yanı sıra. Çok örnekli araç penceresi kapatıldığında durumunda araç penceresi ve içeriği atılır.|*Bir komuttan başlattı*<br /><br /> İletişim kutuları, bir görev tabanlı komut başlatılır.|
|**Örnekler**|*Çok örnekli*<br /><br /> Bazı düzenleyicileri aynı dosyanın birden fazla düzenleyicide açık olmasını da izin verirken, çeşitli düzenleyicileri düzenleme farklı dosyalar ve aynı zamanda açık olabilir (kullanarak **penceresi > Yeni bir pencere** komutu).<br /><br /> Tek bir düzenleyici (Proje Tasarımcısı) aynı anda bir veya birden çok dosya düzenleme.|*Tek veya çok instance*<br /><br /> Bağlam (olduğu gibi özellik tarayıcısı) yansıtacak veya odak/içerik başka windows (görev listesi, Çözüm Gezgini) anında iletme içeriklerini değiştirin.<br /><br /> Hem tek örnekli ve çok örnekli araç pencereleri yok sürece yeterli bir neden için etkin belge penceresi ile ilişkili olması gerekir.|*Tek örnek*|
|**Örnekler**|**Metin düzenleyiciler**, Kod Düzenleyicisi gibi<br /><br /> **Tasarım yüzey**gibi form tasarımcısı ya da bir modelleme yüzeyi<br /><br /> **Denetim düzenleri için iletişim kutularını benzer**, bildirim Tasarımcısı gibi|**Çözüm Gezgini** bir çözüm ve projeler çözümün içerdiği sağlar<br /><br /> **Sunucu Gezgini** pencerede açmak için kullanıcının seçtiği sunucuları ve veri bağlantıları hiyerarşik bir görünümünü sağlar. Veritabanı hiyerarşiden bir sorgu gibi bir nesne açılırken, bir belge penceresi açılır ve sorgu düzenlemesine olanak tanır.<br /><br /> **Özellik tarayıcısı** bir belge penceresi veya başka bir araç penceresi seçili nesne için özellikleri görüntüler. Özellikleri, hiyerarşik bir kılavuz görünümünde veya karmaşık iletişim benzeri denetimlerinde sunulur ve bu özelliklerin değerlerini ayarlamak izin verin.||

##  <a name="BKMK_ToolWindows"></a> Araç pencereleri

### <a name="overview"></a>Genel Bakış
 Araç pencereleri, belge pencerelerinin gerçekleşen kullanıcının iş destekler. Visual Studio işleyebilir ve sağlayan bir temel kök nesnesi temsil eden bir hiyerarşisini göstermek amacıyla kullanılabilir.

 IDE içinde yeni bir araç penceresi dikkate alındığında, yazarlar gerekir:

-   Görev uygun mevcut araç pencereleri ve benzer işlevselliği olan yenilerini oluşturmak değil. Yeni araç pencereleri, yalnızca önemli ölçüde farklı "aracı" ya da benzer bir pencereye ya da varolan pencereye bir özetleyerek hub'ına kapatarak tümleştirilemiyor işlevleri sağlamıyorsa oluşturulmalıdır.

-   Gerekirse, araç penceresinin en üstünde bir standart komut çubuğunu kullanın.

-   Tutarlı denetim sunu ve klavye gezintisi için diğer araç pencerelerinde de zaten mevcut desenlerine sahip olabilir.

-   Diğer araç pencereleri denetim sunuda tutarlı olması.

-   Yalnızca üst belge etkinleştirildiğinde görünecekleri belgeye özgü araç pencereleri otomatik görünen mümkün olduğunda olmalıdır.

-   Pencere içeriklerini klavye (Destek ok tuşlarını) kullanılarak gezilebilir olduğundan emin olun.

#### <a name="tool-window-states"></a>Araç penceresi durumları
 Visual Studio araç pencereleri, bazıları (otomatik gizleme özelliği gibi) kullanıcı etkinleştirilmiş olan farklı durumları sahip. Gibi diğer durumlarını otomatik görünür, doğru bağlamda görüntülenir ve gerekli gizle Araç pencereleri izin verin. Toplam beş araç penceresi durumlar vardır.

- **Yerleşik ve sabitlenmiş** araç pencereleri belge alanını dört tarafına birine eklenebilir. Araç penceresinin başlık çubuğundaki Raptiye simgesi görünür. Araç penceresi kabuk ve diğer araç pencereleri kenarına yatay veya dikey olarak yerleştirilmiş olabilir ve aynı zamanda sekme bağlantılı olabilir.

- **Otomatik gizlenmiş** araç pencereleri sabitlenmemiş. Pencerenin görme, belge alanını kenarında (araç penceresi adını ve simgesini) içeren bir sekme bırakarak dışında kaydırabilirsiniz. Bir kullanıcı sekmenin üzerine geldiğinde kullanıma araç penceresi çıkar.

- **Otomatik görünür** araç pencereleri otomatik olarak kullanıcı Arabirimi, başka bir parçası gibi bir düzenleyici başlatılır veya odağını kazandığında görüntülenir.

- **Kayan** araç pencerelerini IDE dışında gelin. Bu, çoklu monitör yapılandırmaları için kullanışlıdır.

- **Sekmeli belge** araç pencereleri yerleştirilmiş belgenin içinde iyi. Bu, kenarlarını çerçevenin takma izin verdiğinden daha fazla gerçek boyutunuzu gereken nesne tarayıcısı gibi büyük araç pencereleri için kullanışlıdır.

  ![Araç penceresi durumları Visual Studio'da](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702 01_ToolWindowStates")

  **Visual Studio araç penceresi durumları**

#### <a name="single-instance-and-multi-instance"></a>Tek Örnekli ve çok örnekli
 Araç pencereleri, tek örnekli ya da çok örnekli ' dir. Çok örnekli araç pencereleri görünmeyebilir ancak bazı Tek Örnekli araç pencereleri etkin belge penceresi ile ilişkilendirilmiş olabilir. Çok örnekli araç pencereleri, pencerenin yeni bir örneğini oluşturarak penceresi/yeni pencere komutuna yanıt. Aşağıdaki görüntüde pencerede örneği etkin olduğunda yeni pencere komutu etkinleştirme araç penceresi gösterilmektedir:

 ![Visual Studio komutları etkinleştirme araç penceresi](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")

 **Araç penceresi penceresinin örneği etkin olduğunda 'Yeni pencere' komutu etkinleştirme**

 Tek Örnekli araç pencereleri, gizli veya gösterilen çok örnekli araç pencereleri kapatıldığında gizli yanı sıra sırada. Sekme bağlantılı, kayan veya bir Çoklu belge arabirimi (MDI) alt penceresi (bir belge penceresine benzer) olarak ayarlanmış tüm araç pencereleri sabitlenebilir. Tüm araç pencereleri Pencere menüsü uygun pencere yönetimi komutlar yanıt vermesi gerekir:

 ![Visual Studio'da pencere yönetimi komutları](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702 03_WindowManagementControls")

 **Visual Studio Pencere menüsünden pencere yönetimi komutları**

#### <a name="document-specific-tool-windows"></a>Belgeye özgü araç pencereleri
 Bazı araç pencerelerinin, belirli bir belge türüne göre değiştirmek için tasarlanmıştır. Etkin belge penceresini IDE içindeki uygulanabilir işlevselliğini yansıtmak üzere bu pencereleri sürekli olarak güncelleştirin.

 Araç ve belge Anahat araç pencereleri içerikleri seçili Düzenleyici yansıtacak şekilde değiştirin örnekleridir. Bir düzenleyici, bağlamı penceresine sunmaz odağa sahip olduğunda bu windows Filigran gösterir.

#### <a name="navigable-list-tool-windows"></a>Gezinilebilir listesi araç pencereleri
 Bazı araç pencerelerinin, kullanıcının etkileşim gezilebilir öğelerin listesini görüntüleyin. Bu tür pencere, her zaman olmalıdır listesinde, geçerli öğe için geri bildirim penceresi devre dışı olsa bile. Listenin yanıt vermesi gereken **GoToNextLocation** ve **GoToPrevLocation** penceresinde geçerli seçilmiş öğe ayrıca değiştirerek komutları

 Çözüm Gezgini ve sonuçları Bul penceresi gezilebilir listesi araç pencereleri örnekleridir.

### <a name="tool-window-types"></a>Araç penceresi türleri

#### <a name="common-tool-windows-and-their-functions"></a>Ortak Araç pencereleri ve bunların işlevleri

|Tür|Araç penceresi|İşlev|
|----------|-----------------|--------------|
|**Hiyerarşi**|Çözüm Gezgini|Belgelerin listesini görüntüleyen bir hiyerarşik ağaç projeleri, çeşitli dosyalar ve çözüm öğeleri içeriyor. Proje öğeleri görüntüsünü proje türü (örneğin, başvuru tabanlı, dizin tabanlı veya karma mod türleri) sahip bir paketi tarafından tanımlanır.|
|**Hiyerarşi**|Sınıf Görünümü|Sınıfları ve belgelerin, dosyaların bağımsız çalışma kümesinde çeşitli öğelerin bir hiyerarşik ağaç.|
|**Hiyerarşi**|Server Explorer|Çözümdeki tüm sunucuları ve veri bağlantılarını görüntüleyen bir hiyerarşik ağaç.|
|**Hiyerarşi**|Belge Anahattı|Etkin belgeyi hiyerarşik yapısı.|
|**Kılavuz**|Özellikler|Bu özelliklerini düzenlemek için değer seçiciler yanı sıra seçili nesnenin özellikleri listesini görüntüler bir kılavuz.|
|**Kılavuz**|Görev Listesi|Oluşturma/düzenleme/silme görevleri ve açıklamalar kullanıcıya izin veren bir kılavuz.|
|**İçeriği**|Yardım|Kullanıcılarının "Nasıl yaparım?" den yardım almanın çeşitli yöntemler erişmesini sağlayan bir pencere MSDN Forumları videoları.|
|**İçeriği**|Devingen Yardım|Yardım konuları geçerli seçime uygun bağlantılarını görüntüleyen bir araç penceresi.|
|**İçeriği**|Nesne Tarayıcısı|Hiyerarşik nesnenin bileşenlerde sol bölmesinde ve nesnenin özellikleri ve yöntemleri sağ sütunda listesini içeren iki sütunlu çerçeve.|
|**İletişim kutusu**|Bul, Gelişmiş Bul|Bir iletişim kutusu, kullanıcının bulun veya bulun ve çözüm içindeki çeşitli dosyaları Değiştir izin verir.|
|**Diğer**|Araç Kutusu|Tüm tasarımcıları için tutarlı bir sürükleme kaynağı sağlayan, tasarım yüzeyleriyle üzerine bırakılan öğelerini depolamak için kullanılan araç penceresi.|
|**Diğer**|Başlangıç Sayfası|Geliştirici Haberleri, Visual Studio Yardım ve son kullanılan projeler akışlarını erişimi olan kullanıcı portalı Visual Studio için. Visual Studio Belgelerim dizini StartPages klasörüne "Common7\IDE\StartPages\" Visual Studio program dosyaları dizinden StartPage.xaml dosya kopyalamayı ve ardından ya da XAML el ile düzenleme kullanıcılar özel başlangıç sayfaları de oluşturabilirsiniz veya Visual Studio ya da başka bir kod düzenleyicisini açmadan.|
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|İfade ve değişkenler||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Hemen||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Çıkış|Çıkış penceresi, metinsel olayları veya bildirmek için durum olduğunda kullanılabilir.|
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Bellek||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Kesme noktaları||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Çalıştırılıyor||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Belgeler||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Çağrı yığını||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Yerel öğeler||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|İzlemeleri||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Ayrıştırılmış kodu||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|Kaydeder||
|**Hata Ayıklayıcı:** windows görevleri hata ayıklama ve izleme etkinlikleri için belirli bir grup|İş Parçacıkları||

##  <a name="BKMK_DocumentEditorConventions"></a> Belge Düzenleyicisi kuralları

### <a name="document-interactions"></a>Belge etkileşimleri
 "İyi belge" IDE içinde en büyük alanı ve burada kullanıcı genellikle dikkatini tarafından ek araç pencereleri Yardımlı görevlerini tamamlamak için odaklanıyor. Belge düzenleyicileri, kullanıcı açılır ve Visual Studio içinden kaydeder çalışmanın temel birimleri temsil eder. Çözüm Gezgini veya diğer etkin olan hiyerarşi windows bağlı seçimin güçlü bir algılama korurlar. Kullanıcının bu hiyerarşi windows birini işaret edecek ve çözüm, proje veya başka bir kök nesnesi bir Visual Studio paketi tarafından sağlanan belge bulunduğu ve ilişkisini biliyor olması gerekir.

 Belge düzenleme, tutarlı bir kullanıcı deneyimi gerektirir. Elinizdeki yerine pencere yönetimi ve komutları bulma odaklanmak izin vermek için bu belge türü düzenlemek için kullanıcı görevleri için en uygun bir belge görünümü stratejisi seçin.

#### <a name="common-interactions-for-the-document-well"></a>İyi belge için ortak etkileşimleri

-   Ortak tutarlı etkileşim modelinde tutmak **yeni dosya** ve **açık dosya** karşılaşır.

-   Belge penceresi açıldığında, ilgili işlevleri ilgili windows ve menülerde güncelleştirin.

-   Menü komutları uygun şekilde tümleştirilir ortak menüler gibi **Düzenle**, **biçimi**, ve **görünümü** menüleri. Özel komutlar önemli miktarda varsa, yeni bir menü yalnızca belgenin odak olduğunda görünür olan oluşturulabilir.

-   Katıştırılmış bir araç çubuğu Düzenleyicisi üst kısmında yerleştirilebilir. Bu düzenleyici dışında görüntülenen ayrı bir araç çubuğu bulunması tercih edilir.

-   Çözüm Gezgini veya benzer etkin bir seçim her zaman korumak hiyerarşisi penceresi.

-   Çözüm Gezgini'nde bir belgeyi çift aynı eylemi gerçekleştirmesi gereken **açık**.

-   Birden fazla Düzenleyicisi, bir belge türü üzerinde kullanılabilir ise kullanıcı geçersiz ya da belirli belge türü kullanarak varsayılan eylem sıfırlama olmalıdır **birlikte Aç** dosyaya sağ tıklayıp seçme iletişim kutusu **Aç İle** kısayol menüsünden.

-   Belgede bir Sihirbazı da oluşturmayın.

### <a name="user-expectations-for-specific-document-types"></a>Özel belge türleri için kullanıcı beklentileri
 Belge düzenleyicileri birkaç farklı temel türleri vardır ve her bir aynı türden başkalarıyla tutarlı etkileşimleri kümesine sahiptir.

- **Metin tabanlı Düzenleyici:** Kod Düzenleyicisi, günlük dosyaları

- **Tasarım yüzeyine:** WPF forms Tasarımcısı, Windows forms

- **İletişim kutusu stilinde Düzenleyicisi:** bildirim Tasarımcısı, proje özellikleri

- **Model Tasarımcısı:** iş akışı Tasarımcısı, codemap, mimari diyagramı, ilerleme

  Belge de kullandığınız birkaç Düzenleyicisi olmayan türleri de vardır. Belgeler kendilerini düzenleme yapmadığınız sırada bunlar belge pencereleri için standart etkileşimlerini izlemeniz gerekir.

- **Raporları:** IntelliTrace raporu, Hyper-V rapor profil oluşturucusu raporu

- **Pano:** tanılama Merkezi

#### <a name="text-based-editors"></a>Metin tabanlı düzenleyiciler

-   Belgeyi açmaya gerek kalmadan, belge önizlemek için izin verme Önizleme sekmesini modelinde katılır.

-   Belge ana hattı gibi bir yardımcı araç penceresi içinde belgesinin yapısını temsil edilebilir.

-   IntelliSense (uygunsa), diğer kod düzenleyicileri ile tutarlı bir şekilde davranır.

-   Açılır pencereleri veya yardımcı UI izleyin benzer stillerini ve biçimlerini CodeLens gibi var olan benzer kullanıcı arabirimi.

-   Belge durumuyla ilgili iletiler, belgenin üst kısmında, bir bilgi çubuğu denetimini veya durum çubuğu sunulur.

-   Kullanıcı yazı tipleri ve renkler kullanarak görünümünü özelleştirebilirsiniz bir **Araçlar > Seçenekler** sayfası, paylaşılan yazı tipleri ve renkler sayfası ya da bir özel düzenleyiciye getirir.

#### <a name="design-surfaces"></a>Tasarım yüzeyleriyle

-   Boş bir tasarımcı Filigran kullanmaya nasıl başlayacağınızı belirten yüzeyine sahip olmalıdır.

-   Görünümü değiştirme mekanizmaları mevcut desenleri gibi bir kod Düzenleyicisi'ni veya sekme içinde her iki bölmenin etkileşim belge penceresini açmak için çift izler.

-   Yüksek oranda özel araç penceresi gerekli olmadığı sürece tasarım yüzeyine öğeleri ekleme araç kutusu yapılmalıdır.

-   Öğeleri yüzeyinde tutarlı seçimi modelini kullanır.

-   Katıştırılmış araç çubukları içeren belge özel komutları yalnızca, bilinen komutları gibi **Kaydet**.

#### <a name="dialog-style-editors"></a>İletişim kutusu stilinde düzenleyiciler

-   Denetim düzenini normal iletişim düzeni kuralları izlemelidir.

-   Sekmeler ve düzenleyici içindeki belge sekmeleri görünümünü eşleşmemelidir, iki izin verilen iç sekmesini stillerden birini eşleşmesi gerekir.

-   Yalnızca klavyeyi kullanarak denetim ile etkileşimde olması gerekir; Düzenleyici etkinleştirme ve denetimler aracılığıyla veya sekme standart anımsatıcıları kullanarak ya da.

-   Tasarımcı model kaydetme ortak kullanmanız gerekir. Diğer düğmelerin uygun olabilir ancak hiçbir genel Kaydet veya yürütme düğmeleri yüzeyinde yerleştirilmelidir.

#### <a name="model-designers"></a>Model tasarımcıları

-   Boş bir tasarımcı Filigran kullanmaya nasıl başlayacağınızı belirten yüzeyine sahip olmalıdır.

-   Tasarım yüzeyine öğeleri ekleyerek, araç kutusu yapılmalıdır.

-   Öğeleri yüzeyinde tutarlı seçimi modelini kullanır.

-   Katıştırılmış araç çubukları içeren belge özel komutları yalnızca, bilinen komutları gibi **Kaydet**.

-   Bir gösterge gösterir ya da Filigran yüzeyinde görünebilir.

-   Kullanıcı kullanarak yazı tipleri/renkleri özelleştirme olanağına bir **Araçlar > Seçenekler** sayfası, yazı tipleri ve renkler paylaşılan sayfanın ya da bir özel düzenleyiciye.

#### <a name="reports"></a>Raporlar

-   Raporları salt bilgileri genellikle ve Kaydet modelde yer yok. Ancak, bunlar diğer ilgili bilgileri veya genişletme ve daraltma bölümler bağlantılar gibi etkileşim içerebilir.

-   Çalışma yüzeyinde komutların çoğu köprüler düğmeleri olmalıdır.

-   Düzen, bir üst bilgisi ekleyin ve standart rapor düzeni yönergeleri izleyin.

#### <a name="dashboards"></a>Panolar

-   Panolar bir etkileşim modeli kendilerini yoksa, ancak çeşitli diğer araçları sunmak için bir yol görev yapar.

-   Kaydetme modelde yer yok.

-   Düzenleyici etkinleştirme ve denetimler arasında sekmeyle gitmeyi ya da standart anımsatıcıları kullanarak yalnızca klavye kullanma denetimleri etkileşimde olması gerekir.

##  <a name="BKMK_Dialogs"></a> İletişim kutuları

### <a name="introduction"></a>Giriş
 Visual Studio iletişim kutularında, genellikle ayrı bir kullanıcının iş birimi desteklemelidir ve ardından kapatıldı.

 Bir iletişim kutusu ihtiyacınız karar verdiyseniz, tercih sırasına göre üç seçeneğiniz vardır:

1. Tek bir paylaşılan iletişim kutularının Visual Studio'da özelliklerinizi tümleştirin.

2. Mevcut bir benzer iletişim kutusundaki bir desen kullanarak kendi iletişim oluşturun.

3. Yeni bir iletişim kutusu, aşağıdaki etkileşim ve Düzen kılavuzu oluşturun.

   Bu konuda, Visual Studio iş akışı içinde doğru iletişim düzeni iletişim tasarımı için genel kurallar seçip açıklar.

### <a name="themes"></a>Temalar
 Visual Studio iletişim kutularında iki temel stilleri birini izleyin:

#### <a name="standard-unthemed"></a>Standart (unthemed)
 İletişim kutuları çoğu, standart yardımcı programı kutularıdır ve unthemed olmalıdır. Ortak denetimleri yeniden şablonu veya stilize "modern" düğmeleri veya denetimleri oluşturma girişimi. Denetimleri ve chrome görünümünü izleyin [iletişim kutuları için standart Windows Masaüstü etkileşim kuralları](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx).

#### <a name="themed"></a>Tema
 Özel "SIGNATURE" iletişim kutuları temalı olabilir. Temalı iletişim kutuları, bazı özel etkileşim desenleri stil ile ilişkili olan farklı bir görünüm vardır. Tema yalnızca bu gereksinimleri karşılıyorsa iletişim:

- İletişim kutusu, görülebilir ve sıklıkla veya çok sayıda kullanıcı tarafından kullanılan ortak deneyimidir (örneğin, **yeni proje** iletişim.

- İletişim tanınmış ürün marka öğelerini içerir (örneğin, **hesap ayarları** iletişim).

- Temalı diğer iletişim kutuları içeren daha büyük bir akış ayrılmaz bir parçası iletişim kutusu görüntülenir (örneğin, **bağlı hizmet Ekle** iletişim).

- İletişim kutusu, yükseltme veya bir ürün sürümü farklılaştırılması stratejik bir rol oynar bir deneyim, önemli bir parçasıdır.

  Temalı iletişim oluştururken uygun ortam renklerini kullan ve etkileşim desenleri ve doğru düzeni izleyin. (Bkz [Visual Studio için Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>İletişim tasarım
 İyi tasarlanmış bir iletişim kutusu aşağıdaki öğeleri dikkate alın:

-   Desteklenen kullanıcı görevi

-   Metin Stili iletişim, dil ve terminoloji

-   Denetim seçim ve UI kuralları

-   Görsel düzeni belirtimi ve denetimi hizalama

-   Klavye erişimi

#### <a name="content-organization"></a>İçerik kuruluş
 İletişim kutuları temel türlerinin arasındaki farklılıkları dikkate alın:

-   [Basit iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) tek bir kalıcı pencere denetimler sunar. Sunu alanı Seçici veya simge çubuğu gibi karmaşık denetim düzenleri, çeşitleri içerebilir.

-   [İletişim kutuları katmanlı](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) tek bir kullanıcı Arabirimi birden çok denetim grubunu içerdiğinde en ekran gerçek boyutunuzu yapmak için kullanılır. "Kullanıcı belirli bir andaki görmek için gruplandırmanın seçebilir böylece iletişim kutusunun gruplandırmaları sekme denetimleri, gezinti liste denetimleri veya düğmeleri katmanlıdır".

-   [Sihirbazlar](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) yönlendiren bir görevin tamamlanmasına yönelik adımlar mantıksal bir dizi aracılığıyla kullanıcı için kullanışlıdır. Bir dizi seçenek, sıralı panelleri, farklı iş akışları ("dal") önceki panelinde yaptığınız bir seçim bağımlı bazen giriş sunulur.

####  <a name="BKMK_SimpleDialogs"></a> Basit iletişim kutuları
 Basit bir iletişim kutusu denetimleri tek bir kalıcı penceresinde gösterir. Bu sunum, bir alanı Seçici gibi karmaşık denetim düzenleri çeşitleri içerebilir. Basit iletişim kutuları için standart genel düzeni ve bunun yanı sıra karmaşık denetimi grupları için gerekli olan herhangi bir belirli düzeni izleyin.

 ![Visual Studio'da basit bir iletişim kutusu](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704 01_CreateStrongNameKey")

 **Oluşturma katı ad anahtarı Visual Studio'da basit bir iletişim kutusu bir örnektir.**

####  <a name="BKMK_LayeredDialogs"></a> Katmanlı iletişim kutuları
 Katmanlı iletişim kutuları, sekmeler, panolar ve katıştırılmış ağaçları içerir. Bunlar, birden çok kullanıcı Arabirimi tek bir parçası sunulan denetim grubunu olduğunda gerçek boyutunuzu maksimuma çıkarmak için kullanılır. Kullanıcının herhangi bir anda görmek için gruplandırmanın seçebilmeniz gruplandırmaları katmanlıdır.

 En basit durumda gruplandırmaları arasında geçiş yapmak için bir sekme denetimi mekanizmadır. Çeşitli alternatifler kullanılabilir. Önceliklendirme ve katmanlama en uygun stil seçin öğrenmek için bkz.

 **Araçlar > Seçenekler** iletişim katıştırılmış bir ağaç kullanarak katmanlı bir iletişim kutusunun bir örnek verilmiştir:

 ![Visual Studio'da katmanlı iletişim](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704 02_ToolsOptions")

 **Araçlar > Seçenekler katmanlı bir iletişim kutusu Visual Studio'da bir örnektir.**

####  <a name="BKMK_Wizards"></a> Sihirbazlar
 Sihirbazlar, bir görevin tamamlanması kullanıcının bir adımlarının mantıksal sırası üzerinden yönlendiren için kullanışlıdır. Bir dizi seçenek sıralı panellerinde sunulur ve kullanıcı sonraki devam etmeden önce her adımın üzerinden devam etmeniz gerekir. Yeterli kullanılabilir varsayılanlardır sonra **son** düğmesi etkinleşir.

 Kalıcı sihirbazları görevler için kullanılan:

-   Kullanıcı seçenekleri bağlı olarak farklı yolları Burada sunulan dallandırma içerir

-   Sonraki adımlar kullanıcı girişi ile önceki adımları burada bağlıdır, adımlar arasında bağımlılıklar içerir

-   Kullanıcı Arabiriminde sunulan seçimleri ve sonuçtan her adımda açıklamak için kullanılması gereken yeterince karmaşıktır

-   İşlem, bir dizi sunabilen değişiklikler kaydedilmeden önce tamamlanması gereken adımlar gerektiren olan

### <a name="common-conventions"></a>Genel kurallar
 En iyi tasarım ve, iletişim kutuları işlevsellikle elde etmek için iletişim kutusunun boyutu, konum, standartları, denetimi yapılandırması ve hizalama, UI metin, başlık çubukları, denetim düğmeleri ve erişim anahtarları bu kuralları izleyin.

 Düzen özgü yönergeler için bkz: [Visual Studio için Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Boyut
 İletişim kutuları içinde en az 1024 x 768 ekran çözünürlüğü sığması gereken ve ilk iletişim kutusu boyutu 900 x 700 piksel aşmamalıdır. İletişim kutuları yeniden boyutlandırılabilir olabilir, ancak zorunlu değildir.

 Yeniden boyutlandırılabilir iletişim kutuları için iki öneriler şunlardır:

1.  En küçük boyut denetimi için en iyi duruma getirir iletişim için tanımlı olduğunu kırpma olmadan ayarlayın ve makul yerelleştirme büyümeye uyum sağlamak için ayarlayın.

2.  Kullanıcı ölçeklendirilmiş boyutu oturumdan oturuma devam ettiğini. Örneğin, kullanıcı % 150'iletişim kutusuna ölçeklenirse, iletişim kutusunun bir sonraki başlatma % 150 görüntülenir.

#### <a name="position"></a>Konum
 İletişim kutuları ilk kez başlattığınızda IDE içinde ortalanmış yer almalıdır. Yeniden boyutlandırılabilir olmayan iletişim kutuları için değil iletişim kutusunun son konum kalıcı olmasını, sonraki başlatır üzerinde ortalanmış görünmesi için gerekli. Yeniden boyutlandırılabilir iletişim kutuları için boyutu üzerinde sonraki başlatır kalıcı. Kalıcı yeniden boyutlandırılabilir iletişimler için konumu kalıcı gerekmez. IDE içinde ortalanmış görüntüledikten kullanıcının ekran yapılandırması değiştiğinde bir öngörülemeyen ya da kullanılamaz konumda görünen iletişim kutusunun olasılığını ortadan kaldırır. İletişim sık daha büyük bir iş akışının ayrılmaz bir parçası olarak kullanılan, konumlandırılabilir kalıcı olmayan iletişim kutuları için kullanıcının konumunu sonraki açılır üzerinde korunması gerekir.

 İletişim kutuları diğer iletişim kutuları oluşturma gerekir, üstteki iletişim sağa basamaklı ve ana olan yeni bir konuma gitme kullanıcı için açık olacak şekilde aşağı.

#### <a name="modality"></a>Şekil
 Kalıcı olan kullanıcılar tamamlayın veya devam etmeden önce iletişim kutusunu iptal etmek için gerekli olduğu anlamına gelir. Ortam diğer bölümleriyle etkileşmek kullanıcının kalıcı iletişim kutuları engelleyin olduğundan, özelliğin Görev akışı mümkün olduğunca dikkatli kullanmanız gerekir. Visual Studio, kalıcı bir işlem gerekli olduğunda, bir dizi paylaşılan iletişim kutuları, özelliklerini tümleştirebilirsiniz sahiptir. Yeni bir iletişim kutusu oluşturmanız gerekirse, var olan bir iletişim kutusu etkileşim desenini benzer işlevselliği olan izleyin.

 Kullanıcıların gerektiğinde kerede gibi iki etkinlik gerçekleştirmek **Bul** ve **değiştirin** kullanıcı kolayca bunlar arasında geçiş yapabilirsiniz yeni kod yazarken, iletişim kutusu engelleyici olmayan olmalıdır. Visual Studio araç pencereleri bağlantılı görev Düzenleyicisi destekleyen bu tür için genel olarak kullanır.

#### <a name="control-configuration"></a>Denetimi yapılandırma
 Visual Studio'da aynı görevi gerçekleştirir mevcut denetim yapılandırmaları ile tutarlı olmalıdır.

#### <a name="title-bars"></a>Başlık çubukları

- Başlık çubuğunda metin onu başlatan komut adını yansıtması gerekir.

- Herhangi bir simge iletişim başlık çubuklarında kullanılmalıdır. Burada sistem gerektiren durumlarda, Visual Studio logosu kullanın.

- İletişim kutuları olmamalıdır en aza indirmek ya da düğmeleri en üst düzeye çıkarın.

- Başlık çubuğunda Yardımı düğmeleri kullanım dışı bırakıldı. Yeni iletişim kutuları için bunları eklemeyin. Mevcut olduğunda, kavramsal olarak bir görevle ilgili Yardım konusunu başlatmak.

  ![Başlık Çubuğu Özellikleri Visual Studio için](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704 03_TitleBarSpecs")

  **Visual Studio iletişim kutularındaki başlık çubukları için kılavuz belirtimleri.**

#### <a name="control-buttons"></a>Düğme denetimi
 Genel olarak, **Tamam**/**iptal**/**yardımcı** düğmeleri düzenlenmiş yatay olarak iletişim kutusunun sağ alt köşesinde. Bir iletişim kutusu denetim düğmeleri visual karıştırılıyor neden olabilir iletişim kutusunun altındaki çeşitli diğer düğmeleri varsa alternatif dikey yığın izin verilir.

 ![Denetim düğmesi yapılandırmaları Visual Studio'da](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704 04_ControlButtonConfig")

 **Visual Studio kutularındaki denetim düğmeler için kabul edilebilir yapılandırmaları**

 İletişim kutusu, varsayılan denetimi düğme içermesi gerekir. Varsayılan olarak kullanmak için en iyi komutu belirlemek için (öncelik sırasına göre listelenmiş) aşağıdaki seçenekler arasından seçim yapın:

- Varsayılan olarak güvenli ve en güvenli komutu seçin. Bu, veri kaybını önlemeye ve istenmeyen sistem erişimi önlemek büyük olasılıkla komutunu seçerek anlamına gelir.

- Veri kaybı ve güvenlik faktörleri değilseniz, kolaylık üzerinde göre varsayılan komutu'ni seçin. Sık ve yinelenen görevleri iletişim kutusu desteklediğinde, en olası komutu varsayılan olarak dahil olmak üzere kullanıcının iş akışı iyileştirir.

  Varsayılan komut için kalıcı olarak zararlı bir eylem seçmekten kaçının. Böyle bir komut varsa, daha güvenli bir komutu bunun yerine varsayılan olarak'nı seçin.

#### <a name="access-keys"></a>Erişim anahtarları
 Erişim tuşları kullanmayın **Tamam**/**iptal**/**yardımcı** düğmeleri. Bu düğmeler kısayol tuşları için varsayılan olarak eşleştirilir:

|Düğme adı|Klavye kısayolu|
|-----------------|-----------------------|
|Tamam|Enter|
|İptal|Esc|
|Yardım|F1|

#### <a name="imagery"></a>Gözünüzde
 Görüntüleri iletişim kutularında tedbirli şekilde kullanın. Büyük simgeler yalnızca alanı kullanmak iletişim kutularında kullanmayın. Uyarı simgeleri veya durumu animasyonlarını gibi kullanıcıya ileti iletmek için önemli bir bölümü yalnızca olmaları durumunda görüntüleri kullanın.

###  <a name="BKMK_PrioritizingAndLayering"></a> Öncelik ve katmanlama

#### <a name="prioritizing-your-ui"></a>Kullanıcı Arabirimi öncelik
 Belirli kullanıcı Arabirimi öğeleri için forefront getirin ve daha gelişmiş davranışı ve iletişim kutuları (belirsiz komutları dahil) seçeneklerini yerleştirmek gerekli olabilir. Yaygın olarak kullanılan işlevler için forefront yer bunu yaparak ve iletişim kutusu görüntülendiğinde yaparak bunu görünür varsayılan olarak bir metin etiketi ile kullanıcı arabirimini getirin.

#### <a name="layering-your-ui"></a>Kullanıcı Arabirimi katmanlama
 Bir iletişim kutusu gereklidir ancak kullanıcıya sunmak istediğiniz ilgili işlevleri basit bir iletişim kutusunda neler görüntülenebilen ötesine giden karar verdiyseniz, kullanıcı Arabirimi katman gerekir. Visual Studio kullanan en yaygın katmanlama sekmeler ve koridorlarda veya panolar yöntemlerdir. Bazı durumlarda, genişletebileceğiniz ve daraltabileceğiniz bölgeleri uygun olabilir. Uyarlamalı UI, Visual Studio'da genel olarak önerilmez.

 Olumlu ve olumsuz yönleri için sekmesinde benzeri denetimlerde UI katmanlama farklı yöntemleri vardır. Kendi durumunuza uygun olan bir katman teknik seçme emin olmak için aşağıdaki listeyi gözden geçirin.

##### <a name="tabbing"></a>Sekme

|Geçiş mekanizması|Avantajlar ve uygun kullanın|Olumsuz ve uygunsuz kullanım|
|-------------------------|------------------------------------|-----------------------------------------|
|Sekme denetimi|İletişim kutusu sayfaları ilgili kümeleri halinde gruplandırıp<br /><br /> Beşten az (veya tek bir satırda arasında iletişim uyan sekme sayısı) için yararlı iletişim kutusunda ilgili denetimlerin sayfaları<br /><br /> Sekme etiketleri kısa olmalıdır: içeriği kolayca belirleyebilirsiniz bir veya iki sözcük<br /><br /> Ortak bir sistem iletişim kutusu stili<br /><br /> Örnek: **dosya Gezgini > öğesi özellikleri**|Tanımlayıcı kısa etiketler yapmak zor olabilir<br /><br /> Genellikle bir iletişim kutusunda beş sekme geçmiş ölçeklendirilemez<br /><br /> Bir satır için çok fazla sekmeleri varsa uygunsuz; bir alternatif katmanlama tekniği kullanın<br /><br /> Genişletilebilir değil|
|Gezinti kenar çubuğu|Daha fazla kategori sekmeleri daha uyum basit geçiş cihaz<br /><br /> Düz liste kategorileri (hiyerarşi yok)<br /><br /> Genişletilebilir<br /><br /> Örnek: **Özelleştir... > Ekle komutu**|Üçten grubu olması halinde yatay boşluk olmayan bir iyi kullanımı<br /><br /> Görev daha iyi bir açılan uygun olabilir|
|Ağaç denetimi|Sınırsız kategorileri sağlar<br /><br /> Gruplandırma ve/veya kategori hiyerarşisi sağlar<br /><br /> Genişletilebilir<br /><br /> Örnek: **Araçlar > Seçenekler**|Yoğun bir şekilde iç içe Hiyerarşiler aşırı yatay kaydırma neden olabilir<br /><br /> Visual Studio bir overabundance ağaç görünümlerini sahiptir.|
|Sihirbazı|Görev tamamlama, görev tabanlı, sıralı adımlarda size kılavuzluk tarafından yönelik aramalarındaki. Sihirbazın üst düzey bir görevi temsil eder ve tek tek bölmeleri genel görevi tamamlamak için gereken görevleri temsil eder.<br /><br /> Görevin ne zaman kullanıcı Aksi takdirde birden çok düzenleyicileri kullanır ve bir görevi tamamlamak için windows aracı gerekirdi olarak UI sınırları geçtiğinde yararlı<br /><br /> Yararlı görev dallanma gerektirir.<br /><br /> Yararlı görev adımları arasındaki bağımlılıkları içeriyor<br /><br /> Farklı benzer iletişim kutuları sayısını azaltmak için bir iletişim kutusunda bir karar çatal birkaç benzer görevlerle sunulabilir kullanışlıdır.|Bir sıralı iş akışı gerektirmez herhangi bir görev için uygun<br /><br /> Kullanıcılar kısası ve çok çok adımlı bir sihirbaz tarafından kafanız dönüşebilir.<br /><br /> Sihirbazlar kendiliğinden ekran gerçek boyutunuzu sınırlı|

##### <a name="hallways-or-dashboards"></a>Koridorlarda veya panolar
 Koridorlarda ve panolar iletişim kutuları veya diğer iletişim kutuları ve windows noktalarına başlatma olarak hizmet veren panelleri markalarıdır. İyi tasarlanmış "koridor" hemen yalnızca en yaygın seçenekler, komutlar ve kullanıcının kolayca ortak görevleri gerçekleştirin izin ayarları, ortaya çıkarır. Burada gerçek koridor arkasına odaları erişmek için açılan kapılar sağlar gibi daha az yaygın kullanıcı arabirimini ayrı "odaları" (genellikle diğer iletişim kutuları) ana koridor erişilebilir ilgili işlevlerin içine toplanır.

 Alternatif olarak, yeniden düzenleme ayrı konumlara daha az yaygın işlevi yalnızca bir Pano yerine, tek bir koleksiyon içindeki tüm kullanılabilir işlevler sunan UI.

 ![Outlook'ta koridor kavramı](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704 08_Hallway")

 **Outlook içinde ek kullanıcı Arabirimi kullanıma sunmak için koridor kavramı**

##### <a name="adaptive-ui"></a>Uyarlamalı kullanıcı Arabirimi
 Gösterme veya gizleme UI kullanımını temel alarak veya kullanıcının şirket içinde bildirilen diğer bölümleri gizleyerek gerekli kullanıcı Arabirimi sunan bir başka yolu deneyimidir. Bu Visual Studio UI gizlemek veya göstermek ne zaman karar için algoritmalar zor olabilir ve kuralların her zaman bazı durumlarda kümesi için yanlış olacaktır önerilmez.

##  <a name="BKMK_Projects"></a> Projeleri

### <a name="projects-in-the-solution-explorer"></a>Çözüm Gezgini'nde proje
 Çoğu proje olarak tabanlı başvurusu, dizin tabanlı veya karma sınıflandırılır. Üç tür projeleri Çözüm Gezgini'nde aynı anda desteklenir. Kök kullanıcı deneyiminin projeleriyle çalışırken bu pencere içinde gerçekleşir. Farklı proje düğümleri başvurusu, dizin veya karma mod türü projeleri olsa da, projeye özgü kullanıcı desenleri ile ayrışan önce bir başlangıç noktası olarak uygulanması gereken bir ortak etkileşim düzeni yoktur.

 Her zaman projeleri gerekir:

- Proje içeriği düzenlemek için proje klasörleri ekleme özelliği desteği

- Proje kalıcılığı için tutarlı bir modeli koru

  Projeleri için tutarlı etkileşim modelleri de korumanız gerekir:

- Proje öğeleri kaldırma

- Belgeleri kaydetme

- Proje özelliğini düzenleme

- Alternatif bir görünümü'nde projeye düzenleme

- Sürükle ve bırak işlemleri

### <a name="drag-and-drop-interaction-model"></a>Sürükle ve bırak etkileşim modeli
 Projeleri genellikle sınıflandırmak (kalıcı depolama alanında proje öğeleri için yalnızca başvuruları mümkün), kendilerine başvuru tabanlı olarak dizin tabanlı (yalnızca proje öğelerinin fiziksel olarak kalıcı hale getirmek için saklı bir projenin hiyerarşisi içinde) ya da karma (başvurular kalıcı hale getirmek kullanabilirsiniz veya fiziksel öğeleri). IDE içinde aynı anda üç tür projeleri karşılar **Çözüm Gezgini**.

 Sürükle ve bırak açısından bakıldığında, aşağıdaki özelliklere her türde bir proje içinde uygulanması gereken **Çözüm Gezgini**:

- **Proje başvurusu tabanlı:** anahtar projenin'ın depolama alanındaki bir öğeye bir başvuru geçici olarak sürükleyerek noktasıdır. Başvuru-tabanlı bir proje bir taşıma işlemi için bir kaynak olarak davranırken, yalnızca proje öğesine başvuruyu kaldırmanız gerekir. Öğe sabit sürücüden gerçekten silinmemelidir. Başvuru-tabanlı bir proje taşıma (veya kopyalama) işlemi için hedef olarak davranırken, özgün kaynak öğeye bir başvuru öğesinin özel bir kopyasını yapmadan eklemelisiniz.

- **Dizin tabanlı proje:** bir Sürükle ve bırak açısından bakıldığında, proje başvurusu yerine fiziksel öğenin sürüklemekte olduğu. Dizin tabanlı bir proje için bir taşıma işlemi kaynağı olarak davranırken sabit sürücüyü fiziksel silmenizi yanı sıra projeden kaldırma yukarı bitmelidir. Dizin tabanlı bir proje taşıma (veya kopyalama) işlemi için hedef olarak davranırken, hedef konumunda kaynak öğenin bir kopyasını olmanız gerekir.

- **Karma hedef proje:** doğasını (depolama alanındaki bir öğeye bir başvuru) ya da öğe sürüklenen öğe üzerinde bir Sürükle ve bırak açısından bakıldığında, bu tür bir proje davranışını temel alır. Başvurular ve fiziksel öğeleri için doğru davranışı üzerinde açıklanmıştır.

  Projesinde yalnızca bir tür varsa **Çözüm Gezgini**, sürükle ve bırak işlemleri basit olabilir. Her proje sistemi kendi sürükle-bırak davranışı tanımlama yeteneği olduğundan, tahmin edilebilir bir kullanıcı deneyimi sağlamak için (Windows Explorer sürükle-bırak davranışı göre) belirli yönergeleri izlenmesi gerekir:

- Değiştirilmemiş bir sürükleme işlemi **Çözüm Gezgini** (ne zaman Ctrl ya da SHIFT tuşlarını tutulan), bir taşıma işlemi neden olur.

- Shift-sürükleme işlemi aynı zamanda bir taşıma işlemi neden olur.

- CTRL tuşunu işlemi, bir kopyalama işleminde neden olur.

- Başvuru tabanlı ve karma proje sistemleri kaynak öğesine bir bağlantı (veya başvuru) ekleme kavramını destekler. Bu projeler, bir Sürükle ve bırak işleminin hedef olduğunda (zaman **Ctrl + Shift** basılı tutularak), projeye eklenen öğeye bir başvuru neden

  Tüm sürükle ve bırak işlemleri tabanlı başvurusu, dizin tabanlı ve karma projeleri arasında mantıklı birleşimleridir. Özellikle, taşıma tamamlandıktan sonra kaynak öğeyi silmek kaynak dizin tabanlı proje sahip olacağından bir directory tabanlı kaynak ve hedef başvuru tabanlı proje arasında taşıma işlemi izin vermek anlatabilirsiniz sorunlu. Hedef tabanlı başvurusu proje ardından silinmiş bir öğeyi başvurusuyla sonunda.

  Hedef projeye başvuru tabanlı kaynak öğenin bir bağımsız kopyası yapmaması gerekir çünkü bu proje türleri arasında bir kopyalama işlemine izin vermek anlatabilirsiniz yanıltıcıdır. Bir dizin tabanlı proje başvuruları kalıcı hale getirmek kuramadığı benzer şekilde, Ctrl + Üst karakter için bir hedef dizin tabanlı proje sürükleyerek izin verilmemesi. Sürükle ve bırak işlemi desteklenmediği durumlarda, IDE açılan izin vermeyin ve kullanıcı (işaretçi tabloda gösterilen) bırakma imleç görünmesi gerekir.

  Sürükle ve bırak davranışı düzgün bir şekilde uygulamak için sürükleme kaynağı projenin doğası iletişim kurması gereken (örneğin, başvuru veya dizin tabanlı olduğu?) hedef projeye. Bu bilgiler, kaynak tarafından sunulan Pano biçimi ile belirtilir. Bir sürükleme (veya Pano kopyalama işlemi) kaynak olarak bir proje ya da sunmalıdır **CF_VSREFPROJECTITEM**S veya **CF_VSSTGPROJECTITEMS** sırasıyla proje başvurusu tabanlı olup olmamasına bağlı olarak ya da dizin tabanlı. Bu biçimler her ikisi de Windows için benzerdir aynı veri içeriğe sahip **CF_HDROP** listeleri dosya adları olan yerine dize, çift - şeylerdir biçimlendirme**NULL** listesisonlandırıldı **Projref** dizeleri (döndürülen **IVsSolution::GetProjrefOfItem** veya **:: GetProjrefOfProject** uygun şekilde).

  Bir bırakma (veya Pano Yapıştırma işlemi) ve hedef olarak bir proje her ikisini de kabul etmelidir **CF_VSREFPROJECTITEMS** ve **CF_VSSTGPROJECTITEMS**, sürükle ve bırak işlemi tam işleme değişir ancak hedef proje ve kaynak proje doğasına bağlı olarak. Kaynak projenin doğası tarafından sunduğu olup olmadığını bildirir **CF_VSREFPROJECTITEMS** veya **CF_VSSTGPROJECTITEMS**. Bırakma hedefi kendi yapısı anlar ve bu nedenle bir taşıma, kopyalama olmadığını olarak kararlar için yeterli bilgiye sahip ya da bağlantı gerçekleştirilmelidir. Kullanıcı ayrıca Ctrl, SHIFT, veya hem Ctrl ve Shift tuşlarını tuşlarına basarak sürükle ve bırak işlemi gerçekleştirilmesi gereken değiştirir. Bırakma hedefi için hangi işlem önceden de gerçekleştirilmeyecek düzgün bir şekilde belirtmek önemlidir, **DragEnter** ve **DragOver** yöntemleri. **Çözüm Gezgini** kaynak ve hedef projeye aynı projede olup olmadığını otomatik olarak bilir.

  Proje öğeleri (örneğin, bir örnekten diğerine Devenv.exe) Visual Studio örneği üzerinde sürükleyerek özellikle olmayan desteklenmiyor. **Çözüm Gezgini** doğrudan bu devre dışı bırakır.

  Kullanıcının her zaman bir öğenin seçilmesi, hedef konuma sürükleyerek ve öğe kesilmeden önce aşağıdaki fare işaretçileri görünen gözleme bir Sürükle ve bırak işlemi etkisini belirlemek mümkün olması gerekir:

|Fare işaretçisi|Komut|Açıklama|
|-------------------|-------------|-----------------|
|!["Bırakma yok" simgesi fare](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706 01_MouseNoDrop")|Hiçbir bırakma|Öğe belirtilen konuma bırakılamaz.|
|![Fare "Kopyala" simgesini](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706 02_MouseCopy")|Kopyala|Öğesi, hedef konuma kopyalanacak.|
|![Fare "taşıma" simgesi](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706 03_MouseMove")|Taşıma|Öğesi, hedef konuma taşınır.|
|![Fare "Başvuru Ekle" simgesi](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706 04_MouseAddRef")|Başvuru ekleme|Hedef konum için seçili öğeye bir başvuru eklenir.|

#### <a name="reference-based-projects"></a>Başvuru tabanlı projeler
 Aşağıdaki tabloda, hedef başvurulan tabanlı projeler için basılan kaynak öğesi ve değiştirici tuşları yapısına göre gerçekleştirilmelidir sürükle ve bırak (yanı sıra Kes/kopyala/yapıştır) işlemleri özetlenmektedir:

|||Kaynak öğe: başvuru/bağlantı|Kaynak öğe: fiziksel öğe veya dosya sistemi (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Herhangi bir değiştiricisi|Eylem|Taşıma|Bağlantı|
|Herhangi bir değiştiricisi|Hedef|Özgün öğe başvurusu ekler|Özgün öğe başvurusu ekler|
|Herhangi bir değiştiricisi|Kaynak|Özgün öğeye başvuru siler|Özgün öğeye korur|
|Herhangi bir değiştiricisi|Sonuç|**DROPEFFECT_MOVE** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_LINK** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|Shift + sürükleme|Eylem|Taşıma|Hiçbir bırakma|
|Shift + sürükleme|Hedef|Özgün öğe başvurusu ekler|Hiçbir bırakma|
|Shift + sürükleme|Kaynak|Özgün öğeye başvuru siler|Hiçbir bırakma|
|Shift + sürükleme|Sonuç|**DROPEFFECT_MOVE** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|Hiçbir bırakma|
|CTRL + sürükle|Eylem|Kopyala|Hiçbir bırakma|
|CTRL + sürükle|Hedef|Özgün öğe başvurusu ekler|Hiçbir bırakma|
|CTRL + sürükle|Kaynak|Özgün öğeye başvuru korur|Hiçbir bırakma|
|CTRL + sürükle|Sonuç|**DROPEFFECT_COPY** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|Hiçbir bırakma|
|Ctrl + Shift + sürükleme|Eylem|Bağlantı|Bağlantı|
|Ctrl + Shift + sürükleme|Hedef|Özgün öğe başvurusu ekler|Özgün öğe başvurusu ekler|
|Ctrl + Shift + sürükleme|Kaynak|Özgün öğeye başvuru korur|Özgün öğeye korur|
|Ctrl + Shift + sürükleme|Sonuç|**DROPEFFECT_LINK** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_LINK** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|Ctrl + Shift + sürükleme|Not|Windows Gezgini'nde kısayolları sürükle-bırak davranışı ile aynıdır.||
|Kes/Yapıştır|Eylem|Taşıma|Bağlantı|
|Kes/Yapıştır|Hedef|Özgün öğe başvurusu ekler|Özgün öğe başvurusu ekler|
|Kes/Yapıştır|Kaynak|Özgün öğeye başvuru korur|Özgün öğeye korur|
|Kes/Yapıştır|Sonuç|Özgün konumda depolama öğesi kalır.|Özgün konumda depolama öğesi kalır.|
|Kopyala/Yapıştır|Eylem|Kopyala|Bağlantı|
|Kopyala/Yapıştır|Kaynak|Özgün öğe başvurusu ekler|Özgün öğe başvurusu ekler|
|Kopyala/Yapıştır|Sonuç|Özgün öğeye başvuru korur|Özgün öğeye korur|
|Kopyala/Yapıştır|Eylem|Özgün konumda depolama öğesi kalır.|Özgün konumda depolama öğesi kalır.|

#### <a name="directory-based-projects"></a>Dizin tabanlı projeler
 Aşağıdaki tabloda, hedef dizin tabanlı projeler için basılan kaynak öğesi ve değiştirici tuşları yapısına göre gerçekleştirilmelidir sürükle ve bırak (yanı sıra Kes/kopyala/yapıştır) işlemleri özetlenmektedir:

|||Kaynak öğe: başvuru/bağlantı|Kaynak öğe: fiziksel öğe veya dosya sistemi (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Herhangi bir değiştiricisi|Eylem|Taşıma|Taşıma|
|Herhangi bir değiştiricisi|Hedef|Hedef konum öğesine kopyalar|Hedef konum öğesine kopyalar|
|Herhangi bir değiştiricisi|Kaynak|Özgün öğeye başvuru siler|Özgün öğeye başvuru siler|
|Herhangi bir değiştiricisi|Sonuç|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|Shift + sürükleme|Eylem|Taşıma|Taşıma|
|Shift + sürükleme|Hedef|Hedef konum öğesine kopyalar|Hedef konum öğesine kopyalar|
|Shift + sürükleme|Kaynak|Özgün öğeye başvuru siler|Özgün konumundan öğesini siler|
|Shift + sürükleme|Sonuç|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|CTRL + sürükle|Eylem|Kopyala|Kopyala|
|CTRL + sürükle|Hedef|Hedef konum öğesine kopyalar|Hedef konum öğesine kopyalar|
|CTRL + sürükle|Kaynak|Özgün öğeye başvuru korur|Özgün öğeye başvuru korur|
|CTRL + sürükle|Sonuç|**DROPEFFECT_ kopyalama** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ kopyalama** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|Ctrl + Shift + sürükleme||Hiçbir bırakma|Hiçbir bırakma|
|Kes/Yapıştır|Eylem|Taşıma|Taşıma|
|Kes/Yapıştır|Hedef|Hedef konum öğesine kopyalar|Hedef konum öğesine kopyalar|
|Kes/Yapıştır|Kaynak|Özgün öğeye başvuru siler|Özgün konumundan öğesini siler|
|Kes/Yapıştır|Sonuç|Özgün konumda depolama öğesi kalır.|Depolama özgün konumundan öğesi silindiğinde|
|Kopyala/Yapıştır|Eylem|Kopyala|Kopyala|
|Kopyala/Yapıştır|Hedef|Özgün öğe başvurusu ekler|Hedef konum öğesine kopyalar|
|Kopyala/Yapıştır|Kaynak|Özgün öğeye korur|Özgün öğeye korur|
|Kopyala/Yapıştır|Sonuç|Özgün konumda depolama öğesi kalır.|Öğe özgün konuma bileşenler depolama alanında kalır|

#### <a name="mixed-target-projects"></a>Karma hedef projeleri
 Aşağıdaki tabloda, karma hedef projeler için basılan kaynak öğesi ve değiştirici tuşları yapısını temel gerçekleştirilmelidir sürükle ve bırak (yanı sıra Kes/kopyala/yapıştır) işlemleri özetlenmektedir:

|||Kaynak öğe: başvuru/bağlantı|Kaynak öğe: fiziksel öğe veya dosya sistemi (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Herhangi bir değiştiricisi|Eylem|Taşıma|Taşıma|
|Herhangi bir değiştiricisi|Hedef|Özgün öğe başvurusu ekler|Hedef konum öğesine kopyalar|
|Herhangi bir değiştiricisi|Kaynak|Özgün öğeye başvuru siler|Özgün öğeye başvuru siler|
|Herhangi bir değiştiricisi|Sonuç|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve depolama özgün konumundan öğe silindi|
|Shift + sürükleme|Eylem|Taşıma|Taşıma|
|Shift + sürükleme|Hedef|Özgün öğe başvurusu ekler|Hedef konum öğesine kopyalar|
|Shift + sürükleme|Kaynak|Özgün öğeye başvuru siler|Özgün konumundan öğesini siler|
|Shift + sürükleme|Sonuç|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ TAŞIMA** eylem olarak döndürülür **:: bırak** ve depolama özgün konumundan öğe silindi|
|CTRL + sürükle|Eylem|Kopyala|Kopyala|
|CTRL + sürükle|Hedef|Özgün öğe başvurusu ekler|Hedef konum öğesine kopyalar|
|CTRL + sürükle|Kaynak|Özgün öğeye başvuru korur|Özgün öğeye korur|
|CTRL + sürükle|Sonuç|**DROPEFFECT_ kopyalama** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ kopyalama** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|Ctrl + Shift + sürükleme|Eylem|Bağlantı|Bağlantı|
|Ctrl + Shift + sürükleme|Hedef|Özgün öğe başvurusu ekler|Özgün kaynak öğe başvurusu ekler|
|Ctrl + Shift + sürükleme|Kaynak|Özgün öğeye başvuru korur|Özgün öğeye korur|
|Ctrl + Shift + sürükleme|Sonuç|**DROPEFFECT_ bağlantı** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|**DROPEFFECT_ bağlantı** eylem olarak döndürülür **:: bırak** ve özgün konumda depolama öğesi kalır|
|Kes/Yapıştır|Eylem|Taşıma|Taşıma|
|Kes/Yapıştır|Hedef|Hedef konum öğesine kopyalar|Hedef konum öğesine kopyalar|
|Kes/Yapıştır|Kaynak|Özgün öğeye başvuru siler|Özgün konumundan öğesini siler|
|Kes/Yapıştır|Sonuç|Özgün konumda depolama öğesi kalır.|Depolama özgün konumundan öğesi silindiğinde|
|Kopyala/Yapıştır|Eylem|Kopyala|Kopyala|
|Kopyala/Yapıştır|Hedef|Özgün öğe başvurusu ekler|Hedef konum öğesine kopyalar|
|Kopyala/Yapıştır|Kaynak|Özgün öğeye korur|Özgün öğeye korur|
|Kopyala/Yapıştır|Sonuç|Özgün konumda depolama öğesi kalır.|Özgün konumda depolama öğesi kalır.|

 Bu ayrıntılar dikkate sürükleyerek uygularken dikkat edilmelidir **Çözüm Gezgini**:

- Çoklu seçim senaryolarına yönelik tasarım.

- Dosya adları (tam yolu) hedef projede benzersiz olmalıdır veya açılır izin.

- Klasör adları benzersiz olmalıdır (büyük küçük harf duyarsız) düzeyinde bunlar bırakılır.

- Açık veya kapalı (yukarıdaki senaryolarda geçmeyen) sürükleyin, zamanında dosyaları arasındaki davranış farklılıkları vardır.

- Üst düzey dosyaları klasörlerdeki dosyaları biraz daha farklı davranır.

  Dikkat edilmesi gereken başka bir taşıma işlemleri için bir açık Tasarımcı veya düzenleyici sahip öğeleri nasıl ele alınacağını sorunudur. Beklenen bir davranış (tüm proje türleri için geçerlidir) aşağıdaki gibidir:

1. Açık Düzenleyicisi/Tasarımcısı kaydedilmemiş değişiklikler yoksa Düzenleyicisi/Tasarımcı penceresinin sessizce kapatılmalıdır.

2. Açık Düzenleyicisi/Tasarımcısı Kaydedilmemiş değişiklikleriniz varsa, bu ardından sürükleme kaynağı görüntülemesini ve ardından kullanıcıdan aşağıdakine benzer bir isteme içeren pencereyi kapatmadan önce açık belgelerde kaydedilmemiş değişiklikleri kaydetmek için açılan için beklemesi gereken :

   ```
   ==========================================================
        One or more open documents have unsaved changes.
   Do you want to save uncommitted changes before proceeding?
                     [Yes]  [No]  [Cancel]
   ==========================================================
   ```

   Bu kullanıcı, kopya hedef kolaylaştırır önce süren kaydetme fırsatı verir. Yeni bir yöntem **IVsHierarchyDropDataSource2::OnBeforeDropNotify** bu işlemesini etkinleştirmek için eklendi.

   Depolama alanında olduğu gibi hedef ardından öğesinin durumu kopyalayın (kullanıcı seçerseniz kaydedilmemiş değişiklikler düzenleyicide içermeden **Hayır**). Hedef, kopyalama tamamlandıktan sonra (içinde **IVsHierarchyDropDataSource::Drop**), kaynak taşıma işlemi silme bölümünü tamamlamak için fırsatı verilir (içinde **IVsHierarchyDropDataSource::O nDropNotify**).

   Tüm düzenleyicileri kaydedilmemiş değişikliklerle açık bırakılmalıdır. Kaydedilmemiş değişiklikler ile belgeler için tuşların Bu taşıma işlemi kopyalama kısmı gerçekleştirilir, ancak silme bölümü durdurulacak anlamına gelir. Kullanıcı seçtiğinde birden fazla seçim senaryosunda **Hayır**, kaydedilmemiş değişiklikler bu belgelerle kapalı kaldırıldı veya değiştirilmemesi gereken ancak kaydedilmemiş değişiklikler olmayanlar kapalı ve kaldırılması.
