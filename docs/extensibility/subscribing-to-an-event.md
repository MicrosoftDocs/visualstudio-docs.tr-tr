---
title: Bir olaya abone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41ed19cb31924e90ef9326aad5c8cad117996793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141909"
---
# <a name="subscribing-to-an-event"></a>Bir olaya abone olma
Bu kılavuz, çalışan bir belge tablosunda (RDT) olaylara yanıt bir araç penceresi oluşturma açıklanmaktadır. Araç penceresi uygulayan bir kullanıcı denetimi barındıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Yöntemi arabirimi olaylarına bağlanır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK'sını İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda bir isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz: [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>RDT olaylara abone olma  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Bir araç penceresi uzantı oluşturmak için  
  
1.  Adlı bir proje oluşturun **RDTExplorer** VSIX şablonu kullanarak ve adlandırılmış bir özel araç pencere öğesi şablonu Ekle **RDTExplorerWindow**.  
  
     Bir araç penceresi uzantı oluşturma hakkında daha fazla bilgi için bkz: [bir uzantısı bir araç penceresi oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT olaylara abone olma  
  
1.  RDTExplorerWindowControl.xaml dosyasını açın ve Sil adlı düğmesi `button1`. Ekleme bir <xref:System.Windows.Forms.ListBox> denetlemek ve varsayılan adı kabul edin. Kılavuz öğesi aşağıdaki gibi görünmelidir:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Kod görünümünde RDTExplorerWindow.cs dosyasını açın. Aşağıdaki using deyimlerini dosyanın başlangıcı.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Değiştirme `RDTExplorerWindow` bunu sınıf türetme yanı sıra, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> sınıfı, bunu uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> arabirimi.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Arabirimini uygular. İmleç IVsRunningDocTableEvents adına yerleştirin. Ampul sol kenar boşluğunda görmeniz gerekir. Ampul sağındaki aşağı oka tıklayın ve **arabirimi uygulama**.  
  
5.  Arabirimdeki her yöntem satırını değiştirmek `throw new NotImplementedException();` bu:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Bir tanımlama bilgisi alan RDTExplorerWindow sınıfına ekleyin.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Bu tarafından döndürülen tanımlama bilgisi tutan <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> yöntemi.  
  
7.  RDT olaylarını kaydetmek için RDTExplorerWindow'ın önce Initialize() yöntemini geçersiz kılın. ToolWindowPane'nın Initialize() yönteminde oluşturucusundaki her zaman Hizmetleri almanız gerekir.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Hizmet almak için çağrılır bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> arabirimi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Yöntemi RDT olayları uygulayan bir nesneye bağlanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, bu durumda, bir RDTExplorer nesnesi.  
  
8.  RDTExplorerWindow'ın Dispose() yöntemi güncelleştirin.  
  
    ```csharp  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Yöntemi siler arasındaki bağlantıyı `RDTExplorer` ve RDT olay bildirimi.  
  
9. Gövdesi için aşağıdaki satırı ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> işleyici, hemen önce `return` deyimi.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Gövdesi ile benzer bir satır ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> işleyici ve liste kutusunda görmek istediğiniz diğer olaylar.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Projeyi derleyin ve hata ayıklamayı Başlat. Visual Studio deneysel örneği görüntülenir.  
  
12. Açık **RDTExplorerWindow** (**görünüm / diğer Windows / RDTExplorerWindow**).  
  
     **RDTExplorerWindow** ile boş olay Listesi penceresi açılır.  
  
13. Bir çözüm oluşturun veya açın.  
  
     Olarak `OnBeforeLastDocument` ve `OnAfterFirstDocument` olaylar, her olay bildirimi görüntülenir olay listesi.