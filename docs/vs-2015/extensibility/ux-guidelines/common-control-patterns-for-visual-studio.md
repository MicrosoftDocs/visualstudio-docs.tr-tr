---
title: Yaygın Denetim Desenleri
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2de92d2b6083fd587dc38a67e189fa9ca24b660d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052144"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio için yaygın denetim desenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Ortak Denetimler

### <a name="overview"></a>Genel Bakış
 Visual Studio kullanıcı arabiriminde çoğunu ortak denetimleri oluşturur. Visual Studio arabiriminde kullanılan en yaygın denetimleri izlemelidir [Windows Masaüstü etkileşim kuralları](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Bu belge, Visual Studio için özeldir ve özel durumlar veya bu Windows yönergeleri büyütmek ayrıntıları kapsar.

#### <a name="common-controls-in-this-topic"></a>Bu konuda ortak denetimleri

-   [Kaydırma çubukları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

-   [Giriş alanlarını](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

-   [Birleşik giriş kutusu ve aşağı açılır listeler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

-   [Onay kutuları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

-   [Radyo düğmeleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

-   [Grup çerçeveler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

-   [Metin denetimi](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

-   [Düğmeler ve köprüleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

-   [Ağaç görünümleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Görsel stili
 Denetimleri stillendirme yaparken dikkate alınması gereken ilk şey, denetimleri temalı kullanıcı Arabiriminde kullanılacak olan ' dir. Standart kullanıcı arabiriminde denetimlerinin konulu olmayan kullanıcı Arabirimi ve izlemelidir [normal Windows Masaüstü stili](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), yeniden şablonlu değildir ve varsayılan denetim görünümlerini görünmelidir anlamına gelir.

-   **Standart (yardımcı programı) iletişim kutuları:** temalı değil. Re-template yapın. Temel denetim stili varsayılan ayarları kullanın.

-   **Aracı, windows, belge düzenleyicileri, tasarım yüzeyleriyle ve temalı iletişim kutuları:** renk hizmetini kullanan özel temalı görünümünü kullanın.

###  <a name="BKMK_Scrollbars"></a> Kaydırma çubukları
 Kaydırma çubukları izlemelidir [Windows kaydırma çubukları için ortak etkileşim desenleri](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) bunlar içerik bilgilerle gibi Kod Düzenleyicisi'nde genişletilmiş sürece.

###  <a name="BKMK_InputFields"></a> Giriş alanlarını
 Tipik etkileşim davranışını izleyin [metin kutuları için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Görsel stili

-   Giriş alanlarını yardımcı programı iletişim kutularında stil değil. Denetimin iç temel stili kullanın.

-   Temalı giriş alanlarını yalnızca temalı iletişim kutuları ve araç pencerelerinde de kullanılmalıdır.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimleri

-   Salt okunur alanların varsayılan (etkin) ön plan ancak gri (devre dışı) arkaplanla görüntülenir.

-   Alanların gerekli  **\<gerekli >** olarak Filigran belgeler bunları içinde. Nadir durumlarda dışında bir arka plan rengini değiştirmemesi gerekir.

-   Doğrulama hatası: bkz [bildirimler ve Visual Studio için ilerleme durumu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

-   Giriş alanlarını, bunlar gösterilir penceresinin genişliğini uygun değil ya da bir yol gibi uzun bir alan uzunluğunu rasgele eşleştirilecek içeriği sığdıracak şekilde boyutlandırılmalıdır. Uzunluğu bir göstergesi kullanıcıya karakterlerinin kaçının tutulacağını alana izin için sınırlamalar olabilir.

     ![Hatalı giriş alanı denetim genişliği](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl") **hatalı giriş alan uzunluğu: adı bu kadar uzun olacağını düşüktür.**

     ![Giriş alanı denetim genişliği düzeltmek](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl") **doğru giriş alan uzunluğu: beklenen içeriğe için makul bir genişlik giriş alandır.**

###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Birleşik giriş kutusu ve aşağı açılır listeler
 Tipik etkileşim davranışını izleyin [açılan listeler ve birleşik giriş kutuları için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Görsel stili

-   Yardımcı program iletişim kutularında re-template denetimi yapın. Denetimin iç temel stili kullanın.

-   Kullanıcı Arabirimi teması Kombo kutularını ve açılan listeler, denetimler için standart tema izleyin.

#### <a name="layout"></a>Düzen
 Birleşik giriş kutularını ve açılan listeler, bunlar gösterilir penceresinin genişliğini uygun değil ya da bir yol gibi uzun bir alan uzunluğunu rasgele eşleştirilecek içeriği sığdıracak şekilde boyutlandırılmalıdır.

 ![Yanlış bırakma&#45;aşağı Düzen](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")

 **Bir açılır denetimi için yanlış alan uzunluğu**

 ![Doğru bırakma&#45;aşağı Düzen](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")

 **Bir açılır denetimi için doğru alan uzunluğu**

###  <a name="BKMK_CheckBoxes"></a> Onay kutuları
 Tipik etkileşim davranışını izleyin [Windows Masaüstü yönergeleri için onay kutularını](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Görsel stili

-   Yardımcı program iletişim kutularında re-template denetimi yapın. Denetimin iç temel stili kullanın.

-   Temalı kullanıcı Arabiriminde standart tema denetimler için onay kutularını izleyin.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimleri

-   Bir onay kutusu ile etkileşimi hiçbir zaman bir iletişim kutusu açılır veya başka bir bölümüne gitmek gerekir.

-   Onay kutularını metnin ilk satırı taban çizgisi ile hizalar.

     ![Yanlış onay kutusu hizalama](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign") **yanlış onay kutusu hizalama: onay kutusu metni ortalanır.**

     ![Onay kutusu hizalama düzeltmek](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign") **onay kutusunu hizalama düzeltin: onay kutusunu, metnin ilk satırı taban çizgisi ile hizalanır.**

###  <a name="BKMK_RadioButtons"></a> Radyo düğmeleri
 Tipik etkileşim davranışını izleyin [radyo düğmeleri için Windows Masaüstü yönergelerini](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Görsel stili
 Yardımcı program iletişim kutularında, stil radyo düğmeleri yapın. Denetimin iç temel stili kullanın.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimleri
 Radyo seçenekleri içine almak için bir grup çerçeve kullanmak gerekli değildir.

###  <a name="BKMK_GroupFrames"></a> Grup çerçeveler
 Tipik etkileşim davranışını izleyin [grubu çerçeveler için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Görsel stili
 Yardımcı program iletişim kutularında, Stil grubu çerçeve yapın. Denetimin iç temel stili kullanın.

#### <a name="layout"></a>Düzen

-   Grup ayrım sıkı bir düzende korumak gerekli olmadıkça, radyo seçenekleri kapsamak için grubu çerçeve kullanmak gerekli değildir.

-   Hiçbir zaman tek bir denetim için bir grup çerçevesini kullanın.

-   Bazen, yatay bir kural grubu çerçeve kapsayıcısını yerine kullanmak için kabul edilebilir.

##  <a name="BKMK_TextControls"></a> Metin denetimi

### <a name="labels"></a>Etiketler

#### <a name="active-label-state"></a>Etkin etiket durumu

##### <a name="utility-standard-dialogs"></a>Yardımcı programı (standart) iletişim kutuları)

-   Genel olarak, denetim etiketleri için Windows Masaüstü yönergeleri izleyin.

-   Yardımcı program iletişim kutularında, olmayan-kalın yazı tipini ve metin rengi standart ortam, etiketleri görüntülenmesi gerekir. Bkz: [yazı tipleri ve biçimlendirme için Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

-   Üç nokta her zaman etiket izlemelidir.

##### <a name="signature-themed-dialogs"></a>İmza (tema) iletişim kutuları)
 Etiket denetimleri kalın veya açık gri olabilir.

#### <a name="disabled-label-state"></a>Devre dışı bırakılmış etiket durumu
 Etiketler, ilişkili oldukları denetiminin görünümünü yansıtmalıdır. İlişkili denetim devre dışı bırakılırsa, örneğin, ardından etiket gri ve devre dışı görüntülenmesi gerekir. Bu, genellikle işletim sistemi tarafından işlenir ve hiçbir özel olarak değerlendirilmesi gerekir.

#### <a name="dynamic-labels"></a>Dinamik etiketleri
 Geçerli seçime dayanan dinamik etiketleri değiştirin. Mümkün olduğunda, dinamik etiketleri ana/ayrıntı düzenleri görüntülenen bilgileri belirli bir seçim ve genel bilgi için ilgili olduğunu anlamanıza yardımcı olmak için kullanın.

 ![Dinamik içerik ile kullanılan dinamik etiket](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")

 **Dinamik içerik ile kullanılan dinamik bir etiket örneği**

#### <a name="instructional-text"></a>Açıklayıcı metni
 Bazı arabirim öğeleri UI amacını kullanıcının yardımcı olmak için ya da eylem için göstermek için açıklayıcı metni yararlanır.

-   Eğitici metin iletişim kutuları üst kısmında yaygın olarak kullanılır, ancak karmaşık denetimi gruplandırma yönerge sağlamak için diğer alanlarda görünebilir.

-   Eğitici metin etkileşimli olmayan olmakla birlikte, Yardım konuları köprüler içeriyor olabilir.

-   Eğitici metin tutumlu ve yalnızca kullanmak gerektiğinde.

##### <a name="formatting"></a>Biçimlendirme
 Eğitici metin ortam yazı tipi, standart (konulu olmayan) denetim metin olmalıdır. Bkz: [yazı tipleri ve biçimlendirme için Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Eğitici metin yazma hakkında daha fazla bilgi için bkz [UI metni ve terminoloji](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Eğitici metin biçimlendirme](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")

 **Visual Studio iletişim kutusunda eğitici metin**

#### <a name="informational-text"></a>Bilgilendirici metin
 Bilgilendirici metin kullanıcı ek bilgiler sunan bir metindir. Statik veya dinamik ya da bir bildirim olarak kullanılan olabilir. Her zaman salt okunurdur, ancak kullanıcı bilgileri kopyalama olanağı sağlamak yararlı ise dinamik metin bir denetim kapsayıcısı gibi salt okunur metin alanına yerleştirilmelidir.

##### <a name="dynamic-context-specific-text"></a>Dinamik (bağlam özgü) metin
 Bağlama, ne zaman odak kullanıcı anahtarları gibi dinamik bilgi metnini değiştirir. Genellikle, ancak her zaman, dinamik içerik, dinamik bir etiket ile eşleştirilmiştir.

 ![Dinamik bilgi metnini](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")

 **Dinamik bilgilendirici metin bağlama bağlı olarak değişir.**

##### <a name="formatting"></a>Biçimlendirme
 Salt okunur metin alanları görüntülemek için iki yolu vardır: doğrudan üzerinde kullanıcı Arabirimi (yukarıya bakın) yüzey veya grup çerçeve veya metin kutusu gibi başka bir denetimi kapsamında yer alan. Geçerli duruma bağlı olarak doğru. Bu salt okunur bilgiler sunmak nasıl belirlemek için en fazla özellik Tasarımcısı olur.

 Metin salt okunur metin kutusu içinde olabilir. Düzenlenemez gerekir ancak bu genellikle içerik seçilebilen ve kopyalanır, olduğunu gösterir.

 ![Bilgilendirici metin okuma için biçimlendirme&#45;yalnızca alanları](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")

 **Bilgilendirici metin salt okunur alanlar için biçimlendirme**

#### <a name="watermarks"></a>Filigranlar
 İfade aynı olabilse filigranlar eğitici metin arasındaki filigranlar denetim/penceresini boş değil ve görünür eğitici metin kalır her zaman içerik ile değiştirilir farktır.

 Bir pencere veya Denetim boş olduğunda filigranlar kullanılmalıdır. Bunlar alanını doldurmak için yapılması gerektiğini belirtmek ve sürükleme kaynağı gibi ilgili windows açmak için eylem bağlantıları içerebilir.

##### <a name="visual-style"></a>Görsel stili

- Filigranlar yatay olarak pencere içinde ortalanmış.

- Filigranlar sola hizalı değil, merkezi hizalı olmalıdır.

- Filigranlar dikey ortalanmış veya alanının üst kısımda yerleştirilmiş. Alanın üst kısımda yer alan, böylece Filigran belirginleştirmek yukarıdaki yeterli alan olmalıdır.

- Kullanım `Environment.GrayText` belirteç ve standart bir ortam. yazı tipi rengi. Köprüler, paylaşılan standart köprü belirteçleri kullanmalıdır: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, ve `Environment.PanelHyperlinkDisabled`.

- Arka planda filigranlar seçilemez.

- Mümkünse, filigran başlama kullanıcının yardımcı olmak için bağlantılar içerir.

  ![Filigran metni Tasarımcı penceresindeki](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")

  ![Filigran araç penceresindeki metin](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")

  **Filigran metni Visual Studio Örnekleri**

##  <a name="BKMK_ButtonsAndHyperlinks"></a> Düğmeler ve köprüleri

### <a name="overview"></a>Genel Bakış
 Düğme ve bağlantı denetimleri (köprü) izlemelidir [köprüler temel Windows Masaüstü yönergeler](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) ifadesi, boyutlandırma hem de aralık kullanımı.

### <a name="choosing-between-buttons-and-links"></a>Düğmeler ve bağlantıları arasında seçim yapma
 Geleneksel olarak, düğmeler, Eylemler için kullanılmış olan ve köprüler gezinme için ayrılmış. Her durumda düğmeler kullanılabilir, ancak düğmeler ve bağlantıları bazı koşullarda daha birbirinin yerine kullanılabilir. böylece, Visual Studio'da bağlantıları rolünü genişletildi.

 Ne zaman komut düğmeleri kullanın:

- Birincil komutları

- Giriş toplamak için kullanılan windows görüntüleme veya ikincil komutları olsalar bile, seçenekleri yapma

- Yıkıcı veya geri alınamaz eylemleri

- Sihirbazlar ve sayfa içinde taahhüt düğme akışları

  Komut düğmeleri araç pencerelerindeki önlemek veya ikiden fazla sözcük etiketi gerekiyorsa. Bağlantılar, uzun bir etiket olabilir.

  Ne zaman bağlantıları kullanın:

- Başka bir pencere, belge veya web sayfasına gitme

- Bir uzun etiket ya da eylem amacı açıklamak için kısa bir cümle gerektiren durumlar

- Kullanıcı Arabirimi, bir düğme burada doldurmaya sıkı alanları sağlanan eylemi yıkıcı veya geri alınamaz değil

- İkincil komutları durumlarda devre dışı bırakma emphasizing komutların çoğu olduğu

#### <a name="examples"></a>Örnekler
 ![Bilgi çubuğu komut bağlantıları bir durum iletisi](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")

 **Bir durum iletisi aşağıdaki Bilgi Çubuğu'nda kullanılan komutunu bağlantıları**

 ![CodeLens açılan pencerede kullanılan bağlantıları](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")

 **CodeLens açılan pencerede kullanılan bağlantılar**

 ![İkincil komutları kullanılan bağlantıları](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")

 **Burada düğmeleri çok fazla dikkat çekebilir ikincil komutlarında kullanılan bağlantılar**

### <a name="common-buttons"></a>Ortak düğmeleri

#### <a name="text"></a>Metin
 Yazma faydalandığından [UI metni ve terminoloji](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Görsel stili

##### <a name="standard-dialogs"></a>Standart iletişim kutuları
 Visual Studio'da çoğu düğmeler standart iletişim kutularında görüntülenir ve değil biçimlendirilmiş. Bunlar işletim sistemi tarafından belirlenen düğmelerin standart görünümünü yansıtmalıdır.

##### <a name="themed"></a>Tema
 Bazı durumlarda, düğmeler, stil uygulanmış kullanıcı Arabirimi içinde kullanılabilir ve bu düğmeler uygun şekilde biçimlendirilmiş olmalıdır. Bkz: [iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) temalı denetimleri hakkında bilgi için.

### <a name="special-buttons"></a>Özel düğmeler

#### <a name="browse-buttons"></a>Göz at... düğmeler
 **[Gözat...]**  düğmeler, kılavuzlar, iletişim kutuları ve araç pencerelerini ve kalıcı olmayan diğer UI öğeleri kullanılır. Bunlar, kullanıcı denetime bir değer doldurma yönetmenize yardımcı olan bir seçici görüntülenir. Bu düğme, uzun ve kısa iki çeşidi vardır.

 ![Uzun &#91;Gözat... &#93; düğmesi](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")

 **Uzun [Gözat...] düğmesine**

 ![Üç nokta kısa&#45;yalnızca &#91;Gözat... &#93; düğmesi](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")

 **Yalnızca nokta kısa [...] düğmesine**

 Ne zaman yalnızca üç nokta kısa düğmesini kullanın:

- Varsa birden fazla uzun **[Gözat...]**  göz atmak için çeşitli alanları ne zaman izin gibi bir iletişim kutusu düğmesi. Kısa kullanın **[...]**  düğmesini her bu durum tarafından oluşturulan kafa karıştırıcı erişim anahtarlarını önlemek için (**& Gözat** ve **B & özat** aynı iletişim kutusunda).

- Sıkı bir iletişim kutusu veya uzun düğmesi koymak için makul bir yerde olduğunda.

- Bir grid denetiminin düğmesi görünür değilse.

  Düğmeyi kullanarak yönergeleri:

- Bir erişim anahtarı kullanmayın. Klavyeyi kullanarak erişmek için kullanıcı bitişik denetiminden sekme gerekir. Herhangi bir Gözat düğmesi hemen doldurur alan sonra kalan, sekme sırasını olduğundan emin olun. İlk dönemden altında bir alt çizgi hiçbir zaman kullanmayın.

- Microsoft etkin erişilebilirliği (MSAA) kümesi **adı** özelliğini **Gözat...**  ekranında, bu nedenle (üç nokta dahil olmak üzere) okuyucular bunu "Gözatma türü" ve değil "dot nokta nokta" veya "Dönem Dönem-süresi." olarak okur Yönetilen denetimleri için bu ayarı anlamına gelir **AccessibleName** özelliği.

- Üç nokta kullanmamanız **[...]**  Gözat eylemi dışındaki düğmesi. Örneğin, gerekirse bir **[yeni...]**  düğmesini ancak iletişim kutusunun tasarlanması gerekir sonra metin için yeterli alan yok.

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık
 ![Boyutlandırma &#91;Gözat... &#93; düğmeleri](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")

 **Düğmeler [Gözat...] boyutlandırma**

 ![Aralık &#91;Gözat... &#93; düğmeleri](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")

 **Aralığı [Gözat...] düğmeleri**

#### <a name="graphical-buttons"></a>Grafik düğmeleri
 Bazı düğmeleri, her zaman bir grafik görüntüsünü kullanın ve hiçbir zaman alanından tasarruf etmek ve Yerelleştirme sorunları önlemek için metni ekleyin. Bunlar, alan seçicileri ve diğer sıralanabilir listelerinde sıklıkla kullanılır.

> [!NOTE]
>  Kullanıcınız (hiçbir erişim anahtarları vardır) Bu düğme için sekmesinde, bu nedenle bunları mantıklı bir sırada yerleştirin. Name özelliği düğmesinin Ekran okuyucular düğmesi eylemi doğru olarak yorumlayabilir. böylece, geçen eyleme eşleyin.

|||
|-|-|
|Ekle|![Grafik "Ekle" düğmesini](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|
|Kaldır|![Grafik "Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|
|Tümünü Ekle|![Grafik "Tümünü Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|
|Tümünü Kaldır|![Grafik "Tümünü Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|
|Yukarı Taşı|![Grafik "Yukarı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|
|Aşağı Taşı|![Grafik "Aşağı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|
|Sil|![Grafik "Sil" düğmesini](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık
 Grafik bir düğme kısa aynıdır için boyutlandırma **[Gözat...]**  düğmesine (26 x 23 piksel cinsinden):

 ![Düğmesini gösteren saydam rengi olmadan ve](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")

 **Grafik Resmi saydam rengi gösteren olmadan ve düğmesine görünümünü**

### <a name="hyperlinks"></a>Köprüleri
 Köprüler bir Yardım konusu, kalıcı iletişim kutusu veya Sihirbazı açma gibi Gezinti tabanlı eylemler için uygundur. Köprü komutu için kullanılıyorsa, her zaman görünür ve belirgin bir değişiklik için kullanıcı Arabirimi görüntülemelisiniz. Genel olarak, bir eylem (örneğin, iptal, kaydetme ve silme gibi) yürütme eylemleri daha iyi bir düğmeyi kullanarak bildirilir.

#### <a name="writing-style"></a>Yazma stili
 İzleyin [Windows masaüstü kılavuzu için kullanıcı arabirimi metinlerini](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). "Bilgi daha fazla hakkında" kullanmayın "Söyleyin bana daha fazla hakkında" veya "Bu Get help" yapılar. Bunun yerine, Yardım içerik tarafından birincil sorunuzun açısından Yardım bağlantı metni tümce. Örneğin, "**Sunucu Gezgini için bir sunucu nasıl eklerim?**"

#### <a name="visual-style"></a>Görsel stili

-   Köprüler her zaman kullanması gereken [VSColor hizmet](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Köprü doğru biçimlendirilmiş değil ise kırmızı etkinken yanıp veya ziyaret sonra farklı bir renkle gösterilir.

-   Bağlantı bir cümle parça içinde tam bir cümle gibi Filigran olmadıkça durumu üzerine notlarını denetim, alt çizgiler dahil değildir.

-   Üzerine gelindiğinde, alt çizgiler görünmemelidir. Bunun yerine, bağlantı etkin olduğunu kullanıcıya geri bildirim hafif rengi değiştirme ve uygun bağlantıyı imleci ' dir.

##  <a name="BKMK_TreeViews"></a> Ağaç görünümleri

### <a name="overview"></a>Genel Bakış
 Ağaç görünümleri, karmaşık düzenlemek için bir yol üst-alt gruplar halinde listeler sağlar. Bir kullanıcı genişletebilir veya üst grupları Göster ya da temel alınan alt öğeleri gizle daraltabilirsiniz. Daha fazla eylem sağlamak için her öğe ağacı görünümü içinde seçilebilir.

 Bu konu, kabul edilebilir kullanım, doğru tasarım ve ağaç görünümlerini işlevselliğini içerir.

#### <a name="in-this-topic"></a>Bu konuda

-   [Görsel stili](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

-   [Etkileşimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

###  <a name="BKMK_TreeViewVisualStyle"></a> Görsel stili

#### <a name="expanders"></a>Genişleticisi
 Ağaç görünümü denetimleri, genişletici tasarım Windows ve Visual Studio tarafından kullanılan uymalıdır. Her düğüm göster veya gizle temel alınan öğeleri için bir genişletici denetimi kullanır. Genişletici denetimi kullanarak, Windows ve Visual Studio içinde farklı ağaç görünümlerini karşılaşabileceğiniz kullanıcılar için tutarlılık sağlar.

 ![Ağaç görünümü denetiminin düzeltmek](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Doğru: bir expander denetimi kullanarak ağaç görünümü düğümünün uygun stili**

 ![Yanlış ağaç görünümü düğümleri](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")

 **Yanlış: ağaç görünümü düğümünün hatalı stili**

#### <a name="selection"></a>Seçim
 Bir düğüm ağacı görünümü içinde seçili olduğunda, vurgulama ağaç görünümü denetiminde tam genişliğine genişletmeniz gerekir. Bu, kullanıcıların seçmiş olduğunuz hangi öğe NET bir şekilde belirlemesine yardımcı olur. Renk seçimi, geçerli Visual Studio temasını yansıtmalıdır.

 ![Ağaç görünümü denetiminin düzeltmek](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Doğru: Seçili düğümün vurgulama ağaç görünümü denetiminin tüm genişliği uyar.**

 ![Yanlış ağaç görünümü vurgulama](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")

 **Yanlış: ağaç görünümü denetiminin tüm genişliği vurgulama Seçili düğümün uymuyor.**

#### <a name="icons"></a>Simgeler
 Görsel öğeler arasındaki farklar tanımlanmasına yardımcı simgeleri yalnızca ağaç görünümü denetimleri kullanılmalıdır. Genel olarak, simgeleri yalnızca hangi öğelerin türlerini ayırt etmek için bilgi simgeleri taşıyan heterojen listelerinde kullanılmalıdır. Homojen bir listedeki simgeleri kullanarak gürültü sık görülebilir ve kaçınılmalıdır. Bu durumda grubu simgesi (üst) içindeki öğe türü ifade edebilir. Bu kuralın istisnası olarak, simge dinamiktir ve durumunu göstermek için kullanılan olacaktır.

#### <a name="scroll-bars"></a>Kaydırma çubukları
 Kaydırma çubukları, her zaman içerik ağaç görünümü denetiminin içinde sığıyorsa gizlenmelidir. Gizli veya yarı saydam kaydırılabilir bir pencerede ve ağaç görünümünde içeren pencere odaklandığında görünür veya kendisi üzerinde vurgulu ağacı görüntülemek için kaydırma çubuklarını kabul edilebilir olduğu.

 ![Ağaç görünümü kaydırma çubuklu](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")

 **Ağaç görünümü denetiminin sınırları içeriği aştığınız için her iki yatay ve dikey kaydırma çubukları görüntülenir.**

###  <a name="BKMK_TreeViewInteractions"></a> Etkileşimler

#### <a name="context-menus"></a>Bağlam menüleri
 Bir ağaç görünümü düğümü alt menü seçenekleri bağlam menüsü ortaya çıkarabilir. Bu genellikle, bir kullanıcı bir öğeyi sağ veya seçili öğeye sahip bir Windows klavyede menü tuşuna basıldığında gerçekleşir. Düğüm odağı ve seçili önemlidir. Bu, kullanıcının alt ait hangi öğesini tanımlamaya yardımcı olur.

 ![Seçilen Ağaç düğümünün ve bağlam menüsü](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")

 **Kullanıcıya bildirmek için bağlam menüsünü kazançlar odağı hangi öğesi oluştur sahip öğe seçilmedi.**

#### <a name="keyboard"></a>Klavye
 Ağaç görünümünde öğeleri seçin ve klavye kullanarak düğümlerin içerik modelini genişletme/daraltma imkanı sağlamanız gerekir. Bu gezinti bizim erişilebilirlik gereksinimlerini karşıladığını sağlar.

##### <a name="tree-view-control"></a>Ağaç görünümü denetimi
 Visual Studio ağaç denetimleri ortak klavye gezintisi izlemelidir:

-   **Yukarı Ok:** ağacın taşıyarak öğeleri seçin

-   **Aşağı ok:** ağacının taşıyarak öğeleri seçin

-   **Sağ ok:** ağacında bir düğümü genişletin

-   **Sol Ok:** ağacında bir düğümü Daralt

-   **Anahtarı girin:** başlatmak, yükleme, yürütme seçili öğe

##### <a name="trid-tree-view-and-grid-view"></a>Trid (ağaç görünümü ve ızgara görünümü)
 Bir grid'in içindeki ağaç görünümünde içeren karmaşık bir denetim trid denetimidir. Ağaç görünümünde, aşağıdaki eklemelerle olarak aynı klavye komutlarını ağacında doğru genişletme ve daraltma saygı:

- **Sağ ok:** bir düğümünü genişletin. Düğüm genişletildikten sonra en yakın sütuna sağ taraftaki gezinme devam etmelidir. Gezinti satırının sonundaki durdurmanız gerekir.

- **Sekmesi:** yakın hücrenin sağ taraftaki gitmenizi sağlar.  Satırın sonunda, gezinti ve bir sonraki satıra devam eder.

- **SHIFT + Tab:** yakın hücrenin soldaki gitmenizi sağlar.  Satırın başlangıcında, gezinti önceki satırdaki en sağındaki hücreyi devam eder.

  ![Visual Studio'da Trid denetimi](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")

  **Visual Studio'da bir trid denetimi**
