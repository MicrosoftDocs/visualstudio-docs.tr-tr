---
title: Çıkış penceresini genişletme | Microsoft Docs
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
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4afd91c42eeb60d005b1eb186c30d3896e3101f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731394"
---
# <a name="extending-the-output-window"></a>Çıkış Penceresini Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Çıkış** penceresinde okuma/yazma metin bölmelerinin bir kümesidir. Visual Studio, bu yerleşik bölmeler sahiptir: **derleme**, hangi projelerinde yapılar hakkındaki iletileri iletişim kurmak ve **genel**, hangi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] iletileri IDE hakkında iletişim kurar. Projeleri, bir başvuru alma **derleme** bölmesinde otomatik olarak ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> arabirim yöntemleri ve Visual Studio, doğrudan erişim sunar **genel** bölmesi aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> hizmeti. Ek olarak yerleşik bölmeler, oluşturabilir ve kendi özel bölmeleri yönetin.  
  
 Denetleyebileceğiniz **çıkış** penceresini doğrudan aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> arabirimleri. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Tarafından sunulan arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> hizmet, oluşturmaya, almaya ve yok etme için yöntemleri tanımlar **çıkış** pencere bölmeleri. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Arabirimi bölmelerini gösterme, bölmelerini gizleme ve metin işlemek için yöntemleri tanımlar. Denetlemeye yönelik alternatif bir yolu **çıkış** penceredir aracılığıyla <xref:EnvDTE.OutputWindow> ve <xref:EnvDTE.OutputWindowPane> Visual Studio Otomasyon nesne modelindeki nesneler. Bu nesneler neredeyse tüm işlevselliğini kapsülleyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> arabirimleri. Ayrıca, <xref:EnvDTE.OutputWindow> ve <xref:EnvDTE.OutputWindowPane> nesneleri numaralandırır daha kolay hale getirmek için daha yüksek düzeydeki bazı işlevler eklemek **çıkış** pencere bölmeleri ve metin bölmeden alınacak.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Çıkış Bölmesi ' kullanan bir uzantı oluşturma  
 Çıkış bölmesinde farklı yönlerini sınayan bir uzantı yapabilirsiniz.  
  
1.  Adlı bir VSIX projesi oluşturun `TestOutput` bir menü komutuyla adlı **TestOutput**. Daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aşağıdaki başvuruları ekleyin:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  TestOutput.cs içinde aşağıdaki ekleme deyimini kullanarak:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  TestOutput.cs içinde ShowMessageBox yöntemi silin. Aşağıdaki metot taslağı ekleyin:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  TestOutput oluşturucusunun içinde komut işleyici OutputCommandHandler için değiştirin. Komutları ekler bölümü aşağıda verilmiştir:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  Aşağıdaki bölümlerde, çıkış bölmesine uğraşmanızı farklı şekillerde gösterir farklı yöntemleri vardır. OutputCommandHandler() Yöntemin gövdesi için bu yöntemleri çağırabilir. Örneğin, aşağıdaki kod, sonraki bölümde verilen CreatePane() yöntem ekler.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Çıkış penceresi IVsOutputWindow ile oluşturma  
 Bu örnek, yeni bir oluşturma işlemi gösterilmektedir **çıkış** kullanarak pencere bölmesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> arabirimi.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Bu yöntem uzantıya'a tıkladığınızda önceki bölümde verilen eklerseniz **çağırma TestOutput** görmeniz komutu **çıkış** bildiren bir başlık penceresiyle **çıktıyı Göster gelen: CreatedPane** ve sözcükler **oluşturulan bölmesinde budur** bölmesinde.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>OutputWindow ile bir çıkış penceresi oluşturma  
 Bu örnek nasıl oluşturulacağını gösterir. bir **çıkış** kullanarak pencere bölmesi <xref:EnvDTE.OutputWindow> nesne.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Ancak <xref:EnvDTE.OutputWindowPanes> alma koleksiyonu sağlar bir **çıkış** pencere bölmesi başlığı tarafından bölmesinde başlıkları garanti edilmez benzersiz olmalıdır. Bir başlık benzersizliğini doubt kullanırsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> GUID'sine doğru bölmede almak için yöntemi.  
  
 Bu yöntem uzantıya'a tıkladığınızda önceki bölümde verilen eklerseniz **çağırma TestOutput** olan çıkış penceresine bildiren bir başlık görmeniz komut **çıktıyı göster: DTEPane** ve sözcükleri **eklenen DTE bölmesinde** bölmesinde.  
  
## <a name="deleting-an-output-window"></a>Çıkış penceresi siliniyor  
 Bu örnek nasıl sileceğiniz gösterilmektedir bir **çıkış** pencere bölmesi.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Bu yöntem uzantıya'a tıkladığınızda önceki bölümde verilen eklerseniz **çağırma TestOutput** olan çıkış penceresine bildiren bir başlık görmeniz komut **çıktıyı göster: yeni bir bölme** ve sözcükleri **oluşturulan bölmesinde eklenen** bölmesinde. Tıklarsanız **çağırma TestOutput** bölmesinde silinip yeniden komutu.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Çıkış penceresi genel bölmesinde alma  
 Bu örnek, yerleşik alınacağı gösterilmektedir **genel** bölmesinde **çıkış** penceresi.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Bu yöntem uzantıya'a tıkladığınızda önceki bölümde verilen eklerseniz **çağırma TestOutput** komutu, görmeniz **çıkış** penceresi sözcükleri gösterir **bulunan genel bölmesinde** bölmesinde.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Çıkış penceresi derleme bölmesinde alma  
 Bu örnekte, derleme bölmesinde bulup yazma gösterilmektedir. Derleme bölmesinde varsayılan olarak etkin olduğundan, bu da etkinleştirir.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```

