---
title: Renkler ve stil Visual Studio için | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d8285ad08a9ad83ecd137223459a6b29cb7ae69
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561718"
---
# <a name="colors-and-styling-for-visual-studio"></a>Renkler ve stil Visual Studio için

## <a name="use-color-in-visual-studio"></a>Visual Studio'da renk kullanın

Visual Studio'da düzenleme gibi bir iletişim aracı olarak birincil renk kullanılır. Renk en düşük düzeyde kullanın ve istediğiniz durumlar için rezerve:

- Anlamı veya ilişkisi (örneğin, bir platform veya dili değiştiriciler) iletişim

- Dikkatini (örneğin, bir durum değişikliği gösteren)

- Okunabilirliğin artırılması ve kullanıcı arabirimini gezinmek için yer işareti sağlayın

- Desirability artırın

Visual Studio kullanıcı Arabirimi öğeleri için renk atamak için çeşitli seçenekler mevcuttur. Bazen bu şekle zor olabilir out hangi seçeneği kullanmak için beklenen olduğunuz veya doğru şekilde kullanma. Bu konuda size yardımcı olur:

- Visual Studio'daki renkler tanımlamak için kullanılan sistemler ve farklı Hizmetleri anlayın.

- Belirli bir öğeyi doğru seçeneğini belirleyin.

- Doğru şekilde seçmiş olduğunuz seçeneğini kullanın.

> [!NOTE]
> Asla sabit kodlamayın onaltılık, RGB veya sistem renkleri, kullanıcı Arabirimi öğeleri için. Hizmetleri kullanarak hue ayarlama esneklik sağlar. Ayrıca, hizmeti olmadan, temasını değiştirdikten yeteneklerinden yararlanmak mümkün olmayacaktır [VSColor hizmet](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio için renk atamak için yöntemleri arabirim öğeleri

Kullanıcı Arabirimi öğeleri için en uygun yöntemi seçin.

| Kullanıcı Arabirimi | Yöntem | Bunlar nelerdir? |
| --- | --- | --- |
| Gömülü veya tek başına iletişim kutuları. | **Sistem renkleri** | Renk ve kullanıcı Arabirimi öğeleri görünümünü tanımlamak işletim sisteminin sistem adları ortak iletişim kutusu denetimleri ister. |
| Genel VS ortamı ile tutarlı olmasını istediğiniz özel kullanıcı Arabirimi varsa ve kategori ve anlam paylaşılan belirteçlerin eşleşen kullanıcı Arabirimi öğeleri. | **Ortak paylaşılan renkler** | Belirli kullanıcı Arabirimi öğeleri için var olan önceden tanımlanmış bir rengi belirteci adları |
| Ayrı özellik ya da Özellikler grubunu olduğunu ve benzer öğeleri için paylaşılan bir renk yok. | **Özel renkler** | Bir alana özgü olan ve diğer kullanıcı Arabirimi ile paylaşılacak düşünülmemiştir renk belirteç adı |
| Kullanıcı Arabirimi veya içerik (örneğin, metin düzenleyiciler veya özelleştirilmiş Tasarımcı pencereleri için) özelleştirmek son kullanıcı izin vermek istediğiniz. | **Son kullanıcı özelleştirme**<br /><br />**(Araçları &gt; Seçenekleri iletişim kutusu)** | "Yazı tiplerini ve renkleri" sayfasında tanımlanan ayarlar **Araçları &gt; seçenekleri** iletişim kutusu veya belirli bir kullanıcı Arabirimi özelliği için özel bir sayfa. |

### <a name="visual-studio-themes"></a>Visual Studio temalar

Visual Studio özellikleri üç farklı renk temaları: açık, koyu ve mavi. Ayrıca, bir sistem genelinde renk teması erişilebilirlik için tasarlanmış olan yüksek karşıtlık modunu algılar.

Kullanıcılar, Visual Studio'nun ilk kullanım sırasında bir tema seçmeniz istenir ve Temalar giderek daha sonra geçiş yapmak **Araçları &gt; seçenekleri &gt; ortam &gt; genel** ve yeni bir temayı seçme "renk teması" açılan menüsü.

Kullanıcılar ayrıca tüm sistemlerini birden çok yüksek karşıtlıklı tema birine geçiş yapmak için Denetim Masası'nı kullanabilirsiniz. Ardından kullanıcı yüksek karşıtlıklı bir temayı seçerse, kullanıcının yüksek karşıtlık modundan çıktığında için tema değişiklikler kaydedilir ancak Visual Studio renkli tema Seçici Visual Studio'daki renkler artık etkiler. Yüksek Karşıtlık modunu kullanmak hakkında daha fazla bilgi için bkz: [seçme yüksek karşıtlık renklerini](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>VSColor hizmeti

Visual Studio UI öğelerinizi renk değerlerinin her Visual Studio temasını renk değerleri içeren bir adlandırılmış giriş bağlama olanak tanıyan VSColor hizmet olarak bilinen bir ortam rengi hizmetini sağlar. Bu renklerin geçerli kullanıcı tarafından seçilen tema veya sistem yüksek karşıtlık modunu yansıtacak şekilde otomatik olarak değiştirilir sağlar. Hizmetinin tüm renk teması ilgili değişiklikleri yürütmesinin tek bir yerde ele alınır ve ortak paylaşılan renkler hizmetinden kullanıyorsanız, kullanıcı Arabirimi otomatik olarak Visual Studio'nun gelecek sürümlerinde yeni temalar yansıtır anlamına gelir.

### <a name="implementation"></a>Uygulama

Visual Studio kaynak kod belirteci adları ve her teması ilgili renk değerleri listeleri içeren birden fazla paket tanımlama dosyaları içerir. Bu paket tanım dosyalarında tanımlanan VSColors renk hizmet okur. Bu renklerin XAML biçimlendirmede veya kodda başvurulan ve aracılığıyla yüklenen `IVsUIShell5.GetThemedColor` yöntemi veya DynamicResource eşleme.

### <a name="system-colors"></a>Sistem renkleri

Ortak Denetimler, varsayılan olarak sistem renkleri başvuru. Sistem renkleri, oluştururken bir gömülü veya tek başına iletişim gibi kullanmak için kullanıcı Arabirimi istiyorsanız herhangi bir şey gerekmez.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor hizmetinde ortak paylaşılan renkler

Genel Visual Studio ortamının arabirimi öğelerinizin yansıtmalıdır. Tasarladığınız UI bileşeni için uygun olan ortak paylaşılan renkler yeniden kullanarak, arabirimin diğer Visual Studio arabirimleri ile tutarlı olduğunu ve Temalar eklendiğinde veya güncelleştirildiğinde renkleri otomatik olarak güncelleştirecektir emin olun.

Ortak paylaşılan renkler kullanmadan önce doğru kullanma hakkında anladığınızdan emin olun. Yanlış kullanımı ortak paylaşılan renkler, kullanıcılarınız için tutarsız, bozucu veya karmaşık bir deneyim neden olabilir.

### <a name="user-customizable-colors"></a>Kullanıcı tarafından özelleştirilebilir renkleri

Bkz: [son kullanıcılar için renk gösterme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Bazı durumlarda, bir kod Düzenleyicisi'ni veya tasarım yüzeyine oluştururken gibi kullanıcı Arabirimi, özelleştirmek son kullanıcının izni isteyeceksiniz. Özelleştirilebilir kullanıcı Arabirimi bileşenleri bulunduğunda **yazı tipleri ve renkler** bölümünü **Araçları &gt; seçenekleri** iletişim kutusunda, burada kullanıcıların tercih edebilir ön plan rengini, arka plan rengi veya her ikisini de değiştirin.

![Araçlar &gt; Seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "a_ToolsOptionsDialog 0301")<br />Araçlar &gt; Seçenekleri iletişim kutusu

##  <a name="BKMK_TheVSColorService"></a> VSColor hizmeti

Visual Studio VSColor hizmeti veya kabuk renk hizmeti olarak da bilinir bir ortam rengi hizmeti sağlar. Bu hizmet, kullanıcı Arabirimi öğeleri renk değerlerini ayarlamak için her bir Tema renkleri içeren bir ad-değer rengi bağlamak sağlar. Renkleri otomatik olarak geçerli bir kullanıcı tarafından seçilen tema yansıtacak şekilde değişir ve böylece kullanıcı Arabirimi ortam rengi hizmetine bağlı yeni temalarınızı gelecekte Visual Studio sürümlerini tümleştirme VSColor hizmeti tüm kullanıcı Arabirimi öğeleri için kullanılmalıdır.

### <a name="how-the-service-works"></a>Hizmeti nasıl çalışır?

Ortam renk hizmet için kullanıcı Arabirimi bileşeninin .pkgdef VSColors tanımlanan okur. Bu VSColors ardından XAML işaretleme veya kod içinde başvurulan ve aracılığıyla yüklenen `IVsUIShell5.GetThemedColor` veya `DynamicResource` eşleme.

![Ortam renk hizmet mimarisi](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Ortam renk hizmeti mimarisi

### <a name="accessing-the-service"></a>Hizmete erişim

Erişim, ne tür bir renk belirteçler bağlı olarak VSColor hizmetini kullanıyor ve kod türüne sahip birkaç farklı yolu vardır.

#### <a name="predefined-environment-colors"></a>Önceden tanımlanmış ortam renkleri

##### <a name="from-native-code"></a>Yerel koddan

Kabuk erişimi sunan bir hizmet sağlar `COLORREF` renkler. Hizmet/arabirimi şöyledir:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

' % S'dosyasında VSShell80.idl, numaralandırma `__VSSYSCOLOREX` Kabuk renk sabiti vardır. Bunu kullanmak için dizin değeri değerlerden birini geçirin `enum __VSSYSCOLOREX` belgelenmiş, MSDN veya Windows Sistem API'si, sayı, normal bir dizin `GetSysColor`, kabul eder. Bunun yapılması, ikinci parametre kullanılması gereken renk RGB değeri geri alır.

Kalem veya yeni bir renk ile fırça depolanıyorsa gerekir `AdviseBroadcastMessages` (dışına Visual Studio Kabuğu) ve dinler `WM_SYSCOLORCHANGE` ve `WM_THEMECHANGED` iletileri.


Yerel kodda renk hizmete erişmek için bu benzer bir arama yapacağız:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF` Tarafından döndürülen değerler `GetVSSysColorEx()` içeren yalnızca R, G, B bileşenlerinin bir Tema rengi. Bir tema girişi saydamlık kullanıyorsa, alfa kanalı değeri döndürmeden önce göz ardı edilir. Bu nedenle, ilgilenilen ortam rengi saydamlık kanal olduğu önemli bir yerde kullanılmalıdır, kullanmanız `IVsUIShell5.GetThemedColor` yerine `IVsUIShell2::GetVSSysColorEx`, bu konunun ilerleyen kısımlarında açıklandığı gibi.

##### <a name="from-managed-code"></a>Yönetilen koddan

VSColor hizmete aracılığıyla yerel koda erişim oldukça basittir. Yönetilen kod ile çalışıyorsanız, ancak hizmetin nasıl kullanılacağını belirlemek zor olabilir. Aklınızda C# kod parçacığı bu işlemi gösteren şöyledir:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Visual Basic'te çalışıyorsanız, kullanın:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF kullanıcı Arabiriminden

Visual Studio renkleri aracılığıyla uygulamanın içinde verilen değerleri adlarınıza bağlayabileceğiniz `ResourceDictionary`. Renk tablosunu kaynaklardan kullanarak yanı sıra XAML ortam yazı tipi verilerini bağlama örneği aşağıdadır.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Yardımcı sınıflar ve yöntemler yönetilen kod için

Yönetilen kod için yönetilen paket çerçevesini kitaplığı kabuğun (`Microsoft.VisualStudio.Shell.12.0.dll`) birkaç teması renkleri kullanımını etkinleştirme yardımcı sınıfları içerir.

Yardımcı yöntemler de `Microsoft.VisualStudio.Shell.VsColors` MPF sınıfında dahil `GetThemedGDIColor()` ve `GetThemedWPFColor()`. Bu yardımcı yöntemler bir tema giriş olarak renk değeri döndürmesi `System.Drawing.Color` veya `System.Windows.Media.Color`, WinForms ya da WPF kullanıcı Arabirimi kullanılacak.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

Sınıfı, belirli bir WPF renk kaynak anahtarı, VSCOLOR tanımlayıcıları almak için de kullanılabilir ya da tam tersi.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Yöntemlerinin `VsColors` sınıfı VSColor hizmet çağrılır, her zaman renk değeri döndürmek için sorgu. Bir renk değeri olarak almak için `System.Drawing.Color`, daha iyi performans yöntemlerini kullanmayı alternatiftir `Microsoft.VisualStudio.PlatformUI.VSThemeColor` sınıfını VSColor hizmetinden elde edilen renk değerleri önbelleğe alır. Sınıf, dahili olarak Kabuk yayın iletilerini olaylara abone olur ve tema değiştirme olay meydana geldiğinde, önbelleğe alınan değeri atar. Ayrıca, sınıf sağlar. bir. Tema değişikliklere abone olmak için NET dostu olay. Kullanma `ThemeChanged` yeni bir işleyici eklemek ve olay `GetThemedColor()` renk elde etmek için yöntemi değerleri `ThemeResourceKeys` ilgi. Örnek kod şu şekilde görünebilir:

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

##  <a name="BKMK_ChoosingHighContrastColors"></a> Yüksek Karşıtlık renklerini seçme

### <a name="overview"></a>Genel Bakış

Windows, metin ve arka plan görüntüleri, renk karşıtlığını artırmak birçok yüksek karşıtlık sistem düzeyindeki temayla öğeler ekranda farklı daha görünür hale kullanır. Erişilebilirlik nedeniyle, kullanıcılar yüksek karşıtlıklı tema arasında geçiş yaptığınızda Visual Studio arabirimi öğeleri doğru bir şekilde yanıt vermesini önemlidir.

Sistem renkleri olması, yüksek karşıtlıklı tema için kullanılabilir. Sisteminizi rengi adları seçerken, aşağıdaki ipuçlarını unutmayın:

- **Aynı semantik anlama sahiptir sistem renkleri seçin** , renklendirme öğesi olarak. Örneğin, ister bir pencere içinde metin için yüksek karşıtlık renk seçim, WindowText ve değil ControlText kullanın.

- **Ön plan/arka plan çiftlerini seçin** birlikte veya renk seçtiğiniz tüm yüksek karşıtlık Temalar çalışacağından emin emin olmayacaktır.

- **Kullanıcı arabiriminin hangi bölümlerinin en önemli olduğunu belirlemek ve alanlara göze emin olun.** Farklı içerik alanların hiçbir renk çeşitleri olduğundan güçlü renkler kullanımını içerik alanları tanımlamak için ortak, bu nedenle, çok küçük farklılıklar renk tonunu normalde ayırt edebilir, ayrıntı kaybedersiniz.

### <a name="system-color-set"></a>Sistem renk kümesi

Tabloya [WPF ekibi blogu: SystemColors başvuru](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) sistem renk adlarını ve karşılık gelen tonları her tema görüntülenen tam kümesini gösterir.

Bu uygulama için kullanıcı Arabirimi, renkler kümesi sınırlı olduğunda *bekleniyor "normal" Temalar da mevcut İnce ayrıntılar kaybedersiniz*. Araç penceresi içindeki alanları ayırmak için kullanılan ince gri renkli kullanıcı arabiriminin bir örnek aşağıda verilmiştir. Yüksek karşıtlık modunda görüntülenen aynı penceresi ile birlikte kullanıldığında, aynı hue arka planlar olan ve bu alanların Kenarlıklar kenarlık ile tek başına gösterilir görebilirsiniz:

![Nasıl ince Ayrıntılar örneği, yüksek karşıtlıklı kayboluyor](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Nasıl ince Ayrıntılar örneği, yüksek karşıtlıklı kayboluyor

#### <a name="choosing-text-colors-in-an-editor"></a>Bir düzenleyicide metin renklerini seçme

Renklendirilmiş metin, düzenleyicide veya tasarım yüzeyinde, yani benzer öğeleri grupları kolay kimlik doğrulaması için izin verme gibi belirtmek için kullanılır. Yüksek karşıtlıklı bir temayı ancak arasında üçten fazla metin renkleri ayırt etme özelliğine erişiminiz yok. WindowText ve GrayText HotTrackText yalnızca WindowBackground yüzeyler üzerinde kullanılabilir renklerdir. Üçten fazla renk kullanılamaz olduğundan, yüksek karşıtlık modunda görüntülemek istediğiniz en önemli farklar dikkatle seçin.

Her bir düzenleyici yüzeyi üzerinde her yüksek karşıtlıklı tema göründükleri gibi izin verilen belirteç adları tonları:

![Yüksek Karşıtlık Düzenleyicisi karşılaştırma](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Yüksek Karşıtlık Düzenleyicisi karşılaştırma

Mavi tema Düzenleyicisi yüzeyini örnekleri:

![Mavi tema düzenleyicisinde](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Düzenleyicide mavi tema

![Yüksek Karşıtlık #1 tema düzenleyicisinde](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Yüksek Karşıtlık #1 tema düzenleyicide

### <a name="usage-patterns"></a>Kullanım desenleri

Yüksek Karşıtlık renklerini tanımlanmış birçok ortak kullanıcı Arabirim öğeleri zaten var. UI öğelerinizi benzer bileşenleri ile tutarlı olacak şekilde kendi sistem renk adlarının seçerken bu kullanım desenleri başvurabilirsiniz.

| Sistem renk | Kullanım |
| --- | --- |
| ActiveCaption | -Etkin IDE ve rafted penceresi düğmesi karakterlerde hover ve basın<br />-IDE ve rafted windows başlık çubuğu arka planı<br />-Varsayılan durum çubuğu arka plan |
| ActiveCaptionText | -Etkin IDE ve rafted windows için başlık çubuğu ön plan (metin ve karakter)<br />-Arka plan ve kenarlık etkin pencere düğmelerin üzerine gelin ve basın |
| Denetim | -Birleşik giriş kutusu, açılan liste ve arama varsayılan denetim ve arka plan, açılan düğmeyi dahil olmak üzere devre dışı<br />-Dock hedef düğmesi arka plan<br />-Komut çubuğu arka plan<br />-Aracı penceresi arka planı |
| ControlDark | -IDE arka plan<br />-Menü ve komut çubuğu ayırıcılar<br />-Komut çubuğu kenarlığı<br />-Menü gölgeliyor<br />-Aracı penceresi sekmesindeki varsayılan ve üzerine gelindiğinde kullanılacak kenarlık ve ayırıcı<br />-Belge iyi taşma düğmesini arka plan<br />-Dock hedef glif kenarlık |
| ControlDarkDark |-Odaklanmadan, seçili bir belge sekmesi penceresi |
| ControlLight |-Otomatik gizleme sekme kenarlığı<br />-Birleşik giriş kutusu ve aşağı açılan liste kenarlık<br />-Hedef arka planını ve kenarlığı Yerleştir |
| ControlLightLight | -Seçili, odaklanmış provisional kenarlık |
| ControlText | -Birleşik giriş kutusu ve aşağı açılan liste karakter<br />-Araç penceresi seçili sekme metni |
| GrayText |-Birleşik giriş kutusu ve aşağı açılan liste devre dışı kenarlık, aşağı açılan karakter, metin ve menü öğesi metni<br />-Devre dışı menü metni<br />-Arama denetimi 'Arama Seçenekleri' üst bilgi metni<br />-Arama denetimi bölüm ayırıcı |
| Vurgulayın | -Tüm üzerine gelin ve basılı arka planlar ve Kenarlıklar, birleşik giriş kutusu açılan düğmeyi arka plan ve belge iyi taşma düğmesini kenarlığı dışında<br />-Seçili öğenin arka planlar |
| HighlightText | -Tüm üzerine gelin ve basılı foregrounds (metin ve karakter)<br />-Odaklanmış araç penceresi ve belge sekme penceresi denetimi ön<br />-Odaklanmış araç penceresi başlık çubuğu kenarlığı<br />-Odaklanmış, seçili geçici sekmesinde ön plan<br />-Belge iyi taşma düğmesi kenarlığı üzerine gelin ve tuşuna basın<br />-Seçili simge kenarlık|
| HotTrack | -Kaydırma çubuğu thumb arka planını ve kenarlığı makinesinde<br />-Ok glif makinesinde çubuğu kaydırın |
| InactiveCaption | -Etkin olmayan IDE ve üzerine gelindiğinde rafted penceresi düğmesi karakterleri<br />-IDE ve rafted windows başlık çubuğu arka planı<br />-Devre dışı arama denetiminin arka plan |
| InactiveCaptionText | -Etkin olmayan IDE ve rafted windows başlık çubuğu ön plan (metin ve karakter)<br />-Etkin olmayan pencere düğmelerinin arka planı ve kenarlığı üzerine gelindiğinde<br />-Odaklanmadan araç penceresi düğmesi arka planını ve kenarlığı<br />-Devre dışı arama denetimi ön plan |
| Menü | -Aşağı açılan menü arka planı<br />-Checked ya da devre dışı bırakılmış onay işareti arka plan |
| MenuText | -Aşağı açılan menü kenarlık<br />-Onay işaretleri<br />-Karakter menü<br />-Aşağı açılan menü metni<br />-Seçili simge kenarlık |
| Kaydırma çubuğu | -Kaydırma çubuğu ve kaydırma ok arka plan, tüm durumları çubuğu |
| Pencere | -Otomatik gizleme sekmesini arka plan<br />-Menü çubuğunda ve command raf arka plan<br />-Odaklanmadan veya seçili olmayan belge penceresi sekmesini arka plan ve açık ve geçici sekmeleri için belge kenarlık<br />-Odaklanmadan araç penceresinin başlık çubuğu arka plan<br />-Aracı penceresi sekmesini arka plan, hem seçili hem de seçimi kaldırıldı |
| WindowFrame | -IDE kenarlık |
| WindowText | -Otomatik gizleme sekmesini ön plan<br />-Seçili aracı penceresi sekmesini ön plan<br />-Odaklanmadan belge penceresi sekmesinin ve plana odaklanmadan veya seçili geçici sekmesinde ön plan<br />-Ağaç görünüm varsayılan ön plan ve vurgulu içinde seçili olmayan karakter<br />-Araç penceresi seçili sekme kenarlığı<br />-Thumb arka plan, kenarlık ve glif kaydırın |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> Son kullanıcılar için renk gösterme

### <a name="overview"></a>Genel Bakış

Bazen son kullanıcının bir kod Düzenleyicisi'ni veya tasarım yüzeyine oluştururken gibi kullanıcı arabirimini özelleştirme olanak tanıyan isteyebilirsiniz. Bunu yapmak için en yaygın yolu kullanmaktır **Araçları &gt; seçenekleri** iletişim. Özel denetimler gerektiren kullanıcı Arabirimi yüksek oranda özelleştirilmiş sürece aracılığıyla özelleştirmeyi sunmak için en kolay yolu olan **yazı tipleri ve renkler** içinde sayfa **ortam** iletişim bölümü. Özelleştirme için oluşturduğunuz her öğe için ön plan rengini, arka plan rengi veya her ikisini birden değiştirmek kullanıcı seçebilir.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Özelleştirilebilir, renk için bir VSPackage'ı oluşturma

VSPackage yazı tiplerini ve renkleri özel kategoriler aracılığıyla denetleyebilir ve yazı tipleri ve renkler özellik sayfasında öğeleri görüntüler. Bu mekanizma kullanırken VSPackage'ları uygulamalıdır [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) ve onun ilişkili arabirim.

İlkesi, bu mekanizma, mevcut tüm görüntü öğeleri ve bunları içeren kategorileri değiştirmek için kullanılabilir. Bununla birlikte, metin düzenleyicisi veya görüntü öğeleri değiştirmek için kullanılmamalıdır. Metin Düzenleyicisi hakkında daha fazla bilgi için bkz. [yazı tipi ve renk genel bakış](../font-and-color-overview.md).

Özel kategoriler uygulamak veya öğeleri görüntülemek için bir VSPackage gerekir:

- **Oluşturma veya kayıt defterinde kategorileri tanımlama.** IDE'nin uygulaması **yazı tipleri ve renkler** özellik sayfası, belirli bir kategori destekleyen hizmeti için doğru bir şekilde sorgulamak için bu bilgileri kullanır.

- **Oluşturun veya grupları (isteğe bağlı) kayıt defterinde belirleyin.** İki veya daha fazla kategori birleşimini gösteren bir grup tanımlamak yararlı olabilir. Bir grubu tanımlanmazsa, IDE, otomatik olarak alt kategorileri birleştirir ve grup içindeki öğeleri görüntüle dağıtır.

- **IDE desteği uygulayın.**

- **Yazı tipi ve renk değişiklikleri işleyin.**

#### <a name="to-create-or-identify-categories"></a>Oluşturma veya kategori tanımlamak için

Özel bir kategori altında kayıt defteri girdisi türü oluşturmak `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` burada `<Category>` kategorisi yerelleştirilmemiş adıdır.

Kayıt defteri iki değerlerle doldurun:

| Ad | Tür | Veri | Açıklama |
| --- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategori tanımlamak için oluşturulmuş bir GUID |
| Paket | REG_SZ | GUID | Kategori destekleyen VSPackage hizmeti GUİD'si |

 Kayıt defterinde belirtilen hizmet uygulaması sağlamalısınız [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) karşılık gelen bir kategorisi için.

#### <a name="to-create-or-identify-groups"></a>Oluşturma veya grupları tanımlamak için

Özel bir kategori altında kayıt defteri girdisi türü oluşturmak `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` burada `<group>` yerelleştirilmemiş grubunun adıdır.

Kayıt defteri iki değerlerle doldurun:

| Ad | Tür | Veri | Açıklama |
|--- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategori tanımlamak için oluşturulmuş bir GUID |
| Paket | REG_SZ | GUID | Kategori destekleyen VSPackage hizmeti GUİD'si |

Kayıt defterinde belirtilen hizmet uygulaması sağlamalısınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> ilgili grup.

![IVsFontAndColorGroup uygulaması](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Uygulaması `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>IDE desteği uygulamak için

Uygulama [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), ya da döndüren bir [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabirimi veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> arabirimi her kategori için IDE veya sağlanan GUID grubu.

Desteklediği her kategori için ayrı bir örneğini bir VSPackage'ı uygulayan [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabirimi.

Yöntemleri aracılığıyla uygulanan [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) IDE ile sağlamanız gerekir:

- Kategorideki öğeleri görüntüle listesi

- Yerelleştirilebilir adlarını öğeleri görüntüle

- Her üyesi kategori bilgilerini görüntüleme

> [!NOTE]
> Her kategori en az bir görüntü öğesi içermelidir.

IDE kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> çeşitli kategorileri birleşimini tanımlamak için arabirim.

Uygulaması ile bir IDE sağlar:

- Belirli bir grubu oluşturan kategori listesi

- Erişim örneklerini [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) gruptaki her kategori destekleme

- Yerelleştirilebilir grup adları

#### <a name="updating-the-ide"></a>IDE güncelleştiriliyor

IDE yazı tipi ve renk ayarları hakkında bilgi önbelleğe alır. Bu nedenle, IDE yazı tipi ve renk yapılandırmasının her değişiklikten sonra önbelleği güncel olduğundan emin olmanın en iyi uygulamadır.

Önbelleği güncelleştiriliyor aracılığıyla gerçekleştirilir [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirim ve gerçekleştirilen genel veya açık yalnızca seçilen öğeleri olabilir.

### <a name="handling-font-and-color-changes"></a>Yazı tipi ve renk değişiklikleri işleme

VSPackage görüntülenen metin renklendirmesi doğru desteklemek için VSPackage'ı destekleyen renklendirme hizmeti kullanıcı tarafından başlatılan yazı tipleri ve renkler özellikler sayfasını yapılan değişikliklere yanıt vermelidir.

Bunu yapmak için bir VSPackage gerekir:

- **IDE tarafından oluşturulan olayları ele** uygulayarak [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) arabirimi. IDE yazı tipleri ve renkler sayfasının kullanıcı değişiklikleri izleyen uygun olan yöntemi çağırır. Örneğin, çağrı [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) yeni bir yazı tipi seçtiyseniz yöntemi.

  **VEYA**

- **IDE değişiklikleri için yoklama**. Bu sistem uygulanan yapılabilir [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arabirimi. Öncelikle desteği için Kalıcılık, ancak [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) yöntemi görüntü öğeleri için yazı tipi ve renk bilgilerini elde edebilirsiniz. Yazı tipi ve renk ayarları hakkında daha fazla bilgi için bkz. MSDN makalesi [erişme depolanan yazı tipi ve renk ayarlarını](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Yoklama sonuçları doğru olduğundan emin olmak için kullanın [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) önbellek temizleme ve güncelleştirme alma yöntemleri çağrılmadan önce gerekli olup olmadığını belirlemek için arabirimi [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arabirimi.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Özel yazı tipi ve renk kategorisi arabirimleri uygulama olmadan kaydetme

Aşağıdaki kod örneği, özel yazı tipi kaydedin ve arabirimleri uygulama olmadan kategori rengi gösterilmektedir:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Bu kod örneği için:

- `"NameID"` yerelleştirilmiş kategori adı, paket kaynak kimliği =
- `"ToolWindowPackage"` = Paket GUID'si
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` yalnızca bir örnektir ve gerçek değer uygulayan tarafından sağlanan yeni bir GUID olabilir.

### <a name="set-the-font-and-color-property-category-guid"></a>Yazı tipi ve renk özellik kategorisine GUID ayarlayın

Aşağıdaki kod örneği, kategori GUID'leri ayarını gösterir.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
