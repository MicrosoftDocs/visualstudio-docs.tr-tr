---
title: Visual Studio için yaygın denetim desenleri | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e10fdcea9819c34735f285c78a0e2ebb0650f64a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512323"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio için yaygın denetim desenleri
##  <a name="BKMK_CommonControls"></a> Ortak Denetimler  
  
### <a name="overview"></a>Genel Bakış  
Visual Studio kullanıcı arabiriminde çoğunu ortak denetimleri oluşturur. Visual Studio arabiriminde kullanılan en yaygın denetimleri izlemelidir [Windows Masaüstü etkileşim kuralları](/windows/desktop/uxguide/controls). Bu konuda, Visual Studio için özeldir ve özel durumlar veya bu Windows yönergeleri büyütmek ayrıntıları kapsar.  
  
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
Denetimleri stillendirme yaparken dikkate alınması gereken ilk şey, denetimleri temalı kullanıcı Arabiriminde kullanılacak olan ' dir. Standart kullanıcı arabiriminde denetimlerinin konulu olmayan kullanıcı Arabirimi ve izlemelidir [normal Windows Masaüstü stili](/windows/desktop/uxguide/controls), yeniden şablonlu değildir ve varsayılan denetim görünümlerini görünmelidir anlamına gelir.  
  
-   **Standart (yardımcı programı) iletişim kutuları:** temalı değil. Şablonu yeniden kullanmayın. Temel denetim stili varsayılan ayarları kullanın.  
  
-   **Aracı, windows, belge düzenleyicileri, tasarım yüzeyleriyle ve temalı iletişim kutuları:** renk hizmetini kullanan özel temalı görünümünü kullanın.  
  
###  <a name="BKMK_Scrollbars"></a> Kaydırma çubukları  
 Kaydırma çubukları izlemelidir [Windows için ortak etkileşim desenleri kaydırma çubukları](/windows/desktop/Controls/about-scroll-bars) ile içerik bilgilerini genişletilmiş sürece, Kod Düzenleyicisi'nde ister.  
  
###  <a name="BKMK_InputFields"></a> Giriş alanlarını  
 Tipik etkileşim davranışını izleyin [metin kutuları için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-text-boxes).  
  
#### <a name="visual-style"></a>Görsel stili  
  
-   Giriş alanlarını yardımcı programı iletişim kutularında stillere sahip olmamalıdır. Denetimin iç temel stili kullanın.  
  
-   Temalı giriş alanlarını yalnızca temalı iletişim kutuları ve araç pencerelerinde de kullanılmalıdır.  
  
#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimleri  
  
-   Salt okunur alanların varsayılan (etkin) ön plan ancak gri (devre dışı) arkaplanla görüntülenir.  
  
-   Alanların gerekli  **\<gerekli >** olarak Filigran belgeler bunları içinde. Nadir durumlarda dışında bir arka plan rengini değiştirmemesi gerekir.  
  
-   Doğrulama hatası: bkz [bildirimler ve Visual Studio için ilerleme durumu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Giriş alanlarını, bunlar gösterilir penceresinin genişliğini uygun değil ya da bir yol gibi uzun bir alan uzunluğunu rasgele eşleştirilecek içeriği sığdıracak şekilde boyutlandırılmalıdır. Uzunluğu bir göstergesi kullanıcıya karakterlerinin kaçının tutulacağını alana izin için sınırlamalar olabilir.  
  
     ![Hatalı giriş alan uzunluğu: adı bu kadar uzun olacağını düşüktür. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Hatalı giriş alan uzunluğu: adı bu kadar uzun olacağını düşüktür.
  
     ![Giriş alan uzunluğu düzeltin: beklenen içeriğe için makul bir genişlik giriş alandır. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Giriş alan uzunluğu düzeltin: beklenen içeriğe için makul bir genişlik giriş alandır.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Birleşik giriş kutusu ve aşağı açılır listeler  
Tipik etkileşim davranışını izleyin [açılan listeler ve birleşik giriş kutuları için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-drop).  
  
#### <a name="visual-style"></a>Görsel stili  
  
-   Yardımcı program iletişim kutularında, denetim şablonu yeniden kullanmayın. Denetimin iç temel stili kullanın.  
  
-   Kullanıcı Arabirimi teması Kombo kutularını ve açılan listeler, denetimler için standart tema izleyin.  
  
#### <a name="layout"></a>Düzen  
Birleşik giriş kutularını ve açılan listeler, bunlar gösterilir penceresinin genişliğini uygun değil ya da bir yol gibi uzun bir alan uzunluğunu rasgele eşleştirilecek içeriği sığdıracak şekilde boyutlandırılmalıdır.  
  
![Yanlış: açılan genişliğini görüntülenecek içeriği için çok uzun. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Yanlış: açılan genişliğini görüntülenecek içeriği için çok uzun.
  
![Doğru: açılan çeviri büyüme için izin ver, ancak gereksiz yere değil uzun boyutlandırılır. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Doğru: açılan çeviri büyüme için izin ver, ancak gereksiz yere değil uzun boyutlandırılır. 
  
###  <a name="BKMK_CheckBoxes"></a> Onay kutuları  
Tipik etkileşim davranışını izleyin [Windows Masaüstü yönergeleri için onay kutularını](/windows/desktop/uxguide/ctrl-check-boxes).  
  
#### <a name="visual-style"></a>Görsel stili  
  
-   Yardımcı program iletişim kutularında, denetim şablonu yeniden kullanmayın. Denetimin iç temel stili kullanın.  
  
-   Temalı kullanıcı Arabiriminde standart tema denetimler için onay kutularını izleyin.  
  
#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimleri  
  
-   Bir onay kutusu ile etkileşimi hiçbir zaman bir iletişim kutusu açılır veya başka bir bölümüne gitmek gerekir.  
  
-   Onay kutularını metnin ilk satırı taban çizgisi ile hizalar.  
  
     ![Yanlış: onay kutusu metni ortalanır. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Yanlış: onay kutusu metni ortalanır.
  
     ![Doğru: onay kutusunun metnin ilk satırı ile hizalanır. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Doğru: onay kutusunun metnin ilk satırı ile hizalanır.
  
###  <a name="BKMK_RadioButtons"></a> Radyo düğmeleri  
Tipik etkileşim davranışını izleyin [radyo düğmeleri için Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-radio-buttons).  
  
#### <a name="visual-style"></a>Görsel stili  
Yardımcı program iletişim kutularında, stil radyo düğmeleri yapın. Denetimin iç temel stili kullanın.  
  
#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimleri  
Grup ayrım sıkı bir düzende korumak gerekli olmadıkça, radyo seçenekleri kapsamak için grubu çerçeve kullanmak gerekli değildir.  
  
###  <a name="BKMK_GroupFrames"></a> Grup çerçeveler  
Tipik etkileşim davranışını izleyin [grubu çerçeveler için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-group-boxes).  
  
#### <a name="visual-style"></a>Görsel stili  
Yardımcı program iletişim kutularında, grubu çerçeve stili yok. Denetimin iç temel stili kullanın.  
  
#### <a name="layout"></a>Düzen  
  
-   Grup ayrım sıkı bir düzende korumak gerekli olmadıkça, radyo seçenekleri kapsamak için grubu çerçeve kullanmak gerekli değildir.  
  
-   Hiçbir zaman tek bir denetim için bir grup çerçevesini kullanın.  
  
-   Bazen, yatay bir kural grubu çerçeve kapsayıcısını yerine kullanmak için kabul edilebilir.  
  
##  <a name="BKMK_TextControls"></a> Metin denetimi

### <a name="static-text-fields"></a>Statik metin alanları

Bir statik metin alanı salt okunur bilgiler sunar ve kullanıcı tarafından seçilemez. Panoya kopyalamak için kullanıcının, isteyebileceği herhangi bir metin için kullanmaktan kaçının. Ancak, salt okunur, statik metin durumundaki bir değişikliği yansıtacak şekilde değiştirebilirsiniz. Örnekte aşağıdaki kök Namespace metin kutusunun üstüne yapılan değişiklikleri yansıtacak şekilde bilgi grubu değişiklikleri altındaki çıkış adı statik metin.

Statik metin bilgileri görüntülemek için iki yolu vardır.

Statik metin herhangi bir kapsama olmadan bir iletişim kutusu kendi açtığında gruplandırma çakışma yok olabilir. Ek satırların kutusunun gerçekten gerekli olup olmadığına karar. Bir örnek aşağıda gösterildiği gibi bir dizin yolu altında bir Grup satırı tarafından oluşturulan bir bölüm görüntülenir:  

![Statik metin bilgi metin denetimlerinde](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statik metin bilgi metin denetimlerinde

Bir iletişim kutusu burada gruplandırılmış diğer alanlar var ve bilgilerin kapsama okunabilirliği yardımcı ve ne zaman bir bölümü gizli veya gösterilen (olarak **Özellikler penceresi** açıklama bölmesi) veya benzer kullanıcı Arabirimi ile tutarlı olmasını istediğiniz statik metin kutusunun içine yerleştirin. Bu grup kutusu tek bir kural olmalıdır ve ile renkli `ButtonShadow`:

![Özellikler penceresinde statik metin](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Özellikler penceresinde statik metin

### <a name="read-only-text-box"></a>Salt okunur metin kutusu

Bu, kullanıcının alanı içindeki metni seçin, ancak düzenleme olmadan izin verir. Bu metin kutuları ile normal 3-b düz uç tarafından katýna bir `ButtonShadow` dolgu.

Bir metin kutusu etkin hale gelebilir (düzenlenemez), bir kullanıcı denetimi/işaretini onay kutusu veya radyo düğmesini seçerek/seçimini gibi ilişkili bir denetim değiştirir. Örneğin, **Araçları &gt; seçenekleri** sayfası aşağıda gösterilen **giriş sayfası** metin kutusu etkin hale gelir ne zaman **Varsayılanı kullan** onay kutusunun işaretli olduğundan.

![Salt okunur metin kutusu, etkin ve etkin durum gösteriliyor](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Salt okunur metin kutusu, etkin ve etkin durum gösteriliyor

### <a name="using-text-in-dialogs"></a>Metin kutularında kullanma

Metin kutularındaki için anahtar yönergeleri:

-   Metin kutuları ve liste kutuları unthemed kutularındaki çerçeveler için etiketleri ile fiili başlatma, yalnızca ilk sözcük bir ilk büyük olması ve iki nokta ile bitemez.

    > Metin denetimlerinde temalı iletişim kutularını izleyin [Windows Masaüstü UX kılavuzlarına uyum](/windows/desktop/uxguide/top-violations) ve Yardım bağlantıları soru işaretleri dışında bitiş noktalama kazanmaz.

-   Onay kutuları ve seçenek düğmeleri için etiketleri bir fiil, yalnızca ilk sözcük üzerinde bir ilk büyük başlatın ve hiçbir bitiş noktalama işareti vardır.

-   Düğmeler, menüler, menü öğeleri ve sekmeleri için etiketleri ilk harfleri büyük her sözcüğün (harfler büyük) sahip.

-   Etiket terminolojisi diğer iletişim kutuları benzer etiketler ile tutarlı olmalıdır.

-   Mümkünse, bir yazıcı/yazma veya uygulama geliştiriciye geçmeden önce metin onaylaması Düzenleyici vardır.

-   Tüm denetimleri, özel durumlarda etiketleri dışında olmalıdır hangi sekme yeterlidir.
Uygun olduğunda Yardımcısı metin kullanın.

### <a name="helper-text"></a>Yardımcı metni

İletişim kutusunun amacını kullanıcının yardımcı olmak için ya da eylem için göstermek için iletişim kutularında dahil. Yardımcısı metin basit iletişim kutuları Karışıklığı önlemek için yalnızca gerekli olduğunda kullanılmalıdır. İki çeşidi Yardımcısı metin iletişim ve eşik ' dir.

Bulunabileceği Yardımcısı metin izleyin ve yeni alanlar giriş olarak seçici olun. Yardımcı metni için yaygın senaryolar şunlardır:

-   Yardımcısı metin kutularındaki karmaşık bir iletişim kutusu ile etkileşim kurma konusunda ek yön vermek için.

-   Boş araç pencerelerini veya içerik görünür neden olduğunu açıklamak için iletişim kutularını, filigran metni.

-   Bir açıklama bölmesi, alt kısmında ister **Özellikler penceresi**.

-   Başlamak için kullanıcının gerçekleştirmesi gereken eylemi açıklamak için boş bir düzenleyicide metin Filigran.
  
### <a name="dialog-helper-text"></a>İletişim yardımcı metni

Bir kullanıcı deneyimi Tasarımcısı Yardımcısı metin ne zaman uygun olduğunu belirlemek yardımcı olabilir. Tasarımcı Yardımcısı metin yanı sıra genel içeriği nerede görüneceğini tanımlayabilirsiniz. Kullanıcı Yardımı metinde yazma/düzenleyebilir.

### <a name="watermarks"></a>Filigranlar

İletişim kutuları biraz farklı Filigran yönergelerden yararlanır. Bir iletişim kutusu özellikle çok sayıda kullanıcı Arabirimi öğeleri ile (etiketler, ipucu metni, düğmeleri ve diğer kapsayıcı denetimleri metin içeren), meşgul görünebilir, çünkü bu siyah görüntülendiğinde, filigranlar göze daha iyi koyu gri (VSColor: `ButtonShadow`). Genellikle beyaz arka plan ile bir liste kutusu gibi bir denetimi içinde bir filigran görünür (VSColor: `Window`).

-   Koyu gri renkte göründüğünü (VSColor: `ButtonShadow`). Ancak, filigran orta gri ya da diğer renkli görünürse (VSColor: `ButtonFace`) arka plan ve ilgili okunabilirlik hakkında siyah metinle Git yoktur (VSColor: `WindowText`).

-   Filigran, Orta veya sola. Hizalama kararları verirken standart Tasarım Kuralları geçerlidir. Filigran arka planda seçilemez.

![Filigran metni örneği](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Filigran metni örneği

### <a name="context-specific-dynamic-text"></a>Bağlama özgü (dinamik) metin

Dinamik metin kullanılan bir iletişim kutusu veya geçici kullanıcı Arabirimi iki yöntemden biri olabilir: dinamik bir etiket olarak veya dinamik içerik olarak.

-   Dinamik etiketi: bir ortak dinamik metin öğeleri ve özellikleri kılavuz sağında gösterilen bu öğelerin listesini içeren bir iletişim kutusu gibi daha fazla bilgi için seçili öğeyi teklif açıklayıcı panellerinde kullanılır. Sol taraftan bir öğe seçildiğinde, sağ kılavuza bilgi için belirli bir öğeyi gösterir. böylece, özellik kılavuzunda etiketini dinamik olabilir.

-   Dinamik metin: Burada bu şekilde belirli bilgileri ve genel bilgileri görüntülemek gerekir, ancak bakım değil aşırı için gerçekleştirilmesi gereken durumlarda yararlı olabilir.

Bilgileri kopyalamak olanağına sahip kullanıcıların istiyorsanız, dinamik metin salt okunur metin alanında olmalıdır.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Düğmeler ve köprüleri  
  
### <a name="overview"></a>Genel Bakış  
Düğme ve bağlantı denetimleri (köprü) izlemelidir [köprüler temel Windows Masaüstü yönergeler](/windows/desktop/uxguide/ctrl-links) ifadesi, boyutlandırma hem de aralık kullanımı.  
  
### <a name="choosing-between-buttons-and-links"></a>Düğmeler ve bağlantıları arasında seçim yapma  
Geleneksel olarak, düğmeler, Eylemler için kullanılmış olan ve köprüler gezinme için ayrılmış. Her durumda düğmeler kullanılabilir, ancak düğmeler ve bağlantıları bazı koşullarda daha birbirinin yerine kullanılabilir. böylece, Visual Studio'da bağlantıları rolünü genişletildi.  
  
Ne zaman komut düğmeleri kullanın:  
  
-   Birincil komutları  
  
-   Giriş toplamak için kullanılan windows görüntüleme veya ikincil komutları olsalar bile, seçenekleri yapma  
  
-   Yıkıcı veya geri alınamaz eylemleri  
  
-   Sihirbazlar ve sayfa içinde taahhüt düğme akışları  
  
Komut düğmeleri araç pencerelerindeki önlemek veya ikiden fazla sözcük etiketi gerekiyorsa. Bağlantılar, uzun bir etiket olabilir.  
  
 Ne zaman bağlantıları kullanın:  
  
-   Başka bir pencere, belge veya web sayfasına gitme  
  
-   Bir uzun etiket ya da eylem amacı açıklamak için kısa bir cümle gerektiren durumlar  
  
-   Kullanıcı Arabirimi, bir düğme burada doldurmaya sıkı alanları sağlanan eylemi yıkıcı veya geri alınamaz değil  
  
-   İkincil komutları durumlarda devre dışı bırakma emphasizing komutların çoğu olduğu  
  
#### <a name="examples"></a>Örnekler  
![Komut, bir durum iletisi aşağıdaki Bilgi Çubuğu'nda kullanılan bağlantıları](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Bir durum iletisi aşağıdaki Bilgi Çubuğu'nda kullanılan komutunu bağlantıları
  
![CodeLens açılan pencerede kullanılan bağlantıları](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />CodeLens açılan pencerede kullanılan bağlantılar
  
![Burada düğmeleri çok fazla dikkat çekebilir ikincil komutlarında kullanılan bağlantıları](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Burada düğmeleri çok fazla dikkat çekebilir ikincil komutlarında kullanılan bağlantılar
  
### <a name="common-buttons"></a>Ortak düğmeleri  
  
#### <a name="text"></a>Metin  
Yazma faydalandığından [UI metni ve terminoloji](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Görsel stili  
  
##### <a name="standard-unthemed"></a>Standart (unthemed)  
Visual Studio'da çoğu düğmeler yardımcı programı iletişim kutularında görüntülenir ve değil biçimlendirilmiş. Bunlar işletim sistemi tarafından belirlenen düğmelerin standart görünümünü yansıtmalıdır.  
  
##### <a name="themed"></a>Tema  
Bazı durumlarda, düğmeler, stil uygulanmış kullanıcı Arabirimi içinde kullanılabilir ve bu düğmeler uygun şekilde biçimlendirilmiş olmalıdır. Bkz: [iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) temalı denetimleri hakkında bilgi için.  
  
### <a name="special-buttons"></a>Özel düğmeler  
  
#### <a name="browse-buttons"></a>Düğmeler Gözat...  
**[Gözat...]**  düğmeler, kılavuzlar, iletişim kutuları ve araç pencerelerini ve kalıcı olmayan diğer UI öğeleri kullanılır. Bunlar, kullanıcı denetime bir değer doldurma yönetmenize yardımcı olan bir seçici görüntülenir. Bu düğme, uzun ve kısa iki çeşidi vardır.  
  
![Uzun [Gözat...] düğmesine](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />Uzun [Gözat...] düğmesine
  
![Yalnızca nokta kısa [...] düğmesine](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />Yalnızca nokta kısa [...] düğmesine
  
Ne zaman yalnızca üç nokta kısa düğmesini kullanın:  
  
-   Varsa birden fazla uzun **[Gözat...]**  göz atmak için çeşitli alanları ne zaman izin gibi bir iletişim kutusu düğmesi. Kısa kullanın **[...]**  düğmesini her bu durum tarafından oluşturulan kafa karıştırıcı erişim anahtarlarını önlemek için (**& Gözat** ve **B & özat** aynı iletişim kutusunda).  
  
-   Sıkı bir iletişim kutusu veya uzun düğmesi koymak için makul bir yerde olduğunda.  
  
-   Bir grid denetiminin düğmesi görünür değilse.  
  
Düğmeyi kullanarak yönergeleri:  
  
-   Bir erişim anahtarı kullanmayın. Klavyeyi kullanarak erişmek için kullanıcı bitişik denetiminden sekme gerekir. Herhangi bir Gözat düğmesi hemen doldurur alan sonra kalan, sekme sırasını olduğundan emin olun. İlk dönemden altında bir alt çizgi hiçbir zaman kullanmayın.  
  
-   Microsoft etkin erişilebilirliği (MSAA) kümesi **adı** özelliğini **Gözat...**  ekranında, bu nedenle (üç nokta dahil olmak üzere) okuyucular bunu "Gözatma türü" ve değil "dot nokta nokta" veya "Dönem Dönem-süresi." olarak okur Yönetilen denetimleri için bu ayarı anlamına gelir **AccessibleName** özelliği.  
  
-   Üç nokta kullanmamanız **[...]**  Gözat eylemi dışındaki düğmesi. Örneğin, gerekirse bir **[yeni...]**  düğmesini ancak iletişim kutusunun tasarlanması gerekir sonra metin için yeterli alan yok.  
  
##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık  
![Düğmeler [Gözat...] boyutlandırma: standart sürüm 75 x 23 piksel, kısa sürüm 26 x 23 piksel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Düğmeler [Gözat...] boyutlandırma
  
![Aralığı [Gözat...] düğmeleri: standart Gözat düğmesi 7 piksel ve ilgili denetim arasındaki aralık arasındaki boşluğu ilgili denetim ve kısa Gözat düğmesini 5 piksel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Aralığı [Gözat...] düğmeleri
  
#### <a name="graphical-buttons"></a>Grafik düğmeleri  
Bazı düğmeleri, her zaman bir grafik görüntüsünü kullanın ve hiçbir zaman alanından tasarruf etmek ve Yerelleştirme sorunları önlemek için metni ekleyin. Bunlar, alan seçicileri ve diğer sıralanabilir listelerinde sıklıkla kullanılır.  
  
> **Not:** kullanıcınız (hiçbir erişim anahtarları vardır) Bu düğme için sekmesinde, bu nedenle bunları mantıklı bir sırada yerleştirin. Harita `name` sürer ve böylece ekran okuyucular düzgün düğmesi eylemi yorumlama eylem düğmenin özelliği.  
  
| İşlev | Düğme |  
| --- | --- |  
| Ekle | ![Grafik "Ekle" düğmesini](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Kaldır | ![Grafik "Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Tümünü Ekle | ![Grafik "Tümünü Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Tümünü Kaldır | ![Grafik "Tümünü Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Yukarı Taşı | ![Grafik "Yukarı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Aşağı Taşı | ![Grafik "Aşağı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Sil | ![Grafik "Sil" düğmesini](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık  
Grafik bir düğme kısa aynıdır için boyutlandırma **[Gözat...]**  düğmesine (26 x 23 piksel cinsinden):  
  
![Grafik Resmi saydam rengi gösteren olmadan ve düğmesine görünümünü](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Grafik Resmi saydam rengi gösteren olmadan ve düğmesine görünümünü
  
### <a name="hyperlinks"></a>Köprüleri  
Köprüler bir Yardım konusu, kalıcı iletişim kutusu veya Sihirbazı açma gibi Gezinti tabanlı eylemler için uygundur. Köprü komutu için kullanılıyorsa, her zaman görünür ve belirgin bir değişiklik için kullanıcı Arabirimi görüntülemelisiniz. Genel olarak, (, iptal, kaydetme ve silme gibi) bir eylem yürütme eylemleri daha iyi bir düğmeyi kullanarak bildirilir.  
  
#### <a name="writing-style"></a>Yazma stili  
İzleyin [Windows masaüstü kılavuzu için kullanıcı arabirimi metinlerini](/windows/desktop/uxguide/text-ui). "Bilgi daha fazla hakkında" kullanmayın "Söyleyin bana daha fazla hakkında" veya "Bu Get help" yapılar. Bunun yerine, Yardım içerik tarafından birincil sorunuzun açısından Yardım bağlantı metni tümce. Örneğin, "**Sunucu Gezgini için bir sunucu nasıl eklerim?**"  
  
#### <a name="visual-style"></a>Görsel stili  
  
-   Köprüler her zaman kullanması gereken [VSColor hizmet](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Köprü doğru biçimlendirilmiş değil ise kırmızı etkinken yanıp veya ziyaret sonra farklı bir renkle gösterilir.  
  
-   Bağlantı bir cümle parça içinde tam bir cümle gibi Filigran olmadıkça durumu üzerine notlarını denetim, alt çizgiler dahil değildir.  
  
-   Alt çizgi, üzerine gelindiğinde görünür olmaması gerekir. Bunun yerine, bağlantı etkin olduğunu kullanıcıya geri bildirim hafif rengi değiştirme ve uygun bağlantıyı imleci ' dir.  
  
##  <a name="BKMK_TreeViews"></a> Ağaç görünümleri  
  
Ağaç görünümleri, karmaşık düzenlemek için bir yol üst-alt gruplar halinde listeler sağlar. Bir kullanıcı genişletebilir veya üst grupları Göster ya da temel alınan alt öğeleri gizle daraltabilirsiniz. Daha fazla eylem sağlamak için her öğe ağacı görünümü içinde seçilebilir.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Ağaç görünümü görsel stili  
  
#### <a name="expanders"></a>Genişleticisi  
Ağaç görünümü denetimleri, genişletici tasarım Windows ve Visual Studio tarafından kullanılan uymalıdır. Her düğüm göster veya gizle temel alınan öğeleri için bir genişletici denetimi kullanır. Genişletici denetimi kullanarak, Windows ve Visual Studio içinde farklı ağaç görünümlerini karşılaşabileceğiniz kullanıcılar için tutarlılık sağlar.  
  
![Doğru: genişletici denetimi kullanarak ağaç görünümü düğümü uygun stilini](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Doğru: bir expander denetimi kullanarak ağaç görünümü düğümünün uygun stili
  
![Yanlış: ağaç görünümü düğümünün hatalı stili](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Yanlış: ağaç görünümü düğümünün hatalı stili
  
#### <a name="selection"></a>Seçim  
Bir düğüm ağacı görünümü içinde seçili olduğunda, vurgulama ağaç görünümü denetiminde tam genişliğine genişletmeniz gerekir. Bu, kullanıcıların seçmiş olduğunuz hangi öğe NET bir şekilde belirlemesine yardımcı olur. Renk seçimi, geçerli Visual Studio temasını yansıtmalıdır.  
  
![Doğru: Seçili düğümün vurgulama ağaç görünümü denetiminin tüm genişliği uyar. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Doğru: Seçili düğümün vurgulama ağaç görünümü denetiminin tüm genişliği uyar.
  
![Yanlış: ağaç görünümü denetiminin tüm genişliği vurgulama Seçili düğümün sığmıyor. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Yanlış: ağaç görünümü denetiminin tüm genişliği vurgulama Seçili düğümün sığmıyor.
  
#### <a name="icons"></a>Simgeler  
Görsel öğeler arasındaki farklar tanımlanmasına yardımcı simgeleri yalnızca ağaç görünümü denetimleri kullanılmalıdır. Genel olarak, simgeleri yalnızca hangi öğelerin türlerini ayırt etmek için bilgi simgeleri taşıyan heterojen listelerinde kullanılmalıdır. Homojen bir listedeki simgeleri kullanarak gürültü sık görülebilir ve kaçınılmalıdır. Bu durumda grubu simgesi (üst) içindeki öğe türü ifade edebilir. Bu kuralın istisnası olarak, simge dinamiktir ve durumunu göstermek için kullanılan olacaktır.  
  
#### <a name="scroll-bars"></a>Kaydırma çubukları  
Kaydırma çubukları, her zaman içerik ağaç görünümü denetiminin içinde sığıyorsa gizlenmelidir. Gizli veya yarı saydam kaydırılabilir bir pencerede ve ağaç görünümünde içeren pencere odaklandığında görünür veya kendisi üzerinde vurgulu ağacı görüntülemek için kaydırma çubuklarını kabul edilebilir olduğu.  
  
![Ağaç görünümü denetiminin sınırları içeriği aştığınız için her iki yatay ve dikey kaydırma çubukları görüntülenir. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Ağaç görünümü denetiminin sınırları içeriği aştığınız için her iki yatay ve dikey kaydırma çubukları görüntülenir.
  
###  <a name="BKMK_TreeViewInteractions"></a> Ağaç görünümü etkileşimleri  
  
#### <a name="context-menus"></a>Bağlam menüleri  
Bir ağaç görünümü düğümü alt menü seçenekleri bağlam menüsü ortaya çıkarabilir. Bu genellikle, bir kullanıcı bir öğeyi sağ veya seçili öğeye sahip bir Windows klavyede menü tuşuna basıldığında gerçekleşir. Düğüm odağı ve seçili önemlidir. Bu, kullanıcının alt ait hangi öğesini tanımlamaya yardımcı olur.  
  
![Kullanıcıya bildirmek için bağlam menüsünü kazançlar odağı hangi öğesi oluştur sahip öğe seçilmedi. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />Kullanıcıya bildirmek için bağlam menüsünü kazançlar odağı hangi öğesi oluştur sahip öğe seçilmedi.
  
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
  
-   **Sağ ok:** bir düğümünü genişletin. Düğüm genişletildikten sonra en yakın sütuna sağ taraftaki gezinme devam etmelidir. Gezinti satırının sonundaki durdurmanız gerekir.  
  
-   **Sekmesi:** yakın hücrenin sağ taraftaki gitmenizi sağlar.  Satırın sonunda, gezinti ve bir sonraki satıra devam eder.  
  
-   **SHIFT + Tab:** yakın hücrenin soldaki gitmenizi sağlar.  Satırın başlangıcında, gezinti önceki satırdaki en sağındaki hücreyi devam eder.  
  
![Visual Studio trid denetiminde](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Visual Studio'da bir trid denetimi