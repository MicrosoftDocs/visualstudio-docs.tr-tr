---
title: Uzak bir makinede çalıştırma Windows Store apps | Microsoft Docs
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
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a3be715f58d3ed80122dfdd3aaf879c7db8aebd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784552"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Uzak makinede Windows Mağazası uygulamalarını çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Visual Studio uzak Araçlar uygulaması, hata ayıklama, profil ve Visual Studio çalıştıran ikinci bir bilgisayardan bir cihazda çalışan bir Windows Store uygulaması test çalıştırmak sağlar. Visual Studio bilgisayarı, Windows Store uygulamaları dokunmatik, coğrafi konum ve fiziksel yön gibi belirli işlevleri desteklemiyorsa, uzak bir cihazda çalıştırma özellikle etkili olabilir. Bu konu başlığı altında yapılandırmak ve bir uzak oturumu başlatmak için gereken yordamları açıklar.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 Şunları öğrenebilirsiniz:  
  
 [Önkoşullar](#BKMK_Prerequisites)  
  
 [Güvenlik](#BKMK_Security)  
  
 [Uzak cihaza doğrudan bağlanma](#BKMK_DirectConnect)  
  
 [Uzak araçları yükleme](#BKMK_Installing_the_Remote_Tools)  
  
 [Uzaktan hata ayıklama İzleyicisi başlatılıyor](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Uzaktan hata ayıklayıcı yapılandırma](#BKMK_ConfigureRemoteDebugger)  
  
 [Uzaktan hata ayıklama için Visual Studio projesini yapılandırma](#BKMK_ConnectVS)  
  
- [C# ve Visual Basic projeleri için Uzak cihaz seçme](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [JavaScript ve C++ projeleri için Uzak cihaz seçme](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Uzaktan hata ayıklama oturumu çalıştırma](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> Önkoşullar  
 Uzak bir cihazda hata ayıklamak için:  
  
-   Uzak cihaz ve Visual Studio yüklü bilgisayar, ağ üzerinden bağlı veya doğrudan Ethernet kablosu ile bağlı olmalıdır. Internet üzerinden hata ayıklama desteklenmez.  
  
-   Bir geliştirici lisansı uzak cihaz üzerinde yüklü olmalıdır.  
  
-   Uzaktaki cihaz uzaktan hata ayıklama bileşenlerini çalıştırıyor olmalıdır.  
  
-   Yükleme sırasında güvenlik duvarını yapılandırmak için Uzak cihazda yönetici olmanız gerekir. Çalıştırmak veya uzaktan hata ayıklayıcıya bağlanmak için Uzak cihaza kullanıcı erişiminiz olmalıdır.  
  
##  <a name="BKMK_Security"></a> Güvenlik  
 Varsayılan olarak, uzaktan hata ayıklayıcıyı Windows kimlik doğrulaması kullanır.  
  
> [!WARNING]
>  Uzaktan hata ayıklayıcıyı kimlik doğrulaması yok modunda çalıştırmayı seçebilirsiniz, ancak bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Ağın, kötü amaçlı veya tehlikeli trafik riskinden uzak olduğundan eminseniz Kimlik Doğrulaması Yok modunu seçin.  
  
##  <a name="BKMK_DirectConnect"></a> Uzak cihaza doğrudan bağlanma  
 Uzak cihaza doğrudan bağlanmak için Visual Studio bilgisayarını cihaza standart bir Ethernet kablosu ile bağlanın. Cihazın Ethernet bağlantı noktası yoksa kablo bağlantısı için bir USB Ethernet Bağdaştırıcısı kullanabilirsiniz.  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> Uzak araçları yükleme  
  
> [!NOTE]
>  **Sürümler ve güncelleştirmeler**  
>   
>  **Visual Studio 2015 için Uzak Araçlar** Visual Studio'nun önceki sürümleri için desteklenmez.  
>   
>  Visual Studio yüklemenizin güncelleştirme sürümüyle eşleşen Visual Studio 2015 için Uzak Araçlar güncelleştirme sürümünü yüklemeniz önerilir.  
>   
>  VS hata ayıklayıcı, VS 2015 ve VS 2015 için Uzak Araçlar sürümlerinin herhangi bir birleşimini ile uyumludur. Bununla birlikte, Visual Studio'daki en yeni işlev hem Visual Studio'nun hem de Uzak Araçlar'ın en güncel sürümde olmasını gerektirir.  
>   
>  Diğer tanılama araçları, aynı uzak araçlar ve Visual Studio sürümlerini gerektirebilir.  
  
 **Uzak bir cihazda uzak hata ayıklama bileşenlerini yükleme**  
  
 Çalıştırın veya uzak araçlar için yükleme programını kaydetmek için Visual Studio sürümünüzle eşleşen bu tabloda bağlantılardan birini seçin:  
  
|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2015 Güncelleştirme 3|[Uzak Araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials gruba katılın veya yalnızca geçerli Visual Studio aboneliği ile oturum açabilirsiniz. Ardından bağlantıyı gerekirse yeniden açın. Her zaman eşleştirme (x 86, x64 veya ARM sürümü), cihaz işletim sistemi sürümü indirin|
|Visual Studio 2015 (eski)|[Uzak Araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials gruba katılın veya yalnızca geçerli Visual Studio aboneliği ile oturum açabilirsiniz. Ardından bağlantıyı gerekirse yeniden açın. Her zaman eşleştirme (x 86, x64 veya ARM sürümü), cihaz işletim sistemi sürümü indirin|
|Visual Studio 2013|[Uzak Araçlar](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 belgeleri sayfasında indirin|
  
 Yükleme programını indirmeyi seçebilir veya hemen çalıştırabilirsiniz. Yükleme programını çalıştırırken kullanıcı anlaşmasını kabul edin ve ardından **yükleme**.  
  
 Varsayılan olarak, uzaktan hata ayıklama bileşenleri yüklendiği **C:\Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote hata ayıklayıcı** klasör.  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Uzaktan hata ayıklama İzleyicisi başlatılıyor  
  
> [!NOTE]
>  Uzaktan hata ayıklayıcı Visual Studio konak ile iletişime izin vermek için Güvenlik Duvarı'nı yapılandırdığından; uzaktan hata ayıklayıcıyı ilk kez başlattığınızda, uzak cihazda yönetici olması gerekir.  
  
 Uzak Araçlar'ı yükledikten sonra seçin **uzaktan hata ayıklayıcı** üzerinde **Başlat** ekran. **Uzaktan hata ayıklama Yapılandırması** ilk kez uzaktan hata ayıklayıcıyı başlattığınızda görüntülenir.  
  
 Üzerinde **uzaktan hata ayıklama Yapılandırması** iletişim kutusunda:  
  
1.  Windows Web Hizmetleri API'si yüklü değilse seçin **yükleyin**  
  
2.  İçinde **Windows Güvenlik Duvarı Yapılandırma** grubunda, bağlantılara izin vermek istediğiniz ağları seçin. Cihaz şu anda bağlı olduğu ağlar etkinleştirilir. En az bir ağ seçmelisiniz.  
  
3.  Seçin **uzaktan hata ayıklamayı Yapılandır** duvarını ayarlamak ve uzaktan hata ayıklayıcıyı başlatın.  Açık **Visual Studio uzaktan hata ayıklama İzleyicisi** uzak araçlar için kullanıcılara izin vermek ve diğer ayarlamak için iletişim kutusu Gelişmiş Seçenekleri.  
  
4.  **Visual Studio uzaktan hata ayıklama İzleyicisi** iletişim kutusu görüntülenir. Uzak araçlar için kullanıcılara izin verin ve bu iletişim kutusundan diğer gelişmiş seçenekleri ayarlayın.  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> Uzaktan hata ayıklayıcı yapılandırma  
 Uzaktan hata ayıklayıcı yapılandırmasını değiştirmek için iki aracı kullanın.  
  
1. Üzerinde **Araçları** menüsü **Visual Studio uzaktan hata ayıklama İzleyicisi**:  
  
   1.  Seçin **seçenekleri** bağlantı noktası numarasını, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı zaman aşımı aralığını değiştirmek için.  
  
   2.  Seçin **izinleri** uzaktan hata ayıklama iznine sahip kullanıcı eklemek veya kaldırmak için.  
  
       > [!NOTE]
       >  Her kullanıcı hesabı için uzaktan hata ayıklamasına izin verilmelidir.  
  
   Kullandığınız **uzaktan hata ayıklayıcı Yapılandırma Sihirbazı'nı** uzaktan hata ayıklayıcı için Gelişmiş seçeneklerini ayarlamak için. Sihirbazı açmak için seçin **uzaktan hata ayıklayıcı Yapılandırma Sihirbazı'nı** başlangıç ekranında.  
  
2. Üzerinde **Visual Studio uzaktan hata ayıklayıcı yapılandırma** sayfasında tercih edebilirsiniz uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak. Çoğu durumda, bir hizmet olarak çalışma gerekli değildir.  
  
3. Üzerinde **hata ayıklama için Windows Güvenlik Duvarı Yapılandırma** sayfasında, eklemek veya bağlanmak için uzaktan hata ayıklayıcı istediğiniz ağ türünü kaldırın. Cihaz şu anda bağlı olduğu ağlar etkinleştirilir. En az bir ağ seçmelisiniz.  
  
##  <a name="BKMK_ConnectVS"></a> Uzaktan hata ayıklama için Visual Studio projesini yapılandırma  
 Proje özelliklerinde Bağlanılacak uzak cihazı belirtin. Yordam programlama diline bağlı olarak farklılık gösterir. Uzak cihaz ağ adını yazmanız veya uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan seçebilirsiniz.  
  
 ![Select uzaktan hata ayıklayıcı bağlantısı iletişim kutusu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 İletişim kutusu yalnızca Visual Studio bilgisayarının yerel alt ağda olan ve uzaktan hata ayıklayıcıyı çalıştıran cihazları listeler.  
  
> [!TIP]
>  Bir uzak cihaza bağlanırken sorun yaşıyorsanız, cihazın IP adresini girmeyi deneyin. Bir cihazın IP adresini belirlemek için bir komut penceresi açın ve ardından yazın **ipconfig**. IP adresi olarak listelenip listelenmediğini **IPv4 adresi**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> C# ve Visual Basic projeleri için Uzak cihaz seçme  
 ![Uzaktan hata ayıklama için proje özellikleri yönetilen](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Çözüm Gezgini'nde proje adını seçin ve ardından **özellikleri** kısayol menüsünden.  
  
2.  Seçin **hata ayıklama**.  
  
3.  Seçin **uzak makine** gelen **hedef cihaz** listesi.  
  
4.  Uzak cihaz ağ adını **uzak makine** kutusuna veya seçin **Bul** cihazı seçin **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> JavaScript ve C++ projeleri için Uzak cihaz seçme  
 ![C&#43; &#43; proje uzaktan hata ayıklama özellikleri](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Çözüm Gezgini'nde proje adını seçin ve ardından **özellikleri** kısayol menüsünden.  
  
2.  Genişletin **yapılandırma özellikleri** düğümünü ve ardından **hata ayıklama**.  
  
3.  Seçin **uzaktan hata ayıklayıcı** gelen **başlatmak için hata ayıklayıcı** listesi.  
  
4.  Uzak cihaz ağ adını **makine adı** kutusuna veya kutusuna cihazı seçin aşağı oku seçin **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.  
  
##  <a name="BKMK_RunRemoteDebug"></a> Uzaktan hata ayıklama oturumu çalıştırma  
 Başlatın, durdurun ve uzaktan hata ayıklama oturumu, bir yerel oturumda olduğu gibi gidin. Hata ayıklamaya başlamadan önce uzaktan hata ayıklama İzleyicisi uzak cihazda çalıştığından emin olun.  
  
 Ardından **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5). Proje yeniden derlenen, ardından dağıtılan ve uzak cihaz üzerinde başlatıldı. Hata ayıklayıcı kesme noktalarında yürütmeyi askıya alır ve içine, üzerine ve dışına kodunuzu geçebilirsiniz. Seçin **hata ayıklamayı Durdur** hata ayıklama oturumunuzu bitirmek ve uzak uygulamayı kapatmak için. Daha fazla bilgi için [uygulamaları Visual Studio'da hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio ile Store uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio’da uygulamaların hatalarını ayıklama](../debugger/debug-store-apps-in-visual-studio.md)



