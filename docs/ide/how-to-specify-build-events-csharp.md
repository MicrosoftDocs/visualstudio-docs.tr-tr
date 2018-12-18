---
title: 'Nasıl yapılır: belirtin derleme olayları (C#)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: aa82c7f12b3932c1e9f5aac7392d6ef2b8e8a773
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885861"
---
# <a name="how-to-specify-build-events-c"></a>Nasıl yapılır: belirtin derleme olayları (C#)

Oluşturma başlamadan önce veya derleme tamamlandıktan sonra çalışan komutlar belirtmek için derleme olaylarını kullanma. Derleme olayları, yalnızca derlemenin yapı işleminde bu noktaları başarıyla ulaşırsa yürütülür.

Bir proje oluşturulduğunda, derleme öncesi olayları adlı bir dosyaya eklenen *PreBuildEvent.bat* ve derleme sonrası olayları adlı bir dosya eklendiğinde *PostBuildEvent.bat*. Hata denetimini sağlamak istiyorsanız, kendi hata denetimi komutları, yapı adımlarını ekleyin.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Derleme öncesi ve sonrası derleme olayları belirtme

### <a name="to-specify-a-build-event"></a>Derleme olayı belirtmek için

1.  İçinde **Çözüm Gezgini**, derleme olayı belirtmek istediğiniz projeyi seçin.

2.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.

3.  Seçin **Build Events** sekmesi.

4.  İçinde **derleme öncesi olay komut satırı** kutusunda, derleme olay sözdizimini belirtin.

    > [!NOTE]
    > Derleme öncesi olayları, projenin güncel olduğundan ve hiçbir derlemenin tetiklenmesinin çalıştırmayın.

5.  İçinde **derleme sonrası olay komut satırı** kutusunda, derleme olay sözdizimini belirtin.

    > [!NOTE]
    > Ekleme bir `call` deyiminden önce çalışan tüm derleme sonrası komutlar *.bat* dosyaları. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

6.  İçinde **oluşturma sonrası olayı çalıştırılsın** kutusunda, hangi derleme sonrası olay çalıştırmak için koşullar altında belirtin.

    > [!NOTE]
    > Uzun söz dizimi eklemek ya da seçmek için herhangi bir makrolarından derleme [derleme öncesi olay/derleme sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), üç nokta düğmesini (**...** ) düzenleme kutusu görüntülenecek.

     Yapı olay sözdizimi geçerli bir komut isteminde veya bir komut içerebilir bir *.bat* dosya. Tarafından bir toplu iş dosyası adı gelmelidir `call` tüm komutlar yürütülür emin olmak için.

    > [!NOTE]
    > Derleme öncesi veya derleme sonrası olay başarıyla tamamlanmazsa, başarılı bir eylem gösteren bir ile dışında sıfır (0), çıkış kodu olay eyleminizi sağlayarak derleme sonlandırabilirsiniz.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Örnek: derleme sonrası olay kullanarak bildirim bilgileri değiştirmek üzere nasıl

Aşağıdaki yordamı kullanarak uygulama bildiriminde minimum işletim sistemi sürümü ayarlamak gösterilmiştir bir *.exe* bir derleme sonrası olay çağrılan komut ( *. exe.manifest* dosyası Proje dizini). En düşük işletim sistemi sürümünü 4.10.0.0 gibi dört kısımlı bir sayıdır. Bunu yapmak için komut değişir `<dependentOS>` bildiriminin:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir .exe komutu oluşturmak için

1. Komut için bir konsol uygulaması oluşturun. Gelen **dosya** menüsünde **yeni**ve ardından **proje**.

2. İçinde **yeni proje** iletişim kutusunda **Visual C#**, tıklayın **Windows**ve ardından **konsol uygulaması** şablonu. Projeyi adlandırın `ChangeOSVersionCS`.

3. İçinde *Program.cs*, diğer aşağıdaki satırı ekleyin `using` deyimini dosyanın üst:

   ```csharp
   using System.Xml;
   ```

4. İçinde `ChangeOSVersionCS` ad alanını Değiştir `Program` sınıf uygulamasını aşağıdaki kod ile:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function will set the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest).
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

    Komut iki bağımsız değişkeni alır: uygulama bildirimi yolunu (diğer bir deyişle, hangi yapı işlemi oluşturur, bildirim genellikle klasör *Projectname.publish*) ve yeni işletim sistemi sürümü.

5. Projeyi oluşturun. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

6. Kopyalama *.exe* gibi bir dizine dosya *C:\TEMP\ChangeOSVersionVB.exe*.

   Ardından, uygulama bildirimini değiştirmek için bu komutu bir derleme sonrası olay çağırın.

### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir derleme sonrası olay çağırmak için

1.  Yayımlanacak proje için bir Windows uygulaması oluşturun. Gelen **dosya** menüsünde **yeni**ve ardından **proje**.

2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** , tıklayın **Windows Masaüstü**ve ardından **Windows Forms uygulaması** şablonu. Projeyi adlandırın `CSWinApp`.

3.  Seçilen proje **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.

4.  İçinde **Proje Tasarımcısı**, bulun **Yayımla** sayfasında ve ayarlayın **konumu yayımlama** için *C:\TEMP*.

5.  Tıklayarak projeyi yayımlama **Şimdi Yayımla**.

     Bildirim dosyası oluşturulmuş ve koymak *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Bildirimi görüntülemek için dosyaya sağ tıklayın, **birlikte Aç**seçin **program bir listeden seçim**ve ardından **not defteri**.

     Arama için dosyasında `<osVersionInfo>` öğesi. Örneğin, sürüm olabilir:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6.  İçinde **Proje Tasarımcısı**, tıklayın **Build Events** sekmesine **Düzenle derleme sonrası** düğmesi.

7.  İçinde **derleme sonrası olay komut satırı** aşağıdaki komutu yazın:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Proje oluşturduğunuzda, bu komut uygulama bildiriminde minimum işletim sistemi sürümü için 5.1.2600.0 değiştirin.

     Çünkü `$(TargetPath)` makro oluşturulmasını, yürütülebilir dosyanın tam yolunu ifade `$(TargetPath)` *.manifest* belirtin, oluşturulan uygulama bildirimi *bin* dizin. Yayımlama bu bildirimi daha önce belirlediğiniz yayımlama konumuna kopyalar.

8.  Projeyi yeniden yayımlayın. Git **Yayımla** sayfasında ve tıklayın **Şimdi Yayımla**.

     Bildirim yeniden görüntüleyin. Bildirimi görüntülemek için Yayımla dizinini açın, dosyaya sağ tıklayın, **açın**seçin **program bir listeden seçim**ve ardından **not defteri**.

     Sürüm şöyle olmalıdır:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme olayları sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Derleme öncesi olay/derleme sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Nasıl yapılır: belirtin derleme olayları (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)