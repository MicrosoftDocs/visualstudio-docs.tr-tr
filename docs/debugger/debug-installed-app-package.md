---
title: Yüklü bir UWP uygulama paketinin hatalarını ayıklama | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 331fd642001f1e6217736185d4b3bbbd7f56923e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784422"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Visual Studio'da yüklü bir UWP uygulama paketinin hatalarını ayıklama

Windows 10 bilgisayarlar ve Xbox, HoloLens ve IOT cihazlarında yüklü Evrensel Windows Platformu (UWP) uygulama paketleri, Visual Studio hata ayıklaması yapabilirsiniz. 

>[!NOTE]
>Visual Studio yüklü UWP uygulamaları için hata ayıklama telefonlarda desteklenmiyor.
   
UWP uygulamaları için hata ayıklama hakkında daha fazla bilgi için blog gönderilerine bakın [hata ayıklama yüklü uygulama paketleri](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) ve [Evrensel Windows uygulamaları (UWP) oluşturma](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Yerel bir makinede yüklü bir UWP uygulamasında hata ayıklama

1. Visual Studio'da **hata ayıklama** > **diğer hata ayıklama hedefleri** > **yüklenen uygulama paketinin hatalarını ayıklama**.
   
1. İçinde **yüklenen uygulama paketinin hatalarını ayıklama** iletişim altında **bağlantı türü**seçin **yerel makine**.
   
1. Altında **yüklenen uygulama paketleri**ayıklamak istediğiniz uygulamayı seçin veya arama kutusuna adını yazın. Altında görünür olmayan çalışan yüklü uygulama paketi **çalışmıyor**, ve çalışan uygulamalar, altında **çalıştıran**. 
   
   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")
   
1. Gerekirse, kod türü altında değiştirin **hata ayıklama Bu kod türü**ve diğer seçenekleri seçin. 
   - Seçin **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** uygulama başlatıldığında hata ayıklama başlatılamıyor. Hata ayıklama başlatma uygulama ne zaman başlatılır denetim yolları hata ayıklamak için etkili bir yoludur [farklı başlatma yöntemleri](/windows/uwp/xbox-apps/automate-launching-uwp-apps), özel parametrelerle protokolünü etkinleştirme gibi.
   
1. Seçin **Başlat**, veya uygulama çalışıyorsa, **iliştirme**.

> [!NOTE]
> Seçerek herhangi bir çalışan UWP veya başka bir uygulama işlemi de ekleyebilirsiniz **hata ayıklama** > **iliştirme** Visual Studio'da. Çalışan bir işleme iliştirmek için özgün Visual Studio projesi gerekmez, ancak uygulamanın semboller yükleniyor önemli ölçüde için özgün koda sahip olmayan bir işlemin hatalarını ayıklamaya yardımcı. Bkz: [hata ayıklayıcısında sembol ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
## <a name="remote"></a> Bir uzak bilgisayarda veya cihazda yüklü bir UWP uygulamasında hata ayıklama

Visual Studio Windows 10 cihaz veya uzak bir post-oluşturucunun güncelleştirme Windows 10 bilgisayarını, yüklü bir UWP uygulamasında hata ayıklamasına ilk kez hedef cihazda uzaktan hata ayıklama araçlarını yükler. 

1. [Geliştirici modu etkinleştirme](/windows/uwp/get-started/enable-your-device-for-development) Visual Studio bilgisayarı ve uzak cihaz veya bilgisayar.
   
1. Pre-oluşturanın güncelleştirme Windows 10 çalıştıran bir uzak bilgisayara bağlanıyorsanız [el ile yükleyin ve uzaktan hata ayıklayıcıyı başlatmak](../debugger/remote-debugging.md) uzak bilgisayarda.
   
1. Visual Studio bilgisayarda seçin **hata ayıklama** > **diğer hata ayıklama hedefleri** > **yüklenen uygulama paketinin hatalarını ayıklama**.
   
1. İçinde **yüklenen uygulama paketinin hatalarını ayıklama** iletişim altında **bağlantı türü**seçin **uzak makine** veya **cihaz**.
   
   Seçerseniz **cihaz**, bilgisayarınızın bir Windows 10 cihazına fiziksel olarak bağlı olması gerekir.
   
   Uzak makinenin bilgisayar adresi yanındaki görünmüyorsa **adresi**seçin **değişiklik**. 
      
   1. İçinde **uzak bağlantı** yanındaki iletişim kutusunda **adresi**, ad veya bağlanmak istediğiniz bilgisayarın IP adresini yazın.
      
      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")
      
      Hata ayıklayıcı uzak bilgisayara bilgisayar adını kullanarak bağlanamıyorsanız, IP adresini kullanın. IP adresi, Xbox, HoloLens ve IOT cihazlar için kullanın.
   1. Bir kimlik doğrulama seçeneği işaretleyin **kimlik doğrulama modu**.
      
      Çoğu uygulama için varsayılan değer tutmak **Evrensel (şifrelenmemiş Protokolü)**.
   1. Seçin **seçin**. 

1. Altında **yüklenen uygulama paketleri**ayıklamak istediğiniz uygulamayı seçin veya arama kutusuna adını yazın. Altında görünür olmayan çalışan yüklü uygulama paketi **çalışmıyor**, ve çalışan uygulamalar, altında **çalıştıran**. 
   
1. Gerekirse, kod türü altında değiştirin **hata ayıklama Bu kod türü**ve diğer seçenekleri seçin. 
   - Seçin **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** uygulama başlatıldığında hata ayıklama başlatılamıyor. Hata ayıklama başlatma uygulama ne zaman başlatılır denetim yolları hata ayıklamak için etkili bir yoludur [farklı başlatma yöntemleri](/windows/uwp/xbox-apps/automate-launching-uwp-apps), özel parametrelerle protokolünü etkinleştirme gibi.
   
1. Seçin **Başlat**, veya uygulama çalışıyorsa, **iliştirme**.

Yüklü uygulama paketi bağlı Xbox, HoloLens ve IOT cihaz üzerinde ilk kez hata ayıklamaya başladığınızda, Visual Studio uzaktan hata ayıklayıcı hedef cihazınız için doğru sürümünü yükler. Uzaktan hata ayıklayıcı yüklenmesi uzun süre ve ileti **uzaktan hata ayıklayıcı başlatılıyor** gerçekleştiği sırada görüntülenir.

>[!NOTE]
>Şu anda, Xbox veya HoloLens bir cihaz zaten çalışıyorsa ayıklayıcıyı uygulamayı yeniden başlatır.

Uzaktan dağıtım UWP uygulamaları hakkında daha fazla bilgi için bkz. [UWP uygulamaları dağıtma ve hata ayıklama](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) ve [uzak makinede hata ayıklama UWP uygulamaları](run-windows-store-apps-on-a-remote-machine.md). 
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio’da hata ayıklama](../debugger/index.md)  
 [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)  
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)  
 [Windows Güvenlik Duvarı’nı uzaktan hata ayıklama için yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)  
 [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)