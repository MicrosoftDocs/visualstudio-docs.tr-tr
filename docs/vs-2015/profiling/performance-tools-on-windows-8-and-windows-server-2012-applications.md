---
title: Windows 8 ve Windows Server 2012 uygulamalarında performans araçları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e02ce9a9ef06574de999620017b96d470a76e6c9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767525"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 ve Windows Server 2012 uygulamalarında performans araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özelliklerine şekilde Visual Studio performans araçları de yapılan önemli değişiklikler bu platformlarda veri toplama gerekli. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bu konuda, Windows 8 ve Windows Server 2012 platformlarda değişiklikleri için performans araçları açıklanmaktadır.  
  
> [!NOTE]
>  Windows (Windows 7, Windows Server 2008 R2) desteklenen diğer sürümleri için performans araçları değişmedi.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [Visual Studio IDE Windows Store uygulamalarından şirket veri toplama](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Visual Studio IDE içinden masaüstünde Windows 8 veya Windows Server 2012'de çalışan uygulamaları üzerinde veri toplama](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Visual Studio IDE'den örnekleme kullanarak Windows Server 2012 veya Windows 8 masaüstünde çalışan uygulamalar üzerinde veri toplama](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Komut satırından profil oluşturma](#BKMK_Profiling_from_the_command_line)  
  
  [Katman etkileşimi (TIP) verileri toplama](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Visual Studio IDE Windows Store uygulamalarından şirket veri toplama  
 JavaScript ve HTML 5 yazılmış bir Windows Store uygulaması profil, JavaScript kodu için ölçümlü izleme verilerini toplayın. Windows Store uygulaması ya da Visual C++, Visual C# veya Visual Basic içinde yazılan bileşen profil, yerel ve yönetilen kod için örnekleme verileri toplayın. Uygulamanızı yerel olarak veya bir uzak makinede profil oluşturabilirsiniz.  
  
 Bu profil özellikleri ve seçenekleri, Windows Store apps profili oluşturulurken desteklenmez:  
  
- JavaScript uygulamaları örnekleme metodu kullanılarak profili oluşturma.  
  
- Araçlar yöntemini kullanarak, yönetilen ve yerel kod profil oluşturma.  
  
- Eşzamanlılık profili oluşturma  
  
- .NET bellek profili oluşturma  
  
- Katman etkileşimli profil oluşturma (TIP)  
  
- Örnekleme seçenekleri, örnekleme olay ve zamanlama aralığı ayarını veya ek performans sayacı verilerini toplama gibi.  
  
- Performans ve windows sayaç verileri toplama veya ek komut satırı seçenekleri belirtme gibi izleme seçenekleri.  
  
  Windows Store apps profil oluşturma hakkında daha fazla bilgi için Windows geliştirme Merkezi'ndeki aşağıdaki konulara bakın:  
  
  [Yerel makinede Microsoft Store uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Uzak makinede Microsoft Store uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Uygulama performansını analiz edin](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [JavaScript işlev zamanlaması](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Uzak cihaz üzerinde JavaScript işlev zamanlaması](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [JavaScript işlev zamanlaması verilerini çözümleme](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Profili Visual C++, Visual C# ve Visual Basic kodu yerel makinede Windows Store uygulamalarında](http://msdn.microsoft.com/en-us/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Uzak bir cihazdaki Windows Store uygulamalarında profil Visual C++, Visual C# ve Visual Basic kodu](http://msdn.microsoft.com/en-us/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Windows Store uygulamalarında Visual C++, Visual C# ve Visual Basic kodu için performans verilerini çözümleme](http://msdn.microsoft.com/en-us/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Visual Studio IDE içinden masaüstünde Windows 8 veya Windows Server 2012'de çalışan uygulamaları üzerinde veri toplama  
 Araçlar yöntemini kullanarak profil oluşturma Windows 8 için değiştirilmemiştir.  
  
 Katman etkileşimli profil oluşturma (TIP) örnekleme metodu kullanılarak desteklenmiyor.  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Visual Studio IDE'den örnekleme kullanarak Windows Server 2012 veya Windows 8 masaüstünde çalışan uygulamalar üzerinde veri toplama  
 Bu profil özellikleri ve seçenekleri Masaüstü uygulamalarını Windows 8 veya Windows Server 2012 uygulamalar örnekleme metodu kullanılarak profili oluşturulurken desteklenmez:  
  
-   Katman etkileşim profili oluşturma (TIP). İpucu verileri toplama araçları kullanılarak desteklenir.  
  
-   Örnekleme olay ve zamanlama aralığı ayarını veya ek performans sayacı verilerini toplama gibi örnekleme Seçenekleri'ni kullanın.  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> Komut satırından profil oluşturma  
 İki komut satırı araçları, Visual Studio yüklemesini olmayan cihazlar da dahil olmak üzere Windows 8 ve Windows Server 2012 cihazlarında, profil oluşturma verilerini toplamak için kullanın:  
  
|Araç adı|Açıklama|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Windows Store uygulamalarından profil oluşturma verilerini toplar ve Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamaları örnek profil oluşturma verileri toplar...|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|İzleme, eşzamanlılık ve katman etkileşimli profil oluşturma Windows 8 Masaüstü veya Windows Server 2012 üzerinde çalışan uygulamaların verileri toplar. Tüm profil oluşturma veri türlerini Windows'ın önceki sürümlerinden toplar.|  
  
 Her iki araçları, yerel bilgisayarda kullanım için Visual Studio ile yüklenir.  
  
 Profil için cihazlarında uygulamalar Visual Studio yüklü olmayan aşağıdakilerden birini yapın:  
  
-   Visual Studio için Uzak Araçlar'ın bir parçası olarak araçları indirin [MSDN web sitesinde](http://go.microsoft.com/fwlink/?LinkID=219549).  
  
-   Kopyalama ve bilgisayarınızda Visual Studio bağımsız profil oluşturucuyu araçları yükleme programını çalıştırın. Yükleme programları bulunan *VSInstallDir %* **tools\performance Tools\Setups** klasör. Uzak bilgisayarın işletim sistemi (x86/x64) için Kurulum programı seçin.  
  
> [!NOTE]
>  İpucu profil oluşturma verilerini toplamak için uzak bilgisayardaki Visual Studio makinenizden bağımsız profil oluşturucuyu yüklemeniz gerekir.  
  
 Bu profil özellikleri ve seçenekleri komut satırından Windows 8 ve Windows Server 2012 uygulamalarında profil oluşturma sırasında desteklenmez:  
  
-   Örnekleme modu ile kullanarak Windows 8 ve Windows Server 2012 web uygulamalarından veri toplamayı [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).  
  
-   VsPerfCmd.exe'ı kullanarak örnekleme verileri toplama.  
  
-   Örnekleme olay ve zamanlama aralığı ayarını veya ek performans sayacı verilerini toplama gibi örnekleme Seçenekleri'ni kullanın.  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> Katman etkileşimi (TIP) verileri toplama  
 Katman etkileşim profili oluşturma, ADO.NET Hizmetleri aracılığıyla veritabanları ile iletişim kuran çok katmanlı uygulamaların işlevlerini yürütme sürelerini hakkında ek bilgi sağlar. Verileri yalnızca zaman uyumlu işlev çağrıları için toplanır.  
  
 **Visual Studio sürümleri**  
  
 Katman etkileşimli profil oluşturma veri kullanarak toplanması [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], veya [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Ancak, katman etkileşimli profil oluşturma veri yalnızca görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] ve [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Windows 8 ve Windows Server 2012**  
  
1. Windows 8 Masaüstü veya Windows Server 2012 üzerinde çalışan uygulamaların katman etkileşim verileri toplamak için izleme metodunu kullanmanız gerekir.  
  
2. Windows Store uygulamaları için katman etkileşim verileri toplanamıyor.  
  
3. Desteklenen diğer Windows sürümünde tüm profil oluşturma yöntemlerini katman etkileşim verileri içerebilir.  
  
   **Performans Sihirbazı ve performans Gezgini**  
  
   Bir profil oluşturma yürütmesine katman etkileşim verileri toplama seçeneği performans Gezgini'nden eklemeniz gerekir. Ayrıca proje, yürütülebilir dosya veya Web performans Gezgini hedef düğüme eklemeniz gerekir. Bkz: [katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md).  
  
   **Uzak makinede ipucu verileri toplama**  
  
   Uzak makinede katman etkileşim verileri toplamak için kopyalamanız gereken **vs\_profil oluşturucu\_**_\<Platform >_ **\_**  _\<Dil >_**.exe** dosya _VSInstallDir %_**tools\performance Tools\Setups**klasöründe bir Visual Studio uzak bilgisayara makine ve yükleyin. Profil oluşturma araçları kullanamazsınız [Visual Studio uzak Araçları](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) paketini indirin.  
  
   Kullanabileceğiniz [VSPerfCmd](../profiling/vsperfcmd.md) veya [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) profil oluşturma verileri toplamak için.  
  
   **İpucu raporları**  
  
   Katman etkileşim verileri yalnızca içinde görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] veya [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE. Dosya tabanlı katman etkileşim raporlar aracılığıyla [VSPerfReport](../profiling/vsperfreport.md) kullanılabilir değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)   
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)



