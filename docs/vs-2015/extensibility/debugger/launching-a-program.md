---
title: Program başlatma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3af2c1f571287a4a33c1dd57340e2a66197bd59
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753958"
---
# <a name="launching-a-program"></a>Program Başlatma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programda hata ayıklamak istediğiniz kullanıcıları, IDE'den hata ayıklayıcıyı çalıştırmak için F5 tuşuna basabilirsiniz. Bu, bir dizi nihai olarak hangi sırayla bağlı veya bağlı, programa şu şekilde bir hata ayıklama altyapısı (DE), IDE'nin bağlanırken neden olayı başlar:  
  
1. IDE, çözümün etkin proje hata ayıklama ayarları almak için proje paketi ilk çağırır. Ayarlar başlangıç dizinini, ortam değişkenleri, programın çalıştırılacağı bağlantı noktası ve program oluşturma işleminin belirtilmişse kullanmak için DE içerir. Bu ayarlar, hata ayıklama paketi geçirilir.  
  
2. Bir DE belirtilirse, program başlatmak için işletim sistemi DE çağırır. Program başlatma söz konusu kümelerdeki programın çalışma zamanı ortamının yüklü. Örneğin, bir program MSIL yazılmışsa, ortak dil çalışma zamanı programı çalıştırmak için çağrılır.  
  
    veya  
  
    Bir DE belirtilmezse, bağlantı noktası programın çalışma zamanı ortamı yüklenmesine neden programını başlatmak için işletim sistemi çağırır.  
  
   > [!NOTE]
   >  Bir programı başlatmak için kullanılan bir DE, aynı DE programa bağlı olasıdır.  
  
3. Olup DE veya bağlantı noktası program başlatıldı, bağlı olarak DE veya çalışma zamanı ortamı daha sonra bir program açıklaması veya düğümü oluşturur ve program çalışırken bağlantı noktasını bildirir.  
  
   > [!NOTE]
   >  Basit bir gösterimiyse hata ayıklaması yapılabilir bir program, program düğümü olduğu için çalışma zamanı ortamı program düğümü oluşturmanız önerilir. Yalnızca oluşturup bir program düğümünü kaydetmek için tüm DE yüklemek için gerek yoktur. DE tasarlanmışsa IDE, ancak hiçbir IDE sürecinde çalıştırmak için gerçekten çalıştıran, var. bağlantı noktasına bir program düğümü ekleyebilirsiniz bir bileşeni olması gerekir.  
  
   Diğer programları yanı sıra yeni oluşturulan programı ilişkili ilgisi olmayan, başlatılan veya aynı IDE'den hata ayıklama oturumu oluşturmak için ekli.  
  
   Programlı olarak kullanıcı ilk bastığında **F5**, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]'s paketinin Hatalarını Ayıkla çağırır (Bu başlatılmayı program türü ile ilişkili olan) proje paketi aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> sırayla doldurduğu yöntemi, bir <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> çözümün etkin proje hata ayıklama ayarlarıyla yapısı. Bu yapı hata ayıklama pakete yapılan bir çağrıyla geçirilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> yöntemi. Hata ayıklama paketi sonra hata ayıklaması ve herhangi ilişkili hata ayıklama motorlarını programı başlatan oturum hata ayıklama Yöneticisi (SDM) başlatır.  
  
   SDM için geçirilen bağımsız değişkenlerden biri DE programını başlatmak için kullanılacak GUID'dir.  
  
   DE GUID değilse `GUID_NULL`, SDM DE birlikte oluşturur ve ardından çağırır, [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) programını başlatmak için yöntemi. Örneğin, bir program sonra yerel kod halinde yazılmış `IDebugEngineLaunch2::LaunchSuspended` büyük olasılıkla çağıracak `CreateProcess` ve `ResumeThread` (programı çalıştırmak için Win32 işlevlerini).  
  
   Program başlatma söz konusu kümelerdeki programın çalışma zamanı ortamının yüklü. DE ya da çalışma zamanı ortamı oluşturur, ardından bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) bu arabirime geçirir ve program tanımlamak için arabirim [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) program bağlantı noktasını bildirmek için çalışıyor.  
  
   Varsa `GUID_NULL` gönderilir, ardından bağlantı noktası program başlatılır. Program çalışmaya başladığında, çalışma zamanı ortamı oluşturur bir `IDebugProgramNode2` geçirir ve program tanımlamak için arabirim `IDebugPortNotify2::AddProgramNode`. Bu, program çalışırken bağlantı noktası durumu bildirir. Ardından SDM çalışan programa hata ayıklama altyapısı ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Noktasına Bildirme](../../extensibility/debugger/notifying-the-port.md)  
 Bir program çalışıyor ve bağlantı noktası bildirim sonra ne olacağını açıklar.  
  
 [Başlatmadan Sonra Ekleme](../../extensibility/debugger/attaching-after-a-launch.md)  
 Hata ayıklama oturumunu DE program eklemek hazır olduğunda belgeler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)  
 Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerini bağlantılar içerir.

