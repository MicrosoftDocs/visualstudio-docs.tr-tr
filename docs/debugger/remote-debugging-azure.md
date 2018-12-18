---
title: Uzaktan hata ayıklama, IIS ve Azure üzerinde ASP.NET Core | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 821da7c5d131acea62e944055ec6c450e4bc5154
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101114"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Uzaktan hata ayıklama Visual Studio 2017'de azure'da IIS üzerinde ASP.NET Core

Bu kılavuz, ayarlayın ve Visual Studio 2017 ASP.NET Core uygulamasını yapılandırma, Azure kullanılarak IIS'ye dağıtma ve Visual Studio'dan uzak hata ayıklayıcıyı iliştirmek açıklanmaktadır.

Azure'da uzaktan hata ayıklama için önerilen yöntem, senaryoya bağlıdır:

* Azure App Service'te ASP.NET Core hata ayıklamak için bkz: [Snapshot Debugger'ı kullanarak hata ayıklama Azure uygulamaları](../debugger/debug-live-azure-applications.md). Önerilen yöntem budur.
* ASP.NET Core, Azure App Service'nın daha geleneksel hata ayıklama özellikleri kullanarak hata ayıklama için bu konudaki adımları izleyin (bakın [uzaktan hata ayıklama üzerinde Azure App Service'te](#remote_debug_azure_app_service)).

    Bu senaryoda, uygulamanızı Visual Studio'dan azure'a dağıtmanız gerekir ancak el ile yüklemek veya IIS veya uzaktan hata ayıklayıcı (Bu bileşenlerin noktalı çizgiler ile temsil edilir), aşağıdaki çizimde gösterildiği gibi yapılandırmak gerekmez.

    ![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Azure VM'de IIS hata ayıklama için bu konudaki adımları izleyin (bakın [Azure sanal makinesinde uzaktan hata ayıklama](#remote_debug_azure_vm)). Bu özelleştirilmiş bir IIS yapılandırması kullanmanıza olanak tanır, ancak Kurulum ve dağıtım adımları daha karmaşıktır.

    Bir Azure VM için uygulamanızı Visual Studio'dan azure'a dağıtmanız gerekir ve ayrıca IIS rolünü ve uzaktan hata ayıklayıcı, el ile yüklemek aşağıdaki çizimde gösterildiği gibi gerekir.

    ![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Service fabric'te ASP.NET Core hata ayıklamak için bkz: [uzak bir Service Fabric uygulamasında hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Bu öğreticideki adımları tamamladıktan sonra oluşturduğunuz Azure kaynaklarını silmek istediğinizden emin olun. Gereksiz geçmeyecekseniz ücretlendirmeden kaçınmak bu şekilde.


### <a name="requirements"></a>Gereksinimler

Bir proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmiyor. Ülkeler yüksek gecikme süresi veya çevirmeli, Internet gibi düşük bant genişliği bağlantı üzerinden veya Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya edilemeyecek kadar yavaş. Gereksinimlerinin tam listesi için bkz. [gereksinimleri](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Visual Studio 2017 bilgisayar üzerinde ASP.NET Core uygulaması oluşturun 

1. Yeni bir ASP.NET Core uygulaması oluşturun. (Seçin **Dosya > Yeni > Proje**, ardından **Visual C# > Web > ASP.NET Core Web uygulaması**).

    İçinde **ASP.NET Core** şablonları bölümünden **Web uygulaması**.

2. Emin olun **ASP.NET Core 2.0** seçildiğinde, **Docker desteğini etkinleştir** olduğu **değil** seçili ve **kimlik doğrulaması** ayarlanır **Kimlik doğrulamasız**.

3. Projeyi adlandırın **MyASPApp** tıklatıp **Tamam** yeni çözümü oluşturmak için.

4. About.cshtml.cs dosyasını açın ve bir kesim noktası `OnGet` yöntemi (eski şablonlarda, bunun yerine HomeController.cs açın ve kesme noktası kümesinde `About()` yöntemi).

## <a name="remote_debug_azure_app_service"></a> Bir Azure App Service'te uzaktan hata ayıklama ASP.NET Core

Visual Studio'dan kolayca yayımlayın ve IIS tam bir örneğine uygulamanızda hata ayıklama. Ancak, IIS yapılandırmasını önceden ve onu özelleştirebilirsiniz. Daha ayrıntılı yönergeler için bkz. [Visual Studio'yu kullanarak Azure'a bir ASP.NET Core web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (IIS özelleştirme yeteneği gerekiyorsa, hata ayıklama deneyin bir [Azure VM](#remote_debug_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Sunucu Gezgini kullanarak uzaktan hata ayıklama ve uygulama dağıtmak için

1. Visual Studio'da proje düğümünü sağ tıklatın ve seçin **Yayımla**.

    Tüm yayımlama profilleri, daha önce yapılandırdıysanız **Yayımla** bölmesi görünür. Tıklayın **yeni profili**.

1. Seçin **Azure App Service** gelen **Yayımla** iletişim kutusunda **Yeni Oluştur**ve yayımlamak için istemleri takip edin.

    Ayrıntılı yönergeler için bkz. [Visual Studio'yu kullanarak Azure'a bir ASP.NET Core web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Azure App Service’e yayımlama](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Açık **Sunucu Gezgini** (**görünümü** > **Sunucu Gezgini**) seçin ve App Service örneğinde sağ tıklatıp **hata ayıklayıcıekleme**.

1. Çalışan ASP.NET uygulama bağlantısını tıklayın **hakkında** sayfası.

    Visual Studio'da kesme noktasına isabet.

    İşte bu kadar! Bu konu başlığındaki adımları geri kalanı, bir Azure sanal makinesinde uzaktan hata ayıklama için geçerlidir.

## <a name="remote_debug_azure_vm"></a> Azure sanal makinesinde uzaktan hata ayıklama ASP.NET Core

Bir Azure VM için Windows Server oluşturabilir ve ardından yükleyin ve IIS ve diğer gerekli yazılımı bileşenleri yapılandırma. Bu, bir Azure App Service'e dağıtma değerinden daha uzun sürer ve bu öğreticinin kalan adımları izlemeniz gerekir.

İlk olarak, açıklanan tüm adımları izleyin. [yükleme ve çalıştırma IIS](/azure/virtual-machines/windows/quick-create-portal).

Ayrıca ağ güvenlik grubunda 80 numaralı bağlantı noktasını açtığınızda, uzaktan hata ayıklayıcı için bağlantı noktası 4022'yi açın. Bu şekilde, daha sonra açmak zorunda kalmazsınız.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Zaten Azure VM'de IIS içinde çalışan uygulama?

Bu makalede, temel bir Windows server IIS yapılandırmasını ayarlama ve uygulamayı Visual Studio'dan dağıtma adımlarını içerir. Bu adımları sunucuda gerekli bileşenlerin yüklü, uygulamayı doğru şekilde çalıştırabilir ve uzaktan hata ayıklama için hazır olduğunu emin olmak için dahil edilir.

* Uygulamanızı IIS çalıştıran ve yalnızca istiyorsanız uzaktan hata ayıklayıcı indir ve hata ayıklama başlatmak için Git [indirin ve Windows Server'da uzak Araçları'nı yükleme](#BKMK_msvsmon).

* Emin olmak için Yardım istiyorsanız uygulamanızı, dağıtılan, ayarlanır ve böylece hata ayıklaması yapabilirsiniz, IIS'de doğru çalışmasını, bu konudaki tüm adımları izleyin.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcınızın güvenlik ayarlarını güncelleştirin

(Varsayılan olarak etkindir) Internet Explorer Artırılmış Güvenlik Yapılandırması etkinse, bazı web sunucusu bileşenlerini yükleme sağlamak için Güvenilen siteler bazı etki alanları eklemek gerekebilir. Güvenilen siteler giderek ekleme **Internet Seçenekleri > Güvenlik > Güvenilen siteler > siteleri**. Aşağıdaki etki alanlarını ekleyin.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Yazılımı indirdiğinizde, çeşitli web sitesi komut dosyaları ve kaynakları yüklemeye izin vermek için istekleri alabilirsiniz. Bu kaynaklardan bazıları, gerekli değildir, ancak sürecini basitleştirmek için tıklatın **Ekle** istendiğinde.

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server üzerinde ASP.NET Core yükleme

1. Yükleme [.NET Core Windows Server barındırma](https://aka.ms/dotnetcore-2-windowshosting) barındıran sistemde paket. Paket, .NET Core çalışma zamanı, .NET Core kitaplığı ve ASP.NET Core modülü yükler. Daha fazla ayrıntılı yönergeler için bkz: [IIS yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Sistem, Internet bağlantısı yoksa, alma ve yükleme *[Microsoft Visual C++ 2015 yeniden dağıtılabilir](https://www.microsoft.com/download/details.aspx?id=53840)* .NET Core Windows Server barındırma paketini yüklemeden önce.

3. Sistemi yeniden başlatın (veya yürütme **net stop olan /y** ardından **net start w3svc** sistem YOLUNU bir değişiklik almak için bir komut isteminden).

## <a name="choose-a-deployment-option"></a>Bir dağıtım seçeneği seçin

IIS uygulama dağıtmak için yardıma gereksinim duyarsanız, bu seçenekleri göz önünde bulundurun:

* IIS'de bir yayımlama ayarları dosyası oluşturarak ve Visual Studio ayarları içeri aktarma dağıtın. Bazı senaryolarda, uygulamanızı dağıtmak için hızlı bir yolu budur. Yayımlama ayarları dosyası oluşturduğunuzda, IIS'de izinleri otomatik olarak ayarlanır.

* Yerel bir klasöre yayınlayarak ve IIS üzerinde bir hazır uygulamasını klasöre tarafından tercih edilen bir yöntem çıkışı kopyalama dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanabilirsiniz. Visual Studio'ya içeri aktarma ve yayımlama ayarları dosyası oluşturun.

> [!NOTE]
> Bu dağıtım yöntemi, Web dağıtımı kullanır. Web dağıtımı el ile Visual Studio ayarları içeri aktarma yerine yapılandırmak istiyorsanız, barındırma sunucuları için Web dağıtımı 3.6 yerine Web dağıtma 3.6 yükleyebilirsiniz. Ancak, Web dağıtımı el ile yapılandırırsanız, sunucuda bir uygulama klasör izinleri ve doğru değerleri ile yapılandırıldığından emin olun gerekecektir (bkz [yapılandırma ASP.NET Web sitesi](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Yükleme ve Windows Server üzerinde barındırma sunucuları için Web dağıtımı yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>IIS Windows Server'da yayımlama ayarları dosyası oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlayacaktır. Uygulamayı Visual Studio'dan başlatılmazsa, IIS'de uygulamayı başlatın. ASP.NET Core için uygulama havuzu için alan emin olmamız gerekiyor. **DefaultAppPool** ayarlanır **yönetilen kod yok**.

1. İçinde **ayarları** iletişim kutusu, tıklayarak hata ayıklamayı etkinleştir **sonraki**, seçin bir **hata ayıklama** yapılandırma ve ardından **ek dosyaları Kaldır Hedef** altında **dosya yayımlama** seçenekleri.

    > [!NOTE]
    > Yayın yapılandırması seçerseniz, hata ayıklama devre dışı *web.config* yayımladığınızda, dosya.

1. Tıklayın **Kaydet** ve sonra uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlayarak dağıtma

RoboCopy, Powershell kullanarak IIS uygulama kopyalamak istediğiniz veya dosyaları el ile kopyalamak isterseniz, uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="BKMK_deploy_asp_net"></a> Windows Server bilgisayarında ASP.NET Web sitesi yapılandırma

İçeri aktarmakta olduğunuz yayınlama ayarları, bu bölümü atlayabilirsiniz.

1. Açık **Internet Information Services (IIS) Yöneticisi'ni** gidin **siteleri**.

2. Sağ **varsayılan Web sitesi** düğümünü seçip alt **uygulama Ekle**.

3. Ayarlama **diğer** alanı **MyASPApp** uygulama havuzu alanını **yönetilen kod yok**. Ayarlama **fiziksel yolu** için **C:\Publish** (daha sonra dağıtacağınız ASP.NET projesi).

4. IIS Yöneticisi'nde site seçiliyken, seçin **düzenleme izinleri**ve o IUSR, IIS_IUSRS veya uygulama havuzu okuma & yürütme hakları olan yetkili bir kullanıcı için yapılandırılan kullanıcı emin olun.

    Bu kullanıcılara erişim birini görmüyorsanız, okuma ve yürütme hakları olan bir kullanıcı olarak IUSR'yi eklemek için adımları inceleyin.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(İsteğe bağlı) Yayımlama ve uygulamayı yayımlayarak bir yerel klasöre Visual Studio'dan dağıtma

Web dağıtımı kullanmıyorsanız, yayımlama ve dosya sistemi veya diğer araçları kullanarak uygulamayı dağıtırsınız. Dosya sistemini kullanarak bir paket oluşturarak başlayın ve ardından paketi el ile dağıtmak veya PowerShell, RoboCopy ve XCopy gibi diğer araçları kullanın. Bu bölümde, Web dağıtımı kullanmıyorsanız el ile paket Kopyalamakta olduğunuz varsayılır.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> İndirme ve Windows Server'da uzak araçları yükleme

Bu öğreticide, Visual Studio 2017 kullanılmıştır.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Windows Server'da uzaktan hata ayıklayıcı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Gerektiğinde ek kullanıcılar için izinler eklemek için kimlik doğrulama modunu değiştirmek veya bağlantı noktası numarası için uzaktan hata ayıklayıcı değilse [uzaktan hata ayıklayıcı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Visual Studio bilgisayardan ASP.NET uygulamasına ekleme

1. Visual Studio bilgisayarda hata ayıklamaya çalıştığınız çözümü açın (**MyASPApp** bu makaledeki adımları takip ediyorsanız).
2. Visual Studio'da **hata ayıklama > iliştirme** (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017'de, daha önce ekli kullanarak aynı işlemde yeniden ekleyebileceğiniz **hata ayıklama > İliştir...** (Shift + Alt + P). 

3. Niteleyici alanın ayarlanacağı  **\<uzak bilgisayar adı >: 4022**.
4. Tıklayın **Yenile**.
    Bazı işlemler görünür görmelisiniz **kullanılabilir işlemler** penceresi.

    Herhangi bir işlem görmüyorsanız (bağlantı noktası gereklidir) uzak bilgisayar adı yerine IP adresini kullanarak deneyin. Kullanabileceğiniz `ipconfig` IPv4 adresini almak için komut satırında.

    Kullanmak istiyorsanız **Bul** düğmesini gerekebilir [açın UDP bağlantı noktası 3702](#bkmk_openports) sunucusunda.

5. Denetleme **tüm kullanıcıların işlemlerini göster**.

6. Hızlı bir şekilde bulmak için bir işlem adının ilk harfi yazın *dotnet.exe* (için ASP.NET Core).
   
   ASP.NET Core uygulaması için önceki işlem adıydı *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Tıklayın **ekleme**.

8. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda Git **http://\<uzak bilgisayar adı >**.
    
    ASP.NET web sayfası görmeniz gerekir.
9. Çalışan ASP.NET uygulama bağlantısını tıklayın **hakkında** sayfası.

    Visual Studio'da kesme noktasına isabet.

### <a name="bkmk_openports"></a> Sorun giderme: Windows Server üzerinde gerekli bağlantı noktaları açma

Çoğu ayarlar ASP.NET ve uzaktan hata ayıklayıcı yüklemesi tarafından gerekli bağlantı noktalarının açıldığından. Ancak, bir güvenlik duvarının arkasında barındırılan uygulama ve dağıtım sorunlarını giderirken, doğru bağlantı noktalarının açık olduğundan emin olun gerekebilir.

Bir Azure sanal makinesinde aracılığıyla bağlantı noktalarını açmanız gerekir [ağ güvenlik grubu](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic). 

Gerekli bağlantı noktaları:

- 80 - IIS için gerekli
- 4022 - gerekli Visual Studio 2017'den uzaktan hata ayıklama için (bkz [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) daha fazla bilgi için).
- UDP 3702 - (isteğe bağlı) bulma bağlantı sağlar, **Bul** düğme Visual Studio uzaktan hata ayıklayıcı eklerken.

Ayrıca, bu bağlantı noktaları ASP.NET yükleme tarafından zaten açılması gerekir:
- 8172 - (isteğe bağlı) uygulamayı Visual Studio'dan dağıtmak Web dağıtımı için gerekli

