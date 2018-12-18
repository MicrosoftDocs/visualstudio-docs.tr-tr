---
title: 'İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c65f827af864a32bb13a90a0ba9818467298527
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835168"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma
Bu kılavuzda, bir basit matematik kitaplığı SDK'sı, Visual C# kullanarak oluşturma ve sonra bir Visual Studio Uzantısı (VSIX) olarak SDK paketini öğreneceksiniz. Aşağıdaki yordamları tamamlamanız:  
  
-   [SimpleMath Windows çalışma zamanı bileşeni oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [SimpleMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
-   [Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> SimpleMath Windows çalışma zamanı bileşeni oluşturma  
  
1. Menü çubuğunda, **dosya** > **yeni** > **yeni proje**.  
  
2. Şablonlar listesinde genişletin **Visual C#** veya **Visual Basic**, seçin **Windows Store** düğümünü seçip **Windows çalışma zamanı bileşeni** şablonu.  
  
3. İçinde **adı** kutusunda, belirtin **SimpleMath**ve ardından **Tamam** düğmesi.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMath** proje düğümünü ve ardından **özellikleri**.  
  
5. Yeniden adlandırma **Class1.cs** için **Arithmetic.cs** ve aşağıdaki kodu eşleşecek şekilde güncelleştirin:  
  
    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **çözüm 'SimpleMath'** düğümünü seçip **Configuration Manager**.  
  
    **Configuration Manager** iletişim kutusu açılır.  
  
7. İçinde **etkin çözüm yapılandırması** listesinde **yayın**.  
  
8. İçinde **yapılandırma** sütun doğrulayın **SimpleMath** satır kümesine **yayın**ve ardından **Kapat** kabul etmek için düğmeyi değiştirin.  
  
   > [!IMPORTANT]
   >  Yalnızca bir yapılandırma SimpleMath bileşeni için SDK'sı içerir. Bu yapılandırma sürüm yapısı olmanız veya bileşen kullanan uygulamalar olmaz sertifika için geçirmeniz[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].  
  
9. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMath** proje düğümünü ve ardından **yapı**.  
  
##  <a name="createVSIX"></a> SimpleMathVSIX uzantı projesini oluşturmak için  
  
1.  Kısayol menüsünde **çözüm 'SimpleMath'** düğümünü seçin **Ekle** > **yeni proje**.  
  
2.  Şablonlar listesinde genişletin **Visual C#** veya **Visual Basic**, seçin **genişletilebilirlik** düğümünü seçip **VSIX projesi** şablonu.  
  
3.  İçinde **adı** kutusunda, belirtin **SimpleMathVSIX**ve ardından **Tamam** düğmesi.  
  
4.  İçinde **Çözüm Gezgini**, seçin **source.extension.vsixmanifest** öğesi.  
  
5.  Menü çubuğunda, **görünümü** > **kod**.  
  
6.  Var olan XML aşağıdaki XML ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  İçinde **Çözüm Gezgini**, seçin **SimpleMathVSIX** proje.  
  
8.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
9. Listesinde **ortak öğeler**, genişletme **veri**ve ardından **XML dosyası**.  
  
10. İçinde **adı** kutusunda, belirtin `SDKManifest.xml`ve ardından **Ekle** düğmesi.  
  
11. İçinde **Çözüm Gezgini**, kısayol menüsünü açın `SDKManifest.xml`, seçin **özellikleri**ve ardından değiştirin **VSIX Ekle** özelliğini**True**.  
  
12. Dosyanın içeriğini aşağıdaki XML ile değiştirin:  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```  
  
13. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMathVSIX** projesinin **Ekle**ve ardından **yeni klasör**.  
  
14. Klasörü Yeniden Adlandır `references`.  
  
15. Kısayol menüsünü açın **başvuruları** klasörü seçin **Ekle**ve ardından **yeni klasör**.  
  
16. Alt klasöre yeniden adlandır `commonconfiguration`içindeki bir alt klasör oluşturun ve alt klasör adı `neutral`.  
  
17. İlk klasörü yeniden adlandırma şu önceki dört adımı yineleyin `redist`.  
  
     Proje artık aşağıdaki klasör yapısını içerir:  
  
    ```xml
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMath** proje ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
19. İçinde **dosya Gezgini**, gidin *bin\Release* klasörü için kısayol menüsünü açın **SimpleMath.winmd** dosya ve ardından **kopyalama**.  
  
20. İçinde **Çözüm Gezgini**, dosyaya yapıştırın *references\commonconfiguration\neutral* klasöründe **SimpleMathVSIX** proje.  
  
21. Önceki adımı yineleyin yapıştırma **SimpleMath.pri** doyasını *redist\commonconfiguration\neutral* klasöründe **SimpleMathVSIX** proje.  
  
22. İçinde **Çözüm Gezgini**, seçin **SimpleMath.winmd**.  
  
23. Menü çubuğunda, **görünümü** > **özellikleri** (klavye: seçin **F4** anahtar).  
  
24. İçinde **özellikleri** penceresinde değişiklik **derleme eylemi** özelliğini **içerik**ve ardından değiştirmek **VSIX Ekle** özelliği **True**.  
  
25. İçinde **Çözüm Gezgini**, bu işlem için yineleme **SimpleMath.pri**.  
  
26. İçinde **Çözüm Gezgini**, seçin **SimpleMathVSIX** proje.  
  
27. Menü çubuğunda, **derleme** > **derleme SimpleMathVSIX**.  
  
28. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SimpleMathVSIX** proje ve ardından **klasörü dosya Gezgini'nde Aç**.  
  
29. İçinde **dosya Gezgini**, gitmek *\bin\Release* klasörünü açın ve ardından Çalıştır *SimpleMathVSIX.vsix* yüklemek için.  
  
30. Seçin **yükleme** düğmesi, yüklemenin tamamlanmasını bekleyin ve sonra Visual Studio'yu yeniden başlatın.  
  
##  <a name="createSample"></a> Sınıf kitaplığı kullanan örnek bir uygulama oluşturmak için  
  
1. Menü çubuğunda, **dosya** > **yeni** > **yeni proje**.  
  
2. Şablonlar listesinde genişletin **Visual C#** veya **Visual Basic**ve ardından **Windows Store** düğümü.  
  
3. Seçin **boş uygulama** şablon, proje adı **ArithmeticUI**ve ardından **Tamam** düğmesi.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ArithmeticUI** proje ve ardından **Ekle** > **başvuru**.  
  
5. Başvuru türlerinin listesinde, **Windows**ve ardından **uzantıları**.  
  
6. Ayrıntılar bölmesinde **basit matematik SDK** uzantısı.  
  
    SDK'nızı hakkında ek bilgiler görüntülenir. Seçebileceğiniz **daha fazla bilgi** açmak için bağlantıyı https://msdn.microsoft.com/, bu kılavuzda daha önce açıklanan SDKManifest.xml dosyasında belirtildiği gibi.  
  
7. İçinde **başvuru Yöneticisi** iletişim kutusunda **basit matematik SDK** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
8. Menü çubuğunda, **görünümü** > **Nesne Tarayıcısı**.  
  
9. İçinde **Gözat** listesinde **basit matematik**.  
  
     Artık, SDK'yı nedir keşfedebilirsiniz.  
  
10. İçinde **Çözüm Gezgini**açın **MainPage.xaml**ve içeriğini aşağıdaki XAML ile değiştirin:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. Güncelleştirme **MainPage.xaml.cs** aşağıdaki kodu eşleştirmek için:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. Seçin **F5** uygulamayı çalıştırmak için anahtar.  
  
13. Uygulamada, herhangi iki sayıyı girin, bir işlem seçin ve ardından **=** düğmesi.  
  
     Doğru sonucu görünür.  
  
    Başarıyla oluşturulan ve bir uzantı SDK'sı kullanılıyor.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [İzlenecek yol: JavaScript kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)   
 [Bir yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)