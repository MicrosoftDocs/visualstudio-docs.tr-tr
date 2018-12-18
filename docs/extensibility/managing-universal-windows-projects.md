---
title: Evrensel Windows projelerini yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d4039b3d22206afb292e90d46608decd2cfa96a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930238"
---
# <a name="manage-universal-windows-projects"></a>Evrensel Windows projeleri yönetme
Evrensel Windows uygulamaları, Windows 8.1 ve Windows Phone 8.1, geliştiricilerin kod ve diğer varlıkları hem de platformlarda kullanmasına izin vererek hem hedef uygulamalardır. Ayrı projeler, bir Windows ve Windows Phone için diğer kaynakları ve platforma özgü kod tutulur ancak paylaşılan kod ve kaynakları bir paylaşılan projede tutulur. Evrensel Windows uygulamaları hakkında daha fazla bilgi için bkz. [Evrensel Windows uygulamaları](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Projeleri Yönetme visual Studio uzantıları Evrensel Windows uygulaması projeleri tek platform uygulamalardan farklı bir yapı olduğunu bilmeniz gerekir. Bu izlenecek yol, paylaşılan proje gidin ve paylaşılan öğelerini yönetmek nasıl gösterir.  

## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  

### <a name="navigate-the-shared-project"></a>Paylaşılan proje gidin  

1.  Adlı bir C# VSIX projesi oluşturun **TestUniversalProject**. (**Dosya** > **yeni** > **proje** ardından **C#**  >   **Genişletilebilirlik** > **Visual Studio paket**). Ekle bir **özel komut** proje öğesi şablonu (üzerinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle** > **yeni öğe** gidin **genişletilebilirlik**). Dosya adı **TestUniversalProject**.  

2.  Bir başvuru ekleyin *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* ve *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (içinde **Uzantıları** bölümü).  

3.  Açık *TestUniversalProject.cs* ve aşağıdakileri ekleyin `using` ifadeleri:  

    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  

4.  İçinde `TestUniversalProject` sınıf işaret eden özel bir alan ekleyin **çıkış** penceresi.  

    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  

5.  Çıkış Bölmesi'TestUniversalProject oluşturucu içinde başvuru ayarlayın:  

    ```csharp  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  

        this.package = package;  

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  

6.  Mevcut koddan kaldırdığınızdan `ShowMessageBox` yöntemi:  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  

7.  Bu kılavuzda birkaç farklı amaçlar için kullanırız DTE nesnesini Al. Ayrıca, menü düğmesine tıklandığında bir çözüm yüklendiğinden emin olun.  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  

8.  Paylaşılan proje bulun. Paylaşılan proje saf bir kapsayıcıdır; derleme yok veya çıktılar üretir. Aşağıdaki yöntem ilk paylaşılan proje bakarak çözümde bulur <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> paylaşılan proje özelliğine sahip bir nesne.  

    ```csharp  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  

        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  

9. İçinde `ShowMessageBox` yöntemi, çıkış alt yazı (görünen proje adı **Çözüm Gezgini**) paylaşılan proje.  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  

        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  

10. Ektin platform proje alın. Platform, platforma özgü kod hem de kaynaklar içeren projeleri projelerdir. Yeni alan aşağıdaki yöntemi kullanan <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> ektin platform projesi.  

    ```csharp  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  

11. İçinde `ShowMessageBox` yöntemi, çıktı ektin platform proje açıklamalı alt yazısı.  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  

        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  

    ```  

12. Platform projelerini aracılığıyla yineleme. Aşağıdaki yöntem, tüm içeri aktarma (platform) projeleri paylaşılan projeden alır.  

    ```csharp  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  

    > [!IMPORTANT]
    >  Kullanıcı deneysel örneğinde C++ Evrensel Windows uygulama projesi açtıysa, yukarıdaki kod bir özel durum oluşturur. Bu bilinen bir sorundur. Özel durumdan kaçınmak için yerine `foreach` aşağıdakilerle block yukarıda:  

    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  

13. İçinde `ShowMessageBox` yöntemi, çıkışı her platform projesi açıklamalı alt yazısı. Ektin platform projenin başlığını veren satırından sonra aşağıdaki kodu ekleyin. Yüklenen platformu projelerinde, bu listede görüntülenir.  

    ```csharp  
    output.OutputStringThreadSafe("Platform projects:\n");  

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  

    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  

14. Ektin platform proje değiştirin. Aşağıdaki yöntemi kullanarak etkin proje ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  

    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  

15. İçinde `ShowMessageBox` yöntemi ektin platform proje değiştirin. Bu kod içinde `foreach` blok.  

    ```csharp  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  

        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  

16. Şimdi deneyin. Deneysel örneği başlatmak için F5 tuşuna basın. Deneysel örneğinde bir C# hub'ı Evrensel uygulama projesi oluşturun (içinde **yeni proje** iletişim kutusu, **Visual C#** > **Windows**  >   **Windows 8** > **Evrensel** > **Hub uygulaması**). Çözüm yüklendikten sonra Git **Araçları** menüsüne ve ardından **çağırma TestUniversalProject**ve ardından metin iade **çıkış** bölmesi. Aşağıdaki gibi görmeniz gerekir:  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  

### <a name="manage-the-shared-items-in-the-platform-project"></a>Platform projesinde paylaşılan öğeleri yönetme  

1.  Platform projesinde paylaşılan öğeleri bulur. Paylaşılan proje öğelerinde platformu projede paylaşılan öğeleri olarak görünür. Bunları göremez **Çözüm Gezgini**, ancak bunları bulmak için proje hiyerarşisi inceleyebileceğiniz. Aşağıdaki yöntem, hiyerarşi gezer ve paylaşılan tüm öğeleri toplar. Bu isteğe bağlı olarak her bir öğenin başlığını çıkarır. Paylaşılan öğeler yeni bir özelliği tarafından tanımlanan <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  

    ```csharp  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  

        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  

2.  İçinde `ShowMessageBox` yöntemi, platform proje hiyerarşisi öğeleri görmek için aşağıdaki kodu ekleyin. IT içinde `foreach` blok.  

    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  

3.  Paylaşılan öğeler okuyun. Paylaşılan öğeler platform projesinde gizli bağlı dosyalar olarak görünür ve tüm özellikleri olarak sıradan bağlantılı dosyaları okuyabilir. Aşağıdaki kod, yolun tamamı ilk paylaşılan öğenin okur.  

    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  

4.  Şimdi deneyin. Tuşuna **F5** deneysel örneği başlatmak için. Oluşturma bir C# deneysel örneğinde hub'ı Evrensel uygulama projesi (içinde **yeni proje** iletişim kutusu, **Visual C#**   >  **Windows**  >  **Windows 8** > **Evrensel** > **Hub uygulaması**) Git **Araçları** menü tıklayın **TestUniversalProject çağırma**ve ardından metin iade **çıkış** bölmesi. Aşağıdaki gibi görmeniz gerekir:  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Platform projeleri ve paylaşılan projeler değişiklikleri saptayın  

1. Platform projelerde gibi paylaşılan projelerde değişikliklerini algılamak için hiyerarşi ve proje olayları kullanabilirsiniz. Ancak, paylaşılan proje içindeki proje öğeleri paylaşılan proje öğeleri değiştirildiğinde belirli olaylar başlatma yani görünür değildir.  

    Bir projedeki bir dosyayı yeniden adlandırıldığında olayların sırasını göz önünde bulundurun:  

   1. Dosya adı diskte değişti.  

   2. Proje dosyası yeni dosya adını içerecek şekilde güncelleştirilir.  

      Hiyerarşi etkinlikleri (örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) genel olarak kullanıcı Arabiriminde görüntülenen değişiklikleri izlemek **Çözüm Gezgini**. Hiyerarşi etkinlikleri dosya silme ve ardından dosya toplama için bir dosya yeniden adlandırma işlemi göz önünde bulundurun. Ancak, hiyerarşi olay sistemi görünmeyen öğeleri değiştirildiğinde ateşlenir bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olay ama bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> olay. Platform projesinde bir dosyayı yeniden adlandırırsanız, bu nedenle, her ikisi de size <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ancak paylaşılan bir proje dosyasında yeniden adlandırırsanız, yalnızca get <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  

      Proje öğelerinde değişiklikleri izlemek için DTE projesi öğesi olayları işleyebilir (olanları bulunan <xref:EnvDTE.ProjectItemsEventsClass>). Ancak, çok sayıda olayları işlemekte olduğunuz, olayları işleme daha iyi performans elde edebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. Bu izlenecek yolda yalnızca Hiyerarşi etkinlikleri ve DTE olayları göstereceğiz. Bu yordamda, paylaşılan bir proje ve platform projesi için bir olay dinleyicisi eklersiniz. Ardından, bir paylaşılan proje dosyasında ve platform projesinde başka bir dosyaya yeniden adlandırdığınızda, her yeniden adlandırma işlemi için tetiklenen olayları görebilirsiniz.  

      Bu yordamda, paylaşılan bir proje ve platform projesi için bir olay dinleyicisi eklersiniz. Ardından, bir paylaşılan proje dosyasında ve platform projesinde başka bir dosyaya yeniden adlandırdığınızda, her yeniden adlandırma işlemi için tetiklenen olayları görebilirsiniz.  

2. Olay dinleyicisi ekleyin. Projeye yeni bir sınıf dosyası ekleyin ve onu çağırmak *HierarchyEventListener.cs*.  

3. Açık *HierarchyEventListener.cs* dosyasını açıp aşağıdaki using deyimlerini:  

   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  

   ```  

4. Sahip `HierarchyEventListener` sınıfı uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  

   ```  

5. Üyeleri uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, aşağıdaki kod gibi.  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   {  
       private IVsHierarchy hierarchy;  
       IVsOutputWindowPane output;   

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
            this.hierarchy = hierarchy;  
            this.output = outputWindow;  
       }  

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
           return VSConstants.S_OK;  
       }  
   }  

   ```  

6. Aynı sınıf içinde DTE olayı için başka bir olay işleyici ekleme <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, her bir proje öğesini yeniden adlandırılır gerçekleşir.  

   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  

7. Hiyerarşi etkinlikleri için kaydolun. İzlediğiniz her proje için ayrı olarak kaydolmak gerekir. Aşağıdaki kodu ekleyin `ShowMessageBox`, paylaşılan proje ve diğer platformu projelerin herhangi biri için.  

   ```csharp  
   // hook up the event listener for hierarchy events on the shared project  
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
   uint cookie1;  
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  

   // hook up the event listener for hierarchy events on the   
   active project  
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
   uint cookie2;  
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
   ```  

8. DTE projesi öğesi etkinliğe kaydolun <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. İkinci dinleyiciyi kanca sonra aşağıdaki kodu ekleyin.  

   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  

   ```  

9. Paylaşılan öğe değiştirin. Bir platform projesindeki paylaşılan öğeleri değiştiremez; Bunun yerine, bunları paylaşılan projede gerçek sahibi bu öğe değiştirmelisiniz. Karşılık gelen öğe kimliği ile paylaşılan projede alabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, paylaşılan öğenin tam yolunu sunar. Ardından, paylaşılan öğeyi değiştirebilirsiniz. Değişiklik platform projelere yayılır.  

    > [!IMPORTANT]
    >  Olup olmadığı bir proje öğesi paylaşılan öğeyi değiştirmeden önce olduğunu bulmanız gerekir.  

     Aşağıdaki yöntem, bir proje öğesi dosya adını değiştirir.  

    ```csharp  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  

10. Bu yöntem tüm diğer kod arama `ShowMessageBox` dosyayı değiştirmek için paylaşılan proje öğesinde adlandırın. Bu, paylaşılan projede öğenin tam yolunu alır koddan sonra ekleyin.  

    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  

11. Derleme ve projeyi çalıştırın. Deneysel örneğinde bir C# Evrensel hub uygulaması oluşturma, Git **Araçları** menüsüne ve ardından **çağırma TestUniversalProject**ve genel çıkış bölmesinde metnini denetleyin. Paylaşılan proje içindeki ilk öğeyi adını (olmasını bekliyoruz *App.xaml* dosya) değiştirilmelidir; görmeniz gerekir <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> olay harekete geçirildi. Bu durumda, yeniden adlandırma sonrasında *App.xaml* neden *App.xaml.cs* de yeniden adlandırılması için dört olayları (her platform projesi için iki) görmeniz gerekir. (DTE olayları paylaşılan projelerdeki öğelere izlemez.) İki görmelisiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olayları (platformu projelerin her biri için bir tane), ancak Hayır <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> olayları.  

12. Artık bir platform projesinde bir dosyayı yeniden adlandırmayı deneyin ve hazırlanın olayları farkı görebilirsiniz. Aşağıdaki kodu ekleyin `ShowMessageBox` çağrısından sonra `ModifyFileName`.  

    ```csharp  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  

    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  

13. Derleme ve projeyi çalıştırın. Deneysel örneğinde bir C# Evrensel projesi oluşturun, Git **Araçları** menüsüne ve ardından **çağırma TestUniversalProject**ve genel çıkış bölmesinde metnini denetleyin. Platform proje dosyasında yeniden adlandırıldıktan sonra her ikisi de görmelisiniz bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> olay ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olay. Değiştirilmesi dosya değiştirilmesi başka hiçbir dosya neden ve öğelerde platform projesinde yapılan değişikliklerin her yerde yayılan yoksa olmadığından, yalnızca her aşağıdaki olaylardan biri.
