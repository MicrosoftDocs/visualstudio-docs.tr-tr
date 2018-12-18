---
title: Bir başlangıç sayfasına Visual Studio komutları ekleme | Microsoft Docs
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
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a5a0e205d04fb219d000dd87e97735cdfd26162
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748755"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Başlangıç Sayfasına Visual Studio Komutları Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel başlangıç sayfası oluşturduğunuzda, Visual Studio komutları ekleyebilirsiniz. Bu belge, Visual Studio komutları bir başlangıç sayfası XAML nesnelerde bağlamak için farklı yolları açıklanmaktadır.  
  
 XAML içindeki komutlar hakkında daha fazla bilgi için bkz. [komut vermeye genel genel bakış](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Komuttan da komut ekleme  
 Başlangıç sayfası oluşturulan [bir özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md) eklenen <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> ve <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> ad alanları, aşağıdaki gibi.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Başka bir ad alanı için Microsoft.VisualStudio.Shell Microsoft.VisualStudio.Shell.Immutable.11.0.dll derlemesinden ekleyin. (Bu derlemeye olan başvuruyu projenize eklemeniz gerekebilir.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Kullanabileceğiniz `vscom:` Visual Studio komutları için XAML bağlamak için diğer ad ayarlayarak sayfada denetimleri <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> denetimin özellik `vscom:VSCommands.ExecuteCommand`. Ardından ayarlayabilirsiniz <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> özelliğini aşağıdaki örnekte gösterildiği gibi yürütmek için komut adı.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Tüm komutları başında XAML şemaya gösterir, diğer ad gereklidir.  
  
 Değerini ayarlayabilirsiniz `Command` erişilebilen herhangi bir komuta özelliği **komut** penceresi. Kullanılabilir komutların bir listesi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).  
  
 Eklenecek komut ek bir parametre gerektiriyorsa, değerine ekleyebilirsiniz `CommandParameter` özelliği. Alanları, aşağıdaki örnekte gösterildiği gibi kullanarak komutları ayrı parametreler.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Uzantıları komuttan da çağırma  
 Diğer Visual Studio komutları çağırmak için kullanılan aynı sözdizimini kullanarak kayıtlı VSPackages komutları çağırabilirsiniz. Yüklü bir VSPackage ekler, örneğin, bir **giriş sayfası** komutunu **görünümü** menüsünde ayarlayarak bu komut çağırabilirsiniz `CommandParameter` için `View.HomePage`.  
  
> [!NOTE]
>  VSPackage'ı ile ilişkili bir komut çağırırsanız, komut çağrıldığında paketin yüklenmesi gerekir.  
  
## <a name="adding-commands-from-assemblies"></a>Derlemelerden komut ekleme  
 Bir komutu bir derlemeden veya vspackage'ta bir menü komutu ile ilişkilendirilmemiş erişim kodu çağırmak için derleme için bir diğer ad oluşturmak ve diğer ad'ı çağırın.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Bir derlemeden bir komutu çağırmak için  
  
1.  Çözümünüz içinde derlemesine bir başvuru ekleyin.  
  
2.  StartPage.xaml dosyasının en üstüne aşağıdaki örnekte gösterildiği gibi derleme için bir ad alanı yönergesi ekleyin.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Komut ayarlayarak çağırma `Command` aşağıdaki örnekte gösterildiği gibi bir XAML nesnesinin özelliği.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Derlemenizi kopyalayıp içine yapıştırın... \\ *Visual Studio yükleme klasörü*\Common7\IDE\PrivateAssemblies\ bunu çağrılmadan önce yüklendiği emin olmak için.  
  
## <a name="adding-commands-with-the-dte-object"></a>DTE nesnesi ile komut ekleme  
 Bir başlangıç sayfası, hem işaretleme ve kod DTE nesnesine erişebilir.  
  
 Biçimlendirme içinde kullanarak erişebildiğinizden [biçimlendirme uzantısı bağlama](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) çağırmak için söz dizimi <xref:EnvDTE.DTE> nesne. Koleksiyonları döndüren olanlar gibi basit özelliklerine bağlamak için bu yaklaşımı kullanabilirsiniz, ancak yöntemler veya hizmetlerine bağlanamıyor. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> bağlar denetim <xref:EnvDTE._DTE.Name%2A> özelliği ve <xref:System.Windows.Controls.ListBox> numaralandırır denetimin <xref:EnvDTE.Window.Caption%2A> tarafından döndürülen koleksiyon özellikleri <xref:EnvDTE._DTE.Windows%2A> özelliği.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Bir örnek için bkz. [izlenecek yol: bir başlangıç sayfasındaki kullanıcı ayarları kaydediliyor](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Sayfasına Kullanıcı Denetimi Ekleme](../extensibility/adding-user-control-to-the-start-page.md)

