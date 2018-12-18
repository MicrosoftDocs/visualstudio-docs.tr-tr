---
title: 'Nasıl yapılır: görsel stiller etkinken WPF uygulaması yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f03dc4ea85fe0f44ea2253da9544ace9b0068abc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922477"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Nasıl yapılır: Görsel Stiller Etkinken WPF Uygulaması Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görsel stiller, kullanıcı tarafından seçilen tema göre değiştirmek için ortak denetimlerin görünümünü etkinleştirin. El ile etkinleştirmeniz gerekir, böylece varsayılan olarak, Windows Presentation Foundation (WPF) uygulamaları için görsel stillerin etkin değil. Ancak, bir WPF uygulaması için görsel stilleri etkinleştirme ve ardından çözüm yayımlama bir hataya neden olur. Bu konu, bu hatayı ve görsel stiller etkinken WPF uygulaması yayımlama işlemi açıklar. Görsel stiller hakkında daha fazla bilgi için bkz: [görsel stilleri genel bakış](http://msdn.microsoft.com/en-us/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Hata iletisi hakkında daha fazla bilgi için bkz. [ClickOnce Dağıtımları içinde belirli hataları giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Hatayı çözün ve Çözümü yayımlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
- [Görsel stiller etkinken çözüm yayımlama](#BKMK_publishsolwovs).  
  
- [Bir bildirim dosyası oluşturma](#BKMK_CreateManifest).  
  
- [Bildirim dosyası yayımlanmış çözüm yürütülebilir dosyasına katıştırma](#BKMK_embedmanifest).  
  
- [Uygulama ve dağıtım bildirimlerini imzalamak](#BKMK_signappdeplyman).  
  
  Ardından, yayımlanan dosyaların son kullanıcıların uygulamayı yüklemek istediğiniz konuma taşıyabilirsiniz.  
  
##  <a name="BKMK_publishsolwovs"></a> Görsel stiller etkinken çözüm yayımlama  
  
1.  Projenizi görsel stiller etkinken olmadığından emin olun. İlk olarak, projenizin bildirim dosyası için aşağıdaki XML denetleyin. Ardından, XML varsa, XML açıklama etiketi ile alın.  
  
     Görsel stilleri varsayılan olarak etkin değildir.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Aşağıdaki yordamlar projenizle ilişkili bildirim dosyası açmak nasıl gösterir.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Visual Basic projesinde bildirim dosyasını açmak için  
  
    1.  Menü çubuğunda, **proje**, _ProjectName_**özellikleri**burada *ProjectName* WPF projenizin adıdır.  
  
         WPF projeniz için özellik sayfaları görünür.  
  
    2.  Üzerinde **uygulama** sekmesini, **Windows ayarlarını görüntüleme**.  
  
         App.manifest dosyası açılır **Kod Düzenleyicisi**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Bir C# projesinde bildirim dosyasını açmak için  
  
    1.  Menü çubuğunda, **proje**, _ProjectName_**özellikleri**burada *ProjectName* WPF projenizin adıdır.  
  
         WPF projeniz için özellik sayfaları görünür.  
  
    2.  Üzerinde **uygulama** sekmesinde, bildirim alanında görünen adını not edin. Projenizle ilişkili bildirim adıdır.  
  
        > [!NOTE]
        >  Varsa **ekleme bildirimi varsayılan ayarlarla** veya **uygulama bildirimi olmadan oluşturma** görsel stillerin etkin değil bildirim alanında görüntülenir. Bildirim alanında bildirim dosyasının adı varsa, bu yordamdaki bir sonraki adıma geçin.  
  
    3.  İçinde **Çözüm Gezgini**, seçin **tüm dosyaları göster** ().  
  
         Bu düğme, hariç tutulanlar ve normalde gizli olanlar dahil olmak üzere tüm proje öğeleri gösterir. Bildirim dosyası bir proje öğesi görünür.  
  
2.  Derleme ve çözümünüzü yayımlayın. Çözüm yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Bir bildirim dosyası oluşturma  
  
1.  Aşağıdaki XML bir not defteri dosyasına yapıştırın.  
  
     Bu XML görsel stilleri destekleyen denetimleri içeren derlemeyi açıklar.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Not Defteri'nde **dosya**ve ardından **Kaydet**.  
  
3.  İçinde **Kaydet** iletişim kutusundaki **farklı kaydetme türü** aşağı açılan listesinden **tüm dosyaları**.  
  
4.  İçinde **dosya adı** kutusunda, dosyayı adlandırın ve ekleme **.manifest** dosya adının sonuna. Örneğin: **themes.manifest**.  
  
5.  Seçin **klasörlere Gözat** düğmesi, herhangi bir klasör seçin ve ardından **Kaydet**.  
  
    > [!NOTE]
    >  Kalan yordamlar bu dosyanın adı olduğunu varsayar **themes.manifest** ve dosyayı bilgisayarınızda C:\temp dizinine kaydedilir.  
  
##  <a name="BKMK_embedmanifest"></a> Bildirim dosyası yayımlanmış çözüm yürütülebilir dosyasına katıştırma  
  
1. Açık **Visual Studio komut istemi**.  
  
    Nasıl açılacağı hakkında daha fazla bilgi için **Visual Studio komut istemi**, bkz: [komut istemleri](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).  
  
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
  
   ```  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. Komut isteminde, bildirim dosyasını uygulama yürütülebilir dosyasına eklemek için aşağıdaki komutu çalıştırın.  
  
   ```  
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
   ```  
  
##  <a name="BKMK_signappdeplyman"></a> Uygulama ve dağıtım bildirimlerini imzalama  
  
1. Komut isteminde kaldırmak için aşağıdaki komutu çalıştırın `.deploy` yürütülebilir dosyayı geçerli dizinde uzantı.  
  
   ```  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  Bu örnek yalnızca bir dosya olan varsayar `.deploy` dosya uzantısı. Bu dizinde sahip tüm dosyaları yeniden adlandırma emin `.deploy` dosya uzantısı.  
  
2. Komut isteminde, uygulama bildirimini imzalayın için aşağıdaki komutu çalıştırın.  
  
   ```  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  Bu örnek bildirim kullanarak oturum varsayar `.pfx` proje dosyası. Bildirimi imzalamak değil, atlayabilirsiniz `–cf` Bu örnekte kullanılan parametre. Parola gerektiren bir sertifika bildirimine kaydoluyorsanız belirtin `–password` seçeneği (`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`).  
  
3. Komut isteminde eklemek için aşağıdaki komutu çalıştırın `.deploy` bu yordamın önceki bir adımda yeniden adlandırılmış dosya adı uzantısı.  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  Bu örnek yalnızca bir dosya varsayar sahip bir `.deploy` dosya uzantısı. Daha önce olduğu bu dizindeki tüm dosyaları yeniden adlandırma emin `.deploy` dosya adı uzantısı.  
  
4. Komut isteminde, dağıtım bildirimini imzalamak için aşağıdaki komutu çalıştırın.  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  Bu örnek bildirim kullanarak oturum varsayar `.pfx` proje dosyası. Bildirimi imzalamak değil, atlayabilirsiniz `–cf` Bu örnekte kullanılan parametre. Parola gerektiren bir sertifika bildirimine kaydoluyorsanız belirtin `–password` seçeneği, bu örnekte olduğu gibi:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`.  
  
   Bu adımları gerçekleştirdikten sonra yayımlanan dosyaları son kullanıcıların uygulamayı yüklemek istediğiniz konuma taşıyabilirsiniz. Çözüm sık sık güncelleştirme yapmak istiyorsanız, bir komut dosyasına bu komutları taşıyabilir ve her seferinde yeni bir sürüm yayımlayın betiği çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtımları içinde belirli hataları giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Görsel stiller genel bakış](http://msdn.microsoft.com/en-us/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Komut İstemleri](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)



