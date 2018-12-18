---
title: 'İzlenecek yol: bir Windows formunda hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f43835374ac74d50e1e81623ecf268fbfbfe8ca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726600"
---
# <a name="walkthrough-debugging-a-windows-form"></a>İzlenecek Yol: Windows Formunda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
    1.  Visual Basic veya Visual C# için seçin **Windows** düğümünü seçip **Windows Form uygulaması** içinde **şablonları** bölmesi.  
  
    2.  Visual C++ için seçin **CLR** düğümünü seçip **Windows Form uygulaması** içinde **şablonları** bölmesinde...  
  
3.  İçinde **şablonları** bölmesinde **Windows uygulama**.  
  
4.  İçinde **adı** kutusunda, projeyi (örneğin, Walkthrough_SimpleDebug) benzersiz bir ad verin.  
  
5.  **Tamam**'ı tıklatın.  
  
     Visual Studio, yeni bir proje oluşturur ve Windows Forms Tasarımcısı'nda yeni bir form görüntüler. Daha fazla bilgi için [Windows Form Tasarımcısı](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  Üzerinde **görünümü** menüsünde **araç kutusu**.  
  
     Araç Kutusu açılır. Daha fazla bilgi için [araç kutusu](../ide/reference/toolbox.md).  
  
7.  Araç kutusunda tıklayarak **düğmesi** denetlemek ve denetimi Form Tasarım yüzeyine sürükleyin. Düğmeyi form üzerine bırakın.  
  
8.  Araç kutusunda tıklayarak **TextBox** denetlemek ve denetimi Form Tasarım yüzeyine sürükleyin. DROP **TextBox** form üzerinde.  
  
9. Form tasarım yüzeyinde, düğmeyi çift tıklatın.  
  
     Bu sizi kod sayfasına götürür. İşaretçi `button1_Click` içinde olmalıdır.  
  
10. `button1_Click` işlevinde, aşağıdaki kodu ekleyin:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Üzerinde **derleme** menüsünde **Çözümü Derle**.  
  
     Projenin hatasız oluşturması gerekir.  
  
## <a name="debug-your-form"></a>Formunuzda Hata Ayıklama Yapın  
 Şimdi, hata ayıklamayı başlatmak için hazırsınız.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Bu adım adım izleme için oluşturulmuş Windows Formu hata ayıklaması için  
  
1.  Kaynak penceresinde, eklediğiniz metin ile aynı satırda sol kenar boşluğunu tıklatın:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Kırmızı bir nokta belirir ve satırdaki metin kırmızıyla vurgulanır. Kırmızı nokta bir kesme noktası temsil eder. Daha fazla bilgi için [kesme noktaları](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Uygulamayı hata ayıklayıcısı altında çalıştırdığınızda, hata ayıklayıcısı koda ulaşıldığında, yürütmeyi o konumda keser. Ardından uygulamanızın durumunu görüntüleyebilir ve ona hata ayıklama yapabilirsiniz.  
  
    > [!NOTE]
    >  Ayrıca herhangi bir satır sağ kod üzerine **kesme noktası**ve ardından **kesme noktası Ekle** söz konusu satıra bir kesme noktası eklemek için.  
  
2.  ON **hata ayıklama** menüsünde seçin **Başlat**.  
  
     Windows Formu çalışmaya başlar.  
  
3.  Windows Formu'nda, eklediğiniz düğmeyi tıklatın.  
  
     Visual Studio'da bu, sizi kod satırında kesme noktası eklediğiniz satıra götürür. Bu satır, sarı ile vurgulanmış olmalıdır. Şimdi, uygulamanızda değişkenleri görüntüleyebilir ve yürütülmesini denetleyebilirsiniz. Uygulamanız artık yürütmeyi durdurmuştur ve sizden bir eylem bekliyordur.  
  
4.  Üzerinde **hata ayıklama** menüsünde seçin **Windows**, ardından **Watch**, tıklatıp **Watch1**.  
  
5.  İçinde **Watch1** penceresinde, boş bir satıra tıklayın. İçinde **adı** sütununa, `textBox1.Text` (Visual Basic, Visual C# ve J# kullanıyorsanız,) veya `textBox1->Text` (C++ kullanıyorsanız), ardından ENTER tuşuna basın.  
  
     **Watch1** penceresi, tırnak işareti içine alınmış bu değişkenin değerini gösterir:  
  
    ```  
    ""  
    ```  
  
6.  Üzerinde **hata ayıklama** menüsünde seçin **içine adımla**.  
  
     Değişiklikleri textBox1.Text değeri **Watch1** penceresine:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  Üzerinde **hata ayıklama** menüsünde seçin **devam** programınızın hatalarını ayıklamayı devam etmek için.  
  
8.  Windows Formunda, düğmeyi yeniden tıklatın.  
  
     Visual Studio, yürütmeyi yeniden keser.  
  
9. Kesme noktasını temsil eden kırmızı noktayı tıklatın.  
  
     Bu, kesme noktasını kodunuzdan kaldırır.  
  
10. Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Hata Ayıklama için Windows Form Uygulamanıza Ekleme  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] içinde, hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz. Express Edition kullanıyorsanız, bu özellik desteklenmez.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Hata ayıklama için Windows Form Uygulamasına eklemek için  
  
1.  Yukarıda oluşturduğunuz projede, sol kenar boşluğunu tıklatarak, eklediğiniz satırda bir kez daha bir kesme noktası ayarlayın:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  Üzerinde **hata ayıklama** menüsünde **hata ayıklama olmadan Başlat**.  
  
     Çalıştırılabilir haline çift tıklatmışsınız gibi, Windows Formu, Windows altında çalışmaya başlar. Hata ayıklayıcısı iliştirilmemiş.  
  
3.  Üzerinde **hata ayıklama** menüsünde **iliştirme**. (Bu komut ayrıca şurada bulunur **Araçları** menü.)  
  
     **İliştirme** iletişim kutusu görüntülenir.  
  
4.  İçinde **kullanılabilir işlemler** bölmesinde, işlem adını (Walkthrough_SimpleDebug.exe) içinde Bul **işlem** sütun bulup tıklayın.  
  
5.  Tıklayın **iliştirme** düğmesi.  
  
6.  Windows Formunuzda, tek başına bir tane olan düğmeyi tıklatın.  
  
     Hata ayıklayıcısı, kesme noktasında Windows Formunun yürütülmesini keser.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)



