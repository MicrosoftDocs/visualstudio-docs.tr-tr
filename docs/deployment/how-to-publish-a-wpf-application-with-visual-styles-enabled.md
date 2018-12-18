---
title: 'Nasıl yapılır: görsel stiller etkinken WPF uygulaması yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dc45c624d44ed550fb491fc57638ba033090346
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388114"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Nasıl yapılır: görsel stiller etkinken WPF uygulaması yayımlama
Görsel stiller, kullanıcı tarafından seçilen tema göre değiştirmek için ortak denetimlerin görünümünü etkinleştirin. El ile etkinleştirmeniz gerekir, böylece varsayılan olarak, Windows Presentation Foundation (WPF) uygulamaları için görsel stillerin etkin değil. Ancak, bir WPF uygulaması için görsel stilleri etkinleştirme ve ardından çözüm yayımlama bir hataya neden olur. Bu konu, bu hatayı ve görsel stiller etkinken WPF uygulaması yayımlama işlemi açıklar. Görsel stiller hakkında daha fazla bilgi için bkz: [görsel stilleri genel bakış](/windows/desktop/Controls/visual-styles-overview). Hata iletisi hakkında daha fazla bilgi için bkz. [ClickOnce Dağıtımları içinde belirli hataları giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Hatayı çözün ve Çözümü yayımlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
- [Görsel stiller etkinken çözüm yayımlama](#publish-the-solution-without-visual-styles-enabled).  
  
- [Bir bildirim dosyası oluşturma](#create-a-manifest-file).  
  
- [Bildirim dosyası yayımlanmış çözüm yürütülebilir dosyasına katıştırma](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).  
  
- [Uygulama ve dağıtım bildirimlerini imzalamak](#sign-the-application-and-deployment-manifests).  
  
  Ardından, yayımlanan dosyaların son kullanıcıların uygulamayı yüklemek istediğiniz konuma taşıyabilirsiniz.  
  
##  <a name="publish-the-solution-without-visual-styles-enabled"></a>Görsel stiller etkinken çözüm yayımlama  
  
1.  Projenizi görsel stiller etkinken olmadığından emin olun. İlk olarak, projenizin bildirim dosyası için aşağıdaki XML denetleyin. Ardından, XML varsa, XML açıklama etiketi ile alın.  
  
     Görsel stilleri varsayılan olarak etkin değildir.  
  
    ```xml  
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```  
  
     Aşağıdaki yordamlar projenizle ilişkili bildirim dosyası açmak nasıl gösterir.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Visual Basic projesinde bildirim dosyasını açmak için  
  
    1.  Menü çubuğunda, **proje**, *ProjectName* **özellikleri**burada *ProjectName* WPF projenizin adıdır.  
  
         WPF projeniz için özellik sayfaları görünür.  
  
    2.  Üzerinde **uygulama** sekmesini, **Windows ayarlarını görüntüleme**.  
  
         App.manifest dosyası açılır **Kod Düzenleyicisi**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Bir C# projesinde bildirim dosyasını açmak için  
  
    1.  Menü çubuğunda, **proje**, *ProjectName* **özellikleri**burada *ProjectName* WPF projenizin adıdır.  
  
         WPF projeniz için özellik sayfaları görünür.  
  
    2.  Üzerinde **uygulama** sekmesinde, bildirim alanında görünen adını not edin. Projenizle ilişkili bildirim adıdır.  
  
        > [!NOTE]
        >  Varsa **ekleme bildirimi varsayılan ayarlarla** veya **uygulama bildirimi olmadan oluşturma** görsel stillerin etkin değil bildirim alanında görüntülenir. Bildirim alanında bildirim dosyasının adı varsa, bu yordamdaki bir sonraki adıma geçin.  
  
    3.  İçinde **Çözüm Gezgini**, seçin **tüm dosyaları göster**.  
  
         Bu düğme, hariç tutulanlar ve normalde gizli olanlar dahil olmak üzere tüm proje öğeleri gösterir. Bildirim dosyası bir proje öğesi görünür.  
  
2.  Derleme ve çözümünüzü yayımlayın. Çözüm yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="create-a-manifest-file"></a>Bir bildirim dosyası oluşturma  
  
1.  Aşağıdaki XML bir not defteri dosyasına yapıştırın.  
  
     Bu XML görsel stilleri destekleyen denetimleri içeren derlemeyi açıklar.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0" 
        xmlns="urn:schemas-microsoft-com:asm.v1" 
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" 
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" 
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```  
  
2.  Not Defteri'nde **dosya**ve ardından **Kaydet**.  
  
3.  İçinde **Kaydet** iletişim kutusundaki **farklı kaydetme türü** aşağı açılan listesinden **tüm dosyaları**.  
  
4.  İçinde **dosya adı** kutusunda, dosyayı adlandırın ve ekleme *.manifest* dosya adının sonuna. Örneğin: *themes.manifest*.  
  
5.  Seçin **klasörlere Gözat** düğmesi, herhangi bir klasör seçin ve ardından **Kaydet**.  
  
    > [!NOTE]
    >  Kalan yordamlar bu dosyanın adı olduğunu varsayar *themes.manifest* ve dosya için kaydedilen *C:\temp* bilgisayarınızda dizin.  
  
## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Bildirim dosyası yayımlanmış çözüm yürütülebilir dosyasına katıştırma  
  
1. Açık **Visual Studio komut istemi**.  
  
    Nasıl açılacağı hakkında daha fazla bilgi için **Visual Studio komut istemi**, bkz: [komut istemleri](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
   > [!NOTE]
   >  Kalan adımları, çözümünüzü hakkında aşağıdaki varsayımlar:  
   > 
   > - Çözüm adı **MyWPFProject**.  
   >   -   Çözüm, şu dizinde bulunur: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
   > 
   >   Çözüm şu dizine yayımlanır: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
   >   -   En son sürümü yayımlanan uygulama dosyalarını şu dizinde bulunur: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
   > 
   >   Adını veya yukarıda açıklanan dizin konumları kullanın gerekmez. Yukarıda açıklanan konumları ve adını yalnızca çözümünüzü yayımlamak için gerekli adımları göstermek için kullanılır.  
  
2. Komut isteminde yolu yayımlanan uygulama dosyalarının en son sürümünü içeren dizine geçin. Aşağıdaki örnek, bu adım gösterir.  
  
   ```cmd  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. Komut isteminde, bildirim dosyasını uygulama yürütülebilir dosyasına eklemek için aşağıdaki komutu çalıştırın.  
  
   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
   ```  
  
## <a name="sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini imzalama  
  
1. Komut isteminde kaldırmak için aşağıdaki komutu çalıştırın *.deploy* yürütülebilir dosyayı geçerli dizinde uzantı.  
  
   ```cmd  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  Bu örnek yalnızca bir dosya olan varsayar *.deploy* dosya uzantısı. Bu dizinde sahip tüm dosyaları yeniden adlandırma emin *.deploy* dosya uzantısı.  
  
2. Komut isteminde, uygulama bildirimini imzalayın için aşağıdaki komutu çalıştırın.  
  
   ```cmd  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  Bu örnek bildirim kullanarak oturum varsayar *.pfx* proje dosyası. Bildirimi imzalamak değil, atlayabilirsiniz `-cf` Bu örnekte kullanılan parametre. Parola gerektiren bir sertifika bildirimine kaydoluyorsanız belirtin `-password` seçeneği (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3. Komut isteminde eklemek için aşağıdaki komutu çalıştırın *.deploy* bu yordamın önceki bir adımda yeniden adlandırılmış dosya adı uzantısı.  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  Bu örnek yalnızca bir dosya varsayar sahip bir *.deploy* dosya uzantısı. Daha önce olduğu bu dizindeki tüm dosyaları yeniden adlandırma emin *.deploy* dosya adı uzantısı.  
  
4. Komut isteminde, dağıtım bildirimini imzalamak için aşağıdaki komutu çalıştırın.  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  Bu örnek bildirim kullanarak oturum varsayar *.pfx* proje dosyası. Bildirimi imzalamak değil, atlayabilirsiniz `-cf` Bu örnekte kullanılan parametre. Parola gerektiren bir sertifika bildirimine kaydoluyorsanız belirtin `-password` seçeneği, bu örnekte olduğu gibi:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
   Bu adımları gerçekleştirdikten sonra yayımlanan dosyaları son kullanıcıların uygulamayı yüklemek istediğiniz konuma taşıyabilirsiniz. Çözüm sık sık güncelleştirme yapmak istiyorsanız, bir komut dosyasına bu komutları taşıyabilir ve her seferinde yeni bir sürüm yayımlayın betiği çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

-[ClickOnce Dağıtımları içinde belirli hataları giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Görsel stiller genel bakış](/windows/desktop/Controls/visual-styles-overview)
- [Görsel stilleri etkinleştirme](/windows/desktop/Controls/cookbook-overview)
- [Komut İstemleri](/dotnet/framework/tools/developer-command-prompt-for-vs)
