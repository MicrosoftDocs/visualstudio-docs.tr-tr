---
title: Bir menüye alt menü ekleme | Microsoft Docs
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
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14ad9d2daf603dd2ca80a784251f19503fee1cba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738324"
---
# <a name="adding-a-submenu-to-a-menu"></a>Bir Menüye Alt Menü Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek gösteride yer geliştirir [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) menüye ekleme göstererek **TestMenu** menüsü.  
  
 Bir alt başka bir menüde görünen ikincil menüsünde ' dir. Bir alt adını izleyen bir ok ile tanımlanabilir. Adına tıklayarak, alt ve görüntülenecek komutlarının neden olur.  
  
 Bu izlenecek yol Visual Studio menü çubuğunda bir menü bir alt oluşturur ve alt menüsünden Yeni bir komut yerleştirir. İzlenecek yol, yeni bir komut de uygular.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Bir Menüye Alt Menü Ekleme  
  
1.  Bağlantısındaki [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) proje ve menü öğesi oluşturmak için. Bu kılavuzda açıklanan adımları VSIX projesinin adı olduğunu varsayar `TopLevelMenu`.  
  
2.  Open TestCommandPackage.vsct. İçinde `<Symbols>` bölümünde, eklemek bir `<IDSymbol>` öğesi için alt menüyü, alt grup için diğeri için komut tüm `<GuidSymbol>` "guidTopLevelMenuCmdSet." adlı düğüm Bu, içerir, aynı düğümdür `<IDSymbol>` için üst düzey menü öğesi.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Yeni oluşturulan menüye ekleme `<Menus>` bölümü.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Oluşturulduğu grubun üst GUID/ID çiftini belirtir [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), ve üst düzey menü bir alt öğesidir.  
  
4.  2 adımda tanımladığınız menü grubu ekleme `<Groups>` bölüm ve bir alt alt öğesi yapın.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Yeni bir `<Button>` öğesine `<Buttons>` alt öğe olarak 2. adımda oluşturduğunuz komut tanımlamak için bölümünde.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Çözümü derleyin ve hata ayıklamaya başlayın. Deneysel örneği görmeniz gerekir.  
  
7.  Tıklayın **TestMenu** adlı yeni bir alt görmek için **alt menü**. Tıklayın **alt menü** alt menüyü açın ve yeni bir komut görmek için **Test alt komut**. Sonuçlandığını fark **Test alt komut** hiçbir şey yapmaz.  
  
## <a name="adding-a-command"></a>Komut ekleme  
  
1.  TestCommand.cs açın ve aşağıdaki komut kimliği mevcut komut kimliği. sonra ekleyin.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Alt komut ekleyin. Komut Oluşturucu bulun. Çağırdıktan hemen sonra aşağıdaki satırları ekleyin `AddCommand` yöntemi.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` Komut işleyicisi tanımlanması daha sonra. Oluşturucu gibi görünmelidir:  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  SubItemCallback() ekleyin. Yeni alt komutu tıklandığında çağrılan yöntem budur.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
5.  Üzerinde **TestMenu** menüsünde tıklatın **alt menü** ve ardından **Test alt komut**. Bir ileti kutusu görünür ve "TestCommand.SubItemCallback() içinde Test komut" metni görüntülemek gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)

