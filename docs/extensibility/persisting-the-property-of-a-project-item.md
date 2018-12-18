---
title: Proje öğesinin özelliğini kalıcı yapma | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: da231c924e3167a50c885cf18ef878a02b28b166
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915587"
---
# <a name="persist-the-property-of-a-project-item"></a>Proje öğesinin özelliğini kalıcı
Bir kaynak dosyasının yazar gibi bir proje öğesi eklediğiniz bir özellik kalıcı hale getirmek isteyebilirsiniz. Proje dosyasında özelliği depolayarak bunu yapabilirsiniz.

 Bir özellik bir proje dosyasında kalıcı hale getirmek için ilk adım projeyi hiyerarşisini elde edilir bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi. Bu arabirim Otomasyon kullanarak ya da kullanarak elde edebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Arabirim edindikten sonra hangi proje öğesi seçili belirlemek için kullanabilirsiniz. Proje öğesi Kimliğine sahip olduğunuzda, kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> özelliği eklemek için.

 Aşağıdaki yordamlarda, kalıcı *VsPkg.cs* özelliği `Author` değerle `Tom` proje dosyasındaki.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE nesnesi ile proje hiyerarşisi edinme

1.  VSPackage için aşağıdaki kodu ekleyin:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Proje öğesi özelliği DTE nesnesi ile kalıcı hale getirmek için

1.  Yöntemin önceki yordamda verilen kod için aşağıdaki kodu ekleyin:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitorSelection kullanarak proje hiyerarşisi edinme

1.  VSPackage için aşağıdaki kodu ekleyin:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Seçilen proje öğesi özelliği, proje hiyerarşisi verilen kalıcı hale getirmek için

1.  Yöntemin önceki yordamda verilen kod için aşağıdaki kodu ekleyin:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Özellik kalıcı olduğunu doğrulamak için

1. Başlangıç [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve ardından açın veya bir çözüm oluşturun.

2. Projeyi seçin, VsPkg.cs öğesi **Çözüm Gezgini**.

3. Bir kesme noktası kullanın veya aksi halde, VSPackage yüklenir ve SetItemAttribute çalıştığını belirler.

   > [!NOTE]
   > Sorsorgu UI bağlamı VSPackage yapabilecekleriniz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Daha fazla bilgi için [yük VSPackages](../extensibility/loading-vspackages.md).

4. Kapat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve proje dosyasını Not Defteri'nde açın. Görmelisiniz \<Yazar > değeriyle Tom, aşağıda gösterildiği gibi etiketleyin:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Araçlar](../extensibility/internals/custom-tools.md)