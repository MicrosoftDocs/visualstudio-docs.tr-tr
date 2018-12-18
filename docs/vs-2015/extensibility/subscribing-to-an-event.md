---
title: Bir olaya abone olma | Microsoft Docs
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
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e01d10f68436cacdb3a662540723335743b9f10
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776583"
---
# <a name="subscribing-to-an-event"></a>Bir Olaya Abone Olma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, çalıştırılan Belge tablosu (RDT) olaylara yanıt veren bir araç penceresi oluşturma açıklanır. Araç penceresi uygulayan bir kullanıcı denetimi barındıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Yöntemi arabirimi olaylarına bağlanır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>RDT olaylara abone olma  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Araç penceresi içeren bir uzantı oluşturma  
  
1.  Adlı bir proje oluşturma **RDTExplorer** VSIX şablonuyla ve adlı bir özel araç penceresi öğesi şablonu ekleme **RDTExplorerWindow**.  
  
     Araç penceresi içeren bir uzantı oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT olaylarına abone olma  
  
1.  RDTExplorerWindowControl.xaml dosyasını açın ve Sil adlı düğmesi `button1`. Ekleme bir <xref:System.Windows.Forms.ListBox> denetlemek ve varsayılan adı kabul edin. Kılavuz öğesi gibi görünmelidir:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  RDTExplorerWindow.cs dosyayı kod Görünümü'nde açın. Aşağıdaki using deyimlerini dosyanın başına.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Değiştirme `RDTExplorerWindow` bunu sınıfı türetme yanı sıra, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> sınıfı, bunu uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> arabirimi.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Arabirim uygular. İmleç IVsRunningDocTableEvents adına yerleştirin. Sol kenar boşluğunda bir ampul de görürsünüz. Ampul sağındaki aşağı oka tıklayın ve **arabirim uygulama**.  
  
5.  Arabirimdeki her yönteminde satırı değiştirin `throw new NotImplementedException();` bu:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Bir tanımlama bilgisi alan RDTExplorerWindow sınıfına ekleyin.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Bu tarafından döndürülen tanımlama bilgisi tutan <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> yöntemi.  
  
7.  RDT etkinliklere kaydolmak için RDTExplorerWindow'ın Initialize() yöntemi yok sayın. Oluşturucuda ToolWindowPane'nın Initialize() yöntemi her zaman Hizmetleri almanız gerekir.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Hizmet almak için çağrılan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> arabirimi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Uygulayan bir nesneye yöntemi bağlanır RDT olayları <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, bu durumda, bir RDTExplorer nesnesi.  
  
8.  RDTExplorerWindow'ın Dispose() yöntemini güncelleştirin.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Yöntemi arasındaki bağlantıyı siler `RDTExplorer` ve RDT olay bildirimi.  
  
9. Gövdesi için aşağıdaki satırı ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> işleyicisi hemen önce `return` deyimi.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Gövdesi ile benzer bir satır ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> işleyicisi ve liste kutusunda görmek istediğiniz diğer olayları.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio deneysel örneği açılır.  
  
12. Açık **RDTExplorerWindow** (**görünüm / diğer Windows / RDTExplorerWindow**).  
  
     **RDTExplorerWindow** penceresi ile boş olay listesi açılır.  
  
13. Bir çözüm oluşturun veya açın.  
  
     Olarak `OnBeforeLastDocument` ve `OnAfterFirstDocument` olaylar, her olay bildirimi görünür olay listesi.

