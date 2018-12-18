---
title: Çok örnekli araç penceresi oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19a41e172fd68687cffeca91bdfb4bc418ecdf60
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499773"
---
# <a name="create-a-multi-instance-tool-window"></a>Çok örnekli araç penceresi oluşturma
Böylece aynı anda birden çok örneğini açılabilir bir araç penceresi programlayabilirsiniz. Varsayılan olarak, araç pencerelerini açmak yalnızca bir örneğine sahip olabilirsiniz.  
  
 Çok örnekli araç penceresi kullandığınızda, aynı zamanda bilgi birkaç ilgili kaynakları gösterebilirsiniz. Örneğin, çok satırlı yerleştirebilirsiniz <xref:System.Windows.Forms.TextBox> birkaç kod parçacıkları bir programlama oturumu sırasında aynı anda kullanılabilir olacak şekilde bir çok örnekli araç penceresinde denetim. Ayrıca, örneğin, size yerleştirebilirsiniz bir <xref:System.Windows.Forms.DataGrid> denetimi ve bir açılan liste kutusunu çok örnekli araç penceresinde birden çok gerçek zamanlı veri kaynakları aynı anda izlenebilir.  
  
## <a name="create-a-basic-single-instance-tool-window"></a>Temel (tekli) araç penceresi oluşturma  
  
1.  Adlı bir proje oluşturma **MultiInstanceToolWindow** VSIX şablonuyla ve adlı bir özel araç penceresi öğesi şablonu ekleme **MIToolWindow**.  
  
    > [!NOTE]
    >  Araç penceresi içeren bir uzantı oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="make-a-tool-window-multi-instance"></a>Bir araç penceresi çok örneği  
  
1.  Açık *MIToolWindowPackage.cs* dosya ve bulma `ProvideToolWindow` özniteliği. ve `MultiInstances=true` parametresi, aşağıdaki örnekte gösterildiği gibi:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  İçinde *MIToolWindowCommand.cs* dosya, bulma `ShowToolWindos()` yöntemi. Bu yöntemi çağırmanız <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemi ve kümesi kendi `create` bayrak `false` mevcut araç penceresi örnekleri kullanılabilir kadar yineleme böylece `id` bulunur.  
  
3.  Bir araç penceresi örneği oluşturmak için arama <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemi ve kümesi kendi `id` kullanılabilir değerine ve kendi `create` bayrak `true`.  
  
     Varsayılan olarak, değerini `id` parametresinin <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemi `0`. Bu değer, tek örnekli araç penceresi sağlar. Barındırılması birden fazla örnek için her örnek kendi benzersiz olmalıdır `id`.  
  
4.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodunda <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> tarafından döndürülen nesne <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> araç penceresi örneğinin özelliği.  
  
5.  Varsayılan olarak, `ShowToolWindow` araç penceresi öğe şablonu tarafından oluşturulan yöntem, tek örnekli araç penceresi oluşturur. Aşağıdaki örnek nasıl değiştirileceğini gösterir `ShowToolWindow` birden çok örnek oluşturma için yöntemi.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```