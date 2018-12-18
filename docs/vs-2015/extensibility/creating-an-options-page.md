---
title: Seçenekler sayfası oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 63
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c65a91135c9346e0dfcabbe7422501ed4f02704
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751365"
---
# <a name="creating-an-options-page"></a>Seçenekler Sayfası Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda incelemek ve özelliklerini ayarlamak için bir özellik kılavuzunda kullanan basit Araçlar/Seçenekler sayfası oluşturur.  
  
 Bu özelliklerin kaydetmek ve ayarları dosyasından geri yüklemek için aşağıdaki adımları izleyin ve sonra bakın [ayarları kategorisi oluşturma](../extensibility/creating-a-settings-category.md).  
  
 Araçlar Seçenekler sayfaları oluşturmanıza yardımcı olacak iki sınıf MPF sağlar <xref:Microsoft.VisualStudio.Shell.Package> sınıfı ve <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı. Paket sınıfına sınıflara göre bu sayfaları için bir kapsayıcı sağlamak için bir VSPackage oluşturursunuz. Her araç seçenekleri sayfası, DialogPage sınıftan türetme tarafından oluşturun.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Araç seçenekleri kılavuz sayfası oluşturma  
 Bu bölümde, bir basit Araçlar Seçenekler özellik Kılavuzu oluşturun. Bu kılavuz, görüntülemek ve bir özelliğin değerini değiştirmek için kullanın.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX projesi oluşturun ve bir VSPackage'ı eklemek için  
  
1.  Her Visual Studio uzantısı, uzantı varlıkları içeren bir VSIX dağıtım projesi ile başlar. Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adlı VSIX projesi `MyToolsOptionsExtension`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  VSPackage adlı bir Visual Studio Paket öğe şablonu ekleyerek `MyToolsOptionsPackage`. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle iletişim**Git **Visual C# öğeleri / genişletilebilirlik** seçip **Visual Studio paket**. İçinde **adı** iletişim kutusunun altındaki alan, için dosya adını değiştirerek `MyToolsOptionsPackage.cs`. VSPackage'ı oluşturma hakkında daha fazla bilgi için bkz. [VSPackage içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Araçlar Seçenekler özellik kılavuzu oluşturma  
  
1.  MyToolsOptionsPackage dosyası Kod Düzenleyicisi'nde açın.  
  
2.  Aşağıdaki using deyimi.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  OptionPageGrid sınıf bildirme ve türetmeniz <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Geçerli bir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage sınıfa sınıf için bir kategori seçenekleri ve OptionPageGrid için seçenekleri sayfasında ad atamak için. Sonuç şu şekilde görünmelidir:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Ekleme bir `OptionInteger` özelliğini `OptionPageGrid` sınıfı.  
  
    -   Geçerli bir <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> özelliği bir özellik Kılavuzu kategori atamak için.  
  
    -   Geçerli bir <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> özelliği için bir ad atamak için.  
  
    -   Geçerli bir <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> açıklamasını özelliğe atanacak.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Varsayılan uygulaması <xref:Microsoft.VisualStudio.Shell.DialogPage> uygun dönüştürücüler varsa veya yapıları ya da uygun dönüştürücüleri özelliklerine Genişletilebilir dizilerde olan özelliklerini destekler. Dönüştürücüleri listesi için bkz. <xref:System.ComponentModel> ad alanı.  
  
6.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
7.  Visual Studio'nun Deneysel örneğinin üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
     Sol bölmede görmelisiniz **My kategori**. (Hakkında yarı yarıya listede aşağı görüneceğini için seçenekleri kategoriler alfabetik olarak listelenir.) Açık **My kategori** ve ardından **kılavuz sayfam**. Sağ bölmede seçenekler kılavuz görüntülenir. Özellik kategorisi **My seçenekleri**, ve özellik adı **My tamsayı seçeneği**. Özellik açıklaması **benim tamsayı seçeneğini**, bölmesinin en altında görünür. Değer 256'ın başlangıç değerinden başka bir şeye değiştirin. Tıklayın **Tamam**ve ardından yeniden **kılavuz sayfam**. Yeni değer devam ettiğini görebilirsiniz.  
  
     Seçenekler sayfası, Visual Studio'nun Hızlı Başlat da kullanılabilir. IDE'nin sağ üst köşedeki hızlı başlatma penceresinde yazın **My kategori** görürsünüz **My Kategori –> kılavuz sayfam** açılır menüde listelenir.  
  
## <a name="creating-a-tools-options-custom-page"></a>Araçlar Seçenekler özel oluşturma sayfası  
 Bu bölümde, özel bir kullanıcı Arabirimi ile bir araç seçenekleri sayfası oluşturun. Görüntülemek ve bir özelliğin değerini değiştirmek için bu sayfayı kullanın.  
  
1.  MyToolsOptionsPackage dosyası Kod Düzenleyicisi'nde açın.  
  
2.  Aşağıdaki using deyimi.  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Ekleme bir `OptionPageCustom` hemen önce sınıf `OptionPageGrid` sınıfı. Yeni türetin `DialogPage`.  
  
    ```csharp  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  GUID özniteliği ekleyin. OptionString özelliği Ekle:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  İkinci bir uygulama <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage sınıf. Bu öznitelik sınıfı bir kategori seçenekleri ve Seçenekleri sayfası adı atar.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Yeni bir **kullanıcı denetimi** MyUserControl için proje adı.  
  
7.  Ekleme bir **TextBox** kullanıcı denetimi için denetim.  
  
     İçinde **özellikleri** penceresinde, araç çubuğunda tıklatın **olayları** düğmesini ve ardından çift **bırakın** olay. Yeni olay işleyicisi MyUserControl.cs kodunda görüntülenir.  
  
8.  Genel ekleme `OptionsPage` alan, bir `Initialize` denetim sınıfı ve güncelleştirme seçeneğini ayarlamak için olay işleyicisi değeri metin kutusunun içeriğini yöntemi:  
  
    ```csharp  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     `optionsPage` Alan üst öğeye bir başvuru tutan `OptionPageCustom` örneği. `Initialize` Yöntemi görüntüler `OptionString` içinde **TextBox**. Olay işleyicisi geçerli değerini Yazar **TextBox** için `OptionString` bırakır'ne zaman odaklanmak **TextBox**.  
  
9. Paket kod dosyasında, ekleme için bir geçersiz kılma `OptionPageCustom.Window` oluşturma, başlatma ve bir örneğini döndürmek için OptionPageCustom sınıfına özellik `MyUserControl`. Sınıfı gibi görünmelidir:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Derleme ve projeyi çalıştırın.  
  
11. Deneysel örneğinde tıklayın **Araçlar / Seçenekler**.  
  
12. Bulma **My kategori** ardından **özel sayfa**.  
  
13. Değiştirin **OptionString**. Tıklayın **Tamam**ve ardından yeniden **özel sayfam**. Yeni değer kaydetti görebilirsiniz.  
  
## <a name="accessing-options"></a>Erişilebilirlik Seçenekleri  
 Bu bölümde, ilişkili araçları seçenekleri sayfasından barındıran VSPackage bir seçeneğin değerini alın. Herhangi bir genel özelliğin değerini almak için aynı tekniği kullanılabilir.  
  
1.  Adlı bir ortak özellik paketi kod dosyasında, ekleme **OptionInteger** için **MyToolsOptionsPackage** sınıfı.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Bu kod <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> oluşturmak veya almak için bir `OptionPageGrid` örneği. `OptionPageGrid` çağrıları <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> ortak özellikler, seçeneklerini yükleyemedi.  
  
2.  Şimdi adlı bir özel komut öğe şablonu ekleyin **MyToolsOptionsCommand** değerini görüntülemek için. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **özel komut**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme **MyToolsOptionsCommand.cs**.  
  
3.  Komutun gövdesi MyToolsOptionsCommand dosyasında değiştirin `ShowMessageBox` aşağıdaki yöntemi:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
5.  Deneysel örneğinde üzerinde **Araçları** menüsünde tıklatın **çağırma MyToolsOptionsCommand**.  
  
     Geçerli değeri bir ileti kutusu görüntüler `OptionInteger`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçenekler ve Seçenekler Sayfaları](../extensibility/internals/options-and-options-pages.md)

