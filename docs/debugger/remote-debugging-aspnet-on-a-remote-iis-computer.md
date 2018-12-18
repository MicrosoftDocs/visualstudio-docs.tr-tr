---
title: Uzaktan hata ayıklama Uzak IIS bilgisayarında ASP.NET Core | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: bcb0db3a6eab91c517ce731ddf6e201d5a73f1f8
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101079"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Visual Studio 2017'de bir uzak IIS bilgisayarda uzaktan hata ayıklama ASP.NET Core
IIS'ye dağıtılan bir ASP.NET uygulamasında hata ayıklamak için yükleme ve uzak Araçlar, uygulamanızın dağıtıldığı bilgisayarda çalıştırın ve ardından Visual Studio'dan çalışan uygulamanıza ekleyin.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuz, ayarlayın ve Visual Studio 2017 ASP.NET Core yapılandırmak, IIS'ye dağıtma ve Visual Studio uzaktan hata ayıklayıcı ekleme açıklanmaktadır. Uzaktan hata ayıklama için ASP.NET 4.5.2, bkz: [IIS bilgisayarında uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Ayrıca, dağıtabilir ve Azure kullanarak IIS üzerinde hata ayıklayın. Azure App Service için kolayca dağıtabilir ve hatalarını ayıklama, uzaktan hata ayıklayıcıyı kullanarak IIS ve önceden yapılandırılmış bir örneğinde [Snapshot Debugger](../debugger/debug-live-azure-applications.md) ya da [Haya ayıklayıcı Sunucu Gezgini'nden](../debugger/remote-debugging-azure.md).

Bu yordamlar bu sunucu yapılandırmaları üzerinde test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10

## <a name="requirements"></a>Gereksinimler

Bir proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmiyor. Ülkeler yüksek gecikme süresi veya çevirmeli, Internet gibi düşük bant genişliği bağlantı üzerinden veya Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya edilemeyecek kadar yavaş. Gereksinimlerinin tam listesi için bkz. [gereksinimleri](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Zaten IIS içinde çalışan uygulama?

Bu makalede, temel bir Windows server IIS yapılandırmasını ayarlama ve uygulamayı Visual Studio'dan dağıtma adımlarını içerir. Sunucu bileşenleri yüklü, uygulamanın doğru şekilde çalıştırabilir ve uzaktan hata ayıklama için hazır olduğunu istedi emin olmak için bu adımları dahildir.

* Uygulamanızı IIS çalıştıran ve yalnızca istiyorsanız uzaktan hata ayıklayıcı indir ve hata ayıklama başlatmak için Git [indirin ve Windows Server'da uzak Araçları'nı yükleme](#BKMK_msvsmon).

* Emin olmak için Yardım istiyorsanız uygulamanızı, dağıtılan, ayarlanır ve böylece hata ayıklaması yapabilirsiniz, IIS'de doğru çalışmasını, bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Visual Studio 2017 bilgisayar üzerinde ASP.NET Core uygulaması oluşturun 

1. Yeni bir ASP.NET Core uygulaması oluşturun. (**Dosya > Yeni > Proje**, ardından **Visual C# > Web > ASP.NET Core Web uygulaması**).

    İçinde **ASP.NET Core** şablonları bölümünden **Web uygulaması**.

2. Emin olun **ASP.NET Core 2.0** seçildiğinde, **Docker desteğini etkinleştir** olduğu **değil** seçili ve **kimlik doğrulaması** ayarlanır **Kimlik doğrulamasız**.

3. Projeyi adlandırın **MyASPApp** tıklatıp **Tamam** yeni çözümü oluşturmak için.

4. About.cshtml.cs dosyasını açın ve bir kesim noktası `OnGet` yöntemi (eski şablonlarda, bunun yerine HomeController.cs açın ve kesme noktası kümesinde `About()` yöntemi).

## <a name="bkmk_configureIIS"></a> Yükleme ve Windows Server'da IIS yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcınızın güvenlik ayarlarını güncelleştirin

(Varsayılan olarak etkindir) Internet Explorer Artırılmış Güvenlik Yapılandırması etkinse, bazı web sunucusu bileşenlerini yükleme sağlamak için Güvenilen siteler bazı etki alanları eklemek gerekebilir. Güvenilen siteler giderek ekleme **Internet Seçenekleri > Güvenlik > Güvenilen siteler > siteleri**. Aşağıdaki etki alanlarını ekleyin.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Yazılımı indirdiğinizde, çeşitli web sitesi komut dosyaları ve kaynakları yüklemeye izin vermek için istekleri alabilirsiniz. Bu kaynaklardan bazıları, gerekli değildir, ancak sürecini basitleştirmek için tıklatın **Ekle** istendiğinde.

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server üzerinde ASP.NET Core yükleme

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

1. Windows Gezgini'ni açın ve yeni bir klasör oluşturun **C:\Publish**, ASP.NET projesi daha sonra dağıtacağınız.

2. Zaten açık değilse, açmak **Internet Information Services (IIS) Yöneticisi'ni**. (Sunucu Yöneticisi'nin sol bölmesinde, seçin **IIS**. Sunucuya sağ tıklayıp **Internet Information Services (IIS) Yöneticisi'ni**.)

3. Altında **bağlantıları** sol bölmede, Git **siteleri**.

4. Seçin **varsayılan Web sitesi**, seçin **temel ayarları**, ayarlayıp **fiziksel yolu** için **C:\Publish**.

4. Sağ **varsayılan Web sitesi** düğümünü seçip alt **uygulama Ekle**.

5. Ayarlama **diğer** alanı **MyASPApp**, uygulama havuzu varsayılan değeri kabul edin (**DefaultAppPool**) ve **fiziksel yolu** için **C:\Publish**.

6. Altında **bağlantıları**seçin **uygulama havuzları**. Açık **DefaultAppPool** ve uygulama havuzu alanın ayarlanacağı **yönetilen kod yok**.

7. Yeni site IIS Yöneticisi'nde sağ tıklayın, seçin **düzenleme izinleri**ve o IUSR, IIS_IUSRS veya web uygulamasına erişim Okuma & yürütme hakları olan yetkili bir kullanıcı için yapılandırılan kullanıcı emin olun.

    Bu kullanıcılara erişim birini görmüyorsanız, okuma ve yürütme hakları olan bir kullanıcı olarak IUSR'yi eklemek için adımları inceleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Yayımlama ve uygulamayı yayımlayarak bir yerel klasöre Visual Studio'dan dağıtma

Ayrıca, yayımlama ve dosya sistemi veya diğer araçları kullanarak uygulamayı dağıtırsınız.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> İndirme ve Windows Server'da uzak araçları yükleme

Bu öğreticide, Visual Studio 2017 kullanılmıştır.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a> Windows Server'da uzaktan hata ayıklayıcı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Gerektiğinde ek kullanıcılar için izinler eklemek için kimlik doğrulama modunu değiştirmek veya bağlantı noktası numarası için uzaktan hata ayıklayıcı değilse [uzaktan hata ayıklayıcı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Visual Studio bilgisayardan ASP.NET uygulamasına ekleme

1. Visual Studio bilgisayarda hata ayıklamaya çalıştığınız çözümü açın (**MyASPApp** , bu makaledeki tüm adımları izlediğinizden emin).
2. Visual Studio'da **hata ayıklama > iliştirme** (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017'de, daha önce ekli kullanarak aynı işleme iliştirebilirsiniz **hata ayıklama > İliştir...** (Shift + Alt + P). 

3. Niteleyici alanın ayarlanacağı  **\<uzak bilgisayar adı >: 4022**.
4. Tıklayın **Yenile**.
    Bazı işlemler görünür görmelisiniz **kullanılabilir işlemler** penceresi.

    Herhangi bir işlem görmüyorsanız (bağlantı noktası gereklidir) uzak bilgisayar adı yerine IP adresini kullanarak deneyin. Kullanabileceğiniz `ipconfig` IPv4 adresini almak için komut satırında.

    Kullanmak istiyorsanız **Bul** düğmesini gerekebilir [açın UDP bağlantı noktası 3702](#bkmk_openports) sunucusunda.

5. Denetleme **tüm kullanıcıların işlemlerini göster**.
6. Hızlı bir şekilde bulmak için bir işlem adının ilk harfi yazın **dotnet.exe** (için ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Tıklayın **ekleme**.

8. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda Git **http://\<uzak bilgisayar adı >**.
    
    ASP.NET web sayfası görmeniz gerekir.

9. Çalışan ASP.NET uygulama bağlantısını tıklayın **hakkında** sayfası.

    Visual Studio'da kesme noktasına isabet.

## <a name="bkmk_openports"></a> Sorun giderme: Windows Server üzerinde gerekli bağlantı noktaları açma

Çoğu ayarlar ASP.NET ve uzaktan hata ayıklayıcı yüklemesi tarafından gerekli bağlantı noktalarının açıldığından. Ancak, bağlantı noktalarının açık olduğunu doğrulamak gerekebilir.

> [!NOTE]
> Bir Azure sanal makinesinde aracılığıyla bağlantı noktalarını açmanız gerekir [ağ güvenlik grubu](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic).

Gerekli bağlantı noktaları:

- 80 - IIS için gerekli
- 4022 - gerekli Visual Studio 2017'den uzaktan hata ayıklama için (bkz [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ayrıntılı bilgi için.
- 8172 - (isteğe bağlı) uygulamayı Visual Studio'dan dağıtmak Web dağıtımı için gereklidir.
- UDP 3702 - (isteğe bağlı) bulma bağlantı sağlar, **Bul** düğme Visual Studio uzaktan hata ayıklayıcı eklerken.

1. Windows Server üzerindeki bir bağlantı noktasını açmak için Aç **Başlat** menüsünde **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı**.

2. Ardından **gelen kuralları > Yeni Kural > bağlantı noktası**ve ardından **sonraki**. (UDP 3702 için seçin **giden kuralları** yerine.)

3. Altında **belirli yerel bağlantı noktaları**, bağlantı noktası numarasını girin, tıklayın **sonraki**.

4. Tıklayın **bağlantıya izin**, tıklayın **sonraki**.

5. İçin bağlantı noktasını etkinleştirmek ve bir veya daha fazla ağ türlerini seçmek **sonraki**.

    Seçtiğiniz türü, uzak bilgisayarın bağlı olduğu ağ içermelidir.
6. Ad ekleyin (örneğin, **IIS**, **Web dağıtımı**, veya **msvsmon**) tıklayın ve gelen kuralı için **son**.

    Yeni kuralınıza kuralları gelen veya giden kuralları listesinde görmeniz gerekir.

    Windows Güvenlik Duvarı yapılandırma hakkında ayrıntılı bilgi isterseniz bkz [uzaktan hata ayıklama için Windows Güvenlik Duvarı Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
