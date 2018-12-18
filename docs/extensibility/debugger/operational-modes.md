---
title: Çalışma modları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91f3339fd18db8c006855c634e011b14eecc9206
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888949"
---
# <a name="operational-modes"></a>Çalışma modları
Üç moddan, IDE, şu şekilde çalışabilir vardır:  
  
- [Tasarım modu](#vsconoperationalmodesanchor1)  
  
- [Çalıştırma modu](#vsconoperationalmodesanchor2)  
  
- [Kesme modu](#vsconoperationalmodesanchor3)  
  
  Özel hata ayıklama altyapısı (DE) bu modları arasında nasıl geçiş geçiş yöntemleriyle ilgili bilgi sahibi olmasını gerektiren bir uygulama kararıdır. DE olabilir veya doğrudan bu modlardan uygulayamaz. Bu gerçekten kullanıcı eylemi veya DE olayları temel alarak geçiş hata ayıklama paketi modları modlarıdır. Örneğin, bir DE durdurma olayından tarafından kesme modu için çalışma moduna geçiş instigated. Sonu modunda veya adım modunda çalıştırın ya da geçiş adımı veya çalıştırma gibi işlemleri gerçekleştiren kullanıcı tarafından instigated. DE geçiş hakkında daha fazla bilgi için bkz: [yürütme denetimi](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Tasarım modu  
 Tasarım modu süre içerisinde hata ayıklama uygulamanızda özellikleri ayarlayabilirsiniz Visual Studio hata ayıklama, nonrunning durum şeklindedir.  
  
 Yalnızca birkaç hata ayıklama özellikleri, Tasarım modunda kullanılır. Bir geliştirici, kesme noktaları ayarlamak veya izleme ifadeleri oluşturmak tercih edebilirsiniz. DE hiçbir zaman yüklendi veya IDE tasarım modundayken çağrılır. DE ile etkileşim yalnızca çalıştırma ve kesme modu sırasında gerçekleşir.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Çalıştırma modu  
 IDE içinde hata ayıklama oturumunda bir program çalıştığında çalışma modunda gerçekleşir. Uygulama, bir kesme noktasına isabet kadar veya bir özel durum kadar sonlandırma kadar çalışır. Sonlandırma, Tasarım modunda DE geçişleri için uygulama çalıştırıldığında. Bir kesme noktasına isabet ya da bir özel durum kesme modu için DE geçer.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Kesme modu  
 Kesme modu, hata ayıklama programın yürütülmesini askıya alındığında gerçekleşir. Kesme moduna Geliştirici sonuna uygulamanın anlık görüntüsünü sunar ve uygulama durumunu çözümlemek ve uygulamanın nasıl çalıştırılacağını değiştirmek geliştiricinin sağlar. Geliştirici görüntüleyebilir ve kodu düzenleyin, inceleyin veya verileri değiştirme, uygulamayı yeniden başlatın, yürütme bitiş veya aynı noktasından yürütmeye devam et.  
  
 Kesme moduna DE zaman uyumlu durdurma olay gönderme sırasında girilir. Durdurma olaylar olarak da bilinir, zaman uyumlu durdurma olayları bildirmek oturum hata ayıklama Yöneticisi (SDM) ve IDE, ayıklanan uygulamayı kod yürütme durduruldu. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri durdurma olayları örnekleri verilmiştir.  
  
 Geçiş hata ayıklayıcı kesme modundan modu adımı veya çalıştırmak için aşağıdaki yöntemlerden birini yapılan bir çağrıyla durdurma olayları ettirilen:  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Adım modu  
 Adım modu, program kodu veya içine, üzerinden veya bir işlev dışına sonraki satıra adımlar oluşur. Yöntemini çağırarak bir adımı yürütülür [adım](../../extensibility/debugger/reference/idebugprocess3-step.md). Bu yöntem gerektirir `DWORD`belirtin s [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) ve [STEPKIND](../../extensibility/debugger/reference/stepkind.md) giriş parametresi olarak listeleme.  
  
 Program kodu veya bir işlev uygulamasına sonraki satıra başarıyla adımları ya da imleç ya da bir kesme noktası Ayarla çalıştığı DE otomatik olarak geri kesme modu geçer.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yürütme denetimi](../../extensibility/debugger/control-of-execution.md)