---
title: Araç penceresine kısayol menüsü ekleme | Microsoft Docs
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
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 179a103475a47be95cbf45f88640b8a635a7ff34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796226"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Araç Penceresine Kısayol Menüsü Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol bir kısayol menüsü araç penceresine geçirir. Bir kullanıcı bir düğme, metin kutusu veya pencere arkaplanı tıklattığında görünen menüsünde bir kısayol menüsünü olur. Bir kısayol menü komutlarını diğer menü veya araç çubukları üzerindeki komutları olarak aynı şekilde davranır. Bir kısayol menüsü desteklemek için .vsct dosyası içinde belirtin ve yanıt sağ tıklama fare olarak görüntüler.  
  
 WPF kullanıcı denetimi devralan özel araç penceresi sınıfında araç penceresi oluşan <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 Bu izlenecek yol, bir kısayol menüsü .vsct dosyası menü öğelerinde bildirme ve ardından bunları araç penceresi tanımlayan sınıf içinde uygulama yönetilen paket çerçevesini kullanarak bir Visual Studio menü olarak oluşturma işlemi gösterilmektedir. Bu yaklaşım, Visual Studio komutları, kullanıcı Arabirimi öğeleri ve Otomasyon nesne modeli erişimi kolaylaştırır.  
  
 Alternatif olarak, Visual Studio işlevselliği, kısayol menüsünü erişemez, kullanabileceğiniz <xref:System.Windows.FrameworkElement.ContextMenu%2A> kullanıcı denetimi bir XAML öğesinde bir özelliğidir. Daha fazla bilgi için [ContextMenu](http://msdn.microsoft.com/library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Araç penceresi kısayol menüsü paketi oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun `TWShortcutMenu` adlı bir araç penceresi şablonu ekleyin **kısayol menüsü** ona. Araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Kısayol menüsünü belirtme  
 Bu izlenecek yolda gösterilen bir kullanıcı gibi sağlar bir kısayol menüsü araç penceresi arkaplanını doldurmak için kullanılan renkler listesinden seçin.  
  
1.  ShortcutMenuPackage.vsct, guidShortcutMenuPackageCmdSet adlı GuidSymbol öğesi içinde Bul ve kısayol menüsünde, kısayol menü grubu ve menü seçenekleri bildirin. GuidSymbol öğesi gibi görünmelidir:  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2.  Buttons öğesi hemen önce bir menü öğesi oluşturun ve kısayol menüsünden içinde tanımlayabilirsiniz.  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     Bir menü veya araç parçası olmadığından, kısayol menüsünü bir üst öğesi yok.  
  
3.  Groups öğesi kısayol menüsü öğelerini içeren bir Group öğesi oluşturun ve grubun kısayol menüsü ile ilişkilendirebilirsiniz.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  Buttons öğesi içinde kısayol menüsünde görünür tek tek komutlarla tanımlayın. Buttons öğesi gibi görünmelidir:  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5.  GUID, kısayol menüsünü ve menü öğeleri kümesi tanımlarını komutu için ShortcutMenuPackageGuids.cs içinde ekleyin.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Bunlar ShortcutMenuPackage.vsct dosyasının sembolleri bölümünde tanımlanan komut kimlikleri aynı olur. Bağlam grubunun yalnızca .vsct dosyasında gerekli olduğundan buraya dahil edilmez.  
  
## <a name="implementing-the-shortcut-menu"></a>Kısayol menüsünden uygulama  
 Bu bölümde, kısayol menüsünü ve alt komutları uygular.  
  
1.  ShortcutMenu.cs, araç penceresini menü komutu hizmeti alabilir, ancak içerdiği denetleyemezsiniz. Aşağıdaki adımlarda, menü komutu hizmeti kullanıcı denetimi kullanılabilir hale getirmek gösterilmektedir.  
  
2.  ShortcutMenu.cs içinde aşağıdaki ekleme using deyimlerini:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Menü komutu hizmeti alın ve menü komutu hizmeti için oluşturucu geçirme denetimi eklemek için araç penceresinin Initialize() yöntemini geçersiz kılın:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Kısayol menüsü araç penceresi oluşturucuda denetimi ekler satırı kaldırın. Oluşturucu gibi görünmelidir:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  ShortcutMenuControl.xaml.cs, menü komutu hizmeti için özel bir alan ekleyin ve denetimi Oluşturucusu menü komutu hizmeti almak için değiştirin. Ardından bağlam menüsü komutları eklemek için menü komutu hizmeti kullanın. ShortcutMenuControl Oluşturucusu artık şu kod gibi görünmelidir. Komut işleyici daha sonra tanımlanır.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  ShortcutMenuControl.xaml içinde ekleme bir <xref:System.Windows.UIElement.MouseRightButtonDown> olayını en üst düzey <xref:System.Windows.Controls.UserControl> öğesi. XAML dosyası gibi görünmelidir:  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7.  Olay işleyicisi için bir saplama ShortcutMenuControl.xaml.cs içinde ekleyin.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Aşağıdaki using deyimlerini aynı dosyaya:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Uygulama `MyToolWindowMouseRightButtonDown` aşağıdaki gibi olay.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Bu, oluşturur bir <xref:System.ComponentModel.Design.CommandID> nesne için kısayol menüsünü fare tıklatın konumunu tanımlar ve kısayol menüsünü kullanarak söz konusu konumda açılır <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> yöntemi.  
  
10. Komut işleyici uygulayın.  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     Bu durumda, yalnızca bir yöntem tanımlayarak tüm menü öğeleri için olayları işler <xref:System.ComponentModel.Design.CommandID> ve uygun şekilde arka plan rengini ayarlama. Menü öğelerini ilgisiz komutları içeriyorsa, her komut için bir ayrı bir olay işleyicisi oluşturacak.  
  
## <a name="testing-the-tool-window-features"></a>Araç penceresi özelliklerini test etme  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
2.  Deneysel örneğinde tıklayın **görünüm / diğer Windows**ve ardından **kısayol menüsü**. Bunun yapılması, araç penceresi görüntülenmelidir.  
  
3.  Araç penceresi gövdesinde sağ tıklayın. Renk listesi olan bir kısayol menüsü görüntülenmesi gerekir.  
  
4.  Kısayol menüsünde rengi. Araç penceresi arka plan rengini seçilen renge değiştirilmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Hizmetleri Kullanma ve Sağlama](../extensibility/using-and-providing-services.md)

