---
title: Store uygulamalarında (JavaScript) hata ayıklama oturumu başlatın | Microsoft Docs
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e4105d8dda298dd0235acd113a9a0612265fbc0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055890"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>(JavaScript) Visual Studio'da Store uygulamaları için hata ayıklama oturumu başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Bu konu, HTML5 ve JavaScript ile yazılan Windows Store uygulamaları için hata ayıklama oturumu başlatmak açıklar. Tek bir tuş vuruşu ile hata ayıklama başlayabilir veya hata ayıklama oturumu belirli senaryolar için yapılandırmak ve uygulamayı başlatmak için yol seçin.

> [!NOTE]
>  XAML ve Visual C#, Visual C++ veya Visual Basic içinde yazılan uygulamalar için [(VB, C#, C++ ve XAML) bir hata ayıklama oturumu başlatın](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

##  <a name="BKMK_In_this_topic"></a> Bu konudaki
 [Bu konudaki](#BKMK_In_this_topic)

 [Hata ayıklama başlamanın en kolay yolu](#BKMK_The_easy_way_to_start_debugging)

 [Hata ayıklama oturumu yapılandırma](#BKMK_Configure_the_debugging_session)

- [Proje için hata ayıklama özellik sayfasını açın](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Yapı yapılandırma seçenekleri'ni seçin.](#BKMK_Choose_the_build_configuration_options)

- [Dağıtım hedefi seçin](#BKMK_Choose_the_deployment_target)

- [Kullanılacak hata ayıklayıcı seçin](#BKMK_Choose_the_debugger_to_use)

- [(İsteğe bağlı) Uygulamayı hata ayıklama oturumu başlatma gecikmesi](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(İsteğe bağlı) Ağ geri döngüler devre dışı bırak](#BKMK__Optional__Disable_network_loopbacks)

  [Hata ayıklama oturumu başlatma](#BKMK_Start_the_debugging_session)

- [(F5) hata ayıklamayı Başlat](#BKMK_Start_debugging__F5_)

- [Uygulama başlangıcı geciktirmek ancak (F5) hata ayıklamayı Başlat](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Yüklü bir uygulama hata ayıklayıcıda Başlat](#BKMK_Start_an_installed_app_in_the_debugger)

  [Çalışan bir uygulama için hata ayıklayıcının](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Hata ayıklama modunda çalıştırmak için uygulamayı Ayarla](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Hata ayıklayıcının](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Hata ayıklama başlamanın en kolay yolu
 ![Windows için yalnızca geçerli](../debugger/media/windows-only-content.png "windows_only_content")

1. Uygulama çözümünü Visual Studio'da açın.

2. Çözüm, hem Windows Store hem de Windows Store telefon uygulamaları için daha fazla proje içeriyorsa, hatalarını ayıklamak istediğiniz projeyi başlangıç projesi olduğundan emin olun. Çözümü keşfedin, projeyi seçin ve ardından **başlangıç projesi olarak ayarla** bağlam menüsünden.

3. F5 tuşuna basın.

   ![Windows Phone için yalnızca geçerli](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio, yapıları ve hata ayıklayıcısı ekli uygulamayı başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder. Daha fazla bilgi için [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).

##  <a name="BKMK_Configure_the_debugging_session"></a> Hata ayıklama oturumu yapılandırma
 Betik derlenmemiş olduğundan derleme yapılandırma ve platform ayarları geçerli değildir. Bir C++ ya da yönetilen bileşen hata ayıklaması yapıyorsanız ayarlamak **yapılandırma** için **hata ayıklama** ve hedef platformunuzu seçin **yapılandırma** iletişim.

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Proje için hata ayıklama özellik sayfasını açın

1.  Çözüm Gezgini'nde projeyi seçin. Kısayol menüsünde **özellikleri**.

2.  Genişletin **yapılandırma özellikleri** düğümünü seçip **hata ayıklama**

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Yapı yapılandırma seçenekleri'ni seçin.

1.  Gelen **yapılandırma** listesinde **hata ayıklama** veya **(etkin) hata ayıklama**.

2.  Gelen **Platform** liste oluşturmak için hedef platformu seçin. Çoğu durumda **herhangi bir CPU** en iyi seçenektir.

###  <a name="BKMK_Choose_the_deployment_target"></a> Dağıtım hedefi seçin
 Dağıtın ve Visual Studio makinesinde, yerel makinede veya uzak bir makinede Visual Studio benzeticide uygulama hata ayıklama. Hedeften seçtiğiniz **başlatmak için hata ayıklayıcı** listesini **hata ayıklama** projenin özellik sayfası.

 ![Windows için yalnızca geçerli](../debugger/media/windows-only-content.png "windows_only_content")

 Bir Windows Store uygulaması için şu seçeneklerden birini **hedef cihaz** listesi:

|||
|-|-|
|**Yerel Makine**|Uygulama geçerli oturumdaki yerel makinenizde hata ayıklayın. Bkz: [yerel makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simülatör**|Visual Studio simulator için uygulamada hata ayıklama [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar. Simülatör hata ayıklama cihazın işlevselliğini sağlayan masaüstü penceredir — dokunma hareketlerini ve cihaz döndürme gibi — yerel makinede mevcut değildir. Bkz: [simulator'da çalıştırma Windows Store apps](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Uzak makine**|İntranet üzerindeki yerel makineye bağlı veya bir Ethernet kablosuyla doğrudan bağlı bir cihazda uygulama hatalarını ayıklayın. Uzaktan hata ayıklamak için Visual Studio uzak araçları yüklü ve uzak cihazda çalışıyor olması gerekir. Bkz: [uzak bir makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Seçerseniz **uzak makine**, adını veya uzak makinenin IP adresini aşağıdaki yöntemlerden birini belirtin:

- Adını veya uzak makinenin IP adresi girin **makine adı** kutusu.

- Aşağı oku seçin **makine adı** seçin ve kutusunda  **\<bulun... >**. Uzak makineden ardından **uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu.

   ![Uzaktan hata ayıklayıcı bağlantısı Seç](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  Yerel alt ağı üzerinde olan makinelere ve Visual Studio makinesine, bir Ethernet kablosuyla doğrudan bağlı sanal makinelere uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu görüntüler. Başka bir makine belirtmek için adı girin. **makine adı** kutusu.

  ![Windows Phone için yalnızca geçerli](../debugger/media/phone-only-content.png "phone_only_content")

  Bir Windows Store Phone uygulaması için seçin **cihaz** veya öykünücüleri **hedef cihaz** listesi.

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Kullanılacak hata ayıklayıcı seçin
 Varsayılan olarak, hata ayıklayıcı uygulamanızda JavaScript kodu ekler. Yerel C++ ve JavaScript kodu yerine uygulamanızın bileşenlerinin yönetilen kod hata ayıklama seçebilirsiniz. Hata ayıklamak için kod belirttiğiniz **hata ayıklayıcı türü** listesini **hata ayıklama** uygulama projesinin özellik sayfası.

 Bu hata ayıklayıcıları birini **hata ayıklayıcı türü** listesi:

|||
|-|-|
|**Jenom skript**|Uygulamanızı JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel koda göz ardı edilir.|
|**Yalnızca yerel**|Uygulamanızı yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodunu göz ardı edilir.|
|**Betik ile yerel**|Yerel C++ kodunu ve uygulamanızı JavaScript kodunda hata ayıklayın.|
|**Yalnızca yönetilen**|Uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu ve yerel C/C++ kod göz ardı edilir.|
|**(Yönetilen ve yerel) karışık**|Yerel C/C++ kod ve uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu göz ardı edilir.|

###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> (İsteğe bağlı) Uygulamayı hata ayıklama oturumu başlatma gecikmesi
 Hata ayıklamaya başladığınızda varsayılan olarak, Visual Studio uygulama hemen başlar. Hata ayıklama oturumunu başlatmada ancak uygulamanızın başlangıç gecikme. Uygulama, hata ayıklayıcıda Başlat menüsünden veya etkinleştirme sözleşme başlatıldığında veya başka bir işlem veya metodu tarafından başlatıldığında başlatılır. Gecikmeli Başlatma, arka plan olayları uygulama çalışmıyorken meydana gelmesini istediğiniz uygulamanızda hata ayıklamak için de kullanabilirsiniz.

 Uygulamanızın lansmanını gecikme etkinleştirilip etkinleştirilmeyeceğini belirtin **uygulama Başlat** listesini **hata ayıklama** uygulama projesinin özellik sayfası. Bu seçeneklerden birini seçin:

-   Seçin **Hayır** uygulamanızın başlatma gecikme.

-   Seçin **Evet** uygulamayı hemen başlatın.

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (İsteğe bağlı) Ağ geri döngüler devre dışı bırak
 ![Windows için yalnızca geçerli](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedeniyle, standart bir biçimde yüklü bir Windows Store uygulaması, yüklü olduğu cihazın ağ çağrı yapmak için izin verilmiyor. Varsayılan olarak, Visual Studio dağıtımı bu kuraldan dağıtılmış uygulama için bir istisna oluşturur. Bu muafiyet iletişim yordamları tek bir makinede test etmenizi sağlar. Windows Store uygulamanızda göndermeden önce uygulamanızı muafiyet olmadan test etmeniz gerekir.

 Ağ geri döngüsüne muafiyetini kaldırmak için **Hayır** gelen **ağ geri döngüsüne izin** listesini **hata ayıklama** özellik sayfası.

##  <a name="BKMK_Start_the_debugging_session"></a> Hata ayıklama oturumu başlatma

###  <a name="BKMK_Start_debugging__F5_"></a> (F5) hata ayıklamayı Başlat
 Seçeneğini belirlediğinizde **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5), Visual Studio hata ayıklayıcısı ekli uygulamayı başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Uygulama başlangıcı geciktirmek ancak (F5) hata ayıklamayı Başlat
 Uygulamayı hata ayıklama modunda çalıştırabilir, ancak bunu hata ayıklayıcı dışında bir yöntem tarafından başlatılması izin için ayarlayabilirsiniz. Örneğin, başlatma Başlat menüsünden uygulamanızın hatalarını ayıklama veya uygulama başlatmadan bir arka plan işlemi uygulamasında hata ayıklamak için isteyebilirsiniz. Uygulama başlangıcı geciktirmek için şunu yapın:

1. Üzerinde **hata ayıklama** uygulamasının sayfası projesinin özellikleri **Hayır** gelen **uygulama Başlat** listesi.

2. Seçin **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5).

3. Başlat menüsünden bir yürütme sözleşme veya başka bir yordam tarafından uygulamanızı başlatın.

   Uygulamayı hata ayıklama modunda başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

   biçimindeki telefon numarasıdır. Arka plan görevleri hata ayıklama hakkında daha fazla bilgi için bkz. [tetikleyici askıya alma, sürdürme ve arka plan olaylarını Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Yüklü bir uygulama hata ayıklayıcıda Başlat
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

##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Çalışan bir uygulama için hata ayıklayıcının
 Hata ayıklayıcıyı iliştirmek için bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama, hata ayıklama modunda çalışacak şekilde ayarlamak için hata ayıklanabilir Paket Yöneticisi'ni kullanmalıdır. Hata ayıklanabilir Paket Yöneticisi ile Visual Studio uzak Araçları yüklenir.

 Bir uygulamaya haya yararlıdır Windows yüklü olduğu bir uygulama gibi zaten yüklü bir uygulamanın hatalarını ayıklamak için ihtiyacınız olduğunda depolama. Uygulama için kaynak dosyaları varsa, ancak uygulama için bir Visual Studio projesi yok ekleme gereklidir. Örneğin, Visual Studio projelerinin veya çözümlerinin kullanmayan bir özel yapı sistemi olabilir.

 Bir uygulamaya eklemek için:

1.  Uygulama hata ayıklama modunda çalışacak şekilde ayarlayın. Uygulamayı çalışır durumda olduğunda Bunun yapılması gerekir.

2.  Uygulamayı başlatın. Başlangıç menüsünde, bir yürütme sözleşme veya başka bir yöntem, uygulamayı başlatabilirsiniz.

3.  Hata ayıklayıcı, çalışan uygulamaya ekleyin.

###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Hata ayıklama modunda çalıştırmak için uygulamayı Ayarla

1.  Visual Studio uzak Araçlar, uygulamanın yüklendiği cihaza yükleyin. Bkz: [uzak araçları yükleme](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2.  Başlat menüsünde arama `Debuggable Package Manager` ve sonra başlatın.

     UygX hata ayıklama cmdlet'i için düzgün yapılandırılmış bir PowerShell penceresi görünür.

3.  Bir uygulamada hata ayıklamayı etkinleştirmek için uygulamanın Pakettamadı tanımlayıcısı belirtmeniz gerekir. Pakettamadı içeren tüm uygulamaların bir listesini görüntülemek için şunu yazın `Get-AppxPackage` PowerShell komut isteminde.

4.  PowerShell komut isteminde, girin `Enable-AppxDebug` *Pakettamadı* burada *Pakettamadı* uygulamanın Pakettamadı tanımlayıcısıdır.

###  <a name="BKMK_Attach_the_debugger"></a> Hata ayıklayıcının

> [!TIP]
>  JavaScript uygulamaları wwahost.exe işlem örneğinde çalışır. Uygulamaya ekleme yaptığınızda diğer JavaScript uygulamaları çalıştırıyorsanız, uygulamanın çalıştığı wwahost.exe sayısal işlem kimliğini (PID) bilmeniz gerekir.
>
>  Bu durumu düzeltmek için en kolay yolu, tüm diğer JavaScript uygulamaları kapatmak sağlamaktır. Aksi takdirde, uygulamayı başlatın ve wwahost.exe işlemlerin kimlikleri Not önce Windows Görev Yöneticisi'ni açın. Uygulamasındaki eklemek için bir işlem belirttiğinizde **kullanılabilir işlemler** iletişim kutusu, uygulamanın wwahost.exe not almış olanlardan çok farklı bir kimlik olacaktır.

 Hata ayıklayıcıyı iliştirmek için:

1. Üzerinde **hata ayıklama** menüsünde seçin **iliştirme**.

    **İliştirme** iletişim kutusu görüntülenir.

2. Uzak bir cihazdaki bir uygulamaya eklemek için Uzak cihazı belirtin **niteleyicisi** kutusu. Şunları yapabilirsiniz:

   -   Adı girin **niteleyicisi** kutusu.

   -   Aşağı oku seçin **niteleyicisi** kutusuna ve önce eklenmiş cihazların listesinden bir cihaz seçin.

   -   Seçin **Bul** yerel alt ağınız cihazlarda listesinden bir cihaz seçmek için.

3. Hata ayıklamak istediğiniz kod türünü belirtin **ekleme** kutusu.

    Seçin **seçin** ve ardından aşağıdakilerden birini yapın:

   -   Seçin **otomatik olarak hata ayıklanacak kodun türünü belirleme**

   -   Seçin **bu tür kodlarda hata ayıklama** ve ardından listeden bir veya daha fazla tür seçin.

4. İçinde **kullanılabilir işlemler** listesinde, uygun seçin **wwahost.exe** işlem. Kullanım **başlık** uygulamanızı tanımlamak için sütun.

5. Seçin **ekleme**.

   Visual Studio hata ayıklayıcı işleme ekler. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

## <a name="see-also"></a>Ayrıca Bkz.
 [Denetleme (JavaScript) hata ayıklama oturumunda yürütme](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) [tetikleyici askıya alma, sürdürme ve arka plan olaylarını Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [uygulamalarında hata ayıklama Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
