---
title: 'Nasıl yapılır: derleme olayları belirtme (C#) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b645d51594cbb507ea0e6bb27a00eea21e73b7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872024"
---
# <a name="how-to-specify-build-events-c"></a>Nasıl Yapılır: Derleme Olayları Belirtme (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oluşturma başlamadan önce veya derleme tamamlandıktan sonra çalışan komutlar belirtmek için derleme olaylarını kullanma. Derleme olayları, yalnızca derlemenin yapı işleminde bu noktaları başarıyla ulaşırsa yürütülür.  
  
 Bir proje oluşturulduğunda, derleme öncesi olayları PreBuildEvent.bat adlı bir dosyaya eklenir ve derleme sonrası olayları PostBuildEvent.bat adlı bir dosyaya eklenir. Hata denetimini sağlamak istiyorsanız, kendi hata denetimi komutları, yapı adımlarını ekleyin.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>Derleme öncesi ve sonrası derleme olayları belirtme  
  
#### <a name="to-specify-a-build-event"></a>Derleme olayı belirtmek için  
  
1.  İçinde **Çözüm Gezgini**, derleme olayı belirtmek istediğiniz projeyi seçin.  
  
2.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
3.  Seçin **Build Events** sekmesi.  
  
4.  İçinde **derleme öncesi olay komut satırı** kutusunda, derleme olay sözdizimini belirtin.  
  
    > [!NOTE]
    >  Derleme öncesi olayları, projenin güncel olduğundan ve hiçbir derlemenin tetiklenmesinin çalıştırmayın.  
  
5.  İçinde **derleme sonrası olay komut satırı** kutusunda, derleme olay sözdizimini belirtin.  
  
    > [!NOTE]
    >  Ekleme bir `call` .bat dosyaları çalıştıran tüm derleme sonrası komutları önce deyimi. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  İçinde **oluşturma sonrası olayı çalıştırılsın** kutusunda, hangi derleme sonrası olay çalıştırmak için koşullar altında belirtin.  
  
    > [!NOTE]
    >  Uzun söz dizimi eklemek ya da seçmek için herhangi bir makrolarından derleme [derleme öncesi olay/derleme sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), üç nokta düğmesini (**...** ) düzenleme kutusu görüntülenecek.  
  
     Yapı olay sözdizimi geçerli bir komut isteminde veya bir .bat dosyası herhangi bir komutu içerebilir. Tarafından bir toplu iş dosyası adı gelmelidir `call` tüm komutlar yürütülür emin olmak için.  
  
     **Not** ön derleme veya derleme sonrası olay başarıyla tamamlanmazsa, başarılı bir eylem gösteren bir ile dışında sıfır (0), çıkış kodu olay eyleminizi sağlayarak derleme sonlandırabilirsiniz.  
  
## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Örnek: Derleme sonrası olay kullanarak bildirim bilgileri değiştirmek üzere nasıl  
 Aşağıdaki yordamda, bir derleme sonrası olay çağrılan bir .exe komutunu kullanarak uygulama bildiriminde en düşük işletim sistemi sürümünü ayarlama işlemi gösterilmektedir (. exe.manifest dosya proje dizininde). En düşük işletim sistemi sürümünü 4.10.0.0 gibi dört kısımlı bir sayıdır. Bunu yapmak için komut değişir `<dependentOS>` bildiriminin:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir .exe komutu oluşturmak için  
  
1. Komut için bir konsol uygulaması oluşturun. Gelen **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda **Visual C#**, tıklayın **Windows**ve ardından **konsol uygulaması** şablonu. Projeyi adlandırın `ChangeOSVersionCS`.  
  
3. Program.cs'ye aşağıdaki satırı ekleyin `using` deyimini dosyanın üst:  
  
   ```  
   using System.Xml;  
   ```  
  
4. İçinde `ChangeOSVersionCS` ad alanını Değiştir `Program` sınıf uygulamasını aşağıdaki kod ile:  
  
   ```  
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
  
    Komut iki bağımsız değişkeni alır: uygulama bildirimi yolunu (derleme işlemi genellikle Projectname.publish bildirimi oluşturur diğer bir deyişle, klasör) ve yeni işletim sistemi sürümü.  
  
5. Projeyi oluşturun. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
6. .Exe dosyası gibi bir dizine kopyalayın `C:\TEMP\ChangeOSVersionVB.exe`.  
  
   Ardından, uygulama bildirimini değiştirmek için bu komutu bir derleme sonrası olay çağırın.  
  
#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir derleme sonrası olay çağırmak için  
  
1.  Yayımlanacak proje için bir Windows uygulaması oluşturun. Gelen **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#**, tıklayın **Windows**ve ardından **Windows Forms uygulaması** şablonu. Projeyi adlandırın `CSWinApp`.  
  
3.  Seçilen proje **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
4.  Proje Tasarımcısı'nda bulmak **Yayımla** sayfasında ve ayarlayın **konumu yayımlama** için `C:\TEMP\`.  
  
5.  Tıklayarak projeyi yayımlama **Şimdi Yayımla**.  
  
     Bildirim dosyası oluşturulmuş ve koymak `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Bildirimi görüntülemek için dosyaya sağ tıklayın, **birlikte Aç**seçin **program bir listeden seçim**ve ardından **not defteri**.  
  
     Arama için dosyasında `<osVersionInfo>` öğesi. Örneğin, sürüm olabilir:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  Proje Tasarımcısı'nda tıklatın **Build Events** sekmesine **Düzenle derleme sonrası** düğmesi.  
  
7.  İçinde **derleme sonrası olay komut satırı** aşağıdaki komutu yazın:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Proje oluşturduğunuzda, bu komut uygulama bildiriminde minimum işletim sistemi sürümü için 5.1.2600.0 değiştirin.  
  
     Çünkü `$(TargetPath)` makro oluşturulmasını, yürütülebilir dosyanın tam yolunu ifade `$(TargetPath)`.manifest bin dizininde oluşturulan uygulama bildirimi belirtin. Yayımlama bu bildirimi daha önce belirlediğiniz yayımlama konumuna kopyalar.  
  
8.  Projeyi yeniden yayımlayın. Git **Yayımla** sayfasında ve tıklayın **Şimdi Yayımla**.  
  
     Bildirim yeniden görüntüleyin. Bildirimi görüntülemek için Yayımla dizinini açın, dosyaya sağ tıklayın, **açın**seçin **program bir listeden seçim**ve ardından **not defteri**.  
  
     Sürüm şöyle olmalıdır:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme olayları sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Derleme öncesi olay/derleme sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Nasıl yapılır: derleme olayları belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)   
 [Derleme ve Oluşturma](../ide/compiling-and-building-in-visual-studio.md)



