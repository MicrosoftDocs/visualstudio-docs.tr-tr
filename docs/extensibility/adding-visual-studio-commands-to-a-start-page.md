---
title: Bir başlangıç sayfasına Visual Studio komutları ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22ae9ebb5e9acb3fa1787f2af3b0fbb159c1485d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153637"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Visual Studio komutları için bir başlangıç sayfası Ekle
Özel başlangıç sayfası oluşturduğunuzda, Visual Studio komutları ekleyebilirsiniz. Bu belge, Visual Studio komutları bir başlangıç sayfası XAML nesnelerde bağlamak için farklı yolları açıklanmaktadır.  
  
 XAML içindeki komutlar hakkında daha fazla bilgi için bkz. [Commanding genel bakış](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>Komuttan da komutları eklendi  
 Başlangıç sayfası oluşturulan [özel bir başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md) eklenen <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> ve <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> ad alanları, aşağıdaki gibi.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Başka bir ad alanı için Microsoft.VisualStudio.Shell derlemeden ekleme *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Bu derlemeye olan başvuruyu projenize eklemeniz gerekebilir.)  
  
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
  
### <a name="call-extensions-from-the-command-well"></a>Uzantıları komuttan da çağırın  
 Diğer Visual Studio komutları çağırmak için kullanılan aynı sözdizimini kullanarak kayıtlı VSPackages komutları çağırabilirsiniz. Yüklü bir VSPackage ekler, örneğin, bir **giriş sayfası** komutunu **görünümü** menüsünde ayarlayarak bu komut çağırabilirsiniz `CommandParameter` için `View.HomePage`.  
  
> [!NOTE]
>  VSPackage'ı ile ilişkili bir komut çağırırsanız, komut çağrıldığında paketin yüklenmesi gerekir.  
  
## <a name="add-commands-from-assemblies"></a>Derlemelerden komutları eklendi  
 Bir komutu bir derlemeden veya vspackage'ta bir menü komutu ile ilişkilendirilmemiş erişim kodu çağırmak için derleme için bir diğer ad oluşturmak ve diğer ad'ı çağırın.  
  
### <a name="to-call-a-command-from-an-assembly"></a>Bir derlemeden bir komutu çağırmak için  
  
1.  Çözümünüz içinde derlemesine bir başvuru ekleyin.  
  
2.  Üst kısmındaki *StartPage.xaml* , derleme için bir ad alanı yönerge ekleyin aşağıdaki örnekte gösterildiği gibi dosya.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Komut ayarlayarak çağırma `Command` aşağıdaki örnekte gösterildiği gibi bir XAML nesnesinin özelliği.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Derlemenizi kopyalayın ve ardından yapıştırın *... \\{Visual Studio yükleme klasörü} \Common7\IDE\PrivateAssemblies\* bunu çağrılmadan önce yüklendiği emin olmak için.  
  
## <a name="add-commands-with-the-dte-object"></a>DTE nesnesi ile komutları eklendi  
 Bir başlangıç sayfası, hem işaretleme ve kod DTE nesnesine erişebilir.  
  
 Biçimlendirme içinde kullanarak erişebildiğinizden [biçimlendirme uzantısı bağlama](/dotnet/framework/wpf/advanced/binding-markup-extension) çağırmak için söz dizimi <xref:EnvDTE.DTE> nesne. Koleksiyonları döndüren olanlar gibi basit özelliklerine bağlamak için bu yaklaşımı kullanabilirsiniz, ancak yöntemler veya hizmetlerine bağlanamıyor. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> bağlar denetim <xref:EnvDTE._DTE.Name%2A> özelliği ve <xref:System.Windows.Controls.ListBox> numaralandırır denetimin <xref:EnvDTE.Window.Caption%2A> tarafından döndürülen koleksiyon özellikleri <xref:EnvDTE._DTE.Windows%2A> özelliği.  
  
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
  
 Bir örnek için bkz. [izlenecek yol: bir başlangıç sayfasında kullanıcı ayarları kaydediliyor](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Başlangıç sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)