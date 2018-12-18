---
title: Windows Store uygulamaları dağıtma
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 797983f2f5fcc9ae4e12ca5426b521034f03700d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055792"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Visual Studio'dan Windows Store uygulamaları dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")

 Visual Studio dağıtım işlevlerini oluşturur ve bir hedef cihazda oluşturulan Visual Studio ile Windows Store apps kaydeder. Uygulamanın tam olarak nasıl kaydedilir, hedef cihazın yerel veya uzak olup bağlıdır:

- Visual Studio LocalMachine hedeflendiğinde Visual Studio, derleme klasöründen uygulamayı kaydeder.

- Uzak aygıtı hedeflendiğinde Visual Studio gerekli dosyaları uzak makineye kopyalar ve o cihazdaki uygulama kaydeder.

  Dağıtım, kullanarak uygulamanızı Visual Studio'dan hata ayıklaması yaparken otomatiktir **hata ayıklamayı Başlat** seçeneği (klavye: F5) veya **hata ayıklama olmadan Başlat** seçeneği (klavye: CTRL + F5). Ayrıca, uygulamanızı el ile dağıtabilirsiniz. El ile dağıtımı, aşağıdaki senaryolarda kullanışlıdır:

- Yerel veya uzak bir makinede test geçici.

- Hata ayıklamak istediğiniz başka bir uygulamayı başlatacak bir uygulamayı dağıtma.

- Başlatıldığında ayıklanacak bir uygulamayı başka bir uygulama veya metodu tarafından dağıtılıyor.

##  <a name="BKMK_In_this_topic"></a> Bu konudaki
 Bu konu başlığında şunları öğrenebilirsiniz:

 [Windows Store uygulaması dağıtma](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Uzak cihaz belirtme](#BKMK_How_to_specify_a_remote_device)

 [Dağıtım seçenekleri](#BKMK_Deployment_options)

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Windows Store uygulaması dağıtma
 El ile uygulama dağıtma basit bir işlemdir:

1.  Uzak cihaza dağıtıyorsanız, uygulamanın başlangıç projesi özellik Proje sayfasının adını veya cihazın IP adresini belirtin. (Bu olan yapmak için bu konudaki aşağıya listelenen adımları.).

2.  Yanındaki aşağı açılan listeden hata ayıklayıcı Visual Studio araç çubuğunda dağıtım hedefini seçin **hata ayıklamayı Başlat** düğmesi.

     ![Yerel makinede çalıştırma](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3.  Üzerinde **derleme** menüsünde seçin **Dağıt**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Uzak cihaz belirtme
 **Önkoşullar**

 Uzak cihaza bir uygulama dağıtmak için:

-   Bir geliştirici lisansı uzak cihaz üzerinde yüklü olmalıdır.

-   Visual Studio uzak araçları, uzak cihazda yüklü olmalıdır ve uzaktan hata ayıklama İzleyicisi çalışıyor olması gerekir.

     Dağıtım, uygulama dosyaları uzak cihaza göndermek için uzaktan hata ayıklayıcı ağ kanalının kullanır.

#### <a name="to-specify-a-remote-device"></a>Uzak cihaz belirtmek için

1. Başlangıç projesinin hata ayıklama özelliği sayfasında adını veya IP adresini bir uzak dağıtım hedefini belirtin.

2. Hata ayıklama özellik sayfasını açmak için Çözüm Gezgini'nde projeyi seçin ve ardından **özellikleri** kısayol menüsünden.

3. Ardından **hata ayıklama** özellik sayfaları penceresinin düğümde.

4. Adını veya uzak cihazın IP adresini yazın veya CİHAZDAN seçebilirsiniz **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.

    ![Select uzaktan hata ayıklayıcı bağlantısı iletişim kutusu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu, yerel ağ alt ağı ve bir Ethernet kablosuyla doğrudan Visual Studio makinesine bağlı herhangi bir CİHAZDAN şirket cihazları görüntüler.

   **Uzak cihazın bir JavaScript ya da Visual C++ proje sayfada belirtme**

   ![C&#43; &#43; proje uzaktan hata ayıklama özellikleri](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Seçin **uzaktan hata ayıklayıcı** gelen **başlatmak için hata ayıklayıcı** listesi.

6. Uzak cihaz ağ adını **makine adı** kutusu. Veya uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan cihazı seçin için kutusunda aşağı oku seçin.

   **Uzak cihazın bir Visual C# ve Visual Basic proje sayfada belirtme**

   ![Uzaktan hata ayıklama için proje özellikleri yönetilen](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Seçin **uzak makine** gelen **hedef cihaz** listesi.

8. Uzak cihaz ağ adını **uzak makine** kutusuna veya tıklayın **bulmak** cihazı seçin **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.

##  <a name="BKMK_Deployment_options"></a> Dağıtım seçenekleri
 Aşağıdaki dağıtım seçeneklerinden başlangıç projesinin hata ayıklama özellik sayfasından ayarlayabilirsiniz.

 **Ağ geri döngüsüne izin ver** güvenlik nedenleriyle bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] yüklü cihaz ağ çağrı yapmak için standart bir biçimde yüklü uygulama verilmez. Varsayılan olarak, Visual Studio dağıtımı bu kuraldan dağıtılmış uygulama için bir istisna oluşturur. Bu muafiyet iletişim yordamları tek bir makinede test etmenizi sağlar. Uygulamanıza göndermeden önce [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], uygulamanızı muafiyet olmadan test etmeniz gerekir.

 Uygulama ağ geri döngüsü muafiyet kaldırmak için:

- C# ve VB hata ayıklama özellik sayfası Temizle **ağ geri döngüsüne izin ver** onay kutusu.

- JavaScript ve hata ayıklama özellik sayfası **ağ geri döngüsüne izin** değerini **Hayır**.

  **Başlatma, ancak başlatıldığında kodumda Hata Ayıkla (C# ve VB'de) / uygulama başlatma (JavaScript ve C++)** dağıtımını, uygulama başlatıldığında hata ayıklama oturumu otomatik olarak başlayacak şekilde yapılandırmak için:

- C# ve VB hata ayıklama özellik sayfasını kontrol **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** onay kutusu.

- JavaScript ve hata ayıklama özellik sayfası **uygulama Başlat** değerini **Evet**.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio’dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md)
