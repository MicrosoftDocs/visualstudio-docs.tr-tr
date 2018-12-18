---
title: Bir UWP uygulaması için hata ayıklama oturumu başlatın | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
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
ms.openlocfilehash: 181dec6bfa6ebe96528c39b74d68375b8eb7fcb8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062415"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>UWP uygulaması için hata ayıklama oturumu başlatma
  
Bu makalede, bir evrensel Windows Platformu (UWP) uygulamasına yönelik bir Visual Studio hata ayıklama oturumu başlatma açıklar. UWP uygulamaları, XAML ve C++ ve XAML yazılabilir ve C#/Visual Basic, veya HTML ve JavaScript. Bir UWP uygulamasında hata ayıklamayı başlatmak için hata ayıklama oturumu yapılandırmak ve uygulamayı başlatmak için yol seçin.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Visual Studio araç çubuğundaki hata ayıklamayı Başlat 
  
Standart Visual Studio araç çubuğundan yapılandırmak ve hata ayıklamayı başlatmak için en kolay yoludur. 

![Araç çubuğundaki hata ayıklama](../debugger/media/vsrun_select_target_device.png)  
  
1. Gelen **yapılandırma** üzerindeki açılır menüye **standart** araç, select **hata ayıklama**.  
  
1. Gelen **Platform** açılır listesinde, oluşturmak için hedef platformu seçin. 
   
1. Hata ayıklama hedefi yeşil okunun yanındaki açılır listeden seçin. Bir yerel makine, doğrudan bağlı bir cihaz, yerel Visual Studio simulator, uzak cihaz veya öykünücü seçebilirsiniz. 
   
1. Hata ayıklamayı başlatmak için yeşil seçin **Başlat** oku seçin veya araç **hata ayıklama** > **hata ayıklamayı Başlat**, veya basın **F5**. 
   
   Visual Studio, yapıları ve hata ayıklayıcısı ekli uygulamayı başlatır. 

Hata ayıklama, bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Dağıtım hedefi seçenekleri 
  
Visual Studio araç çubuğundaki hata ayıklama hedefi ayarlayabilirsiniz veya proje özellik sayfası hata ayıklama kılavuzuna. Aşağıdaki seçeneklerden birini seçin:

|||  
|-|-|  
|**Yerel Makine**|Uygulama geçerli oturumdaki yerel makinenizde hata ayıklayın.|  
|**Simülatör**|UWP uygulamaları için Visual Studio simulator uygulamasında hata ayıklayın. Simülatör ve yerel makinede yok cihaz döndürme, hareketler dokunma gibi cihaz işlevleri, benzetim masaüstü bir penceredir. Simülatör seçeneği kullanılabilir ancak uygulamanızın **hedef Platform Min. Sürüm** yerel makinede işletim sistemi küçük veya ona eşit. Daha fazla bilgi için [simulator'da çalıştırmak UWP uygulamaları](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Uzak makine**|Yerel makineye bir ağ veya Ethernet kablosu üzerinden bağlı bir cihazda uygulama hatalarını ayıklayın. Visual Studio için Uzak Araçlar, yüklü ve uzak cihaz üzerinde çalışıyor olması gerekir. Daha fazla bilgi için [uzak bir makinede çalıştırmak UWP uygulamaları](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**cihaz**|USB bağlantılı bir cihazda uygulama hatalarını ayıklayın. Cihazın Geliştirici kilidinin ve kilidi ekranında olması gerekir.|  
|**Mobile öykünücüsü**|Öykünücü adında belirtilen öykünücünün önyükleme, uygulamayı dağıtma ve hata ayıklamayı Başlat. Öykünücüler, yalnızca Hyper-V etkin makineler üzerinde kullanılabilir.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Proje özelliği sayfasında hata ayıklamayı Yapılandır 

Ek hata ayıklama seçeneklerini yapılandırmak için projenin hata ayıklama özellikleri sayfasını kullanın. 

**Hata ayıklama özelliklerini açmak için:**

1. İçinde **Çözüm Gezgini**, projeyi seçin ve ardından **özellikleri** simgesini veya projeye sağ tıklayıp seçin **özellikleri**.  
   
1. Sol tarafındaki **özellikleri** bölmesi:
   
   - İçin C# ve Visual Basic uygulamaları, select **hata ayıklama**.  
     
     ![C#ve Visual Basic proje hata ayıklama özellik sayfası](../debugger/media/dbg_csvb_debugpropertypage.png)  
   
   - C++ ve JavaScript uygulamaları için **yapılandırma özellikleri** > **hata ayıklama**.  
     
     ![C++ UWP uygulamasında hata ayıklama özellik sayfası](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Kullanılacak hata ayıklayıcı seçin  

İçin C# ve varsayılan olarak yönetilen kod Visual Basic uygulamalar, Visual Studio hatalarını düzeltir. Diğer veya ek kod türlerinde hata ayıklama seçebilirsiniz. Ayrıca **hata ayıklayıcı türü** projenin bir parçası olan herhangi bir arka plan görevleri için değerler.

C++ uygulamalarında Visual Studio, varsayılan olarak yerel kod hata ayıklamasına. JavaScript uygulamalar, Visual Studio, varsayılan olarak betik hata ayıklamasına. Belirli türlerdeki kod yerine veya ek olarak, yerel kod hatalarını ayıklamak seçebilirsiniz. 

**Hata ayıklanacak kod türlerini belirtmek için:**

- İçin C# ve Visual Basic uygulamaları aşağıdaki hata ayıklayıcıları birini seçin **uygulama türü** ve **arka plan işlem türü** bırakmalar altında **hata ayıklayıcı türü** üzerinde **hata ayıklama** özellik sayfası.  
  
- C + +/ JavaScript uygulamaları aşağıdaki hata ayıklayıcıları birini seçin **hata ayıklayıcı türü** üzerindeki açılır menüye **hata ayıklama** özellik sayfası.

|||  
|-|-|  
|**Yalnızca yönetilen**|Uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu ve yerel C/C++ kod göz ardı edilir.|  
|**Yalnızca yerel**|Uygulamanızı yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodunu göz ardı edilir.|  
|**(Yönetilen ve yerel) karışık**|Yerel C/C++ kod ve uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu göz ardı edilir. C++ projelerinde, bu seçenek olarak adlandırılan **yönetilen ve yerel**.|  
|**Komut Dosyası**|Uygulamanızı JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel koda göz ardı edilir.|  
|**Betik ile yerel**|Yerel C/C++ kod ve uygulamanızı JavaScript kodunda hata ayıklayın. Yönetilen kod yok sayılır. C++ projeleri yalnızca arka plan görevleri de kullanılabilir.|  
|**Yalnızca GPU (C++ AMP)**|Grafik işlem birimi (GPU) üzerinde çalışan yerel C++ kod hatalarını ayıklama. Yalnızca C++ projelerinde kullanılabilir.|  

  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (İsteğe bağlı) ağ geri döngüler devre dışı bırak 
  
 Güvenlik için standart bir biçimde yüklü bir UWP uygulaması üzerinde yüklü olduğu cihazın ağ çağrıları yapılamıyor. İletişim yordamları tek bir makinede test etmek visual Studio muaf uygulamalar bu kuraldan varsayılan olarak, dağıtılmış. Uygulamanızı yayımlamadan önce uygulamanızı muafiyet olmadan test etmeniz gerekir.  
  
**Ağ geri döngüsüne muafiyetini kaldırmak için:**  
  
-   İçin C# ve Visual Basic uygulamaları seçimini **yerel ağ geri döngüsüne izin ver** altındaki onay kutusunu **Başlat seçenekleri** üzerinde **hata ayıklama** özellik sayfası.  
  
-   Visual C++ ve JavaScript uygulamaları için **Hayır** gelen **yerel ağ geri döngüsüne izin** üzerindeki açılır menüye **hata ayıklama** özellik sayfası.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Hata ayıklama (isteğe bağlı) başlattığınızda uygulamayı yeniden yükleyin. 
 Yükleme sorunları tanılamak için bir C# veya Visual Basic uygulama, select **kaldırma ve paketimle yeniden yükle** üzerinde **hata ayıklama** özellik sayfası. Bu seçenek, hata ayıklamaya başladığınızda özgün yükleme yeniden oluşturur. Bu seçenek, C++ ve JavaScript projeleri için kullanılamaz.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Uzaktan hata ayıklama için kimlik doğrulama seçeneklerini ayarlama  
  
Varsayılan olarak, uzaktan hata ayıklayıcı seçtiğinizde çalıştırmak için Windows kimlik bilgilerini sağlamanız gerekir **uzak makine** dağıtım hedefi olarak. Kimlik doğrulama gereksinimini değiştirebilirsiniz. 

**Evrensel (şifrelenmemiş Protokolü)** kimlik doğrulama modudur oluşturan kişinin güncelleştirmesi veya üstü Windows 10 bilgisayarlarını ve IOT, Xbox ve HoloLens cihazlar.  

**Kimlik doğrulama yöntemini değiştirmek için:**  

- İçin C# ve Visual Basic uygulamaları üzerinde **hata ayıklama** özellik sayfasında **uzak makine** olarak **hedef cihaz**. Ardından, **hiçbiri** veya **Evrensel (şifrelenmemiş Protokolü)** için **kimlik doğrulama modu**. 
  
- C++ ve JavaScript uygulamaları için **uzak makine** altında **başlatmak için hata ayıklayıcı** üzerinde **hata ayıklama** özellik sayfası. Ardından, **kimlik doğrulaması yok** veya **Evrensel (şifrelenmemiş Protokolü)** için **kimlik doğrulama türü**. 
  
> [!CAUTION]
> Uzaktan hata ayıklayıcı çalıştırdığınızda, ağ güvenliği olan **hiçbiri** veya **Evrensel (şifrelenmemiş Protokolü)** modu. Bu modlardan olduğunuz yalnızca güvenilen ağlarda emin kötü amaçlı kod veya tehlikeli trafik etkilenmez seçin.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Hata ayıklama başlangıç seçenekleri  
  
Seçtiğinizde, **hata ayıklama** > **hata ayıklamayı Başlat** veya basın **F5**, Visual Studio hata ayıklayıcısı ekli uygulamayı başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Uygulama Başlangıç Gecikmesi hata ayıklamayı Başlat  

Anında hata ayıklamaya başladığınızda varsayılan olarak, Visual Studio uygulamayı başlatır. Uygulamayı hata ayıklama modunda çalıştırabilir, ancak hata ayıklayıcı dışında uygulamayı başlatmak için de ayarlayabilirsiniz. Örneğin, uygulama başlatma Windows gelen hata ayıklama isteyebilirsiniz **Başlat** menü veya bir arka plan işlemi uygulamasında hata ayıklama. Bu seçeneği seçerseniz, uygulama başlatmada hata ayıklayıcısı başlar. 

**Uygulamaları otomatik başlatma devre dışı bırakmak için:**  
  
- İçin C# ve Visual Basic uygulamaları, select **başlatma, ancak başlatıldığında kodumda Hata Ayıkla** altında **Başlat seçenekleri** üzerinde **hata ayıklama** özellik sayfası.  
   
- C++ ve JavaScript uygulamaları için **Hayır** gelen **uygulama Başlat** üzerindeki açılır menüye **hata ayıklama** özellik sayfası.  
  
Arka plan görevleri hata ayıklama hakkında daha fazla bilgi için bkz. [tetikleyici askıya alma, sürdürme ve arka plan olaylarını UWP uygulamaları için](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Yüklü olan veya çalışan bir UWP uygulamasında hata ayıklama 

Kullanabileceğiniz **yüklenen uygulama paketinin hatalarını ayıklama** zaten yüklü veya yerel veya uzak bir cihazda çalışan bir UWP uygulamasında hata ayıklamak için. Microsoft Store uygulaması yüklenmiş veya Visual Studio projesi olmayabilir. Örneğin, uygulamayı Visual Studio kullanmayan bir özel yapı sistemi olabilir.  
  
Yüklü uygulama hemen başlayabilir veya başka bir yöntemle başlatıldığında hata ayıklayıcısının çalışacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için [tetikleyici askıya alma, sürdürme ve arka plan olaylarını UWP uygulamaları için)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Yüklü olan veya çalışan bir UWP uygulamasında hata ayıklayıcıda başlatmak için seçin **hata ayıklama** > **diğer hata ayıklama hedefleri** > **yüklenen uygulama paketinin hatalarını ayıklama**. Daha fazla bilgi için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Hata ayıklayıcıyı çalışan bir Windows 8.x uygulamasına eklemek

Hata ayıklayıcıyı iliştirmek için bir [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uygulama, hata ayıklama modunda çalışacak şekilde ayarlamak için hata ayıklanabilir Paket Yöneticisi'ni kullanmalıdır. Hata ayıklanabilir Paket Yöneticisi, Visual Studio için Uzak Araçlar ile yüklenir.  
  
1. Uzak Araçlar, Visual Studio için uygulamanın yüklendiği cihaza yükleyin. Daha fazla bilgi için [uzak araçları yükleme](../debugger/remote-debugging.md).  
   
1. Windows içinde **Başlat** ekranında, arayın ve başlangıç **hata ayıklanabilir Paket Yöneticisi**.  
   
   UygX hata ayıklama cmdlet'i için düzgün yapılandırılmış bir PowerShell penceresi görünür.  
   
1. Uygulamanın Pakettamadı tanımlayıcısını belirtin. 
   
   1. Tüm uygulamaların Pakettamadı içeren bir listesini görüntülemek için şunu yazın `Get-AppxPackage` PowerShell komut isteminde.  
   
   1. PowerShell komut isteminde, girin `Enable-AppxDebug <PackageFullName>`burada \<Pakettamadı > uygulamasının Pakettamadı tanımlayıcısıdır.  
   
1. Seçin **hata ayıklama** > **işleme**.  
   
1. İçinde **iliştirme** iletişim kutusunda, uzak cihazı belirtin **bağlantı hedefi** kutusu. 
   
   Cihaz adını girin, açılır menüde arasından **bağlantı hedefi** kutusu ya da seçin **Bul** cihazı bulmak için **uzak bağlantıları** iletişim kutusu.  
   
1. Hata ayıklama, yanındaki istediğiniz kod türünü belirtmek için **ekleme** kutusunda **seçin**.  
   
1. İçinde **kod türünü seç** iletişim kutusunda, şunlardan birini seçin:
   - **Hata ayıklanacak kodun türünü otomatik olarak belirlemek**, veya 
   - **Bu tür kodlarda hata ayıklama**ve ardından listeden bir veya daha fazla kod türlerini seçin.  
   
1. İçinde **kullanılabilir işlemler** listesinde, hata ayıklamak için uygulama işlemini seçin.  
   
1. Seçin **ekleme**.  
  
 Visual Studio hata ayıklayıcı işleme ekler. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

> [!NOTE]
> JavaScript uygulamaları çalıştırma örneğinde *wwahost.exe* işlem. Birden fazla JavaScript uygulama çalışıyorsa, bu uygulamanızın sayısal işlem kimliğini (PID) bilmeniz gerekir *wwahost.exe* kendisine eklemek için bir işlem.  
> 
> Diğer tüm JavaScript uygulamaları kapatmak için JavaScript uygulamanıza eklemek için en kolay yolu olan. Ya da çalışan PID dikkat edin *wwahost.exe* işlemleri Windows görev uygulama başlamadan önce Yöneticisi'nde. Uygulamanızı, başlattığınızda, *wwahost.exe* PID olan, daha önce not ettiğiniz olanlardan farklı olacaktır.  

## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio’da uygulamaların hatalarını ayıklama](../debugger/debug-store-apps-in-visual-studio.md)   