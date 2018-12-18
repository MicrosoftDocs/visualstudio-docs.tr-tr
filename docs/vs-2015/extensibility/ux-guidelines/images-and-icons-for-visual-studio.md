---
title: Görüntüler ve Simgeler
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 171de18bc4a9a790488b28c2c50c53c5c2ee05e6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068574"
---
# <a name="images-and-icons-for-visual-studio"></a>Görüntüler ve Visual Studio için simgeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_ImageUseInVisualStudio"></a> Visual Studio görüntü kullanımda
 Yapma resmi oluşturmadan önce göz önünde bulundurun 1000'den fazla görüntüde kullanımını [Visual Studio görüntü kitaplığı](http://www.microsoft.com/en-my/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Görüntü türleri

-   **Simgeler**. Komutlar, hiyerarşileri, şablon ve benzeri görünen küçük resimler. Visual Studio'da kullanılan varsayılan simge boyutu 16 x 16 PNG ' dir. Görüntü hizmeti tarafından otomatik olarak üretilen simgeler HDPI desteği için XAML biçiminde oluşturun.

     **Not:** görüntüleri menü sisteminde kullanılırken, her komut için bir simge oluşturmamalısınız. Başvurun [menüler ve komutlar için Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) Komutunuz bir simge almalısınız görmek için.

-   **Küçük resim.** Yeni Proje iletişim kutusu gibi bir iletişim kutusu Önizleme bölümünde kullanılan görüntüler.

-   **İletişim kutusu görüntüler.** Görünen iletişim kutuları veya sihirbazlar, açıklayıcı bir grafik veya ileti göstergeleri olarak görüntüler. Seyrek ve zor bir konsepti açıklamak veya kullanıcının dikkatini (uyarı, uyarı) elde etmek için yalnızca gerekli olduğunda kullanın.

-   **Animasyonlu görüntüler.** İlerleme göstergesi, durum çubukları ve işlem iletişim kutuları kullanılır.

-   **İmleç.** Burada bir nesne bırakılabilir vb. fareyi kullanarak bir işlem izin verilip verilmeyeceğini belirtmek için kullanılır.

##  <a name="BKMK_IconDesign"></a> Simge tasarım

### <a name="overview"></a>Genel Bakış
 Visual Studio temiz geometri ve olumlu/olumsuz (Açık/Koyu) 50/50 dengesi ve doğrudan, anlaşılır metaphors kullanan modern stili simgeleri kullanır. Anlaşılabilir olması adına, basitleştirme ve bağlam önemli simgesi tasarım noktaları Merkezi.

- **Anlaşılabilir olması adına:** bireyselliğinizi ve anlamı bir simge sağlayan çekirdek benzetimini odaklanın.

- **Basitleştirme:** simgesi çekirdek anlamını azaltmak – yalnızca gerekli öğe ve hiçbir frills temayı alın.

- **Bağlam:** simgesinin çekirdek benzetimini hangi öğelerin oluşturan verirken önemli kavram geliştirme sırasında bir simgenin rolü tüm yönlerini göz önünde bulundurun.

  Simgeler ile birkaç önlemek için tasarım noktaları vardır:

- Uygun olduğunda kullanıcı Arabirimi öğeleri hariç geldiğiniz simgeler kullanmayın. Kullanıcı Arabirimi öğesi ne ortak, yetkisiz değiştirmeye karşı korumalı veya benzersiz değil daha soyut veya sembolik bir yaklaşım belirleyin.

- Belgeler, klasörleri, oklar ve Büyüteç gibi sık kullanılan öğeleri aşırı yok. Bu öğeler simgenin anlamı için yalnızca gerekli olduğunda kullanın. Örneğin, sağ taraftaki Büyüteç yalnızca arama belirtmelidir göz atın ve bulun.

- Bazı eski simge öğeleri perspektif kullanımını korumak olsa da, yeni simgeler olmadan netlik öğesi eksik sürece perspektif ile oluşturmayın.

- Çok fazla simge bilgileri borçlarını yok. Kolayca tanınan veya tanınabilir bir sembol öğrenilen basit bir görüntü çok daha fazla karmaşık bir görüntüden daha kullanışlıdır. Yazının tamamını bir simge bildiremez.

### <a name="icon-creation"></a>Simge oluşturma

#### <a name="concept-development"></a>Kavram geliştirme
 Visual Studio içinde kullanıcı Arabirimi çok çeşitli simge türü vardır. Dikkatli bir şekilde geliştirme sırasında simge türünü göz önünde bulundurun. Belirsiz veya seyrek UI nesneleri simgesi öğeleriniz için kullanmayın. Bu gibi durumlarda, sembolik gibi akıllı etiket simgesiyle tercih. Sol taraftaki soyut etiketin anlamını sağdaki belirsiz, kullanıcı Arabirimi tabanlı sürümden daha belirgin olduğuna dikkat edin:

|||
|-|-|
|**Sembolik tanımayı doğru kullanımı**|**Sembolik tanımayı yanlış kullanımı**|
|![Doğru akıllı etiket simgesi](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404 01_SmartTagCorrect")|![Yanlış akıllı etiket simgesi](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404 02_SmartTagIncorrect")|

 Standart, kolayca tanınabilir kullanıcı Arabirimi öğeleri de simgelerini iş örnekler vardır. Bu tür bir örnek penceredir ekleyin:

|||
|-|-|
|**Bir simge doğru kullanıcı Arabirimi öğesi**|**Bir simge yanlış kullanıcı Arabirimi öğesi**|
|![Doğru pencere Ekle simgesi](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404 03_AddWindowCorrect")|![Yanlış pencere Ekle simgesi](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404 04_AddWindowIncorrect")|

 Simgenin bir anlamı gerekli olmadıkça temel bir öğe bir belge kullanmayın. Belge öğesi ile yenileme anlamına iletişim kurmak gereksiz iken belge ekleme belge öğesinde (aşağıda) anlamı, kaybolur.

|||
|-|-|
|**Belge simgesi doğru kullanımı**|**Belge simgesini yanlış kullanımı**|
|![Doğru belge simgesi](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404 05_DocumentIconCorrect")|![Yanlış belge simgesi](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404 06_DocumentIconIncorrect")|

 "Show" kavramını simgesiyle en iyi ne gösterilir, gibi tüm dosyaları göster örnek olarak gösterilmiştir temsil edilebilir. Bir mercek benzetme, "Görünüm" gibi gerekiyorsa, kaynak görünümü örnek kavramını göstermek için kullanılabilir.

|||
|-|-|
|**"Show"**|**"View"**|
|![Simgesini göster](../../extensibility/ux-guidelines/media/0404-07-show.png "0404 07_Show")|![Görünümü simgesi](../../extensibility/ux-guidelines/media/0404-08-view.png "0404 08_View")|

 Sağ taraftaki temsil yalnızca arayacağı cam simgesi büyütme, bulma ve göz atma. Sol taraftaki türevi artı veya eksi işareti, yalnızca yakınlaştırma temsil / Uzaklaştır.

|||
|-|-|
|**"Arama"**|**"Yakınlaştırma"**|
|![Arama simgesine](../../extensibility/ux-guidelines/media/0404-09-search.png "0404 09_Search")|![Yakınlaştır simgesi](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404 10_Zoom")|

 Ağaç görünümleri klasör simgesini hem bir değiştiricisini kullanmayın. Kullanılabilir olduğunda, yalnızca değiştiricisini kullanın.

|||
|-|-|
|**Doğru ağaç görünümü simgeleri**|**Yanlış ağaç görünümü simgeleri**|
|![Doğru ağaç görünümü simgesi &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![doğru ağaç görünümü simgesi &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Yanlış ağaç görünümü simgesi &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![yanlış ağaç görünümü simgesi &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404 14_ TreeViewIncorrect2")|

### <a name="style-details"></a>Stil ayrıntıları

#### <a name="layout"></a>Düzen
 Standart 16 x 16 simgelerini gösterildiği gibi yığın öğeleri:

 ![Düzen yığını için 16 x 16 simgeler](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404 15_LayoutStack")

 **16 x 16 simgeler için yığın düzeni**

 Durum bildirim öğeleri daha iyi tek başına simgeler kullanılır. İçinde bir bildirim temel öğe üzerinde gibi görev tamamlanma simgesiyle Yığılmış bağlamları vardır:

 ![Visual Studio'da tek başına bildirimi](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")

 **Tek başına bildirimi simgeleri**

 ![Görev tamamlandı simgesi](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404 17_TaskComplete")

 **Görev tamamlandı simgesi**

 Proje simgeleri genellikle birden fazla boyut içeren .ico dosyalarıdır. Çoğu 16 x 16 simge aynı öğeleri içeriyor. Uygun olduğunda proje türü de dahil olmak üzere daha fazla ayrıntı 32 x 32 sürümlere sahip.

 ![Proje Visual Studio'da simgeler](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")

 **VB Windows Denetim Kitaplığı projesini simgeler, 16 x 16 ve 32 x 32**

 Simge, piksel kare içinde ortalayın. Bu mümkün değilse, üst ve/veya çerçevenin sağında simgesi hizalayın.

 ![Piksel kare içinde ortalanmış simgesi](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404 19_IconCentered")

 **Piksel kare içinde ortalanmış simgesi**

 ![Hizalanan simgesi sağ üst köşesinde piksel kare](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404 20_IconTopRight")

 **Simge en üstüne hizalanmış çerçevenin sağ**

 ![Simge Ortalanan ve piksel kare üstüne hizalanmış](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404 21_IconTopAlign")

 **Orta ve çerçeve üstüne hizalanmış simgesi**

 İdeal hizalama ve dengeyi elde etmek için simgenin temel öğe eylem karakterleri ile engellemekte kaçının. Temel öğesinin üstüne yakın bir karakter sola yerleştir. Ek bir öğe eklerken, hizalama ve simge dengesini göz önünde bulundurun.

|||
|-|-|
|**Doğru hizalama ve dengeleyin**|**Yanlış hizalama ve dengeleyin**|
|![Doğru simge bakiyesi ve hizalama](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![Yanlış simgesi bakiyenizi ve hizalama](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|

 Öğe paylaştırmak ve kümelerinde kullanılan simge için boyut eşlik emin olun. Yanlış eşleştirme, daire ve ok büyük boyutlu olduğunu unutmayın ve eşleşmiyor.

|||
|-|-|
|**Doğru boyutta eşlik**|**Hatalı boyut eşlik**|
|![Doğru simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404 24_SizeParityCorrect")|![Yanlış bir simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404 25_SizeParityIncorrect")|

 Tutarlı satır ve görsel ağırlıkları kullanın. Nasıl bir yan yana karşılaştırmayı kullanarak oluşturmakta olduğunuz simgesi diğer simgeye karşılaştırır değerlendirin. Hiçbir zaman tüm 16 x 16 çerçeveyi kullanın, 15 x 15 veya daha küçük. Negatif pozitif (Koyu ışık) oranı 50/50 olmalıdır.

|||
|-|-|
|**Doğru negatif ve pozitif sonuç oranı**|**Hatalı negatif ve pozitif sonuç oranı**|
|![Düzeltmek için simgeler visual ağırlığı &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![Düzeltmek için simgeler visual ağırlığı &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![Düzeltmek için simgeler visual ağırlığı &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![Simgeler için yanlış visual ağırlık](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404 29_VisualWeightIncorrect")|

 Basit, karşılaştırılabilir şekiller ve Tamamlayıcı açıları öğesi bütünlüğü ödün vermeden, öğeleri oluşturmak için kullanın. 45 derecenin veya 90 ° açıları mümkün olduğunca kullanın.

 ![Simge açıları düzeltmek](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404 30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektif
 Açık ve anlaşılır simgesi tutun. Perspektif ve yalnızca gerekli olduğunda bir ışık kaynağı kullanın. Simge öğelerde perspektifini kullanarak kaçınılmalıdır olsa da, bazı öğeler olmadan tanınmayan bağlıdır. Böyle durumlarda, öğenin netlik stilize perspektif iletişim kurar.

 ![3&#45;noktası perspektifini](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404 31_3PointPerspective")

 **3-nokta perspektifi**

 ![1&#45;noktası perspektifini](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404 32_1PointPerspective")

 **1-nokta perspektifi**

 Öğelerin çoğu, karşılıklı veya sağ açılı.

 ![Simge sağ açılı](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404 33_AngledRight")

 Işık kaynağı, yalnızca gerekli netlik nesneye eklerken kullanın.

|||
|-|-|
|**Doğru açık kaynak**|**Yanlış açık kaynak**|
|![Düzeltmek için simgeler ışık kaynaklarına](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![Simgeler için yanlış ışık kaynaklarına](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|

 Anahatları yalnızca okunabilirliği geliştirmek veya benzetimini daha iyi iletişim kurmak için kullanın. Negatif pozitif (dark-light) Bakiye 50/50 olmalıdır.

|||
|-|-|
|**Anahatları doğru kullanımı**|**Anahatları yanlış kullanımı**|
|![Anahatları düzeltmek](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404 36_OutlinesCorrect")|![Yanlış anahatları](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404 37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Simge türü
 **Kabuğu ve komut çubuğu** simgeler en fazla üç aşağıdaki öğelerden oluşur: bir temel, bir değiştiricisi, bir eylem veya bir durum.

 ![Kabuğu ve komut çubuğu simgeler](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404 38_ShellIcons")

 **Kabuk ve simge çubuğu komut örnekleri**

 **Araç penceresini komut çubuğu** simgeler en fazla üç aşağıdaki öğelerden oluşur: bir temel, bir değiştiricisi, bir eylem veya bir durum.

 ![Araç penceresini komut çubuğu simgeleri](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")

 **Araç penceresini komut çubuğu simgelerinin örnekleri**

 **Ağaç görünümü disambiguator** simgeler en fazla üç aşağıdaki öğelerden oluşur: bir temel, bir değiştiricisi, bir eylem veya bir durum.

 ![Ağaç görünümü disambiguator simgeler](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404 40_TreeViewIcons")

 **Ağaç örnekleri disambiguator simgeler görüntüleme**

 **Durum tabanlı değer sınıflandırma** simgeler aşağıdaki durumlarda var: etkin, devre dışı etkin ve etkin olmayan devre dışı bırakıldı.

 ![Durum&#45;tabanlı sınıflandırma değeri simgeler](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")

 **Durum tabanlı değer sınıflandırma simgeler örnekleri**

 **IntelliSense** simgeler en fazla üç aşağıdaki öğelerden oluşur: bir temel bir değiştirici ve bir durum.

 ![IntelliSense simgeler](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404 42_IntelliSenseIcons")

 **IntelliSense simgeler örnekleri**

 **Küçük (16 x 16) proje** simgeler, ikiden fazla öğe olmalıdır: bir temel ve bir değiştirici.

 ![16 x 16 proje simgesi &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404 43_16x16Project1") ![16 x 16 proje simgesi &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404 44_16x16Project2") ![16 x 16 proje simgesi &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404 45_16x16Project3")

 **Küçük (16 x 16) proje simgeleri örnekleri**

 **Büyük (32 x 32) projenin** simgeler en fazla dört aşağıdaki öğelerden oluşur: bir temel, bir ila iki değiştiriciler ve yardımcı bir dili.

 ![32 x 32 proje simgeleri](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404 46_32x32Project")

 **Büyük (32 x 32) proje simgeleri örnekleri**

### <a name="production-details"></a>Üretim ayrıntıları
 Windows Presentation Foundation (WPF) kullanarak tüm yeni kullanıcı Arabirimi öğeleri oluşturulmalı ve tüm yeni simgeleri WPF için 32-bit PNG biçiminde olmalıdır. 24 bit PNG, saydamlık desteklemiyor ve bu nedenle simgelerini önerilmez eski bir biçimidir.

 96 DPI çözünürlüğü kaydedin.

#### <a name="file-types"></a>Dosya türleri

-   **32-bit PNG:** simgeler için tercih edilen biçimi. Bir tek tarama (piksel) görüntüsü depolayabilirsiniz kayıpsız veri sıkıştırma dosya biçimi. alfa kanalı saydamlık, gama düzeltmesi ve titreşimli 32-bit PNG dosyalarını destekler.

-   **32-bit BMP:** olmayan WPF denetimleri için. Ayrıca XP ya da yüksek renk, 32-bit BMP bir alfa kanalı saydamlık rengi true görüntüsüyle bir RGB/bir görüntü biçimi çağırılır. Alfa kanalını bir bit eşlem (Dördüncü) bir ek olarak içinde kaydedildiği Adobe Photoshop belirtilen saydamlık katmanıdır renk kanalı. Siyah arka plan renk derinliği hakkında hızlı görsel bir ipucu sağlamak için tüm dosyalara 32-bit BMP resmi üretim sırasında eklenir. Bu siyah arka plan kullanıcı Arabiriminde kullanıma gizlenmeye alanını temsil eder.

-   **32-bit ICO:** proje simgeleri ve öğe ekleyin. 32-bit gerçek renk saydam alfa kanalı ile tüm ICO dosyalardır (RGB/A). Birden çok boyut ve renk derinliği ICO dosyalarını depolayabileceğiniz için Vista simgeleri genellikle 16 x 16, 32 x 32, 48 x 48 ve 256 x 256 boyutundaki resim boyutları içeren bir ICO biçimindedir. Windows Gezgini'nde düzgün görüntülenmesi için ICO dosyaları kaydedilen her görüntü boyutu için 24-bit ve 8-bit renk derinliği için aşağı gerekir.

-   **XAML:** tasarım yüzeyleriyle ve Windows donatıcıları. XAML, ölçeklendirme ve döndürme, dosyalama ve saydamlık destek vektör tabanlı görüntü dosyaları simgelerdir. Bunlar, bugün Visual Studio'da ortak değildir ancak kendi esnekliğinde nedeniyle daha yaygın hale gelmektedir.

-   **SVG**

-   **24 bit BMP:** Visual Studio komut çubuğu için. True-renk RGB görüntü biçimi, 24 bit BMP knock genişletme saydamlık katman için renk anahtar olarak Eflatun (R = 255, G = 0, B = 255) kullanarak bir katman saydamlığın örneklerinden biri oluşturur simgesi kuralıdır. İçinde 24 bit BMP, tüm pembe yüzey arka plan rengiyle görüntülenir.

-   **24 bit GIF:** Visual Studio komut çubuğu için. Saydamlığı destekleyen bir true renk RGB görüntü biçimi. GIF dosyaları, genellikle Sihirbazı resmi ve GIF animasyonları kullanılır.

### <a name="icon-construction"></a>Simge oluşturma
 Visual Studio'da küçük simge boyutu 16 x 16'dır. En büyük ortak 32 x 32 kullanılır. Tüm 16 x 16, 24 x 24 veya 32 x 32 çerçevesi simge tasarlarken değil doldurmaya göz önünde bulundurun. Kullanıcı tanımayı okunaklı ve Tekdüzen bir simge oluşturma gereklidir. Aşağıdaki noktalara simgeler derlerken uyar.

- Simgeler, NET, anlaşılır ve tutarlı olması gerekir.

- Durum bildirim öğeleri tek simgeler olarak kullanın ve bunları yığın üzerine bir simge temel öğe değil için iyidir. Belirli bağlamlarda Bu, temel bir öğe ile eşleştirmeye durum öğesi kullanıcı Arabirimi gerektirebilir.

- Proje simgeleri genellikle, çeşitli boyutlarda içeren .ico dosyalardır. Yalnızca 16 x 16, 24 x 24 ve 32 x 32 simgeler güncelleştiriliyor. Çoğu 16 x 16 ve 24 x 24 simgeleri aynı öğeleri içerir. 32 x 32 simgeler, uygun olduğunda proje dil türü de dahil olmak üzere daha fazla ayrıntı içerir.

- 32 x 32 simgelerini temel öğeler, genellikle 2-piksel çizgi kalınlığı sahiptir. 1 veya 2 piksel çizgi kalınlığı ayrıntı öğeler için kullanılabilir. Sağduyunuzu en iyi, daha uygun olduğunu belirlemek için kullanın.

- En az 1 piksel aralığı 24 x 24 simgeler ile öğeler için 16 x 16 arasındaki vardır. 2-piksel aralığı ve değiştiricisi ile temel öğe öğeleri arasındaki 32 x 32 simgelerini kullanın.

  ![Öğe aralığı için 16 x 16, 24 x 24 ve 32 x 32 bir simge](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404 47_ElementSpacing")

  **Öğe aralığı simgeler için 16 x 16, 24 x 24 ve 32 x 32 boyutu**

#### <a name="color-and-accessibility"></a>Renk ve erişilebilirlik
 Visual Studio uyumluluk yönergelerine üründeki tüm simgeleri renk ve karşıtlık erişilebilirlik gereksinimleri geçmesi gerekir. Bu simge tersine çevirme sağlanır ve tasarlarken, bunlar program aracılığıyla ürününde çevrilmemesi farkında olmalıdır.

 Visual Studio simgeleri renk kullanarak daha fazla bilgi için bkz: [görüntülerde rengiyle](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

##  <a name="BKMK_UsingColorInImages"></a> Renk görüntülerini kullanma

### <a name="overview"></a>Genel Bakış
 Visual Studio'da simgeler öncelikle tek renkli. Renk belirli bilgileri iletmek için ayrılmıştır ve düzenlemesi için hiçbir zaman. Renk kullanılır:

-   bir eylem belirtmek için

-   durum bildirimi için kullanıcıyı uyarmak için

-   Dil ilişkisi atamak için

-   IntelliSense içinde öğeleri ayırmak için

### <a name="accessibility"></a>Erişilebilirlik
 Visual Studio uyumluluk kuralları, tüm simgeleri renk ve karşıtlık erişilebilirlik gereksinimleri ürün geçişinde işaretli gerektirir. Görsel dil palet renkleri edilmiş ve bu gereksinimleri karşılar.

#### <a name="color-inversion-for-dark-themes"></a>Koyu tema için renk ters çevirme
 Simgeler ile Visual Studio koyu tema doğru Karşıtlık oranı görünür yapmak için bir ters çevirmeyi program aracılığıyla uygulanır. Böylece doğru ters bu kılavuzdaki renkleri kısmen seçildi. Renk kullanımını kısıtlamak için bu paletin veya tersine çevirme uygulandığında öngörülemeyen sonuçlara alırsınız.

 ![Renkleri ters simgeler örnekleri](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405 01_DarkThemeInversion")

 **Ters renklerinin çalıştırılmış simgeler örnekleri**

### <a name="base-palette"></a>Temel palet
 Tüm standart simgeleri üç temel renk içerir. Simgeleri içeren hiçbir gradyanlar veya 3B aracı simgeleri için bir veya iki özel durum ile gölgeler.

|Kullanım|Ad|Değer (açık tema)|Renk örneği|Örnek|
|-----------|----------|---------------------------|------------|-------------|
|Arka plan/koyu|VS BG|424242 / 66,66,66|![Renk örneği 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Temel palet örnek](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405 02_BasePaletteExample")|
|Ön plan/hafif|VS FG|F0EFF1 / 240,239,241|![Renk örneği F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|Anahat|VS çıkış|F6F6F6 / 246,246,246|![Renk örneği F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 Ek olarak temel renkler, her bir simgeyi genişletilmiş paletinden bir ek renk içerebilir.

### <a name="extended-palette"></a>Genişletilmiş paleti

#### <a name="action-modifiers"></a>Eylem Değiştiriciler
 Aşağıdaki dört renkleri tarafından eylem değiştiricileri gerekli eylemleri türlerini gösterir:

|Kullanım|Ad|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|Pozitif|VS eylem yeşil|388A34 / 56,138,52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Negatif|VS eylem kırmızı|A1260D / 161,38,13|![Renk örneği A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|Nötr|VS eylem mavi|00539C / 0,83,156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|/ Yeni Oluştur|VS eylemin turuncu|C27D1A / 194,156,26|![Renk örneği C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Örnekler
 Yeşil "Ekle" gibi pozitif Eylem Değiştiriciler kullanılır "Çalıştırma," "Yürütme" ve "Doğrula."

|||||
|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405 03_ActionModifierRun") **çalıştırın**|![Yürütme sorgu simgesi](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405 04_ExecuteQuery") **sorguyu Yürüt**|![Tüm adımlar simgesinin play](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405 05_PlayAllSteps") **tüm adımları Yürüt**|![Denetim simgesi Ekle](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405 06_AddControl") **denetim Ekle**|

 Kırmızı kullanılan için negatif eylem değiştiricileri gibi "Silme," "Durdur", "İptal" ve "Kapat".

|||||
|-|-|-|-|
|![Sil simgesi ilişki](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405 07_DeleteRelationship") **ilişki Sil**|![Sil simgesi sütun](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405 08_DeleteColumn") **Sütun Sil**|![Sorgu simgesi durdurma](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405 09_StopQuery") **sorguyu durdur**|![Bağlantı çevrimdışı simgesi](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405 10_ConnectionOffline") **bağlantı çevrimdışı**|

 Mavi değiştiriciler en yaygın olarak oklar gibi ","İleri""Geri"Aç" temsil "İçeri Aktar" ve "Dışarı" nötr eylem uygulanır

|||||
|-|-|-|-|
|![Alan simgesi Git](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405 11_GoToField") **alanına gidin**|![Onay toplu&#45;simgesi](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405 12_BatchedCheckIn") **toplu iade**|![Adres Düzenleyicisi simgesinin](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405 13_AddressEditor") **adres Düzenleyicisi**|![İlişkilendirme Düzenleyicisi simgesi](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405 14_AssociationEditor") **ilişkilendirme Düzenleyicisi**|

 Koyu Altın öncelikle "Yeni" değiştiricisi için kullanılır.

|||||
|-|-|-|-|
|![Yeni Proje simgesi](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405 15_NewProject") **yeni proje**|![Oluştur yeni graf simgesi](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405 16_CreateNewGraph") **yeni grafik oluşturma**|![Yeni birim test simgesi](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405 17_NewUnitTest") **yeni birim testi**|![Yeni liste öğesi simgesi](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405 18_NewListItem") **yeni liste öğesi**|

#### <a name="special-cases"></a>Özel durumlar
 Özel durumlarda, renkli eylem değiştirici bağımsız olarak tek başına simgesi olarak kullanılabilir. Simge için kullanılan rengi simgesi ile ilişkili eylemler yansıtır. Bu simgeleri dahil olmak üzere, küçük bir kısmı sınırlıdır:

||||||
|-|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405 03_ActionModifierRun") **çalıştırın**|![Durdurma simgesi](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405 19_Stop") **Durdur**|![Sil simgesi](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405 20_Delete") **Sil**|![Kaydet simgesine](../../extensibility/ux-guidelines/media/0405-21-save.png "0405 21_Save") **Kaydet**|![Navigate geri simgesi](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405 22_NavigateBack") **geri gidin**|

### <a name="code-hierarchy-palette"></a>Kod hiyerarşi paleti

#### <a name="folder"></a>Klasör

|Kullanım|Ad|Değeri (tüm tema)|Renk örneği|Örnek|
|-----------|----------|--------------------------|------------|-------------|
|Klasörleri|Klasör|DCB67A / 220,182,122|![Renk örneği DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Klasör renk simgesi](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405 23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio dilleri
 Her birinin ortak dillerde veya platformlarda Visual Studio'da kullanılabilen, ilişkili bir renk olur. Bu renklerin temel simgesine veya bileşik simge sağ üst köşesinde görüntülenen dil değiştiriciler kullanılır.

|Kullanım|Ad|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF mavi|0095D 7 / 0,149,215|![Renk örneği 0095 D 7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP mor|9B4F96 / 155,79,150|![Renk örneği 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS yeşil (VS eylem yeşil)|388A34 / 56,138,52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|CSS kırmızı|BD1E2D / 189,30,45|![Renk örneği BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|FS mor|672878 / 103,40,120|![Renk örneği 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|JS turuncu|F16421 / 241,100,33|![Renk örneği F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|VB mavi (VS eylem mavi)|00539C / 0,83,156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|TS turuncu|E04C06 / 224,76,6|![Renk örneği E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|Kopyala yeşil|879636 / 135,150,54|![Renk örneği 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Dil değiştiriciler simgelerle örnekleri

|||||||
|-|-|-|-|-|-|
|![Visual Basic simgesi](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405 25_VB") **VB**|![C&#35; simgesi](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405 26_CSharp")**C#**|![C&#43; &#43; simgesi](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405 27_CPlusPlus") **C++**|![F&#35; simgesi](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405 28_FSharp")**F#**|![JavaScript simgesi](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405 29_JavaScript") **JavaScript**|![Python simgesi](../../extensibility/ux-guidelines/media/0405-30-python.png "0405 30_Python") **Python**|
|![HTML simge](../../extensibility/ux-guidelines/media/0405-31-html.png "0405 31_HTML") **HTML**|![WPF simgesi](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405 32_WPF") **WPF**|![ASP simgesi](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405 33_ASP") **ASP**|![CSS simgesi](../../extensibility/ux-guidelines/media/0405-34-css.png "0405 34_CSS") **CSS**|![TypeScript simgesi](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405 35_TypeScript") **TypeScript**||

#### <a name="intellisense"></a>IntelliSense
 Bir özel renk paletini IntelliSense simgelerini kullanın. Bu renklerin IntelliSense açılan listedeki farklı öğeleri hızlı bir şekilde ayırt kullanıcılara yardımcı olmak için kullanılır.

|Kullanım|Ad|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|Olay sınıfı|VS eylemin turuncu|C27D1A / 194,125,26|![Renk örneği C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|Genişletme yöntemi, yöntem, modül temsilcisi|VS eylem mor|652D 90 / 101,45,144|![Renk örneği 652D 90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|Alan, sabit listesi öğesi, makrosu, yapı, birleşim değer türü işleç arabirimi|VS eylem mavi|00539C / 0,83,156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Nesne|VS eylem yeşil|388A34 / 56,138,52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Sabit, özel durum, sabit listesi öğesi, harita, harita öğesi, Namespace, şablonu tür tanımı|Arka plan (VS BG)|424242 / 66,66,66|![Renk örneği 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense simgeler örnekleri

||||||
|-|-|-|-|-|
|![IntelliSense sınıf simgesi](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405 36_IntelliSenseClass") **sınıfı**|![IntelliSense özel olay simgesi](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent") **özel olay**|![IntelliSense temsilci simgesi](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405 38_IntelliSenseDelegate") **temsilci seçme**|![IntelliSense yöntemi arkadaş simgesi](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend") **arkadaş yöntemi**|![Alan simgesi](../../extensibility/ux-guidelines/media/0405-40-field.png "0405 40_Field") **alan**|
|![IntelliSense korumalı sabit listesi öğesi simgesi](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem") **korumalı sabit listesi öğesi**|![IntelliSense nesne simgesi](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405 42_IntelliSenseObject") **nesnesi**|![IntelliSense şablon simgesi](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405 43_IntelliSenseTemplate") **şablonu**|![IntelliSense özel durum kısayol simgesini](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut") **özel durum kısayol**||

### <a name="notifications"></a>Bildirimler
 Visual Studio'da bildirimleri durumunu göstermek için kullanılır. Bildirim palet siyah veya beyaz ön plan dolgu seçeneklerini yanı sıra aşağıdaki dört renkleri bildirimleri aşağıdaki durum düzeyleri tanımlamak için kullanır.

|Kullanım|Ad|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|Durum: nötr|Bildirim mavi (VS mavi)|1BA1E2 / 27,161,226|![Renk örneği 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|Durum: pozitif|Bildirim yeşil (VS yeşil)|339933 / 51,153,51|![Renk örneği 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|Durum: negatif|Bildirim kırmızı (VS kırmızı)|E51400 / 229,20,0|![Renk örneği E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|Durum: uyarı|Bildirim sarı (VS turuncu)|FFCC00 / 255,204,0|![Renk örneği FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|Ön plan dolgusu|Bildirim siyah (siyah)|000000 / 0,0,0|![Renk örneği &#35;000000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|Ön plan dolgusu|Bildirim beyaz (beyaz)|FFFFFF / 255,255,255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Bildirim simgeleri örnekleri

|||||
|-|-|-|-|
|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405 45_Alert") **uyarı**|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405 48_Warning") **Uyarısı**|![Tamamlandı simgesi](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405 46_Complete") **tamamlandı**|![Durdurma simgesi](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405 47_Stop") **Durdur**|

### <a name="visual-studio-online"></a>Visual Studio Team Services
 Genel olarak, Visual Studio Online tarayıcıda barındırılıp özelliklerden oluşur. Farklı ortamlarda rengi değişir, ancak stil aynı kalır.

|Grup|Kullanım|Ad|Değeri (tüm tema)|Renk örneği|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Arka Plan|TFSO BG|656565/ 101, 101, 101|![Renk örneği 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|Anahat|ÇIKIŞ TFSO|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Napa|Arka Plan|Beyaz|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Monako|Arka Plan|Beyaz|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Arka Plan|Beyaz|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Renk örneği 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|Vurgulu|F12 Blue_Hover|2279BF / 34,121,191|![Renk örneği 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|Devre dışı|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Renk örneği ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|Üzerine gelindiğinde kullanılacak arka plan|BG getirin|D9EBF7 / 217,235,247|![Renk örneği D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|Basılan arka plan|Basılan bg|B2D7F0 / 178,215,240|![Renk örneği B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|Anahat|VS ÇIKIŞ|F6F6F6 / 246,246,246|![Renk örneği F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|Bilgiler|Bilgiler|00BCF2 / 0,188,242|![Renk örneği 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|Uyarı|Uyarı|F28300 / 242,131,0|![Renk örneği F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|Hata / negatif|Error_Negative|E81123 / 232,17,35|![Renk örneği E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|Başlat / pozitif|Start_Positive|009E49 / 0,158,73|![Renk örneği 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|Sonu türü|Sonu türü|9B4F96 / 155,79,150|![Renk örneği 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|Olay işareti|Olay işareti|A51F00 / 165,31,0|![Renk örneği A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|Kullanıcı işareti|Kullanıcı işareti|F16220 / 241,98,32|![Renk örneği F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online simgeler örnekleri

|TFS çevrimiçi||||
|----------------|-|-|-|
|![TFS çevrimiçi takım simgesi](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405 49_TFSOnlineTeam") **Online ekibi**|![TFS bilgi simgesi](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405 50_TFSInformation") **bilgileri**|![TFS geçmişi simgesine](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405 51_TFSHistory") **geçmişi**|![TFS dal simgesi](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405 52_TFSBranch") **dal**|

|Napa||||
|----------|-|-|-|
|![Napa içerik simgesi](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405 53_NapaContent") **içeriği**|![Napa office posta simgesini](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405 54_NapaOfficeMail") **Office posta**|![Napa SharePoint simgesini](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405 55_NapaSharePoint") **SharePoint**|![Napa görev bölmesi simge](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405 56_NapaTaskPane") **görev bölmesi**|

|Monako||||
|------------|-|-|-|
|![Monako dosyalar simgesi](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405 57_MonacoFiles") **dosyaları**|![Monako Git simgesi](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405 58_MonacoGit") **Git**|![Monako arama simgesine](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405 59_MonacoSearch") **arama**|![Monako metin simgesi](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405 60_MonacoText") **metin**|

|F12||||
|---------|-|-|-|
|![F12 görünen kod simgesi](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405 61_F12PrettyCode") **oldukça kod**|![F12 uyarı simgesi](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405 62_F12Warning") **Uyarısı**|![F12 öykünmek simgesi](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405 63_F12Emulate") **Emulate**|
