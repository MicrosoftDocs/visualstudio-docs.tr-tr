---
title: Bir Windows formunda hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 545155f622111c2452af3bacb57fd88930ce5ab0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066762"
---
# <a name="walkthrough-debugging-a-windows-form"></a>İzlenecek Yol: Windows Formunda Hata Ayıklama
Bir Windows formülü en yaygın yönetilen uygulamalardan biridir. Bir Windows formu, standart bir Windows uygulaması oluşturur. Bu adım adım işlemleri Visual Basic, C# ya da C++ kullanarak tamamlayabilirsiniz.  
  
 İlk olarak, herhangi bir açık çözümü kapatmanız gerekir.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Bu adım adım izleme için hazırlanmak amacıyla  
  
-   Açık olan bir çözümünüz varsa, kapatın. (Üzerinde **dosya** menüsünde **çözümü Kapat**.)  
  
## <a name="create-a-new-windows-form"></a>Yeni bir Windows Formu Oluşturun  
 Ardından, yeni bir Windows Formu oluşturacaksınız.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Bu anlatım için Windows formunu oluşturmak amacıyla  
  
1.  Üzerinde **dosya** menüsünde seçin **yeni** tıklatıp **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Proje Türleri bölmesinde **Visual Basic**, **Visual C#**, veya **Visual C++** düğümünü, ardından  
  
    1.  Visual Basic veya Visual C# için seçin **Windows Masaüstü** > **Windows Form uygulaması**.  
  
    2.  Visual C++ için seçin **Windows masaüstü uygulaması**.  
  
3.  İçinde **adı** kutusunda, projeyi (örneğin, Walkthrough_SimpleDebug) benzersiz bir ad verin.  
  
4.  **Tamam**'ı tıklatın.  
  
     Visual Studio, yeni bir proje oluşturur ve Windows Forms Tasarımcısı'nda yeni bir form görüntüler. Daha fazla bilgi için [Windows Form Tasarımcısı](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).  
  
5.  Üzerinde **görünümü** menüsünde **araç kutusu**.  
  
     Araç Kutusu açılır. Daha fazla bilgi için [araç kutusu](../ide/reference/toolbox.md).  
  
6.  Araç kutusunda tıklayarak **düğmesi** denetlemek ve denetimi Form Tasarım yüzeyine sürükleyin. Düğmeyi form üzerine bırakın.  
  
7.  Araç kutusunda tıklayarak **TextBox** denetlemek ve denetimi Form Tasarım yüzeyine sürükleyin. DROP **TextBox** form üzerinde.  
  
8. Form tasarım yüzeyinde, düğmeyi çift tıklatın.  
  
     Bu sizi kod sayfasına götürür. İşaretçi `button1_Click` içinde olmalıdır.  
  
10. `button1_Click` işlevinde, aşağıdaki kodu ekleyin:  
  
    ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Üzerinde **derleme** menüsünde **Çözümü Derle**.  
  
     Projenin hatasız oluşturması gerekir.  
  
## <a name="debug-your-form"></a>Formunuzda Hata Ayıklama Yapın  
 Şimdi, hata ayıklamayı başlatmak için hazırsınız.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Bu adım adım izleme için oluşturulmuş Windows Formu hata ayıklaması için  
  
1.  Kaynak penceresinde, eklediğiniz metin ile aynı satırda sol kenar boşluğunu tıklatın:  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ``` 
  
     Kırmızı bir nokta belirir ve satırdaki metin kırmızıyla vurgulanır. Kırmızı nokta bir kesme noktası temsil eder. Daha fazla bilgi için [kesme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Uygulamayı hata ayıklayıcısı altında çalıştırdığınızda, hata ayıklayıcısı koda ulaşıldığında, yürütmeyi o konumda keser. Ardından uygulamanızın durumunu görüntüleyebilir ve ona hata ayıklama yapabilirsiniz.  
  
    > [!NOTE]
    >  Ayrıca herhangi bir satır sağ kod üzerine **kesme noktası**ve ardından **kesme noktası Ekle** söz konusu satıra bir kesme noktası eklemek için.  
  
2.  ON **hata ayıklama** menüsünde seçin **Başlat**.  
  
     Windows Formu çalışmaya başlar.  
  
3.  Windows Formu'nda, eklediğiniz düğmeyi tıklatın.  
  
     Visual Studio'da bu, sizi kod satırında kesme noktası eklediğiniz satıra götürür. Bu satır, sarı ile vurgulanmış olmalıdır. Şimdi, uygulamanızda değişkenleri görüntüleyebilir ve yürütülmesini denetleyebilirsiniz. Uygulamanız artık yürütmeyi durdurmuştur ve sizden bir eylem bekliyordur.  
  
4.  Üzerinde **hata ayıklama** menüsünde seçin **Windows**, ardından **Watch**, tıklatıp **Watch1**.  
  
5.  İçinde **Watch1** penceresinde, boş bir satıra tıklayın. İçinde **adı** sütununa, `textBox1.Text` (Visual Basic veya Visual C# kullanıyorsanız) veya `textBox1->Text` (C++ kullanıyorsanız), ardından ENTER tuşuna basın.  
  
     **Watch1** penceresi, tırnak işareti içine alınmış bu değişkenin değerini gösterir:  
  
    `""`  
 
6.  Üzerinde **hata ayıklama** menüsünde seçin **içine adımla**.  
  
     Değişiklikleri textBox1.Text değeri **Watch1** penceresine:  
  
    `Button was clicked!`  
  
7.  Üzerinde **hata ayıklama** menüsünde seçin **devam** programınızın hatalarını ayıklamayı devam etmek için.  
  
8.  Windows Formunda, düğmeyi yeniden tıklatın.  
  
     Visual Studio, yürütmeyi yeniden keser.  
  
9. Kesme noktasını temsil eden kırmızı noktayı tıklatın.  
  
     Bu, kesme noktasını kodunuzdan kaldırır.  
  
10. Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Hata Ayıklama için Windows Form Uygulamanıza Ekleme  
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] içinde, hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz. Express Edition kullanıyorsanız, bu özellik desteklenmez.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Hata ayıklama için Windows Form Uygulamasına eklemek için  
  
1.  Yukarıda oluşturduğunuz projede, sol kenar boşluğunu tıklatarak, eklediğiniz satırda bir kez daha bir kesme noktası ayarlayın:  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";   
  
2.  On the **Debug** menu, select **Start Without Debugging**.  
  
     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.  
  
3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)  
  
     The **Attach to Process** dialog box appears.  
  
4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.  
  
5.  Click the **Attach** button.  
  
6.  In your Windows Form, click the one and only button.  
  
     The debugger breaks execution of the Windows Form at the breakpoint.  
  
## See Also  
 [Debugging Managed Code](../debugger/debugging-managed-code.md)   
 [Debugger Security](../debugger/debugger-security.md)