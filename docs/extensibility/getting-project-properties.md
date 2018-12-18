---
title: Proje özelliklerini alma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b285c3a41a2d022358378a7e5e16403b83e8172b
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561614"
---
# <a name="get-project-properties"></a>Proje özelliklerini alma
Bu izlenecek yol gösteren bir araç penceresinde proje özellikleri görüntüler.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX projesi oluşturun ve bir araç penceresi eklemek için  
  
1. Her Visual Studio uzantısı, uzantı varlıkları içeren bir VSIX dağıtım projesi ile başlar. Oluşturma bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adlı VSIX projesi `ProjectPropertiesExtension`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C#** > **genişletilebilirlik**.  
  
2. Adlı bir özel araç penceresi öğe şablonu ekleyerek bir araç penceresi `ProjectPropertiesToolWindow`. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle** > **yeni öğe**. İçinde **Yeni Öğe Ekle iletişim**Git **Visual C# öğeleri** > **genişletilebilirlik** seçip **özel araç penceresi**. İçinde **adı** iletişim kutusunun altındaki alan, için dosya adını değiştirerek `ProjectPropertiesToolWindow.cs`. Özel araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Çözümü derleyin ve hata olmadan derlediğinden emin olun.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Araç penceresine proje özelliklerini görüntülemek için  
  
1.  ProjectPropertiesToolWindowCommand.cs dosyasına aşağıdakileri ekleyin using deyimleri.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  İçinde *ProjectPropertiesToolWindowControl.xaml*, varolan bir düğmeyi kaldırma ve araç kutusundan TreeView ekleyin. Ayrıca click olay işleyicisinden kaldırabilirsiniz *ProjectPropertiesToolWindowControl.xaml.cs* dosya.  
  
3.  İçinde *ProjectPropertiesToolWindowCommand.cs*, kullanın `ShowToolWindow()` projesini açın ve özelliklerini okumak için yöntem TreeView özellikleri eklersiniz. ShowToolWindow için kod aşağıdaki gibi görünmelidir:  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
5.  Deneysel örneğinde, bir projeyi açın.  
  
6.  İçinde **görünümü** > **diğer Windows** tıklayın **ProjectPropertiesToolWindow**.  
  
     Tüm Proje Özellikleri'nin ve ilk proje adı ile birlikte araç penceresindeki ağaç denetimi görmeniz gerekir.