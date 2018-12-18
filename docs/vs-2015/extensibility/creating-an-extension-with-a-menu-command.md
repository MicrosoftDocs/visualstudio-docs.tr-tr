---
title: Bir menü komutuyla uzantı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb99149a7b617d8e48e036d9e706e5e1c0a6169b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779313"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Bir Menü Komutuyla Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Not Defteri başlatan bir menü komutuyla uzantı oluşturma işlemini gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Bir menü komutu oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun **FirstMenuCommand**. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Projeyi açtığında, adlı bir özel komut öğesi şablonu ekleme **FirstCommand**. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **özel komut**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme **FirstCommand.cs**.  
  
3.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
     Visual Studio'nun deneysel örneğinde görünür. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örneğinde](../extensibility/the-experimental-instance.md).  
  
4.  Deneysel örneğinde açın **araçları / Uzantılar ve güncelleştirmeler** penceresi. Görmelisiniz **FirstMenuCommand** uzantıyı şurada. (Açarsanız **Uzantılar ve güncelleştirmeler** Visual Studio, çalışma örneğinde göremezsiniz **FirstMenuCommand**).  
  
     Artık Git **Araçları** Deneysel örneğinin menü. Görmelisiniz **çağırma FirstCommand** komutu. Bu noktada yalnızca "içinde FirstCommandPackage FirstMenuCommand.FirstCommand.MenuItemCallback()" ifadesini içeren bir ileti kutusu getirir. Sonraki bölümde bu komut aslında Not defteri başlangıç nasıl göreceğiz.  
  
## <a name="changing-the-menu-command-handler"></a>Menü komut işleyici değiştirme  
 Şimdi komut işleyicinin Not Defteri'ni başlatın güncelleştirelim.  
  
1.  Hata ayıklamayı Durdur ve çalışma Örneğiniz için Visual Studio geri dönün. FirstCommand.cs dosyasını açın ve aşağıdaki deyimi kullanarak:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Özel FirstCommand Oluşturucusu bulun. Burada komutu için komut hizmeti ölçekledikçe ve komut işleyici belirtilen budur. Komut işleyici adı StartNotepad için aşağıdaki gibi değiştirin:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Remove MenuItemCallback yöntemi ve Not Defteri yalnızca başlayacak bir StartNotepad yöntemi ekleyin:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Şimdi deneyin. Ne zaman projesinde hata ayıklamaya başlama ve tıklayın **Araçlar / çağırma FirstCommand**, Not Defteri gündeme örneğini görmeniz gerekir.  
  
     Bir örneğini kullanabilir <xref:System.Diagnostics.Process> herhangi bir yürütülebilir dosya, yalnızca not defteri çalıştırmak için sınıf. Örneğin, calc.exe ile deneyin.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Deneysel ortamı temizleniyor  
 Birden fazla uzantı geliştirme veya yalnızca uzantı kodunuzu farklı sürümleriyle sonuçlarını araştırma, Deneysel ortamınızı, gerektiği gibi çalışmayı durdurabilir. Bu durumda, sıfırlama betiği çalıştırmanız gerekir. Çağrıldığı **Visual Studio 2015 Deneysel örneğini sıfırlama**, ve Visual Studio SDK'ın bir parçası olarak sunulur. Baştan başlamak üzere bu betik Deneysel ortamından uzantılarınızı için tüm başvuruları kaldırır.  
  
 Bu betik iki yoldan biriyle alabilirsiniz:  
  
1.  Masaüstü'nden Bul **Visual Studio 2015 Deneysel örneğini sıfırlama**.  
  
2.  Komut satırından şu komutu çalıştırın:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Uzantınızı dağıtmak  
 İstediğiniz gibi çalışan aracı uzantınızı olduğuna göre arkadaşlarınız ve iş arkadaşları ile paylaşma hakkında düşünmek için zaman var. Visual Studio 2015 yüklü sahip oldukları sürece bu kolay olmasıdır. Yapmanız gereken şey bunları derlediğiniz .vsix dosyasını gönderin. (Yayın modunda oluşturduğunuzdan emin olun.)  
  
 Bu uzantı için .vsix dosyasını FirstMenuCommand bin dizininde bulabilirsiniz. Özellikle, sürüm yapılandırmasını geliştirdim varsayıldığında, onu olacaktır:  
  
 **\<Kod dizini > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Uzantıyı yüklemek için Visual Studio tüm açık örneklerini kapatın ve ardından getirir .vsix dosyasını çift tıklatın arkadaşınız gereken **VSIX yükleyicisi**. Dosyalar kopyalanır **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** dizin.  
  
 Arkadaş Visual Studio'yu yeniden getirirse, kendisinin FirstMenuCommand uzantısı'nda bulabilirsiniz **araçları / Uzantılar ve güncelleştirmeler**. He gidebilirsiniz **Uzantılar ve güncelleştirmeler** kaldırın veya uzantı çok devre dışı.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda Visual Studio uzantısı ile neler yapabileceğinizi yalnızca küçük bir bölümün göstermiştir. Visual Studio uzantıları ile gerçekleştirebileceğiniz diğer (makul kolay) işlemlerden kısa bir listesi aşağıda verilmiştir:  
  
1. Basit bir menü komutu ile pek çok şey yapabilirsiniz:  
  
   1.  Kendi simgesi ekleyin: [menü komutları için simgeler ekleme](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  Menü komutunun metnini değiştirme: [menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  Komut menüsünde bir kısayol eklemek: [menü öğelerine klavye kısayolları bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Farklı türde komutlar, menüler ve araç çubuklarını ekleme: [genişletme menüler ve komutlar](../extensibility/extending-menus-and-commands.md)  
  
3. Yerleşik Visual Studio araç pencerelerini genişletme ve araç pencerelerini Ekle: [genişletme ve aracı Windows özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. IntelliSense, kod önerileri ekleyebilir ve kod düzenleyicileri mevcut diğer özellikleri: [düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Uzantınız için seçenekleri ve özellik sayfaları ve kullanıcı ayarlarını ekleyin: [genişletme özellikleri ve özellik penceresini](../extensibility/extending-properties-and-the-property-window.md) ve [genişletme kullanıcı ayarları ve seçenekleri](../extensibility/extending-user-settings-and-options.md)  
  
   Yeni türde bir proje oluşturma gibi daha fazla iş, diğer tür uzantıların gerektirir ([genişletme projeleri](../extensibility/extending-projects.md)), yeni türde bir düzenleyici oluşturma ([oluşturma özel düzenleyiciler ve tasarımcılar](../extensibility/creating-custom-editors-and-designers.md)), veya uzantınızı bir yalıtılmış Kabuğu'nda Uygulama: [Visual Studio yalıtılmış Kabuğu](../extensibility/visual-studio-isolated-shell.md)

