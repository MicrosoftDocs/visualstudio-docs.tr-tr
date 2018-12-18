---
title: Durum çubuğunu genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e072814120f18c7cc1ea09bf0829266958691ba
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497920"
---
# <a name="extend-the-status-bar"></a>Durum çubuğunu genişletme
IDE'nin en altında Visual Studio durum çubuğunda, bilgilerini görüntülemek için kullanabilirsiniz.  
  
 Durum çubuğu genişlettiğinizde, bilgileri ve kullanıcı Arabirimi dört bölgede görüntüleyebilirsiniz: geri bildirim bölge, ilerleme çubuğu, animasyon bölge ve tasarımcı bölge. Geri bildirim bölge, metni görüntülemek ve görüntülenen metni vurgulayın olanak tanır. İlerleme çubuğu, dosya kaydetme gibi kısa süreli işlemler için artımlı ilerleme durumunu gösterir. Animasyon bölge uzun süre çalışan işlemler veya bir çözümde birden çok proje derleme gibi belirsiz uzunluğu işlemi için bir sürekli döngüye animasyon görüntüler. Ve İmleç konumuna satır ve sütun sayısını Tasarımcı bölgenizi görebilirsiniz.  
  
 Durum çubuğunu kullanarak alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> arabirimi (gelen <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> hizmeti). Ayrıca, herhangi bir nesne üzerinde bir pencere çerçevesi tarihli bir durum çubuğu istemci nesnesi olarak uygulayarak kaydedebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> arabirimi. Bir pencere etkin olduğunda, Visual Studio için bu penceredeki tarihli nesneyi sorgular `IVsStatusbarUser` arabirimi. Bulunursa, çağırır, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> yöntemi döndürülen arabirim ve nesnenin durum çubuğunda bu yöntem içinde güncelleştirebilirsiniz. Belge windows, örneğin, kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> etkin olduklarında Tasarımcı bölgede bilgilerini güncelleştirmek için yöntemi.  
  
 Aşağıdaki yordamlar, bir VSIX projesi oluşturun ve bir özel menü komutu ekleme anladığınızı varsayar. Bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modify-the-status-bar"></a>Durum çubuğunu Değiştir  
 Bu yordamı ayarlayın ve mesaj alın, statik metin görüntülemek ve geri bildirim bölgesindeki durum çubuğunda görüntülenen metni vurgulama gösterilmektedir.  
  
### <a name="read-and-write-to-the-status-bar"></a>Okuma ve yazma için durum çubuğu  
  
1.  Adlı bir VSIX projesi oluşturun **TestStatusBarExtension** ve adlı bir menü komutu eklemek **TestStatusBarCommand**.  
  
2.  İçinde *TestStatusBarCommand.cs*, komut işleyicisi yöntemi kodu değiştirin (`MenuItemCallback`) aşağıdaki:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  Kodu derlemek ve hata ayıklamaya başlayın.  
  
4.  Açık **Araçları** Visual Studio'nun Deneysel örneğinin menü. Tıklayın **çağırma TestStatusBarCommand** düğmesi.  
  
     Durumunda olduklarını görmüş olmalısınız durum çubuğunda şimdi okuma metin **durum çubuğu için az önce yazdığımız.** ' i tıklatın ve görüntülenen ileti kutusunda aynı metni içerir.  
  
### <a name="update-the-progress-bar"></a>Güncelleştirme ilerleme çubuğu  
  
1.  Bu yordamda başlatmak ve ilerleme çubuğunu güncellemek nasıl göstereceğiz.  
  
2.  Açık *TestStatusBarCommand.cs* değiştirin ve dosya `MenuItemCallback` yöntemini aşağıdaki kod ile:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  Kodu derlemek ve hata ayıklamaya başlayın.  
  
4.  Açık **Araçları** Visual Studio'nun Deneysel örneğinin menü. Tıklayın **çağırma TestStatusBarCommand** düğmesi.  
  
     Durumunda olduklarını görmüş olmalısınız durum çubuğunda şimdi okuma metin **ilerleme çubuğu için yazma.** Ayrıca, her saniye için 20 saniye güncelleştirilmesi ilerleme çubuğu görürsünüz. Bundan sonra durum çubuğunu ve ilerleme çubuğu temizlenir.  
  
### <a name="display-an-animation"></a>Bir animasyon görüntüleme  
  
1.  Durum çubuğunu gösterir ya da bir döngü animasyon uzun süreli bir işlemi (örneğin, bir çözümde birden çok proje derleme) görüntüler. Bu animasyonu görmüyorsanız doğru olduğundan emin olun **Araçları** > **seçenekleri** ayarları:  
  
     Git **Araçları** > **seçenekleri** > **genel** işaretini kaldırın ve sekme **istemcide dayalı görsel deneyimi otomatik olarak ayarla Performans**. Ardından alt seçeneği işaretleyin **zengin istemci görsel deneyimini etkinleştir**. Artık Visual Studio'nun Deneysel Örneğinizde proje oluşturduğunuzda, animasyon görebilmek için olmalıdır.  
  
     Bu yordamda bir proje veya çözüm oluşturmaya temsil eden standart bir Visual Studio animasyon görüntüleriz.  
  
2.  Açık *TestStatusBarCommand.cs* değiştirin ve dosya `MenuItemCallback` yöntemini aşağıdaki kod ile:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  Kodu derlemek ve hata ayıklamaya başlayın.  
  
4.  Açık **Araçları** tıklayın ve Visual Studio deneysel örneğinde menüde **çağırma TestStatusBarCommand**.  
  
     İleti kutusu gördüğünüzde, ayrıca durum çubuğunda bir animasyon sağda görmeniz gerekir. İleti kutusu kapatırken animasyon kaybolur.