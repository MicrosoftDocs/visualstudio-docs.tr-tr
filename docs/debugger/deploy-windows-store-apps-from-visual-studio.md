---
title: UWP uygulamaları dağıtma | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: d8006fb0ddcab4ab3eeee1616632d2dc513428ba
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056817"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Visual Studio’dan UWP uygulamaları dağıtma

Visual Studio dağıtım işlevlerini oluşturur ve bir hedef cihazda oluşturulan Visual Studio ile UWP uygulamaları kaydeder. Uygulamanın tam olarak nasıl kaydedilir, hedef cihazın yerel veya uzak olup bağlıdır:

- Visual Studio LocalMachine hedeflendiğinde Visual Studio, derleme klasöründen uygulamayı kaydeder.

- Uzak aygıtı hedeflendiğinde Visual Studio gerekli dosyaları uzak makineye kopyalar ve o cihazdaki uygulama kaydeder.

Dağıtım, kullanarak uygulamanızı Visual Studio'dan hata ayıklaması yaparken otomatiktir **hata ayıklamayı Başlat** seçeneği (klavye: F5) veya **hata ayıklama olmadan Başlat** seçeneği (klavye: CTRL + F5). Ayrıca, uygulamanızı el ile dağıtabilirsiniz. El ile dağıtımı, aşağıdaki senaryolarda kullanışlıdır:

- Yerel veya uzak bir makinede test geçici.

- Hata ayıklamak istediğiniz başka bir uygulamayı başlatacak bir uygulamayı dağıtma.

- Başlatıldığında ayıklanacak bir uygulamayı başka bir uygulama veya metodu tarafından dağıtılıyor.

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Bir UWP uygulaması dağıtma
 El ile uygulama dağıtma basit bir işlemdir:

1.  Uzak cihaza dağıtıyorsanız, uygulamanın başlangıç projesi özellik Proje sayfasının adını veya cihazın IP adresini belirtin. (Bu olan yapmak için bu konudaki aşağıya listelenen adımları.).

2.  Yanındaki aşağı açılan listeden hata ayıklayıcı Visual Studio araç çubuğunda dağıtım hedefini seçin **hata ayıklamayı Başlat** düğmesi.

     ![Yerel makinede çalıştırma](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3.  Üzerinde **derleme** menüsünde seçin **Dağıt**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Uzak cihaz belirtme

**Önkoşullar**

Bir Windows 10 uzak cihazda etkinleştirmelisiniz [Geliştirici modu](/windows/uwp/get-started/enable-your-device-for-development). Windows 10 cihazlarda çalışan oluşturan kişinin güncelleştirme veya uygulamanızı dağıtırken daha sonra uzak Araçlar otomatik olarak yüklenir. Daha fazla bilgi için [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Windows 10 pre-oluşturanın güncelleştirme sürümleri, Visual Studio için Uzak Araçlar, uzak cihazda yüklü olmalıdır ve uzaktan hata ayıklayıcı çalışıyor olması gerekir.

Dağıtım, uygulama dosyaları uzak cihaza göndermek için uzaktan hata ayıklayıcı ağ kanalının kullanır.

#### <a name="to-specify-a-remote-device"></a>Uzak cihaz belirtmek için

1. Başlangıç projesinin hata ayıklama özelliği sayfasında adını veya IP adresini bir uzak dağıtım hedefini belirtin.

2. Hata ayıklama özellik sayfasını açmak için Çözüm Gezgini'nde projeyi seçin ve ardından **özellikleri** kısayol menüsünden.

3. Ardından **hata ayıklama** özellik sayfaları penceresinin düğümde.

4. İçin **hedef cihaz**seçin **uzak makine**.

5. Altında **uzak makine**, tıklayın **Bul**.

6. Adını veya uzak cihazın IP adresini yazın veya CİHAZDAN seçebilirsiniz **uzak bağlantı** iletişim kutusu.

    ![Select uzaktan hata ayıklayıcı bağlantısı iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Uzak bağlantı** iletişim kutusu, yerel ağ alt ağı ve bir Ethernet kablosuyla doğrudan Visual Studio makinesine bağlı herhangi bir CİHAZDAN şirket cihazları görüntüler.

   **Uzak cihazın bir JavaScript ya da Visual C++ proje sayfada belirtme**

   ![C&#43; &#43; proje uzaktan hata ayıklama özellikleri](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Seçin **uzaktan hata ayıklayıcı** gelen **başlatmak için hata ayıklayıcı** listesi.

8. Uzak cihaz ağ adını **makine adı** kutusu. Veya uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan cihazı seçin için kutusunda aşağı oku seçin.

   **Uzak cihazın bir Visual C# ve Visual Basic proje sayfada belirtme**

   ![Uzaktan hata ayıklama için proje özellikleri yönetilen](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Seçin **uzak makine** gelen **hedef cihaz** listesi.

10. Uzak cihaz ağ adını **uzak makine** kutusuna veya tıklayın **bulmak** cihazı seçin **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.

##  <a name="BKMK_Deployment_options"></a> Dağıtım seçenekleri

Aşağıdaki dağıtım seçeneklerinden başlangıç projesinin hata ayıklama özellik sayfasından ayarlayabilirsiniz.

**Ağ geri döngüsüne izin ver**

Güvenlik nedenleriyle bir UWP veya [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] yüklü cihaz ağ çağrı yapmak için standart bir biçimde yüklü uygulama verilmez. Varsayılan olarak, Visual Studio dağıtımı bu kuraldan dağıtılmış uygulama için bir istisna oluşturur. Bu muafiyet iletişim yordamları tek bir makinede test etmenizi sağlar. Uygulamanıza göndermeden önce [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], uygulamanızı muafiyet olmadan test etmeniz gerekir.

Uygulama ağ geri döngüsü muafiyet kaldırmak için:

- Üzerinde C# ve Visual Basic hata ayıklama özellik sayfası, NET **ağ geri döngüsüne izin** onay kutusu.

- JavaScript ve hata ayıklama özellik sayfası **ağ geri döngüsüne izin** değerini **Hayır**.

**Başlatma, ancak başlatıldığında kodumda Hata Ayıkla (C# ve Visual Basic) / uygulama başlatma (JavaScript ve C++)**

Dağıtım, uygulama başlatıldığında hata ayıklama oturumu otomatik olarak başlayacak şekilde yapılandırmak için:

- Üzerinde C# ve Visual Basic hata ayıklama özellik sayfasını kontrol edin, **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** onay kutusu.

- JavaScript ve hata ayıklama özellik sayfası **uygulama Başlat** değerini **Evet**.

## <a name="see-also"></a>Ayrıca Bkz.

- [Gelişmiş uzak dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md)
- [Visual Studio’dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md)
