---
title: 'İzlenecek yol: C++ kullanarak SDK oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0932759213d064c3df717b7b6735c1201e62ce14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773476"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>İzlenecek Yol: C++ Kullanarak SDK Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, yerel C++ matematik kitaplığı SDK, Visual Studio Uzantısı (VSIX) olarak SDK paketi oluşturma ve bir uygulama oluşturmak için kullanmak gösterir. İzlenecek yol, bu adımları ayrılmıştır:  
  
-   [Yerel ve Windows çalışma zamanı kitaplıkları oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [NativeMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Yerel ve Windows çalışma zamanı kitaplıkları oluşturmak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C++**, **Windows Store**ve ardından **DLL (Windows Store apps)** şablonu. İçinde **adı** kutusunda, belirtin `NativeMath`ve ardından **Tamam** düğmesi.  
  
3.  NativeMath.h aşağıdaki kodu eşleşecek şekilde güncelleştirin.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4.  Bu kod eşleştirilecek NativeMath.cpp güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'NativeMath'** ve ardından **Ekle**, **yeni proje**.  
  
6.  Şablonlar listesinde genişletin **Visual C++** ve ardından **Windows çalışma zamanı bileşeni** şablonu. İçinde **adı** kutusunda, belirtin `NativeMathWRT`ve ardından **Tamam** düğmesi.  
  
7.  Bu kod eşleştirilecek Class1.h güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8.  Bu kod eşleştirilecek Class1.cpp güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Menü çubuğunda, **derleme**, **Çözümü Derle**.  
  
##  <a name="createVSIX"></a> NativeMathVSIX uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'NativeMath'** ve ardından **Ekle**, **yeni proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C#**, **genişletilebilirlik**ve ardından **VSIX paketi**. İçinde **adı** kutusunda, belirtin **NativeMathVSIX**ve ardından **Tamam** düğmesi.  
  
3.  VSIX bildirim Tasarımcısı göründüğünde, kapatın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **source.extension.vsixmanifest**ve ardından **kodu görüntüle**.  
  
5.  Var olan XML değiştirmek için aşağıdaki XML kullanın.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NativeMathVSIX** proje ve ardından **Ekle**, **yeni öğe**.  
  
7.  Listesinde **Visual C# öğeleri**, genişletme **veri**ve ardından **XML dosyası**. İçinde **adı** kutusunda, belirtin `SDKManifest.xml`ve ardından **Tamam** düğmesi.  
  
8.  Bu XML dosyasının içeriğini değiştirmek için kullanın:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. İçinde **Çözüm Gezgini**, **NativeMathVSIX** proje, bu klasör yapısını oluşturun:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'NativeMath'** ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
11. İçinde **dosya Gezgini**, \NativeMath\NativeMath.h, kopyalayın ve ardından **Çözüm Gezgini**, **NativeMathVSIX** projesine, içinde \DesignTime\ yapıştırın CommonConfiguration\Neutral\Include\ klasör.  
  
     \Debug\NativeMath\NativeMath.lib kopyalayın ve ardından \DesignTime\Debug\x86\ klasörüne yapıştırın.  
  
     \Debug\NativeMath\NativeMath.dll kopyalayıp \Redist\Debug\x86\ klasörüne yapıştırın.  
  
     DebugNativeMathWRTNativeMathWRT.dll kopyalayıp RedistDebugx86 klasörüne yapıştırın.  
  
     DebugNativeMathWRTNativeMathWRT.winmd kopyalayıp ReferencesCommonConfigurationNeutral klasörüne yapıştırın.  
  
     DebugNativeMathWRTNativeMathWRT.pri kopyalayıp ReferencesCommonConfigurationNeutral klasörüne yapıştırın.  
  
12. \DesignTime\Debug\x86\ klasöründe NativeMathSDK.props adlı bir metin dosyası oluşturun ve içine aşağıdaki içeriği yapıştırın:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Menü çubuğunda, **görünümü**, **diğer Windows**, **Özellikler penceresi** (klavye: F4 tuşuna basın).  
  
14. İçinde **Çözüm Gezgini**seçin **NativeMathWRT.winmd** dosya. İçinde **özellikleri** penceresinde değişiklik **derleme eylemi** özelliğini **içerik**ve ardından değiştirmek **VSIX Ekle** özelliği **True**.  
  
     Bu işlem için yineleme **SimpleMath.pri** dosya.  
  
     Bu işlem için yineleme **NativeMath.Lib** dosya.  
  
     Bu işlem için yineleme **NativeMathSDK.props** dosya.  
  
15. İçinde **Çözüm Gezgini**seçin **NativeMath.h** dosya. İçinde **özellikleri** penceresinde değişiklik **VSIX Ekle** özelliğini **True**.  
  
     Bu işlem için yineleme **NativeMath.dll** dosya.  
  
     Bu işlem için yineleme **NativeMathWRT.dll** dosya.  
  
     Bu işlem için yineleme **SDKManifest.xml** dosya.  
  
16. Menü çubuğunda, **derleme**, **Çözümü Derle**.  
  
17. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NativeMathVSIX** proje ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
18. İçinde **dosya Gezgini**\bin\Debug\ klasöre gidin ve ardından yükleme işlemini başlatmak için NativeMathVSIX.vsix çalıştırın.  
  
19. Seçin **yükleme** düğmesi, yüklemenin tamamlanmasını bekleyin ve sonra Visual Studio'yu yeniden başlatın.  
  
##  <a name="createSample"></a> Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için  
  
1. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2. Şablonlar listesinde genişletin **Visual C++**, **Windows Store**ve ardından **boş uygulama**. İçinde **adı** kutusunda, belirtin **NativeMathSDKSample**ve ardından **Tamam** düğmesi.  
  
3. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NativeMathSDKSample** proje ve ardından **Ekle**, **başvuru**.  
  
4. Üzerinde **ortak özellikler**, **çerçeve ve başvurular** özellik sayfası, başvuru türleri listesinde genişletin **Windows**ve ardından **uzantıları** . Ayrıntılar bölmesinde seçin **yerel matematik SDK** uzantısı seçip **Yeni Başvuru Ekle** düğmesi.  
  
5. İçinde **Başvuru Ekle** iletişim kutusunda **yerel matematik SDK** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
6. Proje özellikleri için NativeMathSDKSample görüntüler.  
  
    Başvuru eklendiğinde NativeMathSDK.props içinde tanımlanan özellikler uygulandı. Bu incelenerek doğrulayın **VC ++ dizinleri** projeye ait özellik **yapılandırma özellikleri**.  
  
7. İçinde **Çözüm Gezgini**mainpage.XAML dosyasını açın ve ardından içeriğini değiştirmek için aşağıdaki XAML kullanın:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Mainpage.xaml.h bu kodu eşleşecek şekilde güncelleştirin:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. MainPage.xaml.cpp bu kodu eşleşecek şekilde güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
11. Uygulamada, herhangi iki sayıyı girin, bir işlem seçin ve ardından **=** düğmesi.  
  
     Doğru sonucu görünür.  
  
    Bu izlenecek yolda gösterilen oluşturun ve çağırmak için bir uzantı SDK kullanma bir [!INCLUDE[wrt](../includes/wrt-md.md)] kitaplığı ve olmayan bir[!INCLUDE[wrt](../includes/wrt-md.md)] kitaplığı.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)

