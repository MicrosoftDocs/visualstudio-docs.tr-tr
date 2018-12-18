---
title: IDebugBreakEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adfe4bf801d419d2eb25ba2191a180ca261a6c3f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103302"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Bu arabirim oturum hata ayıklama Yöneticisi'ni (SDM) zaman uyumsuz bir sonu başarıyla tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE bir program kullanıcı sonları desteklemek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi uygulanan, bu arabirimle aynı nesne üzerinde (SDM kullanan [QueryInterface](/cpp/atl/queryinterface) erişimi `IDebugEvent2` arabirimi).  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 SDM çağrıları [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) zaman kullanıcı istedi Duraklatılacak ayıklanacak program. Program başarıyla duraklatıldı zaman DE gönderir `IDebugBreakEvent2` olay. Bu olay kullanılarak gönderilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) ayıklanacak programın eklendiğinde SDM tarafından sağlanan geri çağırma işlevi.  
  
## <a name="remarks"></a>Açıklamalar  
 Örneğin, bir kullanıcı seçebilirsiniz **sonu tüm** komutunu **hata ayıklama** menü sonsuz bir döngüde çalıştırılan bir program dışında bölün. SDM çağırarak durdurmak için program söyler [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). DE gönderir `IDebugBreakEvent2` program son olarak durduğunda.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)