---
title: 'İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e0bc88c8581b29f43e7efc55ee86019e1f1c3fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736754"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>İzlenecek Yol: C# veya Visual Basic Kullanarak SDK Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, bir basit matematik kitaplığı SDK'sı, Visual C# kullanarak oluşturma ve sonra bir Visual Studio Uzantısı (VSIX) olarak SDK paketini öğreneceksiniz. Aşağıdaki yordamları tamamlamanız:  
  
-   [SimpleMath Windows çalışma zamanı bileşeni oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [SimpleMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> SimpleMath Windows çalışma zamanı bileşeni oluşturma  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **yeni proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C#** veya **Visual Basic**, seçin **Windows Store** düğümünü seçip **Windows çalışma zamanı bileşeni** şablonu.  
  
3.  İçinde **adı** kutusunda, belirtin **SimpleMath**ve ardından **Tamam** düğmesi.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMath** proje düğümünü ve ardından **özellikleri**.  
  
5.  Yeniden adlandırma **Class1.cs** için **Arithmetic.cs** ve aşağıdaki kodu eşleşecek şekilde güncelleştirin:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'SimpleMath'** düğümünü seçip **Configuration Manager**.  
  
     **Configuration Manager** iletişim kutusu açılır.  
  
7.  İçinde **etkin çözüm yapılandırması** listesinde **yayın**.  
  
8.  İçinde **yapılandırma** sütun doğrulayın **SimpleMath** satır kümesine **yayın**ve ardından **Kapat** kabul etmek için düğmeyi değiştirin.  
  
    > [!IMPORTANT]
    >  Yalnızca bir yapılandırma SimpleMath bileşeni için SDK'sı içerir. Bu yapılandırma sürüm yapısı olmanız veya bileşen kullanan uygulamalar olmaz sertifika için geçirmeniz[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMath** proje düğümünü ve ardından **yapı**.  
  
##  <a name="createVSIX"></a> SimpleMathVSIX uzantı projesini oluşturmak için  
  
1.  Kısayol menüsünde **çözüm 'SimpleMath'** düğümünü seçin **Ekle**, **yeni proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C#** veya **Visual Basic**, seçin **genişletilebilirlik** düğümünü seçip **VSIX projesi** şablonu.  
  
3.  İçinde **adı** kutusunda, belirtin **SimpleMathVSIX**ve ardından **Tamam** düğmesi.  
  
4.  İçinde **Çözüm Gezgini**, seçin **source.extension.vsixmanifest** öğesi.  
  
5.  Menü çubuğunda, **görünümü**, **kod**.  
  
6.  Var olan XML aşağıdaki XML ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  İçinde **Çözüm Gezgini**, seçin **SimpleMathVSIX** proje.  
  
8.  Menü çubuğunda, **proje**, **Yeni Öğe Ekle**.  
  
9. Listesinde **ortak öğeler**, genişletme **veri**ve ardından **XML dosyası**.  
  
10. İçinde **adı** kutusunda, belirtin `SDKManifest.xml`ve ardından **Ekle** düğmesi.  
  
11. İçinde **Çözüm Gezgini**, kısayol menüsünü açın `SDKManifest.xml`, seçin **özellikleri**ve ardından değiştirin **VSIX Ekle** özelliğini**True**.  
  
12. Dosyanın içeriğini aşağıdaki XML ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMathVSIX** projesinin **Ekle**ve ardından **yeni klasör**.  
  
14. Klasörü Yeniden Adlandır `references`.  
  
15. Kısayol menüsünü açın **başvuruları** klasörü seçin **Ekle**ve ardından **yeni klasör**.  
  
16. Alt klasöre yeniden adlandır `commonconfiguration`içindeki bir alt klasör oluşturun ve alt klasör adı `neutral`.  
  
17. İlk klasörü yeniden adlandırma şu önceki dört adımı yineleyin `redist`.  
  
     Proje artık aşağıdaki klasör yapısını içerir:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMath** proje ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
19. İçinde **dosya Gezgini**bin\Release klasöre gidin, SimpleMath.winmd dosyası için kısayol menüsünü açın ve ardından **kopyalama**.  
  
20. İçinde **Çözüm Gezgini**, dosyayı references\commonconfiguration\neutral klasörüne yapıştırın **SimpleMathVSIX** proje.  
  
21. Redist\commonconfiguration\neutral klasörüne SimpleMath.pri dosya yapıştırarak önceki adımı yineleyin **SimpleMathVSIX** proje.  
  
22. İçinde **Çözüm Gezgini**, seçin **SimpleMath.winmd**.  
  
23. Menü çubuğunda, **görünümü**, **özellikleri** (klavye: F4 tuşuna basın).  
  
24. İçinde **özellikleri** penceresinde değişiklik **derleme eylemi** özelliğini **içerik**ve ardından değiştirmek **VSIX Ekle** özelliği **True**.  
  
25. İçinde **Çözüm Gezgini**, bu işlem için yineleme **SimpleMath.pri**.  
  
26. İçinde **Çözüm Gezgini**, seçin **SimpleMathVSIX** proje.  
  
27. Menü çubuğunda, **derleme**, **derleme SimpleMathVSIX**.  
  
28. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMathVSIX** proje ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
29. İçinde **dosya Gezgini**\bin\Release klasörüne gidin ve ardından yüklemek için SimpleMathVSIX.vsix çalıştırın.  
  
30. Seçin **yükleme** düğmesi, yüklemenin tamamlanmasını bekleyin ve sonra Visual Studio'yu yeniden başlatın.  
  
##  <a name="createSample"></a> Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için  
  
1. Menü çubuğunda, **dosya**, **yeni**, **yeni proje**.  
  
2. Şablonlar listesinde genişletin **Visual C#** veya **Visual Basic**ve ardından **Windows Store** düğümü.  
  
3. Seçin **boş uygulama** şablon, proje adı **ArithmeticUI**ve ardından **Tamam** düğmesi.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ArithmeticUI** proje ve ardından **Ekle**, **başvuru**.  
  
5. Başvuru türlerinin listesinde, **Windows**ve ardından **uzantıları**.  
  
6. Ayrıntılar bölmesinde **basit matematik SDK** uzantısı.  
  
    SDK'nızı hakkında ek bilgiler görüntülenir. Seçebileceğiniz **daha fazla bilgi** açmak için bağlantıyı http://www.msdn.microsoft.com, bu kılavuzda daha önce açıklanan SDKManifest.xml dosyasında belirtildiği gibi.  
  
7. İçinde **başvuru Yöneticisi** iletişim kutusunda **basit matematik SDK** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
8. Menü çubuğunda, **görünümü**, **Nesne Tarayıcısı**.  
  
9. İçinde **Gözat** listesinde **basit matematik**.  
  
     Artık, SDK'yı nedir keşfedebilirsiniz.  
  
10. İçinde **Çözüm Gezgini**mainpage.XAML dosyasını açın ve içeriğini aşağıdaki XAML ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. MainPage.xaml.cs aşağıdaki kodu eşleşecek şekilde güncelleştirin:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
13. Uygulamada, herhangi iki sayıyı girin, bir işlem seçin ve ardından **=** düğmesi.  
  
     Doğru sonucu görünür.  
  
    Başarıyla oluşturulan ve bir uzantı SDK'sı kullanılıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [İzlenecek yol: JavaScript kullanarak SDK oluşturma](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)

