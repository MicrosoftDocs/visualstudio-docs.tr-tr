---
title: IDebugProcess2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77adecb0f3aef5a9c9d0fc8a05e6b44016dd9ae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121381"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Bu arabirim, bir bağlantı noktası üzerinde çalışan bir işlemi temsil eder. Yerel bağlantı noktası, bağlantı noktası ise, `IDebugProcess2` genellikle yerel makinedeki fiziksel bir işlem temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bu arabirim, bir grup olarak programları yönetmek için özel bir bağlantı noktası sağlayıcı tarafından uygulanır. Bu arabirim bağlantı noktası sağlayıcı tarafından uygulanmalıdır.  
  
 Bir program aracılığıyla başlatmayı destekliyorsa, hata ayıklama altyapısı da bu arabirimi uygulayan [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, bu işlemde tanıtılan programlar grubu ile etkileşim kurmak için öncelikle oturum hata ayıklama Yöneticisi tarafından (SDM) adı verilir.  
  
 Çağrı [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) veya [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) bu arabirimi alınamıyor. Bu arabirim, ayrıca çağrılarak döndürülür `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugProcess2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|İşlemin açıklamasını alır.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Bu işlemde bulunan programları numaralandırır.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Başlık, kolay ad veya işlemin dosya adını alır.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Bu işlemin çalıştığı bir makine sunucusu örneğini alır.|  
|[Sonlandırma](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|İşlemi sonlandırır.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|İş akışına ekler.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM işlem ayırma durumunda belirler.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Hata ayıklayıcı işleminden ayırır.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Sistem işlemi tanımlayıcısını alır.|  
|[Getprocessıd](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Bu işlem için bir genel benzersiz tanımlayıcısını alır.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [KULLANIM DIŞI]|İşlem hata ayıklama oturumu adını alır.<br /><br /> [KULLANIM DIŞI. GEREKEN HER ZAMAN İADE `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|İşlemde çalışan iş parçacıkları numaralandırır.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Bu işlem durdurma kodu çalışan sonraki program isteklerine.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Bu işlemin çalıştığı bağlantı noktasını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `IDebugProcess2` birini veya birkaçını içeriyor [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimleri.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Sonraki](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)