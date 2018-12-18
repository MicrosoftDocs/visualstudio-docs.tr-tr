---
title: Oluşturma ve yönetme kalıcı iletişim kutuları | Microsoft Docs
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
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ef32fa43a1242ce8220f9e6454dbac03f0f5ad7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736633"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Kalıcı İletişim Kutuları Oluşturma ve Bunları Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio içinde kalıcı bir iletişim kutusu oluşturduğunuzda, iletişim kutusu görüntülendiği sırada iletişim kutusunun üst pencere devre dışı bırakıldı emin olun ve ardından iletişim kutusu kapatıldıktan sonra ana pencereyi yeniden etkinleştirmeniz gerekir. Bunu yaparsanız hata iletisini alabilirsiniz: "Microsoft Visual Studio kapatamaz kalıcı bir iletişim kutusu etkin olduğu için. Etkin iletişim kutusunu kapatın ve yeniden deneyin."  
  
 Bunu yapmanın iki yolu vardır. Bir WPF iletişim kutusu varsa türetmeniz için önerilen yöntem olduğu <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>ve sonra çağrı <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> iletişim kutusunu görüntüleyin. Bunu yaparsanız üst pencere kalıcı durumunu yöneten gerekmez.  
  
 İletişim kutusunun WPF değilse veya bazı diğer nedeni, iletişim kutusu türeyemez sınıfı <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, iletişim kutusunun üst çağırarak almalısınız sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> ve kalıcı çağırarak kendiniz yönetmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> yöntemi ile bir iletişim kutusunu görüntüleme ve iletişim kutusunu kapattıktan sonra yeniden parametresi 1 (true) olan bir yöntemini çağırmadan önce 0 (false) parametresi.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>DialogWindow türetilmiş bir iletişim kutusu oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun **OpenDialogTest** ve adlı bir menü komutu eklemek **OpenDialog**. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Kullanılacak <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> sınıfı, aşağıdaki derlemelere başvurular eklemeniz gerekir (Framework sekmesindeki **Başvuru Ekle** iletişim kutusu):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  OpenDialog.cs içinde aşağıdaki ekleme `using` deyimi:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Adlı bir sınıf bildirme **TestDialogWindow** türetilen <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  En aza indirmek ve iletişim kutusunun en üst düzeye çıkarmak için ayarlanmış <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> ve <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  İçinde **OpenDialog.ShowMessageBox** yöntemi, mevcut kodu aşağıdakiyle değiştirin:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Derleme ve uygulamayı çalıştırın. Visual Studio'nun deneysel örneğinde görüntülenmesi gerekir. Üzerinde **Araçları** Deneysel örneğinin menü adlı bir komut görmeniz **çağırma OpenDialog**. Bu komutu tıklattığınızda, iletişim kutusu penceresini görmeniz gerekir. Ekranı Kapla ve en aza indirmek mümkün olması gerekir.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Oluşturma ve yönetme DialogWindow türetilmemiş bir iletişim kutusu  
  
1.  Bu yordam için kullandığınız **OpenDialogTest** ile aynı derleme başvurularını önceki yordamda oluşturduğunuz çözüm.  
  
2.  Aşağıdaki `using` bildirimleri:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Adlı bir sınıf oluşturun **TestDialogWindow2** türetilen <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Özel bir başvuru ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Başvuru ayarlar için bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  İçinde **OpenDialog.ShowMessageBox** yöntemi, mevcut kodu aşağıdakiyle değiştirin:  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  Derleme ve uygulamayı çalıştırın. Üzerinde **Araçları** menü adlı bir komut görmeniz **çağırma OpenDialog**. Bu komutu tıklattığınızda, iletişim kutusu penceresini görmeniz gerekir.

