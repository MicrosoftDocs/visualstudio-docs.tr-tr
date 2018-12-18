---
title: Program başlatma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ab4432eed95fd042bd35d34b6a42d3cd036fcf2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858374"
---
# <a name="launch-a-program"></a>Bir program Başlat
Bir programda hata ayıklamak istediğiniz kullanıcıları basabilirsiniz **F5** IDE'den hata ayıklayıcıyı çalıştırmak için. Bu, bir dizi nihai olarak hangi sırayla bağlı veya bağlı, programa şu şekilde bir hata ayıklama altyapısı (DE), IDE'nin bağlanırken neden olayı başlar:  
  
1. IDE, çözümün etkin proje hata ayıklama ayarları almak için proje paketi ilk çağırır. Ayarlar başlangıç dizinini, ortam değişkenleri, programın çalıştırılacağı bağlantı noktası ve program oluşturma işleminin belirtilmişse kullanmak için DE içerir. Bu ayarlar, hata ayıklama paketi geçirilir.  
  
2. Bir DE belirtilirse, program başlatmak için işletim sistemi DE çağırır. Program başlatma söz konusu kümelerdeki programın çalışma zamanı ortamı yükler. Örneğin, bir program MSIL yazılmışsa, ortak dil çalışma zamanı programı çalıştırmak için çağrılır.  
  
    veya  
  
    Bir DE belirtilmezse, bağlantı noktası programın çalışma zamanı ortamı yüklemeye neden programını başlatmak için işletim sistemi çağırır.  
  
   > [!NOTE]
   >  Bir programı başlatmak için kullanılan bir DE, aynı DE programa bağlı olasıdır.  
  
3. Olup DE veya bağlantı noktası program başlatıldı, bağlı olarak DE veya çalışma zamanı ortamı daha sonra bir program açıklaması veya düğümü oluşturur ve program çalışırken bağlantı noktasını bildirir.  
  
   > [!NOTE]
   >  Basit bir gösterimiyse hata ayıklaması yapılabilir bir program, program düğümü olduğu için çalışma zamanı ortamı program düğümü oluşturmanız önerilir. Yalnızca oluşturup bir program düğümünü kaydetmek için tüm DE yüklemek için gerek yoktur. DE tasarlanmışsa IDE, ancak hiçbir IDE sürecinde çalıştırmak için gerçekten çalıştıran, var. bağlantı noktasına bir program düğümü ekleyebilirsiniz bir bileşeni olması gerekir.  
  
   Diğer programları yanı sıra yeni oluşturulan programı ilişkili ilgisi olmayan, başlatılan veya aynı IDE'den hata ayıklama oturumu oluşturmak için ekli.  
  
   Programlı olarak kullanıcı ilk bastığında **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]'s paketinin Hatalarını Ayıkla çağırır (Bu başlatılmayı program türü ile ilişkili olan) proje paketi aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> sırayla doldurduğu yöntemi, bir <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> çözümün etkin proje hata ayıklama ayarlarıyla yapısı. Bu yapı hata ayıklama pakete yapılan bir çağrıyla geçirilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> yöntemi. Hata ayıklama paketi sonra hata ayıklaması ve herhangi ilişkili hata ayıklama motorlarını programı başlatan oturum hata ayıklama Yöneticisi (SDM) başlatır.  
  
   SDM için geçirilen bağımsız değişkenlerden biri DE programını başlatmak için kullanılacak GUID'dir.  
  
   DE GUID değilse `GUID_NULL`, SDM DE birlikte oluşturur ve ardından çağırır, [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) programını başlatmak için yöntemi. Örneğin, bir program, yerel kod halinde yazılmış `IDebugEngineLaunch2::LaunchSuspended` büyük olasılıkla çağıracak `CreateProcess` ve `ResumeThread` (programı çalıştırmak için Win32 işlevlerini).  
  
   Program başlatma söz konusu kümelerdeki programın çalışma zamanı ortamının yüklü. DE ya da çalışma zamanı ortamı oluşturur, ardından bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) bu arabirime geçirir ve program tanımlamak için arabirim [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) program bağlantı noktasını bildirmek için çalışıyor.  
  
   Varsa `GUID_NULL` gönderilir, ardından bağlantı noktası program başlatılır. Program çalışmaya başladığında, çalışma zamanı ortamı oluşturur bir `IDebugProgramNode2` geçirir ve program tanımlamak için arabirim `IDebugPortNotify2::AddProgramNode`. Bu, program çalışırken bağlantı noktası durumu bildirir. Ardından SDM çalışan programa hata ayıklama altyapısı ekler.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md)  
 Bir program çalışıyor ve bağlantı noktası bildirim sonra ne olacağını açıklar.  
  
 [Başlatmadan sonra ekleme](../../extensibility/debugger/attaching-after-a-launch.md)  
 Hata ayıklama oturumunu DE program eklemek hazır olduğunda belgeler.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)  
 Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerini bağlantılar içerir.