---
title: Bir Store uygulaması için bir hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 847e4144c8846f0247d735ec640fc878a75fa82e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051817"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Visual Studio'da (VB, C#, C++ ve XAML) bir Store uygulaması için hata ayıklama oturumu başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Bu konu, XAML ve Visual C++, Visual C# veya Visual Basic içinde yazılan Store uygulamaları için hata ayıklama oturumu başlatmak açıklar. Uygulama hata ayıklama, hem hata ayıklama oturumu yapılandırma ve uygulamayı başlatmak için yol seçme içerir.

> [!NOTE]
>  HTML ve JavaScript ile yazılan uygulamaları görmek için [(JavaScript) bir hata ayıklama oturumunu başlatmada](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

##  <a name="BKMK_In_this_topic"></a> Bu konudaki
 [Hata ayıklama başlamanın en kolay yolu](#BKMK_The_easy_way_to_start_debugging)

 [Hata ayıklama oturumu yapılandırma](#BKMK_Configure_the_debugging_session)

- [Proje için hata ayıklama özellik sayfasını açın](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Yapı yapılandırma seçenekleri'ni seçin.](#BKMK_Choose_the_build_configuration_options)

- [Dağıtım hedefi seçin](#BKMK_Choose_the_deployment_target)

- [Kullanılacak hata ayıklayıcı seçin](#BKMK_Choose_the_debugger_to_use)

- [(İsteğe bağlı) Hata ayıklama oturumu başlatma gecikmesi](#BKMK__Optional__Delay_starting_the_debug_session)

- [(İsteğe bağlı) Ağ geri döngüler devre dışı bırak](#BKMK__Optional__Disable_network_loopbacks)

- [(İsteğe bağlı) Hata ayıklamaya başladığınızda uygulamayı yeniden yükleyin.](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(İsteğe bağlı) Uzaktan hata ayıklayıcıyı başlatmak için kimlik doğrulama gereksinimini devre dışı bırak](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Hata ayıklama oturumu başlatma](#BKMK_Start_the_debugging_session)

- [(F5) hata ayıklamayı Başlat](#BKMK_Start_debugging__F5_)

- [Uygulama başlangıcı geciktirmek ancak (F5) hata ayıklamayı Başlat](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Yüklü bir uygulama hata ayıklayıcıda Başlat](#BKMK_Start_an_installed_app_in_the_debugger)

- [Çalışan bir uygulama için hata ayıklayıcının](#BKMK_Attach_the_debugger_to_a_running_app_)

  -   [Hata ayıklama modunda çalıştırmak için uygulamayı Ayarla](#BKMK_Set_the_app_to_run_in_debug_mode)

  -   [Hata ayıklayıcının](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Hata ayıklama başlamanın en kolay yolu

1. Uygulama çözümünü Visual Studio'da açın.

2. F5'i seçin.

   Visual Studio, yapıları ve hata ayıklayıcısı ekli uygulamayı başlatır. Yürütme bir kesme noktasına ulaşıldığında, el ile kaldırma işlenen özel durum oluşur, yürütme askıya veya uygulama sona kadar devam eder. Daha fazla bilgi için [(Xaml ve C#) bir hata ayıklama oturumunda gezinme](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

##  <a name="BKMK_Configure_the_debugging_session"></a> Hata ayıklama oturumu yapılandırma

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Proje için hata ayıklama özellik sayfasını açın

1.  Çözüm Gezgini'nde projeyi seçin. Kısayol menüsünde **özellikleri**.

2.  Bu proje için hata ayıklama özellik sayfasını açmak için şunları yapın:

    -   Visual C# ve Visual Basic uygulamaları seçin **hata ayıklama**.

         ![C&#35; &#47; VB proje hata ayıklama özellik sayfasından](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    -   Visual C++ uygulamaları için genişletme **yapılandırma özellikleri** düğümünü seçip **hata ayıklama**.

         ![C&#43; &#43; özellik sayfası hata ayıklama Windows Store app](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Yapı yapılandırma seçenekleri'ni seçin.

1.  Gelen **yapılandırma** listesinde **hata ayıklama** veya **(etkin) hata ayıklama**.

2.  Gelen **Platform** liste oluşturmak için hedef platformu seçin. Çoğu durumda **herhangi bir CPU** (**tüm platformlar** Visual C++'ta) en iyi seçenektir.

###  <a name="BKMK_Choose_the_deployment_target"></a> Dağıtım hedefi seçin
 ![Windows için yalnızca geçerli](../debugger/media/windows-only-content.png "windows_only_content")

 Dağıtın ve Visual Studio makinede Visual Studio simulator, yerel makinede veya uzak bir cihazdaki bir Windows Store uygulamasında hata ayıklama.

- C# ve Visual Basic uygulamaları için hedef seçin **hedef cihaz** listesini **hata ayıklama** projenin özellik sayfası.

- C++ uygulamaları için hedef seçin **başlatmak için hata ayıklayıcı** listesini **hata ayıklama** özellik sayfası:

  Bu seçeneklerden birini seçin:

|||
|-|-|
|**Yerel Makine**|Uygulama geçerli oturumdaki yerel makinenizde hata ayıklayın. Bkz: [yerel makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simülatör**|Visual Studio simulator için uygulamada hata ayıklama [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar. Simülatör hata ayıklama cihazın işlevselliğini sağlayan masaüstü penceredir — dokunma hareketlerini ve cihaz döndürme gibi — yerel makinede mevcut değildir. Bkz: [simulator'da çalıştırma Windows Store apps](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Uzak makine**|İntranet üzerindeki yerel makineye bağlı veya bir Ethernet kablosuyla doğrudan bağlı bir cihazda uygulama hatalarını ayıklayın. Uzaktan hata ayıklamak için Visual Studio uzak araçları yüklü ve uzak cihazda çalışıyor olması gerekir. Bkz: [uzak bir makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Seçerseniz **uzak makine**, adını veya uzak makinenin IP adresini aşağıdaki yöntemlerden birini belirtin:

- Adını veya uzak makinenin IP adresini girin.

  -   C# ve Visual Basic uygulamaları için adı veya IP adresi olarak girin **uzak makine** kutusu.

  -   C++ uygulamaları için adı veya IP adresi olarak girin **makine adı** kutusu.

- Uzak makineden seçin **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.

   İletişim kutusunu açmak için:

  - C# ve Visual Basic uygulamaları seçin **Bul**.

  - C++ uygulamaları için aşağı oku seçin **makine adı** seçin ve kutusunda  **\<bulun... >**.

    ![Select uzaktan hata ayıklayıcı bağlantısı iletişim kutusu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  **Uzaktan hata ayıklayıcı bağlantısı Seç** yerel alt ağı üzerinde olan makinelere ve Visual Studio makinesine, bir Ethernet kablosuyla doğrudan bağlı sanal makinelere iletişim kutusu görüntüler. Başka bir makine belirtmek için adı girin. **makine adı** kutusu.

  ![Windows Phone için yalnızca geçerli](../debugger/media/phone-only-content.png "phone_only_content")

  Dağıtma ve cihazda veya Visual Studio phone öykünücüleri birinde bir Windows Phone Store uygulamasında hata ayıklama. Cihaz veya öykünücüsünden seçin **hedef cihaz** listesi.

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Kullanılacak hata ayıklayıcı seçin
 Varsayılan olarak, Visual Studio, C# ve Visual Basic uygulamaları yönetilen kodda hata ayıklamasına.

 C# ve Visual Basic uygulama hem yönetilen ve yerel C/C++ kodu uygulamanızda hata ayıklamak seçebilirsiniz. Seçin **yönetilmeyen kodun hata ayıklamasını etkinleştir** yerel kod hata ayıklama oturumunuzda eklemek için onay kutusunu.

 Varsayılan olarak, Visual Studio C++ uygulamanızı yerel kodda hata ayıklamasına.

 C++ uygulamaları için hata ayıklama bileşenleri uygulamanızın yerine veya ek olarak, yerel kod içinde olan belirli kod türlerini seçebilirsiniz. Hata ayıklamak için kod belirttiğiniz **hata ayıklayıcı türü** listesini **hata ayıklama** uygulama projesinin özellik sayfası.

 Bu hata ayıklayıcıları birini **uygulama işlemi** listesi:

|||
|-|-|
|**Jenom skript**|Uygulamanızı JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel koda göz ardı edilir.|
|**Yalnızca yerel**|Uygulamanızı yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodunu göz ardı edilir.|
|**Yalnızca yönetilen**|Uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu ve yerel C/C++ kod göz ardı edilir.|
|**(Yönetilen ve yerel) karışık**|Yerel C/C++ kod ve uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu göz ardı edilir.|
|**Yalnızca GPU**|Grafik işlem birimi (GPU) üzerinde çalışan yerel C++ kod hatalarını ayıklama.|

 ![Windows Phone için yalnızca geçerli](../debugger/media/phone-only-content.png "phone_only_content")

 Windows Store telefon uygulamaları için arka plan işlemleri için kullanılacak hata ayıklayıcı ayrıca seçebilirsiniz **arka plan görev işlemi**.

###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (İsteğe bağlı) Hata ayıklama oturumu başlatma gecikmesi
 Hata ayıklamaya başladığınızda varsayılan olarak, Visual Studio uygulama hemen başlar. Hata ayıklama oturumunu başlatmada ancak uygulamanızın başlangıç gecikme. Bu seçeneği belirlediğinizde, uygulama başlangıç ekranından veya etkinleştirme sözleşme başlatıldığında veya başka bir işlem veya metodu tarafından başlatıldığında Hata Ayıklayıcısı'nda başlatılır. Uygulama çalışmıyorken bir arka plan görevinin hatalarını ayıklamak istediğiniz zaman aynı zamanda uygulamanızın başlangıç gecikme.

 Uygulamanızın lansmanını geciktirmek için şunları yapabilirsiniz:

-   Visual C# ve Visual Basic uygulamaları için **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** üzerinde **hata ayıklama** özellik sayfası.

-   Visual C++ uygulamaları için seçin **Evet** gelen **uygulama Başlat** listesini **hata ayıklama** özellik sayfası.

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (İsteğe bağlı) Ağ geri döngüler devre dışı bırak
 ![Windows için yalnızca geçerli](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedeniyle, standart bir biçimde yüklü bir Windows Store uygulaması, yüklü olduğu cihazın ağ çağrı yapmak için izin verilmiyor. Varsayılan olarak, Visual Studio dağıtımı bu kuraldan dağıtılmış uygulama için bir istisna oluşturur. Bu muafiyet iletişim yordamları tek bir makinede test etmenizi sağlar. Windows Store uygulamanızda göndermeden önce uygulamanızı muafiyet olmadan test etmeniz gerekir.

 Ağ geri döngüsüne muafiyetini kaldırmak için:

-   Visual C# ve Visual Basic uygulamaları temizleyin **ağ geri döngüsüne izin** onay kutusunu **hata ayıklama** özellik sayfası.

-   Visual C++ uygulamaları için seçin **Hayır** gelen **ağ geri döngüsüne izin** listesini **hata ayıklama** özellik sayfası.

###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (İsteğe bağlı) Hata ayıklamaya başladığınızda uygulamayı yeniden yükleyin.
 Yükleme ve Visual C# veya Visual Basic uygulamanızın ilk yapılandırma ile ilgili sorunları tanılamak için seçin **Kaldır ve yeniden yükleme paketimle** üzerinde **hata ayıklama** yeniden oluşturmak için özellik sayfası bir hata ayıklamaya başladığınızda özgün yükleme. Bu seçenek, Visual C++ projeleri için kullanılabilir değildir.

###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (İsteğe bağlı) Uzaktan hata ayıklayıcıyı başlatmak için kimlik doğrulama gereksinimini devre dışı bırak
 ![Windows için yalnızca geçerli](../debugger/media/windows-only-content.png "windows_only_content")

 Varsayılan olarak, uzaktan hata ayıklayıcıyı çalıştırmak için kimlik bilgilerini sağlamanız gerekir.

> [!IMPORTANT]
>  Uzaktan hata ayıklayıcıyı kimlik doğrulaması yok modunda çalıştırmayı da seçebilirsiniz, ancak bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Ağın, kötü amaçlı veya tehlikeli trafik riskinden uzak olduğundan eminseniz Kimlik Doğrulaması Yok modunu seçin.

 Kimlik doğrulama gereksinimini kaldırmak için:

1. Visual C# ve Visual Basic uygulamaları temizleyin **kimlik doğrulamasını kullan** onay kutusunu **hata ayıklama** özellik sayfası.

2. Visual C++ uygulamaları için seçin **Hayır** gelen **kimlik doğrulaması iste** listesini **hata ayıklama** özellik sayfası.

   [Bu konudaki](#BKMK_In_this_topic)

##  <a name="BKMK_Start_the_debugging_session"></a> Hata ayıklama oturumu başlatma

###  <a name="BKMK_Start_debugging__F5_"></a> (F5) hata ayıklamayı Başlat
 Seçeneğini belirlediğinizde **hata ayıklamayı Başlat** (klavye: F5) üzerinde **hata ayıklama** menüsünde, Visual Studio başlatılır uygulamayı hata ayıklayıcısı ekli. Yürütme bir kesme noktasına ulaşıldığında, el ile özel bir durum oluştuğunda, yürütme askıya veya uygulama sona kadar devam eder.

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Uygulama başlangıcı geciktirmek ancak (F5) hata ayıklamayı Başlat
 Uygulamayı hata ayıklama modunda çalıştırabilir, ancak start, hata ayıklayıcı dışında bir yöntem için ayarlayabilirsiniz. Örneğin, başlatma Başlat menüsünden uygulamanızın hatalarını ayıklama veya uygulama başlatmadan bir arka plan işlemi uygulamasında hata ayıklamak için isteyebilirsiniz. Uygulama başlangıcı geciktirmek için şunu yapın:

- Üzerinde **hata ayıklama** uygulamasının özellik sayfası (**hata ayıklama** Visual c++)

  -   Visual C# ve Visual Basic uygulamaları seçin **başlatma, ancak başlatıldığında kodumda Hata Ayıkla**.

  -   Visual C++ uygulamaları için seçin **Evet** gelen **uygulama Başlat** listesi.

- Seçin **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5).

- Başlat menüsünden bir yürütme sözleşme veya başka bir yordam tarafından uygulamanızı başlatın.

  Uygulamayı hata ayıklama modunda başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

  biçimindeki telefon numarasıdır. Arka plan görevleri hata ayıklama hakkında daha fazla bilgi için bkz. [tetikleyici askıya alma, sürdürme ve arka plan olaylarını Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Yüklü bir uygulama hata ayıklayıcıda Başlat
 F5'i kullanarak hata ayıklamaya başladığınızda, Visual Studio oluşturur ve uygulamayı dağıtır, hata ayıklama modunda çalıştırmak için uygulama ayarlar ve başladıktan sonra. Bir cihazda zaten yüklü olan bir uygulamayı başlatmak için yüklenen uygulama paketinin hatalarını ayıklama iletişim kutusunu kullanın. Bu yordam, Windows Mağazası'ndan veya uygulama için kaynak dosyaları varsa, ancak uygulama için bir Visual Studio projesi yok yüklü olduğu bir uygulamanın hatalarını ayıklamak ihtiyacınız olduğunda yararlıdır. Örneğin, Visual Studio projelerinin veya çözümlerinin kullanmayan bir özel yapı sistemi olabilir.

 Uygulamayı yerel cihaza yüklenebilir veya uzak bir cihazda olabilir.  Uygulamayı hemen başlayabilir veya başka bir işlem veya yöntem başlatıldığında gibi Başlat menüsünden veya etkinleştirme sözleşme, uygulama, bir arka plan işlemi hata ayıklama istediğinizde, hata ayıklama modunda çalıştırmak için de ayarlayabilirsiniz hata ayıklayıcıda çalışmasını ayarlayabilirsiniz Uygulama başlatmadan. Daha fazla bilgi için [tetikleyici askıya alma, sürdürme ve arka plan olaylarını Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Hata ayıklama modunda çalıştırmak için yüklü bir uygulama için bunu yapmanız gerekir:

> [!NOTE]
>  Bu yordamı başlattığınızda, uygulama çalışmıyor olması gerekir.

1. Üzerinde **hata ayıklama** menüsünde seçin **yüklenen uygulama paketinin hatalarını ayıklama**

2. Aşağıdaki seçeneklerden birini listeden seçin:


   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Yerel Makine**  |                                                                                                                Uygulama geçerli oturumdaki yerel makinenizde hata ayıklayın. Bkz: [yerel makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simülatör**    | Visual Studio simulator için uygulamada hata ayıklama [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar. Simülatör hata ayıklama cihazın işlevselliğini sağlayan masaüstü penceredir — dokunma hareketlerini ve cihaz döndürme gibi — yerel makinede mevcut değildir. Bkz: [simulator'da çalıştırma Windows Store apps](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Uzak makine** |                          İntranet üzerindeki yerel makineye bağlı veya bir Ethernet kablosuyla doğrudan bağlı bir cihazda uygulama hatalarını ayıklayın. Uzaktan hata ayıklamak için Visual Studio uzak araçları yüklü ve uzak cihazda çalışıyor olması gerekir. Bkz: [uzak bir makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |


3. Uygulamadan seçin **yüklenen uygulama paketleri** listesi.

4. Kullanmak için hata ayıklama altyapısı seçin **hata ayıklama Bu kod türü** listesi.

5. (İsteğe bağlı). Seçin **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** diğer bir yöntem tarafından başlatıldığında bir uygulamanın hatalarını ayıklamak için veya bir arka plan işlemi hata ayıklamak için.

   Tıkladığınızda **Başlat**, uygulama başlatıldığında veya hata ayıklama modunda çalışacak şekilde ayarlanmış.

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Çalışan bir uygulama için hata ayıklayıcının
 Hata ayıklayıcıyı iliştirmek için bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama, hata ayıklama modunda çalışacak şekilde ayarlamak için hata ayıklanabilir Paket Yöneticisi'ni kullanmalıdır. Hata ayıklanabilir Paket Yöneticisi ile Visual Studio uzak Araçları yüklenir.

 Haya ayıklayıcı bir uygulama için yararlıdır, yüklendiği bir uygulama gibi bir zaten yüklü uygulamanın hatalarını ayıklamak ihtiyacınız olduğunda [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. Uygulama için kaynak dosyaları varsa, ancak uygulama için bir Visual Studio projesi yok ekleme gereklidir. Örneğin, Visual Studio projelerinin veya çözümlerinin kullanmayan bir özel yapı sistemi olabilir.

 Hata ayıklayıcı bir uygulamaya ekleme adımları gerektirir:

1.  Uygulama hata ayıklama modunda çalışacak şekilde ayarlayın. Uygulamayı çalışır durumda olduğunda Bunun yapılması gerekir.

2.  Uygulamayı başlatın. Başlangıç ekranında, bir yürütme sözleşme veya başka bir yöntem, uygulamayı başlatabilirsiniz.

3.  Hata ayıklayıcı, çalışan uygulamaya ekleyin.

####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Hata ayıklama modunda çalıştırmak için uygulamayı Ayarla

1.  Visual Studio uzak Araçlar, uygulamanın yüklendiği cihaza yükleyin. Bkz: [uzak araçları yükleme](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2.  Başlangıç ekranından arama `Debuggable Package Manager` ve sonra başlatın.

     UygX hata ayıklama cmdlet'i için düzgün yapılandırılmış bir PowerShell penceresi görünür.

3.  Bir uygulamada hata ayıklamayı etkinleştirmek için uygulamanın Pakettamadı tanımlayıcısı belirtmeniz gerekir. Pakettamadı içeren tüm uygulamaların bir listesini görüntülemek için şunu yazın `Get-AppxPackage` PowerShell komut isteminde.

4.  PowerShell komut isteminde, girin `Enable-AppxDebug` *Pakettamadı* burada *Pakettamadı* uygulamanın Pakettamadı tanımlayıcısıdır.

####  <a name="BKMK_Attach_the_debugger"></a> Hata ayıklayıcının
 Hata ayıklayıcıyı iliştirmek için:

1. Üzerinde **hata ayıklama** menüsünde seçin **iliştirme**.

    **İliştirme** iletişim kutusu görüntülenir.

2. Uzak bir cihazdaki bir uygulamaya eklemek için Uzak cihazı belirtin **niteleyicisi** kutusu. Şunları yapabilirsiniz:

   -   Adı girin **niteleyicisi** kutusu.

   -   Aşağı oku seçin **niteleyicisi** kutusuna ve ardından önce eklenmiş cihazların listesinden bir cihaz seçin.

   -   Seçin **Bul** yerel alt ağınız cihazlarda listesinden bir cihaz seçmek için.

3. Hata ayıklamak istediğiniz kod türünü belirtin **ekleme** kutusu.

    Seçin **seçin** ve ardından aşağıdakilerden birini yapın:

   -   Seçin **otomatik olarak hata ayıklanacak kodun türünü belirleme**

   -   Seçin **bu tür kodlarda hata ayıklama** ve ardından listeden bir veya daha fazla tür seçin.

4. İçinde **kullanılabilir işlemler** listesinde, uygulama işlemini seçin.

5. Seçin **ekleme**.

   Visual Studio hata ayıklayıcı işleme ekler. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

   [Bu konudaki](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio uygulamalarında hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md) [hata ayıklama oturumunda gezinme (Xaml ve C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
