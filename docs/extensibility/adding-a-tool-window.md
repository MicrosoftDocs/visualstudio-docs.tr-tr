---
title: Araç penceresi ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 550e483ec2a8cd4b4126e4c0838dc8d2870af59c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151937"
---
# <a name="add-a-tool-window"></a>Araç penceresi ekleme
Bu kılavuzda bir araç penceresi oluşturun ve aşağıdaki yollarla Visual Studio ile tümleştirme hakkında bilgi edinin:  
  
-   Bir denetim için araç penceresini ekleyin.  
  
-   Araç penceresine araç çubuğu ekleyin.  
  
-   Araç çubuğuna komut ekleme.  
  
-   Komutlar uygulayın.  
  
-   Araç penceresi için varsayılan konum olarak ayarlayın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-tool-window"></a>Araç penceresi oluşturma  
  
1.  Adlı bir proje oluşturma **FirstToolWin** VSIX şablonuyla ve adlı bir özel araç penceresi öğesi şablonu ekleme **FirstToolWindow**.  
  
    > [!NOTE]
    >  Araç penceresi içeren bir uzantı oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Denetim için araç penceresi ekleme  
  
1.  Varsayılan Denetim kaldırın. Açık *FirstToolWindowControl.xaml* ve silme **Me tıklayın!** düğmesi.  
  
2.  İçinde **araç kutusu**, genişletme **tüm WPF denetimleri** bölümünde ve sürükleyin **medya öğesi** denetimini **FirstToolWindowControl** formu. İstediğiniz denetimi seçin ve **özellikleri** penceresinde, bu öğe adı **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Araç penceresine araç çubuğu ekleme  
 Aşağıdaki şekilde bir araç çubuğu ekleyerek, renkler ve gradyanlar IDE geri kalanı ile tutarlı olduğunu garanti.  
  
1.  İçinde **Çözüm Gezgini**açın *FirstToolWindowPackage.vsct*. *.Vsct* dosya grafik kullanıcı arabirimi (GUI) öğelerini tanımlar, araç penceresinde XML kullanarak.  
  
2.  İçinde `<Symbols>` bölümünde, bulma `<GuidSymbol>` düğümü olan `name` özniteliği `guidFirstToolWindowPackageCmdSet`. Aşağıdaki iki ekleme `<IDSymbol>` listesi öğelerine `<IDSymbol>` bir araç çubuğu ve araç çubuğu grubu tanımlamak için bu düğümünde öğeleri.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Yukarıdaki `<Buttons>` bölümünde, oluşturun bir `<Menus>` bu benzer bölümü:  
  
    ```xml  
    <Menus>  
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">  
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
            <Strings>  
                <ButtonText>Tool Window Toolbar</ButtonText>  
                <CommandName>Tool Window Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Menü birkaç farklı tür vardır. Bu menü tarafından tanımlanan bir araç çubuğunda bir araç penceresi olup kendi `type` özniteliği. `guid` Ve `id` ayarları yapmak araç çubuğunun tam kimliği. Genellikle, `<Parent>` menüsü içeren grubudur. Ancak, bir araç kendi üst öğe olarak tanımlanır. Bu nedenle, aynı tanımlayıcı için kullanılan `<Menu>` ve `<Parent>` öğeleri. `priority` Özniteliktir sadece ' 0'.  
  
4.  Araç çubukları, menüler birçok yönden benzer. Örneğin, menü komutları grupları yalnızca olabilir gibi araç çubukları ayrıca gruplarınız olabilir. (Menülerde, komut gruplarını yatay çizgilerle ayrılır. Araç çubukları gruplar tarafından visual Bölücü ayrılmış değil.)  
  
     Ekleme bir `<Groups>` içeren bölümü bir `<Group>` öğesi. Bu kimliği içinde bildirilen grubu tanımlar `<Symbols>` bölümü. Ekleme `<Groups>` hemen sonrasına bölümünde `<Menus>` bölümü.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Üst GUID ve ID GUID ve ID araç için ayarlayarak, Grup araç çubuğuna ekleyin.  
  
## <a name="add-a-command-to-the-toolbar"></a>Araç çubuğuna komut ekleme  
 Bir düğme olarak görüntülenen araç, bir komut ekleyin.  
  
1.  İçinde `<Symbols>` bölümünde, aşağıdaki Idsymbol öğeleri yalnızca araç çubuğu ve araç sonra Grup bildirimleri bildirin.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Bir Button öğesi içinde Ekle `<Buttons>` bölümü. Bu öğe ile araç penceresi araç çubuğunda görünür bir **arama** simgesi (Büyüteç).  
  
    ```xml  
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">  
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <Strings>  
            <CommandName>cmdidWindowsMediaOpen</CommandName>  
            <ButtonText>Load File</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Açık *FirstToolWindowCommand.cs* ve sonra yalnızca varolan alanların sınıfında aşağıdaki satırları ekleyin.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     Bunun yapılması komutlarınızı kodda kullanılabilir hale getirir.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>İçin FirstToolWindowControl MediaPlayer özellik ekleme  
 Araç çubuğu denetimleri için olay işleyicilerindeki kodunuzu FirstToolWindowControl sınıfı alt Media Player denetimi erişebilir olması gerekir.  
  
 İçinde **Çözüm Gezgini**, sağ *FirstToolWindowControl.xaml*, tıklayın **kodu görüntüle**ve FirstToolWindowControl sınıfa aşağıdaki kodu ekleyin.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Araç çubuğu ve araç penceresi örneği  
 Bir araç ve çağıran bir menü komutu eklemek **açık dosya** iletişim ve seçilen ortam dosyasını yürütür.  
  
1.  Açık *FirstToolWindow.cs* ve aşağıdakileri ekleyin `using` deyimleri.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  FirstToolWindow sınıf içinde FirstToolWindowControl denetim genel bir başvuru ekleyin.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  Oluşturucu sonunda, yeni oluşturulan denetime bu denetim değişkeni ayarlayın.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Oluşturucu içinde araç örneği oluşturur.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  Bu noktada FirstToolWindow Oluşturucusu şu şekilde görünmelidir:  
  
    ```csharp  
    public FirstToolWindow() : base(null)  
    {  
        this.Caption = "FirstToolWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
        control = new FirstToolWindowControl();  
        base.Content = control;  
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
            FirstToolWindowCommand.ToolbarID);  
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    }  
    ```  
  
6.  Araç çubuğuna menü komutunu ekleyin. FirstToolWindowCommand.cs sınıfında, aşağıdaki ekleyin using deyimi  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  FirstToolWindowCommand sınıfında ShowToolWindow() yönteminin sonunda aşağıdaki kodu ekleyin. Sonraki bölümde ButtonHandler komut uygulanacaktır.  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Araç penceresinde bir menü komutu uygulamak için  
  
1.  Çağıran bir ButtonHandler yöntemi FirstToolWindowCommand sınıfta ekleyin **açık dosya** iletişim. Bir dosyayı seçili olduğunda, medya dosyası yürütülür.  
  
2.  FirstToolWindowCommand sınıfında FirstToolWindow pencerenin FindToolWindow() yönteminde oluşturulan özel bir başvuru ekleyin.  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Yukarıda tanımlanan (ButtonHandler komut işleyici pencere denetime erişebilirsiniz. böylece penceresini ayarlamak için ShowToolWindow() yöntemi Değiştir Tam ShowToolWindow() yöntemi aşağıda verilmiştir.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
                            throw new NotSupportedException("Cannot create tool window");  
        }  
  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
         var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),  
            FirstToolWindowCommand.cmdidWindowsMediaOpen);  
        var menuItem = new MenuCommand(new EventHandler(  
            ButtonHandler), toolbarbtnCmdID);  
        mcs.AddCommand(menuItem);  
    }  
    ```  
  
4.  ButtonHandler yöntemi ekleyin. Oynatmak için medya dosyasını belirtmek bir kullanıcı için bir OpenFileDialog oluşturur ve sonra seçilen dosyayı yürütür.  
  
    ```csharp  
    private void ButtonHandler(object sender, EventArgs arguments)  
    {  
        OpenFileDialog openFileDialog = new OpenFileDialog();  
        DialogResult result = openFileDialog.ShowDialog();  
        if (result == DialogResult.OK)  
        {  
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);  
        }  
    }  
    ```  
  
## <a name="set-the-default-position-for-the-tool-window"></a>Araç penceresi için varsayılan konumu ayarlayın  
 Ardından, araç penceresi için IDE'de varsayılan konumu belirtin. Araç penceresi için yapılandırma bilgilerini konusu *FirstToolWindowPackage.cs* dosya.  
  
1.  İçinde *FirstToolWindowPackage.cs*, bulma <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> özniteliği `FirstToolWindowPackage` sınıfını FirstToolWindow oluşturucuya geçirir. Varsayılan konumu belirtmek için aşağıdaki örnekte oluşturucuya daha fazla parametre eklemeniz gerekir.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     İlk adlandırılmış parametre `Style` ve değeri `Tabbed`, yani pencere varolan pencereye bir sekmede olacaktır. Yerleştirme konumunu tarafından belirtilen `Window` parametresi, bu durumda, n GUID **Çözüm Gezgini**.  
  
    > [!NOTE]
    >  IDE'de pencereleri türleri hakkında daha fazla bilgi için bkz. <xref:EnvDTE.vsWindowType>.  
  
## <a name="test-the-tool-window"></a>Araç penceresi test  
  
1.  Tuşuna **F5** Visual Studio Deneysel derlemesi yeni bir örneğini açın.  
  
2.  Üzerinde **görünümü** menüsünde **diğer Windows** ve ardından **ilk araç penceresi**.  
  
     Media player araç penceresi aynı konumda açılmalıdır **Çözüm Gezgini**. Hala öncekiyle aynı konumda görüntüleniyorsa, pencere düzenini Sıfırla (**penceresi / pencere düzenini Sıfırla**).  
  
3.  Düğmesine tıklayın (sahip **arama** simgesi) araç penceresindeki. Örneğin, desteklenen bir ses veya video dosyası seçin *C:\windows\media\chimes.wav*, tuşuna **açık**.  
  
     Çan sesi duymak.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)