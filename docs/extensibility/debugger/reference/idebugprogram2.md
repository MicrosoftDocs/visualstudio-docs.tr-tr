---
title: IDebugProgram2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392d9bd350d6207e6725c31c659a6edf1518a807
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122606"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Bu arabirim, bir işlemde çalışan bir program temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) ve özel bağlantı noktası tedarikçi bir işlemde bir programı temsil etmek için bu arabirimi uygular. Oturum hata ayıklama Yöneticisi'ni (SDM) de bilgi sağlamak için bu arabirimi uygulayan [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay bu arabirim için yeni bir program döndürür. Bu arabirim birden çok arabirimlerindeki birçok yöntem için parametre olarak da kullanılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugProgram2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Bu programı çalışan iş parçacıklarının numaralandırır.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Programın adını alır.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Bu programı çalıştırmayı işlem alır.|  
|[Sonlandırma](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Bu program sonlandırır.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Bu program ekler.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Hata ayıklama altyapısı (DE) bir programda ayırabilirsiniz belirler.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Bu programdan hata ayıklayıcı ayırır.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Bu program için bir genel benzersiz tanımlayıcısını alır.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Alır özellikleri program.|  
|[Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bu program durdurulmuş bir durumdan çalışmaya devam eder. Herhangi bir önceki yürütme durumu temizlenir.|  
|[Devam etmek](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bu program durdurulmuş bir durumdan çalışmaya devam eder. Herhangi bir önceki yürütme durumu korunur.|  
|[Adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Bir adımı gerçekleştirir.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Bu program yürütme sonraki durdurma isteği, kendi iş parçacığı çalıştırır kod defa.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Bu programı çalıştırmayı hata ayıklama altyapısı (DE) tanıtıcısı ve adını alır.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Bir kaynak dosyası belirtilen konumda kod bağlamları numaralandırır.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Bu program için bellek bayt alır.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Bu program veya bu programın parçası için ayrıştırılmış akışı alır.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Bu program yükledi ve yürütüyor modülleri numaralandırır.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Düzenle ve devam (ÇÖZÜCÜ) güncelleştirme bu program için alır.<br /><br /> Bu yöntem bir özel hata ayıklama altyapısı uygulamaz (her zaman döndürmelidir `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Bu programın kodunu yolları numaralandırır.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Bir döküm bir dosyaya yazar.|  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program bir işlem bir veya daha fazla program yapılır sırasında belirli bir çalışma zamanı mimaride çalışan iş parçacığı bir kapsayıcıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)