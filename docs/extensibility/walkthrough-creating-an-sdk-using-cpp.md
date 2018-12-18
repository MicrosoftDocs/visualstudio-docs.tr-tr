---
title: 'İzlenecek yol: C++ kullanarak SDK oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6311526df299da860c829520a2087ecc8d786600
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930654"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>İzlenecek yol: C++ kullanarak SDK oluşturma
Bu izlenecek yol, yerel C++ matematik kitaplığı SDK, Visual Studio Uzantısı (VSIX) olarak SDK paketi oluşturma ve bir uygulama oluşturmak için kullanmak gösterir. İzlenecek yol, bu adımları ayrılmıştır:  
  
-   [Yerel ve Windows çalışma zamanı kitaplıkları oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [NativeMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Yerel ve Windows çalışma zamanı kitaplıkları oluşturmak için  
  
1.  Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C++** > **Windows Evrensel**ve ardından **DLL (Evrensel Windows uygulamaları)** şablonu. İçinde **adı** kutusunda, belirtin `NativeMath`ve ardından **Tamam** düğmesi.  
  
3.  Güncelleştirme *NativeMath.h* aşağıdaki kodu eşleştirilecek.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Güncelleştirme *NativeMath.cpp* bu kodu eşleştirmek için:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'NativeMath'** ve ardından **Ekle** > **yeni proje**.  
  
6.  Şablonlar listesinde genişletin **Visual C++** ve ardından **Windows çalışma zamanı bileşeni** şablonu. İçinde **adı** kutusunda, belirtin `NativeMathWRT`ve ardından **Tamam** düğmesi.  
  
7.  Güncelleştirme *Class1.h* bu kodu eşleştirmek için:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Güncelleştirme *Class1.cpp* bu kodu eşleştirmek için:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
##  <a name="createVSIX"></a> NativeMathVSIX uzantı projesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'NativeMath'** ve ardından **Ekle** > **yeni proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C#** > **genişletilebilirlik**ve ardından **VSIX projesi**. İçinde **adı** kutusunda, belirtin **NativeMathVSIX**ve ardından **Tamam** düğmesi.
  
3.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **source.extension.vsixmanifest**ve ardından **kodu görüntüle**.  
  
4.  Var olan XML değiştirmek için aşağıdaki XML kullanın.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NativeMathVSIX** proje ve ardından **Ekle** > **yeni öğe**.  
  
6.  Listesinde **Visual C# öğeleri**, genişletme **veri**ve ardından **XML dosyası**. İçinde **adı** kutusunda, belirtin `SDKManifest.xml`ve ardından **Tamam** düğmesi.  
  
7.  Bu XML dosyasının içeriğini değiştirmek için kullanın:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. İçinde **Çözüm Gezgini**altında **NativeMathVSIX** proje, bu klasör yapısını oluşturun:  
  
    ```xml  
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
  
9. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'NativeMath'** ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
10. İçinde **dosya Gezgini**, kopyalama *$SolutionRoot$\NativeMath\NativeMath.h*ve ardından **Çözüm Gezgini**altında **NativeMathVSIX**yapıştırın, proje *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  klasör.  
  
     Kopyalama *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*, ardından yapıştırın *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  klasör.  
  
     Kopyalama *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* yapıştırın *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  klasör.  
  
     Kopyalama *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* yapıştırın *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* klasör.  
     Kopyalama *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* yapıştırın *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* klasör.  
  
     Kopyalama *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* yapıştırın *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* klasör.  
  
11. İçinde *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  klasöründe adlı bir metin dosyası oluşturun *NativeMathSDK.props*, ardından aşağıdaki içeriği yapıştırın:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Menü çubuğunda, **görünümü** > **diğer Windows** > **Özellikler penceresi** (klavye: seçin **F4**anahtar).  
  
13. İçinde **Çözüm Gezgini**seçin **NativeMathWRT.winmd** dosya. İçinde **özellikleri** penceresinde değişiklik **derleme eylemi** özelliğini **içerik**ve ardından değiştirmek **VSIX Ekle** özelliği **True**.  
  
     Bu işlem için yineleme **NativeMath.h** dosya.  
  
     Bu işlem için yineleme **NativeMathWRT.pri** dosya.  
  
     Bu işlem için yineleme **NativeMath.Lib** dosya.  
  
     Bu işlem için yineleme **NativeMathSDK.props** dosya.  
  
14. İçinde **Çözüm Gezgini**seçin **NativeMath.h** dosya. İçinde **özellikleri** penceresinde değişiklik **VSIX Ekle** özelliğini **True**.  
  
     Bu işlem için yineleme **NativeMath.dll** dosya.  
  
     Bu işlem için yineleme **NativeMathWRT.dll** dosya.  
  
     Bu işlem için yineleme **SDKManifest.xml** dosya.  
  
15. Menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
16. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NativeMathVSIX** proje ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
17. İçinde **dosya Gezgini**, gitmek *$SolutionRoot$ \NativeMathVSIX\bin\Debug* klasörünü açın ve ardından Çalıştır *NativeMathVSIX.vsix* yüklemeyi başlatmak için.  
  
18. Seçin **yükleme** düğmesi, yüklemenin tamamlanmasını bekleyin ve sonra Visual Studio'yu başlatın.  
  
##  <a name="createSample"></a> Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için  
  
1. Menü çubuğunda, **dosya** > **yeni** > **proje**.  
  
2. Şablonlar listesinde genişletin **Visual C++** > **Windows Evrensel** seçip **boş uygulama**. İçinde **adı** kutusunda, belirtin **NativeMathSDKSample**ve ardından **Tamam** düğmesi.  
  
3. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **NativeMathSDKSample** proje ve ardından **Ekle** > **başvurusu**.  
  
4. İçinde **Başvuru Ekle** iletişim kutusunda, başvuru türleri listesini genişletin **Evrensel Windows**ve ardından **uzantıları**. Son olarak, seçin **yerel matematik SDK** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.
  
5. Proje özellikleri için NativeMathSDKSample görüntüler.  
  
    İçinde tanımlanan özellikler *NativeMathSDK.props* başvuru eklendiğinde uygulandı. Nesnenin özelliklerini inceleyerek uygulandığını doğrulayabilirsiniz **VC ++ dizinleri** projeye ait özellik **yapılandırma özellikleri**.  
  
6. İçinde **Çözüm Gezgini**açın **MainPage.xaml**ve ardından içeriğini değiştirmek için aşağıdaki XAML kullanın:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Güncelleştirme *Mainpage.xaml.h* bu kodu eşleştirmek için:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Güncelleştirme *MainPage.xaml.cpp* bu kodu eşleştirmek için:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Seçin **F5** uygulamayı çalıştırmak için anahtar.  
  
10. Uygulamada, herhangi iki sayıyı girin, bir işlem seçin ve ardından **=** düğmesi.  
  
     Doğru sonucu görünür.  
  
    Bu izlenecek yolda gösterilen oluşturun ve çağırmak için bir uzantı SDK kullanma bir [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] kitaplığı ve olmayan bir[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] kitaplığı.  
  
## <a name="next-steps"></a>Sonraki adımlar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Bir yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)
