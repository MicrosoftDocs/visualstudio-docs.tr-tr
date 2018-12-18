---
title: Idebugapplication110 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793973"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 Arabirimi
`IDebugApplication110` Arabirimi işlevselliğini genişleten [Idebugapplication arabirimi](../../winscript/reference/idebugapplication-interface.md). Bu arabirim örneği uygulaması üzerinde QueryInterface çağırarak alabilirsiniz [Idebugapplication arabirimi](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Bu arabirim PDM v11.0 ve sonraki sürümler tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 `IDebugApplication110` Arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Zaman uyumlu bir çağrı ana iş parçacığı üzerinde yapar.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Zaman uyumsuz bir çağrı ana iş parçacığı üzerinde yapar.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Herhangi bir yandan bildirilmesini belirtilen tanıtıcıları bekler bu iş parçacığına gönderilen çağrıları iş parçacıkları arası. Bu yöntem, hata ayıklayıcı iş parçacığından çağrılmalıdır.|