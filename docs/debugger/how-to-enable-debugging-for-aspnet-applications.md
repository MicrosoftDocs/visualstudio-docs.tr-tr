---
title: ASP.NET uygulamaları için hata ayıklamayı | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/18
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 41da2eb360bac4c50f85bd908f980f5ee3c1d141
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813433"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio'da ASP.NET veya ASP.NET Core uygulamalarının hatalarını ayıklama

Visual Studio ASP.NET ve ASP.NET Core uygulamalarında hata ayıklaması yapabilirsiniz. İşlem, ASP.NET ve ASP.NET Core arasında farklılık gösterir ve olup, IIS Express veya yerel bir IIS sunucusunda çalıştırın. 

>[!NOTE]
>Aşağıdaki adımları ve ayarlar yalnızca yerel bir sunucuya hata ayıklama uygulamaları için geçerlidir. Hata ayıklama uygulamaları uzak bir IIS sunucusunun kullandığı **iliştirme**ve bu ayarları yok sayar. Daha fazla bilgi ve yönergeler için IIS üzerinde uzaktan hata ayıklama ASP.NET uygulamaları için bkz. [ASP.NET hatalarını uzaktan ayıklama IIS bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) veya [uzaktan uzak bir IIS bilgisayarında ASP.NET Core hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Yerleşik IIS Express sunucusu Visual Studio'ya dahildir. IIS Express ASP.NET ve ASP.NET Core projeleri için varsayılan hata ayıklama sunucusu ve önceden yapılandırılmış. Bu, hata ayıklama ve ilk hata ayıklama ve test için ideal en kolay yoludur. 

Uygulamayı çalıştırmak için yapılandırılmış bir ASP.NET veya ASP.NET Core uygulaması yerel IIS sunucusunda (sürüm 8.0 veya üzeri) hata ayıklaması yapabilirsiniz. Yerel IIS üzerinde hata ayıklamak için aşağıdaki gereksinimleri karşılaması gerekir: 

<a name="iis"></a>
- Seçin **geliştirme zamanı IIS desteğini** Visual Studio'yu yüklerken. (Gerekirse, Visual Studio yükleyiciyi yeniden çalıştırın, seçin **Değiştir**ve bu bileşen ekleyin.)
- Visual Studio, bir yönetici olarak çalıştırıyor olmanız. 
- Yükleme ve IIS, ASP.NET ve/veya ASP.NET Core uygun sürümleri ile doğru şekilde yapılandırın. Daha fazla bilgi ve yönergeler için bkz. [IIS 8.0 kullanarak ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) veya [ana bilgisayar Windows IIS üzerinde ASP.NET Core](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Uygulama hatasız IIS üzerinde çalıştığından emin olun.

## <a name="debug-aspnet-apps"></a>ASP.NET uygulamalarının hatalarını ayıklama 

IIS Express varsayılandır ve önceden yapılandırılmış. Yerel IIS üzerinde hata ayıklama, karşıladığınızdan emin olun [IIS yerel hata ayıklama için gereksinimleri](#iis). 

1. Visual Studio'da ASP.NET projesi seçin **Çözüm Gezgini** tıklatıp **özellikleri** simgesi, tuşuna **Alt**+**Enter**, veya sağ tıklayıp seçin **özellikleri**.
   
1. Seçin **Web** sekmesi.
   
1. İçinde **özellikleri** bölmesi altında **sunucuları**, 
   - IIS Express için seçin **IIS Express** açılır listeden.
   - Yerel IIS için
     1. Seçin **yerel IIS** açılır listeden.
     1. Yanındaki **proje URL'si** alanın, Seç **sanal dizin oluştur**IIS'de uygulamanın kurulumunu henüz ayarlamadıysanız,.
   
1. Altında **hata ayıklayıcıları**seçin **ASP.NET**.
   
   ![ASP.NET hata ayıklayıcı ayarları](media/dbg-aspnet-enable-debugging2.png "ASP.NET hata ayıklayıcı ayarları")
   
1. Kullanım **dosya** > **seçili öğeleri Kaydet** veya **Ctrl**+**S** yaptığınız değişiklikleri kaydedemezsiniz. 
   
1. Projenizde, bir uygulamanın hatalarını ayıklamak için bazı kodlar üzerinde kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırma ayarlandığından emin olun **hata ayıklama**, ve istediğiniz tarayıcıyı görünür **IIS Express (\<tarayıcı adı >)** veya **yerel IIS (\< Tarayıcı adı >)** öykünücü alanında. 
   
1. Hata ayıklamayı başlatmak için seçin **IIS Express (\<tarayıcı adı >)** veya **yerel IIS (\<tarayıcı adı >)** araç çubuğunda, seçin **Start Debugging**gelen **hata ayıklama** tuşuna basın veya menü **F5**. Hata ayıklayıcı kesme noktalarında duraklatır. Hata ayıklayıcı kesme noktaları isabet edilemiyor olup [sorunlarını giderme hata ayıklama](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core uygulamalarında hata ayıklama 

IIS Express varsayılandır ve önceden yapılandırılmış. Yerel IIS üzerinde hata ayıklama, karşıladığınızdan emin olun [IIS yerel hata ayıklama için gereksinimleri](#iis). 

1. Visual Studio'da ASP.NET Core projesi seçin **Çözüm Gezgini** tıklatıp **özellikleri** simgesi, tuşuna **Alt**+**Enter**, veya sağ tıklayıp seçin **özellikleri**.

1. Seçin **hata ayıklama** sekmesi.
   
1. İçinde **özellikleri** bölmesinde, sonraki **profili**, 
   - IIS Express için seçin **IIS Express** açılır listeden.
   - Yerel IIS uygulama adı, açılan listeden seçin veya seçin **yeni**, yeni bir profil adı oluşturun ve seçin **Tamam**.
   
1. Yanındaki **başlatma**, şunlardan birini seçin **IIS Express** veya **IIS** açılır listeden. 
   
1. Emin **tarayıcıyı başlatın** seçilir.
   
1. Altında **ortam değişkenlerini**, emin **ASPNETCORE_ENVIRONMENT** değeriyle varsa **geliştirme**. Aksi takdirde, seçin **Ekle** ve ekleyin.
   
   ![ASP.NET Core hata ayıklayıcısı ayarları](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core hata ayıklayıcısı ayarları")
   
1. Kullanım **dosya** > **seçili öğeleri Kaydet** veya **Ctrl**+**S** yaptığınız değişiklikleri kaydedemezsiniz. 
   
1. Projenizde, bir uygulamanın hatalarını ayıklamak için bazı kodlar üzerinde kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırma ayarlandığından emin olun **hata ayıklama**ve her iki **IIS Express**, ya da yeni IIS profil adı öykünücü alanında görünür. 
   
1. Hata ayıklamayı başlatmak için seçin **IIS Express** veya  **\<IIS profil adı >** araç çubuğunda, seçin **hata ayıklamayı Başlat** gelen **hataayıklama** tuşuna basın veya menü **F5**. Hata ayıklayıcı kesme noktalarında duraklatır. Hata ayıklayıcı kesme noktaları isabet edilemiyor olup [sorunlarını giderme hata ayıklama](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Hata ayıklama sorunlarını giderme

Yerel IIS hata ayıklama, kesme noktasına ilerleme olamaz, gidermek için bu adımları izleyin. 

1. IIS web uygulamasını başlatmak ve doğru şekilde çalıştığından emin olun. Çalışan web uygulaması bırakın.
   
2. Visual Studio'dan seçin **hata ayıklama > iliştirme** veya basın **Ctrl**+**Alt**+**P**, ve ASP.NET veya ASP.NET Core işleme bağlanın (genellikle **w3wp.exe** veya **dotnet.exe**). Daha fazla bilgi için [iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md) ve [ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md).

Bağlanmak ve kullanarak, kesme noktasına isabet varsa **iliştirme**, ancak kullanarak **hata ayıklama** > **hata ayıklamayı Başlat** veya **F5**, bir proje özelliklerinde büyük olasılıkla hatalı bir ayardır. HOSTS dosyası kullanıyorsanız, aynı zamanda doğru bir şekilde yapılandırıldığından emin olun.

## <a name="configure-debugging-in-the-webconfig-file"></a>Web.config dosyasında hata ayıklamayı Yapılandır  

ASP.NET projeleri *web.config* dosyaları varsayılan olarak, hata ayıklama ayarları dahil olmak üzere iki uygulama yapılandırması ve başlatma bilgiler içerir. *Web.config* dosyaları yapılandırılmalıdır doğru hata ayıklama için. **Özellikleri** önceki bölümlerde güncelleştirme ayarlarında *web.config* dosyaları, ancak de yapılandırabilirsiniz bunları el ile. 

> [!NOTE]
> ASP.NET Core projeleri başlangıçta yok *web.config* kullanın ancak dosyalar *appsettings.json* ve *launchSettings.json* dosyaları uygulama yapılandırması ve başlatma bilgiler. Uygulama dağıtımı oluşturur bir *web.config* dosya veya dosyalar projesinde, ancak genellikle hata ayıklama bilgisi içermez.

> [!TIP]
> Dağıtım işleminizin güncelleştirebilir *web.config* ayarları, bu nedenle hata ayıklama denemeden önce emin olun *web.config* hata ayıklama için yapılandırılır.
  
**El ile yapılandırmak için bir *web.config* hata ayıklama için dosya:**

1. Visual Studio'da ASP.NET proje açmak *web.config* dosya.  
  
2. *Web.config* bir XML dosyası, yüzden etiketlerle işaretlenmiş iç içe yerleştirilmiş bölümler içerir. Bulun `configuration/system.web/compilation` bölümü. (Varsa `compilation` öğesi mevcut değil, oluşturun.)
  
3. Emin olun `debug` özniteliğini `compilation` ayarlanır `true`. (Varsa `compilation` öğesi içermediğinden bir `debug` özniteliği, ekleyin ve değerini `true`.) 
  
   Yerel IIS yerine varsayılan IIS Express sunucusu kullanıyorsanız, emin `targetFramework` öznitelik değeri `compilation` IIS sunucusundaki framework öğeyle eşleşir.
  
   `compilation` Öğesinin *web.config* dosya, aşağıdaki örnekteki gibi görünmelidir:

   > [!NOTE]
   > Bu örnekte, bir kısmi *web.config* dosya. Genellikle ek XML bölümlerinde vardır `configuration` ve `system.web` öğeleri ve `compilation` öğe ayrıca diğer öznitelikler ve öğeler içerebilir.
  
   ```xml
   <configuration>  
      ...  
      <system.web>  
          <compilation  debug="true"  targetFramework="4.6.1" ... > 
             ...  
          </compilation>  
      </system.web>  
   </configuration>  
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] otomatik olarak herhangi bir değişiklik algıladığında *web.config* dosyaları ve yeni yapılandırma ayarlarını uygular. Bilgisayar ya da değişikliklerin etkili olması IIS sunucusunu yeniden başlatmanız gerekmez.  
  
Bir Web sitesi ile içerebilir birkaç sanal dizinler ile alt dizinleri, *web.config* dosyalarında her biri. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamaları aracılığıyla yapılandırma ayarlarınızı devralır *web.config* URL yolunda daha yüksek düzeylerde dosyaları. Hiyerarşik *web.config* dosyası ayarlarını uygulamak için tüm [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hiyerarşideki bunları aşağıda uygulamalar. Farklı bir yapılandırma ayarı bir *web.config* hiyerarşide daha düşük bir dosya, daha yüksek dosyasındaki ayarları geçersiz kılar.  
  
Örneğin belirtirseniz `debug="true"` içinde <em>www.microsoft.com/aaa/web.config</em>, herhangi bir uygulamada *aaa* klasör veya herhangi bir alt *aaa* bu ayarı devralır Bu uygulamalardan birini kendi ayarı geçersiz kılarsa dışındaki *web.config* dosya.  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>Dosya sistemi kullanılarak hata ayıklama modunda yayımlama

IIS için uygulamaları yayımlamak için farklı yolu vardır. Bu adımlarda, oluşturma ve hata ayıklama dosya sistemi kullanılarak yayımlama profili dağıtma gösterilmektedir. Bunu yapmak için Visual Studio'yu bir yönetici olarak çalıştırıyor olmanız gerekir. 

> [!IMPORTANT]
> Kod veya yeniden değiştirirseniz, yeniden yayımlamak için bu adımları yinelemeniz gerekir. 

1. Visual Studio'da projeye sağ tıklayıp seçin **Yayımla**.

3. Seçin **IIS, FTP, vb.** tıklatıp **Yayımla**.

    ![IIS yayımlama](media/dbg-aspnet-local-iis.png "IIS yayımlama")

4. İçinde **CustomProfile** iletişim için **yayımlama yöntemi**, seçin **dosya sistemi**.

5. İçin **hedef konum**seçin **Gözat** (**...** ).
   
   - ASP.NET, seçin **yerel IIS**uygulama için oluşturduğunuz Web sitesini seçin ve ardından **açık**.
     
     ![IIS'ye ASP.NET Yayımlama](media/dbg-aspnet-local-iis1.png "IIS'ye ASP.NET Yayımlama")
     
   - ASP.NET Core için seçin **dosya sistemi**, uygulama için ayarlayabilir ve ardından klasörü seçin **açık**.

1. Seçin **sonraki**. 

1. Altında **yapılandırma**seçin **hata ayıklama** açılır listeden.

1. Seçin **Kaydet**.

1. İçinde **Yayımla** iletişim kutusunda, emin **CustomProfile** (veya yeni oluşturduğunuz profil adı) görünür ve **LastUsedBuildConfiguration** ayarlanır  **Hata ayıklama**. 

1. Seçin **yayımlama**.

    ![IIS yayımlama](media/dbg-aspnet-local-iis-select-site.png "IIS yayımlama")

> [!IMPORTANT]
> Hata ayıklama modu, uygulamanızın performansını önemli ölçüde azaltır. En iyi performans için ayarlanmış `debug="false"` içinde *web.config* ve bir üretim uygulaması dağıttığınızda veya performans ölçümleri gerçekleştirmeden bir yayın yapısı belirtmek.  

## <a name="see-also"></a>Ayrıca bkz.  
[ASP.NET hata ayıklama: sistem gereksinimleri](aspnet-debugging-system-requirements.md)   
[Nasıl yapılır: bir kullanıcı hesabı altında çalışan işlemini çalıştırma](how-to-run-the-worker-process-under-a-user-account.md)   
[Nasıl yapılır: ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md)   
[Dağıtılmış web uygulamalarında hata ayıklama](debugging-deployed-web-applications.md)   
[İzlenecek yol: web formunda hata ayıklama](walkthrough-debugging-a-web-form.md)   
[Nasıl yapılır: ASP.NET özel durumlarında hata ayıklama](how-to-debug-aspnet-exceptions.md)   
[Web uygulamalarında hata ayıklama: hatalar ve sorun giderme](debugging-web-applications-errors-and-troubleshooting.md)
  
