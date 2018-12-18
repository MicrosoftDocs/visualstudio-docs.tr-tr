---
title: Uzak makinede UWP uygulamalarının hatalarını ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 0350358c2225851619a84216c929b8d7435dc4e3
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750721"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Visual Studio'dan uzak makinede UWP uygulamalarının hatalarını ayıklama
  
Visual Studio, hata ayıklama, profil ve bir evrensel Windows Platformu (UWP) uygulamasını başka bir bilgisayar veya cihaz üzerinde test çalıştırmak için kullanabilirsiniz. Visual Studio bilgisayarı dokunmatik, coğrafi konum ve fiziksel yön gibi UWP özel işlevler desteklemediğinde, uzak makinede UWP uygulaması çalıştıran özellikle yararlıdır. 

##  <a name="BKMK_Prerequisites"></a> Önkoşullar  

Visual Studio'dan uzak bir cihazdaki bir UWP uygulamasında hata ayıklamak için:  
  
- Uzaktan hata ayıklama için Visual Studio projesini yapılandırılması gerekir.
- Uzak makinede Visual Studio bilgisayarı gerekir bir ağ üzerinden bağlı veya doğrudan USB veya Ethernet kablosu ile bağlı. Internet üzerinden hata ayıklama desteklenmez.  
- Yapmanız gerekenler [Geliştirici Modu'nu](/windows/uwp/get-started/enable-your-device-for-development) hem Visual Studio bilgisayarı ve uzak makine. 
- Uzak bilgisayarlar, Visual Studio için Uzak Araçlar çalıştırmalıdır. 
  - Bazı Windows 10 sürümleri başlatın ve uzak Araçlar'ı otomatik olarak çalıştırın. Aksi takdirde, [yükleyin ve Visual Studio için Uzak Araçlar çalıştırın](#BKMK_download).
  - Windows Mobile 10 cihazları gerektirir veya uzak araçları destek kullanmayın. 

##  <a name="BKMK_ConnectVS"></a> Uzaktan hata ayıklama için Visual Studio projesi yapılandırma
<a name="BKMK_DirectConnect"></a> Proje kullandığınız **özellikleri** için Bağlanılacak uzak cihazı belirtin. Ayarlar programlama diline bağlı olarak farklılık gösterir. 

> [!CAUTION]
> Varsayılan olarak, özellik sayfasında ayarlar **Evrensel (şifrelenmemiş Protokolü)** olarak **kimlik doğrulama türü** Windows 10 uzak bağlantılar için. Ayarlamanız gerekebilir **kimlik doğrulaması yok** uzaktan hata ayıklayıcıya bağlanmak için. **Evrensel (şifrelenmemiş Protokolü)** ve **kimlik doğrulaması yok** protokollerine sahip hiçbir ağ güvenliği için geliştirme ve uzak makineler arasında aktarılan veriler savunmasızdır. Bu kimlik doğrulama türleri için yalnızca güvenilen ağlar emin kötü amaçlı veya tehlikeli trafik etkilenir değil'ı seçin. 
>
>Seçerseniz **Windows kimlik doğrulaması** için **kimlik doğrulama türü**, hata ayıklama sırasında uzak makineye oturum açmanız gerekir. Uzaktan hata ayıklayıcı ayrıca altında çalışmalıdır **Windows kimlik doğrulaması** moduyla Visual Studio makinesinde aynı kullanıcı hesabı.

###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Yapılandırma bir C# veya Visual Basic projesi için uzaktan hata ayıklama  

1. Seçin C# veya Visual Studio'da Visual Basic projesi **Çözüm Gezgini** seçip **özellikleri** simgesi, tuşuna **Alt** +  **Girin**, veya sağ tıklayıp seçin **özellikleri**.
  
1.  Seçin **hata ayıklama** sekmesi.  
  
1.  Altında **hedef cihaz**seçin **uzak makine** uzak bir bilgisayar için veya **cihaz** doğrudan bağlı bir Windows Mobile 10 cihaz için.  
  
1.  Uzak bir makine için ağ adı veya IP adresini girin **uzak makine** alanına **Bul** cihazın aranacak [Uzaktan bağlantılar iletişim kutusunda](#remote-connections). 
    
    ![Uzaktan hata ayıklama için proje özellikleri yönetilen](../debugger/media/vsrun_managed_projprop_remote.png "yönetilen hata ayıklama, proje özellikleri")  
    
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Uzaktan hata ayıklama için JavaScript ya da C++ projesi yapılandırma   
  
1.  Visual Studio'da C++ veya JavaScript proje seçin **Çözüm Gezgini** seçip **özellikleri** simgesi, basın **Alt**+**girin** , veya sağ tıklayıp seçin **özellikleri**.
  
1.  Seçin **hata ayıklama** sekmesi.  
  
3.  Altında **başlatmak için hata ayıklayıcı**seçin **uzak makine** uzak bir bilgisayar için veya **cihaz** doğrudan bağlı bir Windows Mobile 10 cihaz için. 
  
1.  Uzak bir makine için girin veya ağ adı veya IP adresini seçin **makine adı** alanı ya da seçin ve aşağı açılan **bulun** cihazın aranacak [Uzaktan bağlantılar iletişim kutusu ](#remote-connections). 

    ![Uzaktan hata ayıklama için C++ proje özelliklerini](../debugger/media/vsrun_cpp_projprop_remote.png "C++ hata ayıklama, proje özellikleri")
    
### <a name="remote-connections"></a> Uzaktan bağlantılar iletişim kutusunu kullanın

İçinde **uzak bağlantıları** iletişim kutusu, belirli bir uzak bilgisayar adı veya IP adresi için veya arayabilirsiniz otomatik bağlantıları yenile yuvarlak ok simgesini seçerek algıla. İletişim kutusu, şu anda uzaktan hata ayıklayıcıyı çalıştıran cihazları yerel alt ağdaki arar. Tüm cihazlar olarak algılanabilir **uzak bağlantıları** iletişim kutusu. 

 ![Uzak bağlantı iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "Uzaktan bağlantılar iletişim")  

>[!TIP]
>Ada göre uzak cihaza bağlanamıyorsa, IP adresini kullanarak deneyin. Uzak cihaz üzerindeki IP adresini belirlemek için girin **ipconfig** komut penceresinde. IP adresi olarak görünür **IPv4 adresi**.  
    
## <a name="BKMK_download"></a> Visual Studio için Uzak Araçlar'ı yükleme ve indirme

Visual Studio'nın uzak bir bilgisayarda uygulamalarında hata ayıklamak, Visual Studio için Uzak Araçlar uzak bilgisayarda çalışmalıdır. 

- Windows Mobile 10 cihazları gerektirmez veya uzak Araçlar'ı destekler. 
- (Sürüm 1703) oluşturan kişinin çalıştıran Windows 10 bilgisayarları güncelleştirmek ve uygulamayı dağıttığınızda daha sonra Windows 10 Xbox, IOT ve HoloLens cihazları uzak araçları otomatik olarak yüklenir. 
- Pre-oluşturanın güncelleştirme Windows 10 bilgisayarlarında, gerekir el ile indirin, yükleyin ve hatalarını ayıklamaya başlamadan önce uzak Araçlar uzak bilgisayar üzerinde çalışıyor olabilir.

**Uzak araçları indirme ve yükleme için:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Uzak araçları yapılandırma

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> UWP uygulamalarında uzaktan hata ayıklama 

Uzaktan hata ayıklama, yerel hata ayıklama ile aynı çalışır. 

1. Uzaktan hata ayıklama İzleyicisi'Pre-oluşturanın güncelleştirme sürümlerinde Windows 10 'un emin olun (*msvsmon.exe*) uzak cihazda çalışıyor.  
   
1. Visual Studio bilgisayarda doğru hata ayıklama hedef emin olun (**uzak makine** veya **cihaz**) araç çubuğundaki yeşil ok yanında görünür. 
   
1. Seçerek hata ayıklamayı Başlat **hata ayıklama** > **hata ayıklamayı Başlat**, ENTER tuşuna basın **F5**, veya araç çubuğundaki yeşil oku seçerek. 
   
   Proje yeniden derlenir, ardından dağıtır ve uzak cihazda başlar. Hata ayıklayıcı kesme noktalarında yürütmeyi askıya alır ve, üzerinden, kodun içine ve dışına müdahale edebilirsiniz. 
   
1. Gerekirse, seçin **hata ayıklama** > **hata ayıklamayı Durdur** veya basın **Shift**+**F5** hata ayıklamayı durdurmak ve Uzak uygulamayı kapatın.
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Gelişmiş uzak dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Visual Studio ile UWP uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio’da UWP uygulamalarının hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
