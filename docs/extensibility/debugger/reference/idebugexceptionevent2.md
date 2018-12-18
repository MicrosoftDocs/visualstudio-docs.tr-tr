---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f2cb866c12cacc2c0fcc81c3021e7cc5af448d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119682"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Şu anda yürütülmekte olan programa bir özel durum oluştuğunda hata ayıklama altyapısı (DE) Bu arabirim oturum hata ayıklama Yöneticisi (SDM) gönderir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE ayıklanacak programa bir özel durum oluştu rapor için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi uygulanan, bu arabirimle aynı nesne üzerinde. SDM kullanan [QueryInterface](/cpp/atl/queryinterface) erişimi `IDebugEvent2` arabirimi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Aygıtların oluşturur ve bir özel durum raporlamak için bu olay nesnesi gönderir. Olay kullanılarak gönderilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) ayıklanacak programın eklendiğinde, SDM tarafından sağlanan geri çağırma işlevi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugExceptionEvent2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Bu olay şu özel durum hakkında ayrıntılı bilgi alır.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Bu olay şu özel durum okunabilir bir açıklamasını alır.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Hata ayıklama altyapısı (DE) yürütme devam ettiğinde ayıklanacak programın bu özel durum geçirme seçeneğiniz destekleyip desteklemediğini belirler.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Özel durum yürütme devam ettiğinde ayıklanacak programın geçirileceğini ya da özel durum atılmalıdır belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Açıklamalar  
 Bu özel durum olayı ilk fırsat veya ikinci fırsat özel durum önceki çağrısıyla belirlendiyse, görmek için DE denetler olay göndermeden önce [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). İlk fırsat özel durum olarak belirlenmişse `IDebugExceptionEvent2` olay SDM gönderilir. Aksi durumda, uygulamaya özel durumu işlemek için bir fırsat DE sunar. Hiçbir özel durum işleyicisi verdiyse ve özel bir ikinci fırsat özel durum belirlendiyse `IDebugExceptionEvent2` olay SDM gönderilir. Aksi takdirde, programın yürütülmesi DE sürdürür ve işletim sistemi veya çalışma zamanı özel durumu işler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)