---
title: 'İzlenecek yol: Web formunda hata ayıklama | Microsoft Docs'
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
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7024a9abc58117bf28ed78de107b1c17ddad601f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747266"
---
# <a name="walkthrough-debugging-a-web-form"></a>İzlenecek Yol: Web Formunda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda açıklanan adımları hatalarını nasıl ayıklayacağınız Göster bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, Web formu olarak da bilinir. Başlat ve yürütmeyi durdurun, kesme noktaları ayarlayın ve değişkenleri incelemek nasıl gösterir **Watch** penceresi.  
  
> [!NOTE]
>  Bu izlenecek yolu tamamlamak için sunucu bilgisayarında yönetici ayrıcalıkları olmalıdır. Varsayılan olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlem aspnet_wp.exe veya w3wp.exe olarak çalışan bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlem. Hata ayıklamak için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], bilgisayarda yönetici ayrıcalıklarına sahip olduğu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalıştırır. Daha fazla bilgi için, bkz. [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
 İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Web formu oluşturma  
  
1.  Açık bir çözüm zaten varsa, kapatın.  
  
2.  Üzerinde **dosya** menüsünde tıklatın **yeni**ve ardından **Web sitesi**.  
  
     **Yeni Web sitesi** iletişim kutusu görüntülenir.  
  
3.  İçinde **şablonları** bölmesinde tıklayın **ASP.NET Web sitesi**.  
  
4.  Üzerinde **konumu** satır, tıklayın **HTTP** listeden ve metin kutusuna yazın **http://localhost/WebSite**.  
  
5.  İçinde **dil** listesinde **Visual C#** veya **Visual Basic**.  
  
6.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yeni bir proje oluşturur ve varsayılan HTML kaynak kodunu gösterir. Ayrıca adlı yeni bir sanal dizin oluşturur **Web sitesi** altında **varsayılan Web sitesi** IIS'de.  
  
7.  Tıklayın **tasarım** sekmesinde alt kenar boşluğu.  
  
8.  Tıklayın **araç kutusu** sekmesinde sol kenar boşluğu veya üzerinde seçin **görünümü** menüsü.  
  
     **Araç kutusu** açılır.  
  
9. İçinde **araç kutusu**, tıklayın **düğmesi** denetlemek ve Default.aspx temel tasarım yüzeyine ekleyin.  
  
10. İçinde **araç kutusu**, tıklayın **Textbox** denetimi ekleyin ve denetimi Default.aspx, temel tasarım yüzeyine sürükleyin.  
  
11. Bıraktığınız düğme denetimini çift tıklayın.  
  
     Bu sizi kod sayfasına götürür: C# veya Default.aspx.vb için Default.aspx.cs [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. İmleç işlevi olmalıdır `Button1_Click`.  
  
12. İçinde `Button1_Click` işlev, aşağıdaki kodu ekleyin:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     Projenin hatasız oluşturması gerekir.  
  
     Artık, hata ayıklamaya başlamak hazırsınız.  
  
### <a name="to-debug-the-web-form"></a>Web formu hata ayıklaması için  
  
1.  Default.aspx.cs veya Default.aspx.vb penceresinde, eklediğiniz metin ile aynı satırda sol kenar boşluğunu tıklatın:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Kırmızı bir nokta belirir ve satırdaki metin kırmızıyla vurgulanır. Kırmızı nokta bir kesme noktası temsil eder. Uygulamayı hata ayıklayıcısı altında çalıştırdığınızda, hata ayıklayıcısı koda ulaşıldığında, yürütmeyi o konumda keser. Ardından uygulamanızın durumunu görüntüleyebilir ve ona hata ayıklama yapabilirsiniz. Daha fazla bilgi için [kesme noktaları](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
3.  **Hata ayıklama etkin** iletişim kutusu görüntülenir. Seçin **hata ayıklamayı etkinleştirmek için Web.config dosyasını değiştirme** seçeneğini ve tıklayın **Tamam**.  
  
     Internet Explorer, başlatılır ve yalnızca tasarlanmış sayfası görüntülenir.  
  
4.  Internet Explorer'da düğmesine tıklayın.  
  
     İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bu sizi satırına kod sayfası Default.aspx.cs veya Default.aspx.vb kesme noktasına ayarlandığı götürür. Bu satır, sarı ile vurgulanmış olmalıdır. Şimdi, uygulamanızda değişkenleri görüntüleyebilir ve yürütülmesini denetleyebilirsiniz. Uygulamanızı çalıştırma durdurur ve sizden bir komutu bekler.  
  
5.  Üzerinde **hata ayıklama** menüsünde tıklayın **Windows**, ardından **izleme**ve ardından **Watch1**.  
  
6.  İçinde **Watch** penceresinde, tür **TextBox1.Text**.  
  
     **Watch** penceresi, değişkenin değerini gösterir `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  Üzerinde **hata ayıklama** menüsünü tıklatın **Step Over**.  
  
     Değerini `TextBox1.Text` değişiklikleri **Watch** okunacak penceresi:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Üzerinde **hata ayıklama** menüsünü tıklatın **devam**.  
  
9. Internet Explorer'da düğmesine tekrar tıklayın.  
  
     Yürütme kesme noktasında yeniden durdurur.  
  
10. Default.aspx.cs veya Default.aspx.vb penceresinde kırmızı nokta sol kenar boşluğunda tıklayın.  
  
     Bu kesme noktasını siler.  
  
11. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Durdur**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Hata ayıklama için Web formu eklemek için  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içinde, hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz. En etkili hata ayıklama için yürütülebilir dosya, sembol (PDB) dosyaları ile bir hata ayıklama sürümü derleyin.  
  
2.  Default.aspx.cs veya Default.aspx.vb penceresinde tekrar, eklediğiniz satırda bir kesme noktası ayarlamak için sol kenar boşluğunda tıklayın:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklama olmadan Başlat**.  
  
     Internet Explorer altında çalıştırmak Web formu başlatır, ancak hata ayıklayıcısı iliştirilmemiş.  
  
4.  Ekleme [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlem. Daha fazla bilgi için [dağıtılan Web uygulamaları hata ayıklama](../debugger/debugging-deployed-web-applications.md).  
  
5.  Internet Explorer'da formunuza düğmesine tıklayın.  
  
     İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Default.aspx.cs, Default.aspx.vb veya Default.aspx kesme noktasına isabet.  
  
6.  İşiniz bittiğinde hata ayıklama, üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Durdur**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)



