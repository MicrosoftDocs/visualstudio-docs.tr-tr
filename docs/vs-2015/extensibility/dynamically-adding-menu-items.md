---
title: Dinamik olarak menü öğeleri ekleme | Microsoft Docs
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
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8f188c71cb1e25364cee34c6a97c87b3a265ee7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809759"
---
# <a name="dynamically-adding-menu-items"></a>Dinamik Olarak Menü Öğeleri Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışma zamanında menü öğelerini belirterek ekleyebilirsiniz `DynamicItemStart` (kodda) menüsünde sayısını tanımlama görüntüleme ve komut işleme daha sonra Visual Studio komut tablosu (.vsct) dosyasında bir yer tutucu düğmesi tanımı bayrağı komutu. VSPackage'ı yüklendiğinde, yer tutucu Dinamik menü öğeleri ile değiştirilir.  
  
 Visual Studio kullanan dinamik listelerinde **en son kullanılan** (MRU) listesinde, son açtığınız belgeleri adlarını görüntüler ve **Windows** windows adlarını gösteren liste şu anda açık olan.   `DynamicItemStart` Bir komut tanımı bayrağı VSPackage açılıncaya kadar komutu bir yer tutucu olduğunu belirtir. VSPackage'ı açıldığında, yer tutucu 0 ya da çalışma zamanında oluşturulan ve dinamik listeye eklenen diğer komutları ile değiştirilir. VSPackage'ı açılıncaya kadar dinamik listesi göründüğü menüsünde konumu görmek mümkün olmayabilir.  Dinamik listeyi doldurmak için VSPackage'ı ilk karakterine yer tutucu kimliği aynı olan bir Kimliğe sahip bir komut aramak için Visual Studio ister. Visual Studio eşleşen bir komut bulduğunda, komutun adını dinamik listesine ekler. Ardından kimliği artırır ve kalmayana kadar daha fazla dinamik komutları dinamik listeye eklemek için başka bir eşleşen komutunu arar.  
  
 Bu izlenecek yol, üzerinde bir komut ile Visual Studio çözümünde başlangıç projesi ayarlama işlemi gösterilmektedir **Çözüm Gezgini** araç çubuğu. Etkin çözüm projeleri dinamik açılan listesine sahip bir menü denetleyicisi kullanır. Bu komut çözüm olduğunda görünmesini engellemek için açık olan veya açık çözüme tek bir proje varsa, yalnızca bir çözüm birden çok proje olduğunda VSPackage yüklenir.  
  
 .Vsct dosyaları hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Bir Menü Komutuyla Uzantı Oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun `DynamicMenuItems`.  
  
2.  Projeyi açtığında, bir özel komut öğe şablonu ekleyin ve adlandırın **DynamicMenu**. Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>.Vsct dosyası öğeleri ayarlama  
 Dinamik menü öğeleri araç çubuğuna menü denetleyicisi oluşturmak için aşağıdaki öğeleri belirtin:  
  
-   Grupları, menü denetleyicisi içeren bir ve açılır menü öğelerini içeren başka iki komutu  
  
-   Bir menü öğesi türü `MenuController`  
  
-   İki düğme, bir simge veya araç ipucu sağlayan bir yer tutucu menü öğeleri ve başka bir görevi görür.  
  
1.  Komut kimlikleri DynamicMenuPackage.vsct içinde tanımlayın. Semboller bölümüne gidin ve Idsymbol öğeleri değiştirin **guidDynamicMenuPackageCmdSet** GuidSymbol blok. İki grup, menü denetleyicisi, yer tutucu komut ve bağlantı komutu için Idsymbol öğeleri tanımlamak gerekir.  
  
    ```csharp  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  Grupları bölümünde, mevcut gruplarını silin ve az önce tanımladığınız iki gruplarını ekleyin:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     MenuController ekleyin. Her zaman görünür olmadığından DynamicVisibility komut bayrağını ayarlayın. ButtonText görüntülenmez.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Dinamik menü öğeleri için bir yer tutucu olarak biri diğeri bir yer işareti olarak iki düğme için MenuController ekleyin.  
  
     Yer tutucu düğmenin üst **MyMenuControllerGroup**. DynamicItemStart DynamicVisibility ve TextChanges komut bayrakları için yer tutucu düğmesi ekleyin. ButtonText görüntülenmez.  
  
     Bağlantı düğmesi, simge ve araç ipucu metni içerir. Ayrıca üst bağlantı düğmesi olduğunu **MyMenuControllerGroup**. NoShowOnMenuController komut bayrak düğme açılan menüden denetleyicisi gerçekten etmediğinden emin olun ve kalıcı bağlantı yapmak için FixMenuController komut bayrağını ekleyin.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Simge (kaynak klasördeki) projeye eklemek ve ardından .vsct dosyası içinde başvuru ekleyin. Bu izlenecek yolda, proje şablonunda yer oklar simgesi kullanırız.  
  
5.  Semboller bölüm hemen önce komutları bölümüne dışında bir VisibilityConstraints bölümü ekleyin. (Sonra sembolleri eklerseniz, bir uyarı alabilirsiniz.) Bu bölümde, menü denetleyicisi, yalnızca zaman birden çok proje içeren bir çözüm yüklendikten göründüğünü emin olur.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Dinamik menü komutunu uygulama  
 Devralınan bir Dinamik menü komut sınıfı oluşturma <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. Bu uygulama, oluşturucu eşleşen komutları için kullanılacak bir koşulu belirtir. Geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> bu koşul için kullanılacak yöntemi <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> özelliği çağrılacak komut tanımlar.  
  
1.  DynamicItemMenuCommand.cs adlı yeni bir C# sınıf dosyası oluşturun ve adlı bir sınıf ekleyin **DynamicItemMenuCommand** öğesinden devralan <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Aşağıdaki using deyimlerini:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Eşleşme koşulu depolamak için özel bir alan ekleyin:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Devralınan bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> oluşturucu ve bir komut işleyici belirtir ve bir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> işleyici. Komut eşleme için bir koşul ekleyin:  
  
    ```csharp  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Geçersiz kılma <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> BT'nin eşleşme koşulu ve kümeleri çağırır yöntemi <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> özelliği:  
  
    ```csharp  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## <a name="adding-the-command"></a>Komut ekleme  
 Dinamik menüler ve menü öğeleri de dahil olmak üzere, menü komutlarını ayarladığınız DynamicMenu oluşturucudur.  
  
1.  DynamicMenuPackageGuids.cs içinde komut kümesi GUID'si ve komut Kimliğini ekleyin:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  DynamicMenu.cs dosyasına aşağıdakileri ekleyin using deyimlerini:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  DynamicMenu sınıfında özel bir alan ekleme **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Bir özel rootItemId alan ekleyin:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  DynamicMenu oluşturucusunun içinde menü komutunu ekleyin. Sonraki bölümde biz komut işleyicisi tanımlama olasılığınız `BeforeQueryStatus` eşleşme koşulu ve olay işleyicisi.  
  
    ```csharp  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## <a name="implementing-the-handlers"></a>İşleyicileri uygulama  
 Dinamik menü öğelerini menü denetleyicisi üzerinde uygulamak için dinamik bir öğe tıklatıldığında komut işlemesi gerekir. Ayrıca, menü öğesi durumunu ayarlar mantığı uygulamalıdır. İşleyicileri DynamicMenu sınıfına ekleyin.  
  
1.  Uygulamak için **başlangıç projesi ayarlama** komutu, ekleme **OnInvokedDynamicItem** olay işleyicisi. Projenin adı çağrıldıktan ve mutlak yolu ayarlayarak başlangıç projesi olarak ayarlar komut metni ile aynı olan arar <xref:EnvDTE.SolutionBuild.StartupProjects%2A> özelliği.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Ekleme `OnBeforeQueryStatusDynamicItem` olay işleyicisi. Bu önce adlı işleyici, bir `QueryStatus` olay. Menü öğesi bir "gerçek" öğesi, diğer bir deyişle, değil yer tutucu öğe olup olmadığını belirler ve olup (projeyi başlangıç projesi olarak zaten ayarlanmış anlamına gelir) zaten öğesi denetlenir.  
  
    ```csharp  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## <a name="implementing-the-command-id-match-predicate"></a>Komut kimliği eşleşme koşulu uygulama  
  
1.  Eşleşme koşulu hemen uygulayın. İki şey belirlemek ihtiyacımız: ilk olarak mı komut kimliği (olduğu büyüktür veya eşittir bildirilen komut kimliği), geçerli ve saniye (Bu projeleri çözümdeki sayısından daha az) bir olası projesini olup olmadığını belirtir.  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Yalnızca bir çözüm birden çok proje olduğunda yüklenecek VSPackage'ı ayarlama  
 Çünkü **başlangıç projesi ayarlama** komut değil mantıklı etkin çözüm birden fazla proje sahip olmadığı sürece, bu durumda yalnızca otomatik olarak yüklemek için VSPackage ayarlayabilirsiniz. Kullandığınız <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> UI bağlamı birlikte <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. DynamicMenuPackage.cs dosyasında aşağıdaki öznitelikleri DynamicMenuPackage sınıfına ekleyin:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Test başlangıç projesi Ayarla komutu  
 Artık kodunuzu test edebilirsiniz.  
  
1.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
2.  Deneysel örneğinde, birden fazla proje içeren bir çözüm açın.  
  
     Ok simgesini görürsünüz **Çözüm Gezgini** araç çubuğu. Çözüm içindeki farklı projelerde temsil eden bir menü öğeleri genişlettiğinizde, görüntülenmesi gerekir.  
  
3.  Projelerden birine iade ettiğinizde, başlangıç projesi olur.  
  
4.  Çözümü kapatın veya yalnızca bir proje içeren bir çözüm açın, araç çubuğu simgesi ortadan kalkması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

