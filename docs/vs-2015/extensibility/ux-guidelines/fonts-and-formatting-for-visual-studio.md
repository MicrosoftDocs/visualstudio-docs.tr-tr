---
title: Yazı Tipleri ve Biçimlendirme
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2afab1da7efb3b444d2c72d1050e2e72c7649f10
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068590"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Yazı tipleri ve Visual Studio için biçimlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> Ortam yazı tipi
 Visual Studio içindeki tüm yazı tiplerini özelleştirme için kullanıcıya sunulmalıdır. Bu temelde aracılığıyla gerçekleştirilir **yazı tipleri ve renkler** sayfasını **Araçlar > Seçenekler** iletişim. Yazı tipi ayarlarını üç ana kategoride şunlardır:

-   **Ortam yazı tipi** — iletişim kutuları, menüler, araç pencereleri ve belge pencereleri de dahil olmak üzere tüm arabirimi öğeleri için kullanılan birincil yazı tipini IDE (tümleşik geliştirme ortamı). Varsayılan olarak, ortam yazı tipi 9 pt Segoe UI'Windows ' ın geçerli sürümlerinde gibi görünen bir sistem yazı tipini bağlıdır. Bir yazı tipi için tüm arabirim öğeleri kullanılarak, bir IDE genelinde tutarlı bir yazı tipi görünümü sağlamaya yardımcı olur.

-   **Metin düzenleyici** — yüzey kod ve diğer metin tabanlı düzenleyiciler Metin Düzenleyicisi'nde özelleştirilebilir olduğunu öğeleri sayfasında **Araçlar > Seçenekler**.

-   **Özel koleksiyonlar** — kullanıcı arabirimi öğeleri özelleştirmesini tasarımlarına için özel yazı tipleri kullanıma sunan Tasarımcı windows yüzey kendi Ayarları sayfasında **Araçlar > Seçenekler**.

### <a name="editor-font-customization-and-resizing"></a>Düzenleyici yazı tipi özelleştirme ve yeniden boyutlandırma
 Kullanıcıların genellikle büyütün veya boyutunun ve/veya genel kullanıcı arabirimi bağımsız kendi tercih göre düzenleyici metin rengi yakınlaştırma. Ortam yazı tipi, şirket içinde ya da bir düzenleyici/designer'ın bir parçası olarak görünebilir öğeleri kullanıldığından, bu yazı tipi sınıflandırmalar biri değiştiğinde Beklenen davranış dikkat edin önemlidir.

 Görünür kullanıcı Arabirimi öğeleri parçası Düzenleyicisi ancak olan oluştururken *içerik*, öğeleri tahmin edilebilir bir biçimde yeniden boyutlandırın. böylece ortam yazı tipini ve metin yazı kullanmak önemlidir.

1.  Kod metin düzenleyicide kod metin yazı tipi ayarla yeniden boyutlandırabilir ve düzenleyici metin yakınlaştırma düzeyi için yanıt.

2.  Arabirimin diğer tüm öğeleri ortam yazı tipi ayarına bağlı ve genel değişiklikleri ortamında yanıtlar. Bu içerir (ancak bunlarla sınırlı değil):

    -   Metin bağlam menüleri

    -   Ampul menüsü metin, hızlı gibi bir düzenleyici kenarlığı metin düzenleyicisi bölmesine bulun ve bölmesine gidin

    -   Find dosyalar ya da yeniden düzenleyin gibi iletişim kutularında etiket metni

### <a name="accessing-the-environment-font"></a>Ortam yazı tipi erişme
 Yöntemini çağırarak, WinForms ya da yerel kod içinde ortam yazı tipi erişilebilir **IUIHostLocale::GetDialogFont** SID_SUIHostLocale hizmet arabirimden sorgulama sonra.

 Windows Presentation Foundation (WPF) iletişim penceresi sınıfınızı kabuğun türetilen **DialogWindow** sınıfı yerine WPF'nin **penceresi** sınıfı.

 XAML içinde kod şöyle görünür:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (Değiştir `Microsoft.VisualStudio.Shell.11.0` MPF dll geçerli sürümüyle.)

 İletişim kutusunu görüntülemek için çağrı "**ShowModal()**" sınıfındaki **ShowDialog()**. **ShowModal()** Kabuğu'nda doğru kalıcı duruma ayarlar, iletişim kutusunun üst penceresine ve benzeri ortalanır sağlar.

 Kod aşağıdaki gibidir:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** bool döndürür? (boş değer atanabilir Boolean) ile **DialogResult**, kullanılabilen gerekirse. Dönüş değeri ile iletişim kapatılırsa true **Tamam**.

 Bir iletişim kutusu değil ve barındırılan bazı WPF UI kendi görüntülemek gerekiyorsa **HwndSource**, bir açılan pencere veya Win32/WinForms ana penceresi penceresinin WPF alt penceresi gibi ayarlamanız gerekir **FontFamily**ve **FontSize** kök öğesinde, bir WPF öğesi. (Kabuk ana penceresinde özelliklerini ayarlar, ancak bunlar bir HWND da devralınan değil). Kaynakları, özellikleri, şöyle bağlanabilir sağlar:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

###  <a name="BKMK_Formatting"></a> Biçimlendirme (ölçeklendirme/kalın) başvurusu
 Bazı iletişim kutularını kalın olarak belirli bir metin veya dışında ortam yazı tipi boyutu gerektirir. Yazı tipleri ortam yazı tipi daha büyük, daha önce "ortam yazı tipi + 2" olarak kodlanmış veya benzer. Sağlanan kod parçacıkları yüksek DPI monitör desteği ve görünen metin her zaman doğru boyut ve Ağırlık (açık veya Semilight gibi) göründüğünden emin olun.

> **Not: biçimlendirme uygulamak için önce bulunan yönergeleri takip ettiğiniz sağlayın [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Ortam yazı tipi ölçeklendirmek için TextBlock ya da belirtildiği gibi bir etiket stilini ayarlayın. Her biri, doğru kullanıldığında, bu kod parçacıkları uygun boyut ve Ağırlık çeşitlemeleri dahil olmak üzere doğru yazı tipi oluşturur.

 "Yerleşik vsuı" Microsoft.VisualStudio.Shell ad alanına bir başvuru olduğu:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>%375 ortam yazı tipi + açık
 **Olarak görünür:** 34 pt Segoe UI Light

 **Kullanım için:** (nadir) benzersiz markalı kullanıcı Arabirimi, gibi başlangıç sayfası

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>%310 ortam yazı tipi + açık
 **Olarak görünür:** 28 pt Segoe UI Light

 **Kullanım için:** büyük imza iletişim başlıklar, ana raporlarda başlığı

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>% 200'ortam yazı tipi + Semilight
 **Olarak görünür:** 18 punto Georgia Segoe UI Semilight

 **Kullanım için:** başlıklar, küçük ve orta ölçekli kutularındaki başlıkları

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>%155 ortam yazı tipi
 **Olarak görünür:** 14 pt Segoe UI

 **Kullanım için:** belgede bölüm başlıkları yanı sıra kullanıcı Arabirimi veya raporları

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>% 133 ortam yazı tipi
 **Olarak görünür:** 12 pt Segoe UI

 **Kullanım için:** imza iletişim kutuları ve belge daha küçük bir alt başlıklar yanı sıra, kullanıcı Arabirimi

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>%122 ortam yazı tipi
 **Olarak görünür:** 11 pt Segoe UI

 **Kullanım için:** bölüm başlıkları imza iletişim kutuları, üst düğümleri ağaç görünümünde, dikey sekme gezinme

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın
 **Olarak görünür:** kalın 9 pt Segoe UI

 **Kullanım için:** etiketleri ve imza iletişim kutuları, raporlar ve belge içinde alt başlıklar yanı sıra kullanıcı Arabirimi

 **Yordam kodu:** burada "textBlock" önceden tanımlanmış bir TextBlock ve "etiket" önceden tanımlanmış bir etiket.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** TextBlock veya etiket stili gösterilen şekilde ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Yerelleştirilebilir stilleri
 Bazı durumlarda, çevirmenlerin kalın metin Doğu Asya dilleri için kaldırma gibi farklı yerel ayarlar için yazı tipi stillerini değiştirmeniz gerekecektir. Yazı tipi stillerini yerelleştirmesi mümkün kılmak için bu stilleri .resx dosyasının içinde olması gerekir. Bunu gerçekleştirmek ve yine de Visual Studio form Tasarımcısı'nda yazı tipi stilleri düzenlemek için en iyi yolu, tasarım zamanında yazı tipi stillerini açıkça ayarlamaktır. Bu tüm yazı tipi nesnesi oluşturur ve üst yazı tipi devralma sonu görünebilir olsa da, yalnızca FontStyle özelliğine yazı ayarlamak için kullanılır.

 İletişim formun yeteneklerinizi çözümüdür **FontChanged** olay. İçinde **FontChanged** olayı, tüm denetimler yol ve yazı tipleriyle ayarlanmış olup olmadığını denetleyin. Ayarlanırsa, formun yazı tipi ve denetimin önceki yazı tipi stili göre yeni bir yazı tipiyle değiştirin. Bu kod örneğidir:

```
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Bu kodu kullanmadan, formun yazı tipi güncelleştirildiğinde, yazı tipi denetimleri de güncelleştirir garanti eder. İletişim kutusunun bir örneğini almak başarısız olabilir çünkü bu yöntem Ayrıca formun oluşturucudan çağrılmalıdır **IUIService** ve **FontChanged** olay asla harekete. Takma **FontChanged** yeni yazı tipi iletişim kutusu zaten açık olsa bile dinamik olarak çekmek iletişim kutularını izin verir.

### <a name="testing-the-environment-font"></a>Test ortamı yazı tipi
 Kullanıcı Arabirimi ortam yazı tipi kullanarak ve boyutu ayarlara uyar sağlamak için açık **araçları > Seçenekler > ortam > yazı tipleri ve renkler** ve altında "Ortam yazı tipi" seçin "ayarlarını göster:" açılır menüsünde.

 ![Yazı tipleri ve renkler sayfa araçlarındaki &#62; Seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "a_OptionsFonts 0201")

 **Yazı tipleri ve renkler ayarlarında Araçlar > Seçenekler iletişim kutusu**

 Yazı tipi çok varsayılandan farklı bir değere ayarlayın. Bu, UI güncelleştirilmediği belirginleştirmek için Serif (örneğin, "Times yeni Roman") ile bir yazı tipi seçin ve çok büyük bir boyuta ayarlayın. Ardından ortamın uyar emin olmak için kullanıcı Arabirimi test edin. Lisans iletişim kutusunu kullanarak bir örnek aşağıda verilmiştir:

 ![Kullanmayan ortam yazı tipi iletişim kutusu örneği](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "b_WrongFontDialog 0201")

 **Ortam yazı tipi uymaz UI metni örneği**

 Bu durumda, "Kullanıcı bilgileri" ve "Ürün bilgileri" yazı uyarak değil. Bazı durumlarda bu bir açık bir tasarım seçiminin olabilir ancak açık yazı tipi redline belirtimleri bir parçası olarak belirtilmediği takdirde bir hata olabilir.

 Yazı tipi sıfırlamak için "kullanımı" altında Varsayılanlar **Araçlar > Seçenekler > ortam > yazı tipleri ve renkler**.

##  <a name="BKMK_TextStyle"></a> Metin stili
 Metin stili yazı tipi boyutu, ağırlığı ve büyük/küçük harf ifade eder. Uygulama Kılavuzu için bkz. [ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Metin büyük/küçük harf

#### <a name="all-caps"></a>Tümü büyük harf
 Tüm harflerini büyük başlıklar ve etiketler Visual Studio için kullanmayın.

#### <a name="all-lowercase"></a>Tümü küçük harf
 Başlıklar ve etiketler Visual Studio'da tamamen küçük harflerden kullanmayın.

#### <a name="sentence-and-title-case"></a>Tümce ve başlık çalışması
 Visual Studio'da metin ilk harfler büyük ya da durum bağlı olarak belirli bir cümle kullanmanız gerekir.

|Başlık çalışması için kullanın:|Cümle için kullanın:|
|-------------------------|----------------------------|
|İletişim başlığı|Etiketler|
|Grup kutuları|Onay kutuları|
|Menü öğeleri|Radyo düğmeleri|
|Bağlam menüsü öğeleri|Liste kutusu öğeleri|
|Düğmeler|Durum çubukları|
|Tablo etiketleri||
|Sütun üstbilgileri||
|Araç ipuçları||

##### <a name="title-case"></a>İlk harfler büyük
 Başlık, hangi çoğunu veya tümünü bir tümce içinde bir kelimelerin ilk harflerini büyük harfe stil durumdur. Visual Studio'da ilk harfler büyük dahil olmak üzere birçok öğeleri için kullanılır:

- **Araç ipuçları.** Örnek: "Seçili öğelerin önizlemesini görüntüle"

- **Sütun üstbilgileri.** Örnek: "Sistem"yanıtı

- **Menü öğeleri.** Örnek: "Tümünü Kaydet"

  İlk harfler büyük kullanırken zaman sözcükler büyük harf ve bunları küçük bırakmak ne zaman için yönergeler şunlardır:

|Büyük harfe|Açıklamalar ve örnekler|
|---------------|---------------------------|
|Tüm adlar||
|Tüm fiiller|"Is" ve "olması için" diğer biçimleri gibi|
|Tüm zarflar|"Den" ve "," dahil olmak üzere|
|Tüm sıfat|"This" ve "," dahil olmak üzere|
|Tüm zamirler|İyelik eki dahil olmak üzere "," de "Olduğu gibi" gelebildiği, bir kısaltma "," ve fiili "is"|
|Bölümleri konuşma ne olursa olsun, ilk ve son sözcükler||
|Fiili ifade parçası olan edat|"Tüm Windows kapatmadan" veya "sisteminin kapatılmasını"|
|Tüm harflerini bir kısaltma|HTML, XML, URL, IDE, RGB|
|İkinci bir isim veya uygun sıfat ise ya da eşit ağırlık sözcükler varsa bir bileşik sözcük word|Çapraz, ön Microsoft yazılım okuma/yazma erişimi, çalışma zamanı|

|Küçük|Örnekler|
|---------------|--------------|
|Bir bileşik sözcük başka bir konuşma bölümü veya ilk sözcük değiştirerek bir participle ise ikinci sözcüğü|Sınav zamanı kapatması nasıl yapılır konuları|
|Bir başlık ilk sözcük olmadığı sürece, makaleler|bir,|
|Koordinat bağlaçlar|Ayrıca, ancak, nor, veya|
|Edat sözcükten oluşan dört veya daha az harf fiili tümcecik dışında|içine, üzerine olarak için üzerinde en üstüne çıkış,|
|"Hedef" bir çizilmesinin ifadeye kullanıldığında|"Sabit Disk biçimine"|

##### <a name="sentence-case"></a>Normal tümce düzeni
 Cümle, yazma, cümlenin yalnızca ilk sözcük büyük harfle, tüm uygun isimleri ve gelebildiği birlikte için standart büyük/küçük harf yöntemidir "I." Genel olarak, cümle okumak özellikle olduğunda içerik bir makine tarafından çevrilir dünya çapında bir kitle için daha kolay olur. Cümle için kullanın:

1.  **Durum çubuğu iletileri.** Bu basit, kısa ve durum bilgileri sağlar. Örnek: "proje dosyası yükleniyor"

2.  **Diğer tüm kullanıcı Arabirimi öğeleri**dahil etiketleri, onay kutuları, radyo düğmeleri ve liste kutusu öğeleri. Örnek: "tüm öğeler Select listesinde"

### <a name="text-formatting"></a>Metin biçimlendirme
 Visual Studio 2013'te biçimlendirme varsayılan metin tarafından kontrol edilir bir [ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Bu hizmet bir IDE (tümleşik geliştirme ortamı) boyunca tutarlı yazı tipi görünümünü sağlar ve kullanıcılarınız için tutarlı bir deneyim sağlamak için kullanmalısınız.

 Visual Studio yazı tipi hizmet tarafından kullanılan varsayılan boyutu, Windows gelir ve 9 pt görünür.

 Ortam yazı tipinin biçimlendirme uygulayabilirsiniz. Bu konu, nasıl ve nerede kapsar stilleri kullanmak için. Uygulama bilgileri için başvurmak [ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Kalın metin
 Kalın metin, Visual Studio'da gerektiğinde kullanılır ve için ayrılmış olması gerekir:

-   Sihirbazlar soru etiketler

-   Çözüm Gezgini'nde etkin proje belirleme

-   Özellikler araç penceresinde geçersiz kılınmış değerleri

-   Visual Basic Düzenleyicisi açılır listelerindeki belirli olaylar

-   Belge Anahattı web sayfaları için sunucu tarafından oluşturulan içeriği

-   bölüm başlıkları karmaşık iletişim veya Tasarımcısı kullanıcı Arabirimi

#### <a name="italics"></a>İtalik
 Visual Studio, italik veya kalın italik metin kullanmaz.

#### <a name="color"></a>Renk

-   Mavi (gezinti ve komut vermeye genel) köprüler için ayrılmıştır ve yönlendirme için asla kullanılmamalıdır.

-   Daha büyük başlıklar (ortam yazı tipi veya daha fazla %155 x), bu amaçlar için renkli:

    -   Visual Studio UI imzası Visual geçirmeye itraz et sağlamak için

    -   Dikkat çekmek için belirli bir alana

    -   Standart koyu gri/siyah ortam metin renkten Tahliye sunmak için

-   Mevcut Visual Studio markası renkleri, öncelikli olarak ana mor #FF68217A başlıklarının rengi faydalanın.

-   Renk başlıklarında kullanırken uymalısınız [Windows renk yönergeleri](https://msdn.microsoft.com/library/dn742482.aspx)Karşıtlık oranı ve diğer erişilebilirlik konuları dahil olmak üzere.

### <a name="font-size"></a>Yazı tipi boyutu
 Visual Studio kullanıcı Arabirimi tasarımı, daha fazla boşluk ile daha açık bir görünümünü sunar. Mümkünse, chrome ve başlık çubukları sınırlı veya kaldırılan. Bilgi yoğunluklu Visual Studio'da bir gereksinim olsa da, tipografi önemli olan, daha açık satır aralığı ve yazı tipi boyutu ve ağırlıklarını çeşitlemesi Otomasyona olmaya devam eder.

 Aşağıdaki tablolarda, tasarım ayrıntıları ve kullanılan Visual Studio'da görünen yazı tipleri için görsel örnekler içerir. Boyut ve Ağırlık, Semilight veya görünümlerini kodlanmış ışığı gibi bazı görünen yazı tipi farklılıklar vardır.

 Tüm görüntü yazı tipleri için kod parçacıkları uygulama bulunabilir [(ölçeklendirme/kalın) başvuru biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>%375 ortam yazı tipi + açık

|||
|-|-|
|**Kullanım:** nadir. Benzersiz markalı yalnızca kullanıcı Arabirimi.<br /><br /> **Yapın:**<br /><br /> -Cümle kullanma<br />-Her zaman hafif kullanın<br /><br /> **Yapma:**<br /><br /> -Kullanımı için kullanıcı Arabirimi dışında imza başlangıç sayfası gibi kullanıcı Arabirimi<br />-Kalın, italik veya Kalın İtalik<br />-Gövde metni kullan<br />-Araç pencerelerini kullanma|**Olarak görünür:** 34 pt Segoe UI Light<br /><br /> **Görsel örnek:**<br /><br /> *Şu anda kullanılmıyor. Başlangıç sayfası kullanılabilir.*|

#### <a name="310-environment-font--light"></a>%310 ortam yazı tipi + açık

|||
|-|-|
|**Kullanım:**<br /><br /> -Daha büyük başlıkta imza iletişim kutuları<br />-Ana rapor başlığı<br /><br /> **Yapın:**<br /><br /> -Cümle kullanma<br />-Her zaman hafif kullanın<br /><br /> **Yapma:**<br /><br /> -Kullanımı için kullanıcı Arabirimi dışında imza başlangıç sayfası gibi kullanıcı Arabirimi<br />-Kalın, italik veya Kalın İtalik<br />-Gövde metni kullan<br />-Araç pencerelerini kullanma|**Olarak görünür:** 28 pt Segoe UI Light<br /><br /> **Görsel örnek:**<br /><br /> ![%310 ortam yazı tipi örneği &#43; ışık başlık](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202 a_EF310")|

#### <a name="200-environment-font--semilight"></a>% 200'ortam yazı tipi + Semilight

|||
|-|-|
|**Kullanım:**<br /><br /> -Başlıklar<br />-Küçük ve orta ölçekli kutularındaki başlıklar<br /><br /> **Yapın:**<br /><br /> -Cümle kullanma<br />-Her zaman Semilight ağırlık kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya Kalın İtalik<br />-Gövde metni kullan<br />-Araç pencerelerini kullanma|**Olarak görünür:** 18 punto Georgia Segoe UI Semillight<br /><br /> **Görsel örnek:**<br /><br /> ![% 200'ortam yazı tipi örneği &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202 b_EF200")|

#### <a name="155-environment-font"></a>%155 ortam yazı tipi

|||
|-|-|
|**Kullanım:**<br /><br /> -Belgedeki bölüm başlıkları yanı sıra kullanıcı Arabirimi<br />-Raporlar<br /><br /> **:** Cümle kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya Kalın İtalik<br />-Gövde metni kullan<br />-Visual Studio standart denetimleri kullanın<br />-Araç pencerelerini kullanma|**Olarak görünür:** 14 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Örnek %155 ortam yazı tipi başlığının](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202 c_EF155")|

#### <a name="133-environment-font"></a>% 133 ortam yazı tipi

|||
|-|-|
|**Kullanım:**<br /><br /> -İmza iletişim kutularındaki daha küçük bir alt başlıklar<br />-Daha küçük alt başlıklar belgedeki yanı sıra kullanıcı Arabirimi<br /><br /> **:** Cümle kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya Kalın İtalik<br />-Gövde metni kullan<br />-Visual Studio standart denetimleri kullanın<br />-Araç pencerelerini kullanma|**Olarak görünür:** 12 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Örnek %133 ortam yazı tipi başlığının](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202 d_EF133")|

#### <a name="122-environment-font"></a>%122 ortam yazı tipi

|||
|-|-|
|**Kullanım:**<br /><br /> -İmza iletişim kutularındaki bölüm başlıkları<br />-Ağaç görünümünde üst düğümleri<br />-Dikey sekme gezinme<br /><br /> **:** Cümle kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya Kalın İtalik<br />-Gövde metni kullan<br />-Visual Studio standart denetimleri kullanın<br />-Araç pencerelerini kullanma|**Olarak görünür:** 11 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Örnek %122 ortam yazı tipi başlığının](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202 e_EF122")|

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın

|||
|-|-|
|**Kullanım:**<br /><br /> -Etiketler ve imza iletişim kutularındaki alt başlıklar<br />-Etiketler ve raporlarında alt başlıklar<br />-Etiketler ve belge içinde alt başlıklar yanı sıra, kullanıcı Arabirimi<br /><br /> **Yapın:**<br /><br /> -Cümle kullanma<br />-Kalın ağırlık kullanma<br /><br /> **Yapma:**<br /><br /> -Yatık veya Kalın İtalik<br />-Gövde metni kullan<br />-Visual Studio standart denetimleri kullanın<br />-Araç pencerelerini kullanma|**Olarak görünür:** kalın 9 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Ortam yazı tipi örneği &#43; kalın başlık](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202 f_EFB")|

#### <a name="environment-font"></a>Ortam yazı tipi

|||
|-|-|
|**Kullanım:** diğer tüm metni<br /><br /> **:** Cümle kullanın<br /><br /> **Sağlamadığı:** italik veya Kalın İtalik|**Olarak görünür:** 9 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Ortam yazı tipi örneği](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202 g_EF")|

### <a name="padding-and-spacing"></a>Doldurma ve aralık
 Başlıklar, bunları uygun vurgulamak için onları boşluk gerektirir. Bu alanı noktası boyutu ve yatay bir kuralı ya da ortam yazı tipi metin satırı gibi başlık yaklaştı diğerlerine bağlı olarak değişir.

-   İdeal doldurma bir başlığın kendisi büyük harf karakter yükseklik alanı %90 olmalıdır. Örneğin, 26 pt cap yüksekliğini 28 pt Segoe UI Light başlığı var ve doldurma yaklaşık 23 pt ya da yaklaşık olarak 31 piksel olması gerekir.

-   Başlık en az boşluk, büyük harf karakter yüksekliği yüzdesi 50 olmalıdır. Daha az alan başlığı bir kural veya diğer sıkı sığdırma öğesi ile birlikte kullanılabilir.

-   Kalın ortam yazı tipi, metin, varsayılan satır yüksekliği boşlukları ve doldurma izlemelidir.

## <a name="see-also"></a>Ayrıca Bkz.
 [MSDN: Yazı tiplerini (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: kullanıcı arabirimi metinlerini (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
