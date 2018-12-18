---
title: Idebugapplicationthread110 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794060"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 Arabirimi
İçin daha fazla işlevsellik sağlayan [Idebugapplicationthread arabirimi](../../winscript/reference/idebugapplicationthread-interface.md) arabirimi.  
  
> [!IMPORTANT]
>  Bu arabirim PDM v11.0 ve sonraki sürümler tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 `IDebugApplicationThread110` Arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Zaman uyumsuz bir çağrı ana iş parçacığı üzerinde yapar.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Kaç tane iş parçacığı istekleri mekanizmaları geçiş PDM'ın iş şu anda işleme sayısı. Genellikle 0 veya 1, ancak bu bir iş parçacığı arama işlemi başlatır, ancak iş parçacığı dışında bir zaman uyumlu çağrıyı tetikler veya aksi takdirde iş parçacığı askıya alır (örneğin, hata ayıklayıcıyı veren IDebugApplicationEvents olay tetikleme tarafından daha yüksek olması olası iş parçacığı)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) bu iş parçacığında çağrılır ve henüz tamamlanmadı.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Bu iş parçacığı (örneğin, SynchronousCallInThread) mekanizmaları geçiş PDM'ın iş parçacığı kullanılarak yapılan çağrıları işleyebilecek bir durumda değil.|