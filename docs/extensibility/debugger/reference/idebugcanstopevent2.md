---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48f049648fcbd93d7ad7411a4dfeba8bbdb4431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105612"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Bu arabirim, geçerli kod konumda durdurulup durdurulmayacağı oturum hata ayıklama Yöneticisi'ni (SDM) istemek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) kaynak kod atlama desteklemek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi uygulanan, bu arabirimle aynı nesne üzerinde (SDM kullanan [QueryInterface](/cpp/atl/queryinterface) erişimi `IDebugEvent2` arabirimi).  
  
 Bu arabirim uygulaması SDM'ın çağrısı iletişim kurması gereken [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) hata ayıklama altyapısı. Örneğin, bu işleme iş parçacığında hata ayıklama altyapının iletiye gönderilen bir ileti ile yapılabilir veya bu arabirimi uygulayan nesne hata ayıklama altyapısı başvuru tutun ve hata ayıklama motoruna içine geçirilen bayrağı geri arama `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu yöntem kodu yürütme ve DE devam etmek için DE sorulan her zaman atlama DE gönderebilirsiniz. Bu olay kullanılarak gönderilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) ayıklanacak programın eklendiğinde SDM tarafından sağlanan geri çağırma işlevi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugCanStopEvent2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Bu olay nedeni alır.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Ayıklanacak program veya bu olayı (ve gönderme durdurma nedenini açıklayan bir olay) konumunda Durdur yalnızca yürütme devam belirtir.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Bu olay konumunu açıklar belge bağlamını alır.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Bu olay konumunu açıklar kod bağlamını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlev ve DE kullanıcı adımları hiçbir hata ayıklama bilgisi var. bulur veya hata ayıklama bilgileri var, ancak DE bu konumda görüntülenebilir kaynak kodunu bilmez DE bu arabirim gönderir.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)