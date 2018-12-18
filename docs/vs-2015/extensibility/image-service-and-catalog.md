---
title: Görüntü hizmeti ve kataloğu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0e01d60bd7fab0b435f1b10ae744c3454aa0e44
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774373"
---
# <a name="image-service-and-catalog"></a>Görüntü Hizmeti ve Kataloğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzu, rehberlik ve en iyi uygulamalar Visual Studio Görüntü hizmeti ve görüntü Visual Studio 2015'te tanıtılan Kataloğu'nu benimseme içerir.  

 Visual Studio 2015'te sunulan Görüntü hizmeti, geliştiricilerin en iyi görüntü için cihaz ve kullanıcının içinde görüntülendikleri bağlamı için doğru Tema oluşturma da dahil olmak üzere bu görüntüyü görüntülemek için seçilen tema alma sağlar. Görüntü hizmet benimsenmesi, varlık bakım, HDPI ölçeklendirme ve Tema oluşturma ile ilgili önemli sorunlu noktaları ortadan kaldırmanın yardımcı olur.  

|||  
|-|-|  
|**Bugün sorunları**|**Çözümler**|  
|Arka plan rengi karıştırma|Yerleşik Alfa karışım kullanma|  
|Tema oluşturma (bazıları) görüntüleri|Tema meta verileri|  
|Yüksek Karşıtlık modunu kullanmak|Yüksek Karşıtlık alternatif kaynaklar|  
|Farklı DPI modları için birden fazla kaynak gerekiyor|Vektör tabanlı geri dönüş kaynak seçilebilir|  
|Yinelenen görüntüleri|Görüntü kavramı başına bir tanımlayıcı|  

 Görüntü hizmeti neden benimseyin?  

- Her zaman Visual Studio'dan en son "kusursuz kalitede" Görüntü Al  

- Gönder ve kendi görüntülerinizi kullanın  

- Windows yeni DPI ölçeklendirme eklediğinde kullanıma görüntülerinizi test gerekmez.  

- Eski mimari bulutta, uygulamalarında adresi  

  Visual Studio shell araç önce ve sonra görüntü hizmeti kullanarak:  

  ![Görüntü hizmeti önce ve sonra](../extensibility/media/image-service-before-and-after.png "önce ve sonra görüntü hizmeti")  

## <a name="how-it-works"></a>Nasıl çalışır?  
 Görüntü hizmeti, tüm desteklenen UI çerçevesi için uygun bir bit eşlemli görüntüsü belirtebilirsiniz:  

- WPF: BitmapSource  

- WinForms: System.Drawing.Bitmap  

- Win32: HBITMAP  

  Görüntü hizmeti Akış Diyagramı  

  ![Görüntü hizmeti Akış Diyagramı](../extensibility/media/image-service-flow-diagram.png "Görüntü hizmeti Akış Diyagramı")  

  **Görüntü bilinen adlar**  

  Bir resim bilinen adı (veya kısa için bilinen ad) bir resim varlığı veya Resim Kitaplığı'ndaki Görüntü listesi varlığı benzersiz olarak tanımlayan bir GUID/ID çiftidir.  

  **Bilinen adlar**  

  Visual Studio görüntü katalog ve tüketilebilir herkese açık şekilde herhangi bir Visual Studio bileşeni veya uzantısı tarafından bulunan bir resim bilinen adlar kümesi.  

  **Görüntü bildirim dosyaları**  

  Görüntü bildirimi (.imagemanifest) dosyaları bu varlıkları ve gerçek görüntü veya her varlık temsil eden görüntüleri temsil eden bir takma ad, resim varlıkları kümesini tanımlayan XML dosyalarıdır. Tek başına resimler görüntü bildirimleri tanımlayabilirsiniz veya eski kullanıcı Arabirimi desteği görüntü listeler. Ayrıca, varlık veya ayrı ayrı görüntülere her varlık arkasında ne zaman ve bu varlıkları nasıl görüntüleneceğini değiştirmek için ayarlanabilen öznitelikleri vardır.  

  **Görüntü bildirim şeması**  

  Tam görüntü bildiriminin şöyle görünür:  

```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  

 **Semboller**  

 Okunabilirlik ve bakıma yardımcı olmak gibi görüntüsü bildirimine ait öznitelik değerleri simgeleri kullanabilirsiniz. Semboller şöyle tanımlanır:  

```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  

|||  
|-|-|  
|**Alt öğe**|**Tanım**|  
|{1&gt;İçeri Aktar&lt;1}|Belirtilen bildirim dosyası geçerli bildirimde kullanmak için simgelerin alır|  
|Guid|Simgenin bir GUID temsil eder ve GUID biçimlendirme eşleşmelidir|  
|Kimlik|Simgenin bir kimliği temsil eder ve negatif olmayan bir tamsayı olmalıdır|  
|Dize|Simgenin bir rastgele dize değeri temsil eder.|  

 Simgeler büyük/küçük harfe ve başvurulan $(symbol-name) söz dizimini kullanarak:  

```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  

 Tüm bildirimler için önceden tanımlanmış bazı semboller. Bu URI özniteliğinde kullanılabilir \<kaynak > veya \<alma > yerel makinedeki başvuru yolları öğesine.  

|||  
|-|-|  
|**Sembol**|**Açıklama**|  
|CommonProgramFiles|% CommonProgramFiles % ortam değişkeninin değeri|  
|LocalAppData|% LocalAppData % ortam değişkeninin değeri|  
|ManifestFolder|Bildirim dosyasını içeren klasör|  
|MyDocuments|Geçerli kullanıcının Belgelerim klasörün tam yolu|  
|ProgramFiles|% ProgramFiles % ortam değişkeninin değeri|  
|Sistem|Windows\System32 klasöründe|  
|WinDir|% WinDir % ortam değişkeninin değeri|  

 **Görüntü**  

 \<Görüntü > öğe bilinen adı tarafından başvurulan bir görüntü tanımlar. GUID ve ID birlikte ele alındığında, görüntü bilinen adına oluşturur. Görüntü için bilinen ad tüm görüntü kitaplığı arasında benzersiz olması gerekir. Birden fazla görüntü belirli bir takma ad varsa, kitaplığı oluşturulurken karşılaşılan ilk korunur bir sağlayıcıdır.  

 En az bir kaynak içermelidir. Boyutu nötr kaynakları geniş bir grup boyutları arasında en iyi sonuçlar verir, ancak gerekli değildir. Hizmet, görüntü içinde tanımlanmamış bir boyut istenirse \<Görüntü > öğesi ve boyutu nötr kaynağı yok, hizmetin en iyi boyut özgü kaynağını seçin ve istenen boyuta ölçeklendirin.  

```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  

|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Guid|[Gerekli] Görüntü bilinen adına GUID kısmını|  
|Kimlik|[Gerekli] Resim bilinen adı kimliği bölümü|  
|AllowColorInversion|[İsteğe bağlı, varsayılan true] Görüntü programlı olarak koyu renkli bir arka plan üzerinde kullanıldığında ters renklerini olup olmadığını gösterir.|  

 **Kaynak**  

 \<Kaynak > öğesi (XAML ve PNG) tek bir görüntü kaynağı varlık tanımlar.  

```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  


|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Öznitelik** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            **Tanım**                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      URI      |                                                                                                                                                                                                                                                                                                               [Gerekli] Gelen görüntü burada yüklenebilir tanımlayan URI. Aşağıdakilerden biri olabilir:<br /><br /> -A [paketi URI](http://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) kullanarak uygulama: / / / yetkilisi<br />-Bir mutlak bileşen kaynak başvurusu<br />-Yerel bir kaynak içeren bir dosya yolu                                                                                                                                                                                                                                                                                                               |
|  Arka Plan   | [İsteğe bağlı] Ne tür bir arka plan kaynak kullanılması amaçlanmıştır gösterir.<br /><br /> Aşağıdakilerden biri olabilir:<br /><br /> *Açık:* kaynağı açık bir arka plan üzerinde kullanılabilir.<br /><br /> <em>Koyu:</em>kaynağı koyu renkli bir arka plan üzerinde kullanılabilir.<br /><br /> *Yüksek Karşıtlık:* kaynağı, yüksek karşıtlık modunda herhangi bir arka plan üzerinde kullanılabilir.<br /><br /> *HighContrastLight:* kaynağı, yüksek karşıtlık modunda açık bir arka plan üzerinde kullanılabilir.<br /><br /> *HighContrastDark:* kaynağı, yüksek karşıtlık modunda koyu renkli arka plan üzerinde kullanılabilir.<br /><br /> Arka plan özniteliği belirtilmezse, kaynağı herhangi bir arka plan üzerinde kullanılabilir.<br /><br /> Arka planda ise *ışık*, *koyu*, *HighContrastLight*, veya *HighContrastDark*, hiçbir zaman ters kaynağının renkler. Arka plan atlanırsa veya kümesine *Karşıtlık*, kaynağın renkleri ters çevirmeyi görüntünün tarafından denetlenir **AllowColorInversion** özniteliği. |
|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

 A \<kaynak > öğesi aşağıdaki isteğe bağlı alt öğeleri tam olarak birine sahip olabilir:  

||||  
|-|-|-|  
|**Öğe**|**Öznitelikler (tümü gereklidir)**|**Tanım**|  
|\<Boyutu >|Değer|Kaynak (cihaz birimlerindeki) verilen boyutta görüntüleri için kullanılacaktır. Görüntü, kare olur.|  
|\<SizeRange >|MinSize, Maxsıze|Kaynak MinSize (cihaz birimindeki) görüntülerini MaxSize aralığında kullanılacak. Görüntü, kare olur.|  
|\<Boyutlar >|Genişlik, yükseklik|Kaynak, belirtilen genişlik ve yükseklik (cihaz birimindeki) görüntülerini için kullanılır.|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak için (cihaz birimlerindeki) maksimum genişliği/yüksekliğinin en küçük genişliği/yüksekliğinin tıempo'nun aralığında kullanılır.|  

 A \<kaynak > öğesi de isteğe bağlı olabilir \<NativeResource > alt öğe tanımlar bir \<kaynak > yönetilen bir derleme yerine yerel bir derleme yüklenir.  

```xml  
<NativeResource Type="type" ID="int" />  
```  

|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Tür|[Gerekli] XAML ya da PNG yerel kaynak türü|  
|Kimlik|[Gerekli] Yerel kaynak tamsayı kimliği bölümünü|  

 **ImageList**  

 \<ImageList > öğesi içinde tek bir Şerit döndürülebilecek görüntülerin koleksiyonu tanımlar. Şerit, gerektiğinde isteğe bağlı olarak oluşturulmuştur.  

```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  

|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Guid|[Gerekli] Görüntü bilinen adına GUID kısmını|  
|Kimlik|[Gerekli] Resim bilinen adı kimliği bölümü|  
|Harici|[İsteğe bağlı, varsayılan false] Görüntünün geçerli bildiriminde görüntü bilinen adına başvuruda bulunup bulunmadığını gösterir.|  

 Kapsanan görüntü için bilinen ad geçerli bildiriminde tanımlanan görüntü başvurusu yok. Kapsanan görüntünün görüntü kitaplığı'nda bulunamazsa boş bir yer tutucu resminin onun yerine kullanılır.  

## <a name="using-the-image-service"></a>Görüntü hizmeti kullanma  

### <a name="first-steps-managed"></a>İlk adımları (yönetilen)  
 Görüntü hizmeti kullanmak için projenize bazılarını veya tümünü aşağıdaki derlemelere başvurular eklemeniz gerekir:  

-   **Microsoft.VisualStudio.ImageCatalog.dll**  

    -   Yerleşik Görüntü Kataloğu KnownMonikers kullanıyorsanız gereklidir  

-   **Microsoft.VisualStudio.Imaging.dll**  

    -   İfadesini kullanıyorsanız gereklidir **CrispImage** ve **ImageThemingUtilities** içinde WPF kullanıcı Arabirimi  

-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  

    -   İfadesini kullanıyorsanız gereklidir **ImageMoniker** ve **Imageattributes** türleri  

    -   **EmbedInteropTypes** ayarlanmalıdır true  

-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  

    -   İfadesini kullanıyorsanız gereklidir **IVsImageService2** türü  

    -   **EmbedInteropTypes** ayarlanmalıdır true  

-   **Microsoft.VisualStudio.Utilities.dll**  

    -   İfadesini kullanıyorsanız gereklidir **BrushToColorConverter** ImageThemingUtilities için. **ImageBackgroundColor** içinde WPF kullanıcı Arabirimi  

-   **Microsoft.VisualStudio.Shell. \<VSVersion >.0**  

    -   İfadesini kullanıyorsanız gereklidir **Ivsuıobject** türü  

-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  

    -   WinForms ilgili UI Yardımcıları kullanıyorsanız gereklidir  

    -   **EmbedInteropTypes** ayarlanmalıdır true  

### <a name="first-steps-native"></a>İlk adımları (yerel)  
 Görüntü hizmeti kullanmak için bazılarını veya tümünü projenize aşağıdaki üst bilgiler dahil etmek gerekir:  

-   **KnownImageIds.h**  

    -   Yerleşik Görüntü Kataloğu kullanıyorsanız gereklidir **KnownMonikers**, ancak kullanamazsınız **ImageMoniker** ne zaman iade değerlerini gibi türü **Ivshierarchy GetGuidProperty**veya **GetProperty** çağırır.  

-   **KnownMonikers.h**  

    -   Yerleşik Görüntü Kataloğu kullanıyorsanız gereklidir **KnownMonikers**.  

-   **ImageParameters140.h**  

    -   İfadesini kullanıyorsanız gereklidir **ImageMoniker** ve **Imageattributes** türleri.  

-   **VSShell140.h**  

    -   İfadesini kullanıyorsanız gereklidir **IVsImageService2** türü.  

-   **ImageThemingUtilities.h**  

    -   Tema oluşturma sizin adınıza idare görüntü service gerisini halleder başlatamadı gereklidir.  

    -   Görüntü hizmeti, görüntü Tema oluşturma yerine bu başlığı kullanmayın.  

-   **VSUIDPIHelper.h**  

    -   Geçerli DPI almak için DPI Yardımcıları kullanıyorsanız gereklidir.  

## <a name="how-do-i-write-new-wpf-ui"></a>Yeni bir WPF UI nasıl yazılır?  

1.  Yukarıdaki gerekli derleme başvurularını ekleyerek başlangıç ilk adımlar bölümüne projenize. Bunların tümünü ekleyin, böylece yalnızca gereksinim duyduğunuz başvuruları eklemek gerekmez. (Not: kullanıyorsanız veya erişimi **renkleri** yerine **Fırçalar**, başvuru atlayabilirsiniz sonra **yardımcı programları**, bu yana dönüştürücü gerekmez.)  

2.  İstediğiniz görüntüyü seçin ve takma adı alın. Kullanan bir **KnownMoniker**, veya kendi özel görüntüler ve takma ad varsa kendi kullanın.  

3.  Ekleme **CrispImages** , XAML için. (Örneğe bakın.)  

4.  Ayarlama **ImageThemingUtilities.ImageBackgroundColor** UI hiyerarşinizdeki özelliği. (Burada arka plan rengi bilinir, açık olmayan mutlaka konumda ayarlanmalıdır **CrispImage**.) (Örneğe bakın.)  

```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  

 **Varolan bir WPF UI'ı nasıl güncelleştirebilirim?**  

 Varolan WPF Başlamayabileceğini bildirir.UI üç temel adımdan oluşur göreceli olarak basit bir işlemdir:  

1.  Tümünü Değiştir \<Görüntü > ile kullanıcı Arabirimi öğelerinde \<CrispImage > öğeleri  

2.  Tüm kaynak özniteliklerini değiştirmek için bilinen ad öznitelikleri  

    -   Görüntüyü hiçbir zaman değiştirir ve kullanmakta olduğunuz **KnownMonikers**, statik olarak bu özelliğe bağlama **KnownMoniker**. (Yukarıdaki örnekte bkz.)  

    -   Görüntüyü hiçbir zaman değiştirir ve kendi özel görüntünüzü kullanıyorsanız, statik olarak için kendi ad bağlayın.  

    -   Görüntü değiştirebilirsiniz, bilinen ad özniteliği özellik değişiklikleri bildiren bir kod özelliği bağlayın.  

3.  Herhangi bir UI hiyerarşi içinde ayarlamak **ImageThemingUtilities.ImageBackgroundColor** emin renkleri ters çevirmeyi yapmak için düzgün şekilde çalışır.  

    -   Bu kullanımını gerektirebilir **BrushToColorConverter** sınıfı. (Yukarıdaki örnekte bkz.)  

## <a name="how-do-i-update-win32-ui"></a>Win32 UI nasıl güncelleştirebilirim?  
 Aşağıdaki uygun yerlerde görüntüleri ham yüklenmesini değiştirileceğini kodunuza ekleyin. Gerektiğinde HICONs HIMAGELIST karşı karşı HBITMAPs döndürmek için değerleri geçin.  

 **Görüntü hizmeti alın**  

```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  

 **Görüntü isteme**  

```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  

CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  

```  

## <a name="how-do-i-update-winforms-ui"></a>WinForms UI nasıl güncelleştirebilirim?  
 Aşağıdaki uygun yerlerde görüntüleri ham yüklenmesini değiştirileceğini kodunuza ekleyin. Bit eşlemler simgeleri ve gerektiğinde döndürmek için değerleri geçin.  

 **Using deyimi Oyla**  

```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  

 **Görüntü hizmeti alın**  

```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  

```  

 **İstek resmi**  

```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  

// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  

```  

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Görüntü bilinen yeni bir araç penceresinde nasıl kullanabilirim?  
 Visual Studio 2015 için VSIX paketi proje şablonunu güncelleştirildi. Yeni bir araç penceresi oluşturmak için VSIX projesine sağ tıklayın ve "Yeni öğe... Ekle" seçeneğini belirleyin (Ctrl + Shift + A). Proje dili için genişletilebilirlik düğümünde seçin "Özel araç penceresi," araç penceresi bir ad verin ve "Ekle" düğmesine basın.  

 Bu araç penceresinde adlar kullanmak için anahtar yerlerdir. Her biri için yönergeleri izleyin:  

1. Sekmeleri küçük geldiğinizde araç penceresi sekmesinin yeterli (Ctrl + sekme penceresi değiştirici da kullanılır).  

    Öğesinden türetilen sınıfın oluşturucusunda bu satırı ekleyin **ToolWindowPane** türü:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  

2. Araç penceresini açmak için komutu.  

    Paket için .vsct dosyası, aracı pencerenin komut düğmesi düzenleyin:  

   ```xml  
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
     <Icon guid="ImageCatalogGuid" id="Blank" />  
     <!-- Add this -->  
     <CommandFlag>IconIsMoniker</CommandFlag>  
     <Strings>  
       <ButtonText>MyToolWindow</ButtonText>  
     </Strings>  
   </Button>  
   ```  

   **Görüntü bilinen adlar var olan bir araç penceresinde nasıl kullanabilirim?**  

   Görüntü bilinen adlar kullanmak için mevcut bir araç penceresi güncelleştirme yeni bir araç penceresi oluşturma adımlarını benzer.  

   Bu araç penceresinde adlar kullanmak için anahtar yerlerdir. Her biri için yönergeleri izleyin:  

3. Sekmeleri küçük geldiğinizde araç penceresi sekmesinin yeterli (Ctrl + sekme penceresi değiştirici da kullanılır).  

   1.  (Varsa), türetilen sınıfın oluşturucusunda bu satırları kaldırmak **ToolWindowPane** türü:  

       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  

   2.  #1. adım, bkz. "Nasıl yaparım kullanım görüntü bilinen yeni bir araç penceresinde?" Yukarıdaki bölümde.  

4. Araç penceresini açmak için komutu.  

   -   #2. adım, bkz. "Nasıl yaparım kullanım görüntü bilinen yeni bir araç penceresinde?" Yukarıdaki bölümde.  

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Görüntü bilinen adlar .vsct dosyası içinde nasıl kullanabilirim?  
 .Vsct dosyanızı aşağıdaki açıklama eklenen satırları tarafından belirtildiği gibi güncelleştirin:  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  

 **Ne my .vsct dosyası ayrıca Visual Studio'nun eski sürümleriyle okunması gerekir?**  

 Visual Studio'nun eski sürümlerini algılamaz **IconIsMoniker** bayrağı komutu. Görüntü hizmeti görüntülerden desteklemiyor, ancak eski stil görüntüleri Visual Studio'nun eski sürümlerini kullanmaya devam Visual Studio sürümlerinde kullanabilirsiniz. Bunu yapmak için .vsct dosyası değişmeden (ve bu nedenle, Visual Studio'nun eski sürümleriyle uyumlu) bırakın ve bir .vsct dosyanın tanımlanan GUID/ID çiftleri eşleyen bir CSV (virgülle ayrılmış değerler) dosyası oluşturma \<bit eşlemler > görüntü öğesi GUID/ID çiftleri bilinen ad.  

 Eşleme CSV dosya biçimi şöyledir:  

```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  

 CSV dosyasını paket ile dağıtılır ve konumuna tarafından belirtilen **IconMappingFilename** özelliği **ProvideMenuResource** paket özniteliği:  

```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  

 **IconMappingFilename** göreli bir yol örtük olarak kökü $PackageFolder $ (Yukarıdaki örnek) olduğu gibi veya mutlak bir yol açıkça kökü @"%UserProfile%\ gibi bir ortam değişkeni tarafından tanımlanan bir dizin dir1\dir2\MyMappingFile.csv".  

## <a name="how-do-i-port-a-project-system"></a>Proje sistemi nasıl taşımalısınız?  
 **Bir proje için ImageMonikers sağlamak nasıl**  

1. Uygulama **VSHPROPID_SupportsIconMonikers** projenin **Ivshierarchy**ve true döndürür.  

2. Ya da uygulama **VSHPROPID_IconMonikerImageList** (özgün proje kullandıysanız **VSHPROPID_IconImgList**) veya **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (özgün proje kullandıysanız  **VSHPROPID_IconHandle** ve **VSHPROPID_OpenFolderIconHandle**).  

3. Uzantı noktaları bunları istemesi durumunda simgeleri "eski" sürümlerini oluşturmak için simgeler için özgün VSHPROPIDs uygulamasını değiştirin. **IVsImageService2** simgeleri getirmek için gereken işlevleri sağlar  

   **Ek gereksinimler vb / C# proje özellikleri**  

   Yalnızca uygulama **VSHPROPID_SupportsIconMonikers** projenizin olduğunu tespit ederse **en dıştaki flavor**. Aksi takdirde, gerçekte görüntü bilinen adlar gerçek en dıştaki flavor desteklemeyebilir ve, temel özellik etkili bir şekilde "özelleştirilmiş görüntülerinizi gizlemek".  

   **Görüntü bilinen adlar CPS'de nasıl kullanabilirim?**  

   Özel görüntüleri (ortak proje sistemi) CPS'de ayarlama el ile veya Project sistem genişletilebilirliği SDK ile birlikte gelen öğe şablonu aracılığıyla yapılabilir.  

   **Project sistem genişletilebilirliği SDK'sını kullanma**  

   Konumundaki yönergeleri [proje türü/öğe türü için özel simgeler sağlayın](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) CPS görüntülerinizi özelleştirmek için. CPS hakkında daha fazla bilgi şu adreste bulunabilir: [Visual Studio Proje sistemi genişletilebilirlik belgeleri](https://github.com/Microsoft/VSProjectSystem)  

   **El ile ImageMonikers kullanın**  

4. Uygulama ve dışarı aktarma **IProjectTreeModifier** proje sisteminizde arabirimi.  

5. Belirleyen **KnownMoniker** veya kullanmak istediğiniz özel görüntü bilinen ad.  

6. İçinde **ApplyModifications** yöntemi aşağıdakileri benzer yeni ağaç döndürmeden önce herhangi bir yöntem aşağıdaki örnekteki:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
   ```  

7. Yeni bir ağaç oluşturuyorsanız, benzer NewTree yöntemi içinde istenen adlar geçirerek özel görüntüleri ayarlayabilirsiniz aşağıdaki örnekteki:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                /*filePath*/<value>,  
                                                /*browseObjectProperties*/<value>,  
                                                icon,  
                                                expandedIcon);  
   ```  

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Bir bilinen ad tabanlı görüntü şeridi için bir gerçek görüntü şeridi nasıl dönüştürebilirim?  
 **HIMAGELISTs desteği gerekir**  

 Görüntü hizmeti kullanmak için güncelleştirmek istediğiniz, ancak görüntü listeleri etrafında geçirme gerektiren API'leri tarafından kısıtlanmıştır kodunuz için zaten varolan bir görüntü şeridi varsa, yine de görüntü hizmeti avantajlarını elde edebilirsiniz. Bir bilinen ad tabanlı görüntü şeridi oluşturmak için bildirim mevcut adlar oluşturmak için aşağıdaki adımları izleyin.  

1. Çalıştırma **ManifestFromResources** aracı, görüntü şeridi geçirme. Bu Şerit için bir bildirim oluşturur.  

   -   Önerilen: kullanımını uyacak şekilde bildirimi olmayan varsayılan bir ad sağlayın.  

2. Yalnızca kullanıyorsanız **KnownMonikers**, aşağıdakileri yapın:  

   -   Değiştirin \<görüntüleri > ile bildiriminin \<görüntüleri / >.  

   -   Tüm subimage kimlikleri kaldırmak (hepsi birlikte \<imagestrip adı > _ ##).  

   -   Önerilen: AssetsGuid simge ve görüntü şeridi sembol kullanımını uyacak şekilde yeniden adlandırın.  

   -   Her değiştirin **ContainedImage**ait GUID $(ImageCatalogGuid) ile her değiştirin **ContainedImage**'s $ Kimliğiyle (\<bilinen ad >) ve dış = "true" özniteliği eklemek için her **ContainedImage**  

       -   \<bilinen ad > ile değiştirilmelidir **KnownMoniker** görüntü eşleşen ancak "KnownMonikers." adından kaldırıldı.  

   -   Ekle < alma Manifest="$(ManifestFolder)\\< yükleme dizini yolu göreli\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> üstüne \<sembolleri > bölümü.  

       -   Göreli yol bildirimi yazma Kurulum içinde tanımlanan dağıtım konumu tarafından belirlenir.  

3. Çalıştırma **ManifestToCode** görüntü şeridi için Görüntü hizmeti sorgulamak için kullanabileceğiniz bir bilinen ad var olan kod sahip olacak şekilde sarmalayıcılar aracı.  

   -   Önerilen: sarmalayıcıları ve bunların kullanımını uyacak şekilde ad alanları için varsayılan olmayan adlar sağlar.  

4. Tüm ekler, yazma Kurulum/dağıtım ve diğer kod değişikliklerini Görüntü hizmeti ve yeni dosyaları ile çalışma.  

   Örnek bildirim ne gibi görünmelidir görmek için hem iç hem de dış görüntüleri dahil olmak üzere:  

```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  

  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  

  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  

  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  

</ImageManifest>  
```  

 **HIMAGELISTs destek gerekmez**  

1.  Belirlemek **KnownMonikers** , görüntü şeridi görüntüleri eşleşen veya resimleri için kendi adlar, görüntü şeridi içinde oluşturun.  

2.  Görüntü şeridi takma adların yerine kullanmak için gerekli dizin, görüntüyü almak için kullanılan her eşleme güncelleştirin.  

3.  Güncelleştirilmiş eşleme aracılığıyla bilinen adlar istemek için Görüntü hizmeti kullanmak için kodunuzu güncelleştirin. (Bu güncelleştirme gelebilir **CrispImages** yönetilen kod veya HBITMAPs veya HICONs görüntü Hizmeti'nden istiyor ve yerel kod için geçirme etrafında.)  

## <a name="testing-your-images"></a>Görüntülerinizin test etme  
 Görüntü kitaplığı Görüntüleyicisi aracı, her şeyin doğru şekilde yazılmadığından emin olmak için görüntü bildirimlerini test etmek için kullanabilirsiniz. Aracı bulabilirsiniz [Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx). Bu araç ve diğerleri için belgeler bulunabilir [burada](http://aka.ms/VSImageThemeTools).  

## <a name="additional-resources"></a>Ek kaynaklar  

### <a name="samples"></a>Örnekler  
 Bazı Visual Studio samples github'da görüntü hizmetin çeşitli Visual Studio genişletilebilirlik noktaları bir parçası olarak nasıl kullanılacağını göstermek için güncelleştirilmiştir.  

 Denetleme [ http://github.com/Microsoft/VSSDK-Extensibility-Samples ](http://github.com/Microsoft/VSSDK-Extensibility-Samples) son örnekleri için.  

### <a name="tooling"></a>Araç kullanımı  
 Görüntü hizmeti için destek araçları kümesi oluşturma/Görüntü hizmeti ile çalışan kullanıcı Arabirimi güncelleştirilirken yardımcı olmak için oluşturuldu. Her araç hakkında daha fazla bilgi için Araçlar ile birlikte gelen belgelerine bakın. Araçlar parçası olarak dahil [Visual Studio 2015 SDK.](http://msdn.microsoft.com/library/bb166441.aspx)  

 **ManifestFromResources**  

 Kaynakları aracı bildiriminden görüntü kaynakları (PNG veya XAML) listesini alır ve bu görüntüleri görüntü hizmeti ile kullanmak için bir görüntü bildirim dosyası oluşturur.  

 **ManifestToCode**  

 Kod aracı bildirime, görüntü bildirim dosyasını alır ve bildirim değerlerin kod (C++, C# veya VB) veya .vsct dosyaları başvuru için bir sarmalayıcı dosyası oluşturur.  

 **ImageLibraryViewer**  

 Görüntü kitaplığı Görüntüleyicisi aracı görüntü bildirimleri yükleyebilir ve üzerlerinde değişiklik bildirimi doğru yazılmasını emin olmak için Visual Studio olduğu aynı şekilde izin verir. Kullanıcı, arka plan, boyutları, DPI ayarı, yüksek karşıtlık ve diğer ayarlarını değiştirebilirsiniz. Ayrıca Bildirimlerde hataları bulmak için yükleme bilgileri görüntüler ve bildirimde her görüntü kaynağı bilgilerini görüntüler.  

## <a name="faq"></a>SSS  

-   Yüklenirken dahil herhangi bir bağımlılığın olup \<başvuru Include="Microsoft.VisualStudio.*. Interop.14.0.DesignTime"/ >?  

    -   Ayarlama EmbedInteropTypes = "Tüm birlikte çalışma DLL'lere true".  

-   Bir görüntü bildirimi uzantım ile nasıl dağıtabilirim?  

    -   .İmagemanifest dosyayı projenize ekleyin.  

    -   "VSIX'e dahil et", True olarak ayarlayın.  

-   Ben CPS proje sistemimin güncelleştiriliyor. Ne **IMAGENAME** ve **StockIconService**?  

    -   o CPS adlar kullanmak için güncelleştirildiği sırada bu kaldırıldı. Çağrısı yapması **StockIconService**, istenen geçirmeniz yeterlidir **KnownMoniker** yöntemi veya özelliği kullanılarak **ToProjectSystemType()** uzantı yöntemi CPS yardımcı programları. Bir eşleme bulabilirsiniz **IMAGENAME** için **KnownMonikers** aşağıda:  

        |||  
        |-|-|  
        |**Görüntü adı**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  

    -   Ben tamamlanma listesi sağlayıcım güncelleştiriliyor. Hangi **KnownMonikers** eski eşleşen **StandardGlyphGroup** ve **StandardGlyph** değerleri?  

        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||Başvuru|  
        |GlyphLibrary||Kitaplığı|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||İletişim kutusu|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||Sonrakine Git|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||Kod parçacığı|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Yinelenme|  
        |GlyphXmlItem||Etiket|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||Belge|  
        |GlyphForwardType||Sonrakine Git|  
        |GlyphCallersGraph||CallTo|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||CallTo|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|

