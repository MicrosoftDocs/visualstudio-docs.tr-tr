---
title: VSIX renk Düzenleyicisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ac81f039bf5357f9488aeba439c27814cdf7e3d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727594"
---
# <a name="vsix-color-editor"></a>VSIX Renk Düzenleyicisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio uzantısı renk Düzenleyicisi araç oluşturabilir ve Visual Studio için özel renkler düzenleyebilirsiniz. Renkleri kodda kullanılabilir, böylece aracı tema kaynak anahtarlarını da oluşturabilirsiniz. Bu araç, renk teması oluşturma destekleyen Visual Studio uzantısı yapmak için kullanışlıdır. Bu araç, .pkgdef ve .xml dosyaları açabilirsiniz. Visual Studio temasından (.vstheme dosyaları) ile Visual Studio uzantısı renk Düzenleyicisi için .xml dosya uzantısı değiştirme tarafından kullanılabilir. Ayrıca, .vstheme dosya geçerli bir .xml dosyasına içeri aktarılabilir.  
  
 ![VSIX renk Düzenleyicisi Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX renk Düzenleyicisi Hero")  
  
 **Paket tanımlama dosyaları**  
  
 Paket tanımı (.pkgdef) dosyaları, temalar tanımlayan dosyalarıdır. Renkleri .pkgdef dosyasına derlenir Tema rengi .xml dosyaları içinde depolanır. .Pkgdef dosyaları çalışma zamanında işlenen, Visual Studio aranabilir yerlere dağıtılan ve birleştirmeniz Temalar tanımlayın.  
  
 **Renk belirteçleri**  
  
 Bir renk belirteci, dört öğeden oluşur:  
  
-   **Kategori adı:** renkler kümesi için mantıksal bir gruplandırması. İstenen kullanıcı Arabirimi öğesi veya kullanıcı Arabirimi öğeleri grup için özel renkler zaten varsa var olan bir kategori adı kullanın.  
  
-   **Belirteç adı:** belirteci ayarlar ve renk belirteci için açıklayıcı bir ad. Çiftleri ve, uygulandıkları durumları tanımlanması daha kolaydır, böylece bunlar adlandırılmalıdır ve tüm durumlarına yanı sıra arka plan ve ön plan (metin) belirteci adları ayarlar içerir.  
  
-   **Renk değerleri (veya tonları):** her renkli tema için gerekli. Her zaman arka plan ve metin rengi değerleri çiftlerinde oluşturun. Metin (ön plan) rengi her zaman çizilen arka plan rengi karşı okunabilir olması için arka plan/ön plan renkleri eşlenirler. Bu renklerin bağlanır ve kullanıcı Arabiriminde birlikte kullanılır. Arka plan metin ile kullanılmak üzere tasarlanmamıştır, ön plan rengi tanımlamaz.  
  
-   **Sistem renk adı:** kullanılmak üzere yüksek karşıtlık görüntüler.  
  
## <a name="how-to-use-the-tool"></a>Aracı'nı kullanma  
 Mümkün olduğunca ve uygun olan yerlerde, mevcut Visual Studio renkleri yenilerini yapmak yerine yeniden kullanılabilir. Ancak, hiçbir uygun renkler tanımlandığı durumlarda, özel renkler, bir uzantı Tema oluşturma uyumlu tutmak oluşturulmalıdır.  
  
 **Yeni renk belirteç oluşturma**  
  
 Visual Studio uzantısı renk düzenleyicisini kullanarak özel renkler oluşturmak için aşağıdaki adımları izleyin:  
  
1. Yeni renk belirteçleri için kategori ve belirteç adlarını belirleyin.  
  
2. Kullanıcı Arabirimi öğesi için yüksek karşıtlık her teması ve sistem renk için kullanacağı tonları seçin.  
  
3. Yeni renk belirteçler oluşturmak için renk düzenleyicisini kullanın.  
  
4. Visual Studio Uzantısı'nda renkleri kullanın.  
  
5. Değişiklikler Visual Studio'daki test edin.  
  
   **1. adım: kategori ve yeni renk belirteçleri için belirteç adlarını belirleyin.**  
  
   Tercih edilen adlandırma şeması için bir VSColor **[Category] [UI türü] [durumu]**. Yedekli olduğu gibi "renk" sözcüğü VSColor adları kullanmayın.  
  
   Kategori adları, mantıksal Gruplamalar sağlar ve mümkün olduğunca sayısı azalacağından'olarak tanımlanmamalıdır. Örneğin, tek bir araç penceresi adı bir kategori adı olabilir, ancak tüm iş birimi veya projeyi takım adı değil. Girdileri kategoriler halinde gruplandırmak, aynı ada sahip renkler arasında karışıklığı önlemeye yardımcı olur.  
  
   Belirteç adı, öğe türü ve durumlar ya da "durumu rengi uygulanır," açıkça belirtmeniz gerekir. Örneğin, bir etkin veri ipucunun **[UI türü]** adlandırılabilir "**DataTip**" ve **[durumu]** adlandırılabilir "**etkin**," içinde elde edilen bir renk adı "**DataTipActive**." Veri ipuçları metin olduğundan, bir ön ve arka plan rengi tanımlanması gerekir. Bir arka plan/ön eşleştirme kullanarak, renk düzenleyicisini otomatik olarak renkleri oluşturacaksınız "**DataTipActive**" arka planı ve "**DataTipActiveText**" ön için.  
  
   Kullanıcı Arabirimi parçası yalnızca bir durum varsa **[durumu]** adının bir kısmını atlanabilir. Örneğin, bir arama kutusu, kenarlık vardır ve kenarlığın rengi etkileyecek durumu değişiklik yapılmaz, ardından kenarlığın rengi belirteç adını yalnızca çağrılabilir "**SearchBoxBorder**."  
  
   Bazı yaygın durum adları şunlardır:  
  
- Etkin  
  
- Etkin değil  
  
- Fareyi üzerine getirme  
  
- MouseDown  
  
- Seçili  
  
- Odaklanmış  
  
  Liste öğesi denetimi bölümleri için birkaç belirteç adları örnekleri:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **2. adım: kullanıcı Arabirimi öğesi için yüksek karşıtlık her teması ve sistem renk için kullanacağı tonları seçin.**  
  
  Özel renkler için kullanıcı Arabirimi seçerken, benzer ve var olan bir kullanıcı Arabirimi öğesi seçin ve renklerini temel olarak kullanın. Uygun ara ve tüm doğru şekilde davranmaz incelemesi ve testi, renkler, hazır kullanıcı Arabirimi öğeleri için yapılmıştır.  
  
  **3. adım: yeni renk belirteçler oluşturmak için renk düzenleyicisini kullanın.**  
  
  Renk düzenleyicisini başlatın ve yeni bir özel tema renkleri .xml dosyasını oluşturun veya açın. Seçin **Düzenle > Yeni renk** menüsünde. Bu kategoriyi belirten bir iletişim kutusu ve o kategorideki renk girişi için bir veya daha fazla adları açar:  
  
  ![VSIX renk Düzenleyicisi yeni renk](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX renk Düzenleyicisi yeni renk")  
  
  Var olan bir kategori seçin ya da seçin **yeni kategori** yeni bir kategori oluşturmak için. Yeni bir kategori adı oluşturma başka bir iletişim kutusu açılır:  
  
  ![VSIX renk Düzenleyicisi yeni kategori](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX renk Düzenleyicisi yeni kategori")  
  
  Yeni kategori sonra kullanılabilir olur **yeni renk** Kategori açılan menüsü. Bir kategori seçmek sonra her yeni renk belirteç için satır başına bir ad girin ve "Oluştur" bittiğinde seçin:  
  
  ![VSIX renk Düzenleyicisi yeni renk dolgulu](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "doldurulmuş VSIX renk Düzenleyicisi yeni renk")  
  
  Renk değerleri "None ile" renk tanımlanmadı belirten arka plan/ön plan çiftler halinde gösterilir. Not: bir renk metin rengi/arka plan rengi çifti yoksa daha sonra yalnızca arka plan tanımlanması gerekir.  
  
  ![VSIX renk Düzenleyicisi renk değerleri](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX renk Düzenleyicisi renk değerleri")  
  
  Bir renk belirteç düzenlemek için bu belirteci temasını (sütun) için bir renk girişi seçin. Renk değeri 8 basamaklı ARGB biçiminde bir onaltılık renk değeri yazmak, hücreye sistem renk adı girerek veya renk kaydırıcıları bir dizi veya sistem renkleri listesi aracılığıyla istediğiniz renk seçmek için aşağı açılan menüyü kullanarak ekleyin.  
  
  ![VSIX renk Düzenleyicisi düzenleme renk](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX renk Düzenleyicisi düzenleme rengi")  
  
  ![VSIX renk Düzenleyicisi arka plan](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX renk Düzenleyicisi arka plan")  
  
  Metin görüntülemek gerekmeyen bileşenler için yalnızca bir renk değeri girin: arka plan rengi. Aksi takdirde, eğik çizgi ile ayrılmış hem arka plan hem de metin rengi için değerleri girin.  
  
  Değerleri için yüksek karşıtlık girerken, geçerli Windows sistem renk adlarını girin. Sabit kodlanmış ARGB değerlerini girmeyin. Geçerli sistem renk adlarının bir listesini, renk değeri açılan menülerden "Arka plan: Sistem" veya "Ön plan: Sistem"'i seçerek görüntüleyebilirsiniz. Metin bileşenleri olan öğeler oluştururken, doğru arka plan/metin sistem renk çifti veya metin okunamıyor.  
  
  Renk belirteçlerini düzenleme oluşturma ve ayarlama işiniz bittiğinde, istenen .xml ya da .pkgdef biçiminde kaydedin. Hiçbiri ile bir arka plan rengi belirteçleri veya ön plan kümesi boş renkler .xml biçiminde olarak kaydedilir, ancak .pkgdef biçiminde atıldı. .Pkgdef dosyası için boş renklerini Kaydet denerseniz, bir iletişim kutusu rengi kaybı, sizi uyarır.  
  
  **4. adım: bir Visual Studio Uzantısı'nda renkleri kullanın.**  
  
  Yeni renk tanımlama sonra belirteçleri, "Derleme"İçerik"olarak ayarlama eylemi" ile proje dosyasında .pkgdef içerir ve "VSIX içinde dahil" "True" olarak ayarlayın.  
  
  ![VSIX renk Düzenleyicisi pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef VSIX renk Düzenleyicisi")  
  
  Visual Studio uzantısı renk Düzenleyicisi'nde dosyayı seçin > özel erişmek için kullanılan kodunu görüntülemek için kaynak kodu görüntüle WPF tabanlı kullanıcı Arabiriminde renkleri.  
  
  ![VSIX renk Düzenleyicisi kaynak kodu Görüntüleyicisi](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX renk Düzenleyicisi kaynak kodu Görüntüleyicisi")  
  
  Projedeki bir statik sınıfta bu kodu ekleyin. Bir başvuru **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** kullanmak için projeye eklenmesi gerekiyor **ThemeResourceKey** türü.  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 Bu, XAML koddaki renkleri erişim sağlar ve tema değişikliklerine yanıt verme kullanıcı Arabirimi sağlar.  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **5. adım: Visual Studio'da değişiklikleri test etmek.**  
  
 Renk Düzenleyicisi Visual Studio uzantı paketi derlenmeden renkleri için Canlı değişiklikleri görüntülemek için çalışan örneklerini renk belirteçleri geçici olarak uygulayabilirsiniz. Bunu yapmak için her bir tema sütunun başlığına bulunan "Bu tema, Visual Studio windows çalıştıran için uygulama" düğmesini tıklatın. VSIX renk Düzenleyicisi kapalı olduğunda bu geçici bir tema kaybolur.  
  
 ![VSIX renk Düzenleyicisi uygulamak](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX renk Düzenleyicisi Uygula")  
  
 Değişiklikleri kalıcı hale getirmek için yeniden oluşturun ve bu renkleri kullanıp kullanmayacağını kod yazma ve yeni renkleri .pkgdef dosyasına ekleyerek sonra Visual Studio uzantısı yeniden dağıtın. Visual Studio uzantısı yeniden yeni renkler için kayıt defteri değerlerini temaları geri kalanı ile birleştirin. Ardından Visual Studio'yu yeniden başlatın, kullanıcı arabirimini görüntülemek ve yeni renkleri beklendiği gibi göründüğünü doğrulayın.  
  
## <a name="notes"></a>Notlar  
 Bu araç, önceden var olan Visual Studio temasından veya özel bir Visual Studio Tema renkleri düzenleme için özel renkler oluşturmak için kullanılması amaçlanmıştır. Özel tam Visual Studio temasından oluşturmak için indirme [Visual Studio Color Theme Editor uzantısı](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b) Visual Studio uzantıları Galerisi.  
  
## <a name="sample-output"></a>Örnek Çıktı  
 **XML renk çıktısı**  
  
 Aracı tarafından oluşturulan .xml dosyası şuna benzer olacaktır:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **PKGDEF renk çıktısı**  
  
 Araç tarafından oluşturulan .pkgdef dosyası aşağıdakine benzer olacaktır:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **C# kaynak anahtarlarını sarmalayıcı**  
  
 Aracı tarafından oluşturulan renk kaynak anahtarlarını şuna benzer olacaktır:  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **WPF kaynak sözlüğü sarmalayıcı**  
  
 Renk **ResourceDictionary** araç tarafından oluşturulan anahtarları, aşağıdakine benzer olacaktır:  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```

