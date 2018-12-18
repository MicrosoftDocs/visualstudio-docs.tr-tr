---
title: Proje özelliklerini alma | Microsoft Docs
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
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7137012fb5b1a562257134ae7f87b19068db165
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749240"
---
# <a name="getting-project-properties"></a>Proje Özelliklerini Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol gösteren bir araç penceresinde proje özellikleri görüntüler.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX projesi oluşturun ve bir araç penceresi eklemek için  
  
1.  Her Visual Studio uzantısı, uzantı varlıkları içeren bir VSIX dağıtım projesi ile başlar. Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adlı VSIX projesi `ProjectPropertiesExtension`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Adlı bir özel araç penceresi öğe şablonu ekleyerek bir araç penceresi `ProjectPropertiesToolWindow`. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle iletişim**Git **Visual C# öğeleri / genişletilebilirlik** seçip **özel araç penceresi**. İçinde **adı** iletişim kutusunun altındaki alan, için dosya adını değiştirerek `ProjectPropertiesToolWindow.cs`. Özel araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Çözümü derleyin ve hata olmadan derlediğinden emin olun.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Araç penceresine proje özelliklerini görüntülemek için  
  
1.  ProjectPropertiesToolWindowCommand.cs dosyasına aşağıdakileri ekleyin using deyimleri.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  ProjectPropertiesToolWindowControl.xaml, varolan bir düğmeyi kaldırın ve araç kutusundan TreeView ekleyin. Bu gibi durumlarda, tıklama olayı işleyicisi de ProjectPropertiesToolWindowControl.xaml.cs dosyasından kaldırabilirsiniz.  
  
3.  ProjectPropertiesToolWindowCommand.cs, projeyi açmak ve özelliklerini okumak için ShowToolWindow() yöntemi kullanın ve ardından TreeView özellikleri ekleyin. ShowToolWindow için kod aşağıdaki gibi görünmelidir:  
  
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
  
6.  İçinde **görünüm / diğer Windows** tıklayın **ProjectPropertiesToolWindow**.  
  
     Tüm Proje Özellikleri'nin ve ilk proje adı ile birlikte araç penceresindeki ağaç denetimi görmeniz gerekir.

