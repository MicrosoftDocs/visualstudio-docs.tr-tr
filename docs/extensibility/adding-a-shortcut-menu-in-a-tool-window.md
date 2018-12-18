---
title: Araç penceresine kısayol menüsü ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5567fd2fe72b8fcc102c8609ac0d155f78141a9
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078621"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Araç penceresine kısayol menüsü ekleme
Bu izlenecek yol bir kısayol menüsü araç penceresine geçirir. Bir kullanıcı bir düğme, metin kutusu veya pencere arkaplanı tıklattığında görünen menüsünde bir kısayol menüsünü olur. Bir kısayol menü komutlarını diğer menü veya araç çubukları üzerindeki komutları olarak aynı şekilde davranır. Bir kısayol menüsü desteklemek için projeyi belirtin *.vsct* dosya ve yanıt olarak sağ tıklama fare görüntüleyin.  
  
 WPF kullanıcı denetimi devralan özel araç penceresi sınıfında araç penceresi oluşan <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 Bu izlenecek yol, bir kısayol menüsünü menü öğelerinde bildirerek bir Visual Studio menü olarak oluşturma işlemi gösterilmektedir *.vsct* dosya ve ardından araç penceresini tanımlar sınıfında uygulanacağı yönetilen paket çerçevesini kullanarak. Bu yaklaşım, Visual Studio komutları, kullanıcı Arabirimi öğeleri ve Otomasyon nesne modeli erişimi kolaylaştırır.  
  
 Alternatif olarak, Visual Studio işlevselliği, kısayol menüsünü erişemez, kullanabileceğiniz <xref:System.Windows.FrameworkElement.ContextMenu%2A> kullanıcı denetimi bir XAML öğesinde bir özelliğidir. Daha fazla bilgi için [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-the-tool-window-shortcut-menu-package"></a>Araç penceresi kısayol menüsü paketi oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun `TWShortcutMenu` adlı bir araç penceresi şablonu ekleyin **kısayol menüsü** ona. Araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Kısayol menüsünü belirtme  
 Bu izlenecek yolda gösterilen bir kullanıcı gibi sağlar bir kısayol menüsü araç penceresi arkaplanını doldurmak için kullanılan renkler listesinden seçin.  
  
1.  İçinde *ShortcutMenuPackage.vsct*guidShortcutMenuPackageCmdSet adlı GuidSymbol öğesi içinde Bul ve kısayol menüsünde, kısayol menü grubu ve menü seçenekleri bildirin. GuidSymbol öğesi gibi görünmelidir:  
  
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
  
5.  İçinde *ShortcutMenuCommand.cs*, GUID, kısayol menüsünü ve menü öğeleri Ayarla komutu tanımları ekleyin.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Semboller bölümünde tanımlanan komut kimlikleri aynı bunlar *ShortcutMenuPackage.vsct* dosya. Yalnızca gerekli olduğu için bağlam grubunun buraya dahil edilmez *.vsct* dosya.  
  
## <a name="implementing-the-shortcut-menu"></a>Kısayol menüsünden uygulama  
 Bu bölümde, kısayol menüsünü ve alt komutları uygular.  
  
1.  İçinde *ShortcutMenu.cs*, araç penceresini menü komutu hizmeti alabilir, ancak içerdiği denetleyemezsiniz. Aşağıdaki adımlarda, menü komutu hizmeti kullanıcı denetimi kullanılabilir hale getirmek gösterilmektedir.  
  
2.  İçinde *ShortcutMenu.cs*, aşağıdaki using deyimlerini:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Menü komutu hizmeti alın ve menü komutu hizmeti oluşturucuya geçirme denetimi eklemek için araç penceresinin Initialize() yöntemini geçersiz kılın:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
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
  
5.  İçinde *ShortcutMenuControl.xaml.cs*menü komutu hizmeti için özel bir alan ekleyin ve denetimi Oluşturucusu menü komutu hizmeti almak için değiştirin. Ardından bağlam menüsü komutları eklemek için menü komutu hizmeti kullanın. ShortcutMenuControl Oluşturucusu artık şu kod gibi görünmelidir. Komut işleyici daha sonra tanımlanır.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  İçinde *ShortcutMenuControl.xaml*, ekleme bir <xref:System.Windows.UIElement.MouseRightButtonDown> olayını en üst düzey <xref:System.Windows.Controls.UserControl> öğesi. XAML dosyası gibi görünmelidir:  
  
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
  
7.  İçinde *ShortcutMenuControl.xaml.cs*, olay işleyicisi için bir saplama ekleyin.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
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
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuCommand.ColorMenu);  
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
            case ShortcutMenuCommand.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuCommand.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuCommand.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     Bu durumda, yalnızca bir yöntem tanımlayarak tüm menü öğeleri için olayları işler <xref:System.ComponentModel.Design.CommandID> ve uygun şekilde arka plan rengini ayarlama. Menü öğelerini ilgisiz komutları içeriyorsa, her komut için bir ayrı bir olay işleyicisi oluşturacak.  
  
## <a name="test-the-tool-window-features"></a>Araç penceresi özelliklerini test etme  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
2.  Deneysel örneğinde tıklayın **görünüm / diğer Windows**ve ardından **kısayol menüsü**. Bunun yapılması, araç penceresi görüntülenmelidir.  
  
3.  Araç penceresi gövdesinde sağ tıklayın. Renk listesi olan bir kısayol menüsü görüntülenmesi gerekir.  
  
4.  Kısayol menüsünde rengi. Araç penceresi arka plan rengini seçilen renge değiştirilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)