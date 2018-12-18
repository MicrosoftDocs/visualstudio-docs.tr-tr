---
title: Nasıl tetikleyeceğinizi askıya alma, sürdürme ve arka plan olaylarını Windows Store uygulamaları için
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
- vs.debug.error.background_task_activate_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 610614614b47caa04115b8a469793cfca94c666b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061879"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio"></a>Visual Studio'daki Windows Mağazası uygulamaları için askıya alma, sürdürme ve arka plan olayları nasıl tetiklenir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ne zaman değil ayıkladığınız Windows **işlem ömrü Yönetimi** (PLM), uygulamanızın yürütme durumunu denetler — başlatma, askıya alma, sürdürme ve uygulama yanıt kullanıcı eylemleri ve cihaz durumu olarak sonlandırılıyor. Windows hata ayıklaması yapıyorsanız, bu etkinleştirme olaylarını devre dışı bırakır. Bu konu, hata ayıklayıcı bu olayları tetiklemesine açıklar.

 Bu konuda ayrıca hata ayıklama işlemini açıklamaktadır **arka plan görevleri**. Arka plan görevlerinin bile, uygulama çalışmıyorken bir arka plan işlemi belirli işlemlerin gerçekleştirilmesi etkinleştirin. Uygulamanızı hata ayıklama moduna için hata ayıklayıcı kullanabilirsiniz ve ardından — UI başlatmadan — başlatın ve arka plan görevinin hatalarını ayıklama.

 İşlem ömrü yönetimi ve arka plan görevleri hakkında daha fazla bilgi için bkz. [devam ettirme, başlatma ve çoklu](http://msdn.microsoft.com/en-us/04307b1b-05af-46a6-b639-3f35e297f71b).

##  <a name="BKMK_In_this_topic"></a> Bu konudaki
 [Tetikleyici işlem ömrü Yönetimi olayları](#BKMK_Trigger_Process_Lifecycle_Management_events)

 [Tetikleyici arka plan görevleri](#BKMK_Trigger_background_tasks)

- [Standart hata ayıklama oturumunda bir arka plan görevi olay tetikleme](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)

- [Uygulamayı çalışır durumda değilken bir arka plan görevi tetikleyin](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)

  [İşlem ömrü yönetimi olaylarını tetiklemek ve arka plan görevleri yüklü bir uygulamadan](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)

  [Arka plan görevi etkinleştirmesi hatalarını tanılama](#BKMK_Diagnosing_background_task_activation_errors)

##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Tetikleyici işlem ömrü Yönetimi olayları
 Kullanıcı veya Windows düşük güç durumu girdiğinde uzağa geçtiğinde Windows uygulamanız askıya alabilirsiniz. Yanıt verebilirsiniz `Suspending` olay kalıcı depolama için ilgili uygulama ve kullanıcı verileri kaydetmeyi ve kaynaklar serbest bırakılacaksa. Ne zaman uygulama sürdürüldü gelen **askıya alındı** durum geçirilmeden **çalıştıran** durum ve askıya alındığında sırada nerede olduğu gelen devam eder. Yanıt verebilirsiniz `Resuming` geri yüklemek veya uygulama durumunu yenileyin ve kaynaklarınızı geri kazanmanız için olay.

 Bellekte mümkün olduğunca çok askıya alınan uygulamaları korumak Windows çalışır ancak bellekte tutmak için yeterli kaynak yoksa Windows uygulamanızı sonlandırabilirsiniz. Bir kullanıcı da açıkça uygulamanızı kapatabilirsiniz. Kullanıcı bir uygulamanın kapatıldığını belirten özel olay yok.

 Visual Studio hata ayıklayıcıda, el ile askıya alma, sürdürme ve uygulamalarınızın yaşam döngüsü olayları işleme hata ayıklama sonlandırın. Bir işlem yaşam döngüsü olayı hata ayıklamak için:

1.  Hata ayıklamak istediğiniz olay işleyicisinde bir breakpooint ayarlayın.

2.  Tuşuna **F5** hata ayıklama başlatılamıyor.

3.  Üzerinde **hata ayıklama konumu** araç ateşlenmesine istediğiniz olayı seçin:

     ![Askıya alma, sürdürme, sonlandırma ve arka plan görevleri](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

     Unutmayın **askıya alma ve sonlandırma** uygulama kapanır ve hata ayıklama oturumu sona erer.

##  <a name="BKMK_Trigger_background_tasks"></a> Tetikleyici arka plan görevleri
 Herhangi bir uygulama bile uygulama çalışmıyorken belirli sistem olaylara yanıt vermek için bir arka plan görevi olarak kaydedebilirsiniz. Arka plan görevleri doğrudan kullanıcı Arabirimi güncelleştirmeleri kod çalıştıramazsınız; Bunun yerine, bunlar kullanıcıya güncelleştirmeleri kutucuk, rozet güncelleştirmeleri ve kutlama bildirimleri için bilgileri gösterir. Daha fazla bilgi için [arka plan görevleri uygulamanızla destekleme](http://msdn.microsoft.com/en-us/4c7bb148-eb1f-4640-865e-41f627a46e8e)

 Uygulamanız için arka plan görevleri, hata ayıklayıcı'dan başlayan olayları tetikleyebilir.

> [!NOTE]
>  Hata ayıklayıcı, cihaz durumu değişikliği belirten olaylar gibi verileri içermeyen olayları tetikleyebilir. Kullanıcı girişini veya diğer veri gerektiren bir arka plan görevleri el ile tetiklemek sahip.

 Uygulamanız çalışmıyorken bir arka plan görev olayı tetiklemek için en gerçekçi yoludur. Ancak, standart hata ayıklama oturumunda olarak olay tetiklemeyi de desteklenir.

###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Standart hata ayıklama oturumunda bir arka plan görevi olay tetikleme

1.  Arka plan görevi kodda hata ayıklamak istediğiniz bir kesme noktası ayarlayın.

2.  Tuşuna **F5** hata ayıklama başlatılamıyor.

3.  Üzerinde olaylar listesinden **hata ayıklama konumu** araç başlamak istiyorsanız arka plan görevi seçin.

     ![Askıya alma, sürdürme, sonlandırma ve arka plan görevleri](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Uygulamayı çalışır durumda değilken bir arka plan görevi tetikleyin

1.  Arka plan görevi kodda hata ayıklamak istediğiniz bir kesme noktası ayarlayın.

2.  Başlangıç projesi için hata ayıklama özellik sayfasını açın. Çözüm Gezgini'nde projeyi seçin. Üzerinde **hata ayıklama** menüsünde seçin **özellikleri**.

     C++ projeleri için genişletmeniz gerekebilir **yapılandırma özellikleri** seçip **hata ayıklama**.

3.  Aşağıdakilerden birini yapın:

    -   Visual C# ve Visual Basic projeleri seçin **başlatma, ancak başlatıldığında kodumda Hata Ayıkla**

         ![C&#35;&#47;VB hata ayıklama başlatma uygulama özelliği](../debugger/media/dbg-csvb-dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    -   JavaScript ve Visual C++ projeleri için seçin **Hayır** gelen **uygulama başlatma** listesi.

         ![C&#43;&#43;&#47;VB başlatma uygulama hata ayıklama özelliği](../debugger/media/dbg-cppjs-dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4.  Tuşuna **F5** uygulama hata ayıklama moduna yerleştirilecek. Not **işlem** listesini **hata ayıklama konumu** araç, hata ayıklama modunda olduğunu belirtmek için uygulama paketi adı görüntüler.

     ![Arka plan görev işlemi listesi](../debugger/media/dbg-backgroundtask-processlist.png "DBG_BackgroundTask_ProcessList")

5.  Üzerinde olaylar listesinden **hata ayıklama konumu** araç başlamak istiyorsanız arka plan görevi seçin.

     ![Askıya alma, sürdürme, sonlandırma ve arka plan görevleri](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> İşlem ömrü yönetimi olaylarını tetiklemek ve arka plan görevleri yüklü bir uygulamadan
 Hata ayıklayıcıya zaten yüklü bir uygulama yüklemek için yüklü uygulamayı hata ayıklama iletişim kutusunu kullanın. Örneğin, Windows mağazası veya hata ayıklama uygulama ancak bir Visual Studio için kaynak dosyalara sahip olduğunda uygulamanın proje için uygulamanın yüklü olduğu bir uygulamayı hata ayıklama. Yüklü uygulama hata ayıklama iletişim kutusu, hata ayıklama modunda Visual Studio makinenizde veya uzak bir cihazda ya da hata ayıklama modunda çalıştırabilir, ancak başlatma ayarlamak için bir uygulama Başlat sağlar. Bkz **yüklü bir uygulama hata ayıklayıcıda Başlat** ya da bölümünü [JavaScript](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Start_an_installed_app_in_the_debugger) veya [Visual C++, Visual C# ve Visual Basic](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md#BKMK_Start_an_installed_app_in_the_debugger) sürümlerini **başlatma hata ayıklama oturumu** daha fazla bilgi için.

 Hata ayıklayıcıya uygulama yüklendikten sonra yukarıda açıklanan yordamlardan herhangi birini kullanabilirsiniz.

##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Arka plan görevi etkinleştirmesi hatalarını tanılama
 Arka plan altyapısı için Windows Olay Görüntüleyicisi'nde tanılama günlükleri, tanılama ve arka plan görevi hatalarında sorun giderme için kullanabileceğiniz ayrıntılı bilgiler içeriyor. Günlüğü görüntülemek için:

1.  Olay Görüntüleyici uygulamasını açın.

2.  İçinde **eylemleri** bölmesinde seçin **görünümü** emin **Analitik ve hata ayıklama günlüklerini göster** denetlenir.

3.  Üzerinde **Olay Görüntüleyicisi'ni (yerel)** ağacında, düğümleri genişletin **uygulama ve hizmet günlükleri** / **Microsoft** / **Windows**   /  **BackgroundTasksInfrastructure**.

4.  Seçin **tanılama** günlük.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio ile Store uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md) [uygulamaları Visual Studio'da hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md) [uygulama yaşam döngüsü](http://msdn.microsoft.com/en-us/53cdc987-c547-49d1-a5a4-fd3f96b2259d) [devam ettirme, başlatma ve çoklu](http://msdn.microsoft.com/en-us/04307b1b-05af-46a6-b639-3f35e297f71b)
