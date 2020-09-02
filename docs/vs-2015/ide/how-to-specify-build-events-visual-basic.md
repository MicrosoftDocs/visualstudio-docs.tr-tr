---
title: 'Nasıl yapılır: derleme olaylarını belirtme (Visual Basic) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 820f4ac8b154579664e01b12aa8146e4668cc17b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670675"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic derleme olayları, derleme sürecinin bir parçası olarak betikleri, makroları veya diğer eylemleri çalıştırmak için kullanılabilir. Derleme öncesi olaylar derlemeden önce oluşur; Derleme sonrası olaylar derleme sonrasında oluşur.

 Derleme olayları, **Proje Tasarımcısı**' nın **derleme** sayfasından erişilebilen **derleme olayları** iletişim kutusunda belirtilir.

> [!NOTE]
> Visual Basic Express, derleme olaylarının girişini desteklemez. Bu yalnızca tam Visual Studio ürününde desteklenir.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Oluşturma öncesi ve oluşturma sonrası olayları belirtme

#### <a name="to-specify-a-build-event"></a>Derleme olayı belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Derle** sekmesine tıklayın.

3. **Derleme olayları iletişim kutusunu** açmak Için **Olayları oluştur** düğmesine tıklayın.

4. Oluşturma öncesi veya oluşturma sonrası eyleminiz için komut satırı bağımsız değişkenlerini girin ve ardından **Tamam**' a tıklayın.

    > [!NOTE]
    > `call`. Bat dosyalarını çalıştıran tüm derleme sonrası komutlarının önüne bir ifade ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

    > [!NOTE]
    > Oluşturma öncesi veya oluşturma sonrası olaylarınız başarıyla tamamlanmazsa, olay eyleminizi, sıfırdan farklı bir eylem belirten (0) dışında bir kodla çıkış yaparak derlemeyi sonlandırabilirsiniz.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Örnek: derleme sonrası bir olay kullanarak bildirim bilgilerini değiştirme
 Aşağıdaki yordamda, derleme sonrası olayından (proje dizinindeki. exe. manifest dosyası) çağrılan bir. exe komutu kullanılarak uygulama bildiriminde en düşük işletim sistemi sürümünün nasıl ayarlanacağı gösterilmektedir. En düşük işletim sistemi sürümü, 4.10.0.0 gibi dört bölümden oluşan bir sayıdır. Bunu yapmak için, komut `<dependentOS>` bildirimin bölümünü değiştirir:

```
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek üzere bir. exe komutu oluşturmak için

1. Komut için bir konsol uygulaması oluşturun. **Dosya** menüsünde **Yeni**' ye ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Visual Basic** düğümünde **Windows** ' u ve ardından **konsol uygulama** şablonu ' nu seçin. Projeyi adlandırın `ChangeOSVersionVB` .

3. Module1. vb dosyasında, aşağıdaki satırı `Imports` dosyanın en üstündeki diğer deyimlere ekleyin:

   ```
   Imports System.Xml
   ```

4. Aşağıdaki kodu içine ekleyin `Sub Main` :

   ```
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

    Komut iki bağımsız değişken alır. İlk bağımsız değişken, uygulama bildiriminin yoludur (yani, yapı işleminin bildirimi oluşturduğu klasör, genellikle ProjectName. Publish). İkinci bağımsız değişken yeni işletim sistemi sürümüdür.

5. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

6. . Exe dosyasını gibi bir dizine kopyalayın `C:\TEMP\ChangeOSVersionVB.exe` .

   Sonra, uygulama bildirimini değiştirmek için bu komutu derleme sonrası bir olayda çağırın.

#### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek üzere derleme sonrası olayını çağırmak için

1. Yayımlanacak proje için bir Windows uygulaması oluşturun. **Dosya** menüsünde **Yeni**' ye ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusundaki **Visual Basic** düğümünde **Windows** ' u ve ardından **Windows uygulama** şablonu ' nu seçin. Projeyi adlandırın `VBWinApp` .

3. **Çözüm Gezgini**' de proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

4. Proje tasarımcısında **Yayımla** sayfasına gidin ve **Yayımlama konumunu** olarak ayarlayın `C:\TEMP\` .

5. **Şimdi Yayımla**' ya tıklayarak projeyi yayımlayın.

     Bildirim dosyası oluşturulacak ve yerleştirilecek `C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest` . Bildirimi görüntülemek için, dosyaya sağ tıklayın ve **birlikte Aç**' a tıklayın ve ardından **Listeden programı seç**' e tıklayın ve ardından **Notepad**' e tıklayın.

     Dosyasında öğesi için arama yapın `<osVersionInfo>` . Örneğin, sürüm şu olabilir:

    ```
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. Proje tasarımcısında **Derle** sekmesine gidin **ve derleme olayları iletişim kutusunu** açmak için **olayları** derle düğmesine tıklayın.

7. **Oluşturma sonrası olay komut satırı** kutusunda, aşağıdaki komutu girin:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Projeyi derlediğinizde, bu komut uygulama bildirimindeki en düşük işletim sistemi sürümünü 5.1.2600.0 olarak değiştirir.

     `$(TargetPath)`Makro, oluşturulmakta olan yürütülebilir dosyanın tam yolunu ifade eder. Bu nedenle, $ (TargetPath). manifest, bin dizininde oluşturulan uygulama bildirimini belirtir. Yayımlama, bu bildirimi daha önce ayarladığınız yayımlama konumuna kopyalar.

8. Projeyi yeniden yayımlayın. **Yayımla** sayfasına gidin ve **Şimdi Yayımla**' ya tıklayın.

     Bildirimi yeniden görüntüleyin. Bildirimi görüntülemek için yayımlama dizinine gidin, dosyaya sağ tıklayın ve **birlikte Aç** ' a tıklayın ve ardından **Listeden program**' ı seçin ve ardından **Notepad**' e tıklayın.

     Sürüm şu anda şunu okumalı:

    ```
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme özelliklerini yönetme](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c) derleme [sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md) [Yayımlama sayfası, proje Tasarımcısı](../ide/reference/publish-page-project-designer.md) [derleme öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [How to: Specify Build Events (C#)](../ide/how-to-specify-build-events-csharp.md)
