---
title: IDebugProgram2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0f89f024f0542b8cb20cfbf531fe9f7cf3da561
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741085"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir işlemde çalışan bir program temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) ve özel bağlantı noktası sağlayıcısı bir programda bir işlemi temsil etmek için bu arabirimi uygulayın. Oturum hata ayıklama Yöneticisi (SDM) da bilgileri sağlamak için bu arabirimi uygulayan [iliştirme](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay için yeni bir program bu arabirimi döndürür. Bu arabirim, birçok birden çok arabirim yöntemleri için parametre olarak da kullanılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugProgram2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Bu programa çalışan iş parçacıklarının numaralandırır.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Programın adını alır.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Bu programı çalıştırmayı işlemi alır.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Bu program sona erer.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Bu programa ekler.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Hata ayıklama altyapısı (DE) bir programdan ayırabilirsiniz belirler.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Hata ayıklayıcı bu programdan ayrılır.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Bu program için genel olarak benzersiz bir tanımlayıcı alır.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Alır özellikleri program.|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bu program bir durdurulmuş çalışmaya devam eder. Herhangi bir önceki yürütme durumu temizlenir.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bu program bir durdurulmuş çalışmaya devam eder. Herhangi bir önceki yürütme durumu korunur.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Bir adımı gerçekleştirir.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Bu program yürütme sonraki durdurma isteği, iş parçacığı kodun birini zaman.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Bu programı çalıştırmayı hata ayıklama altyapısı (DE) tanıtıcısı ve adını alır.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Belirli bir pozisyon kaynak dosyada kod bağlamları numaralandırır.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Bu program için bellek bayt alır.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Bu program veya bu programın bir parçası için Ayrıştırılmış kod akışı alır.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Bu program yüklendi ve yürütülmekte olan modülleri numaralandırır.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Bu program için Düzenle ve devam et (ENC) güncelleştirme alır.<br /><br /> Bu yöntem bir özel hata ayıklama altyapısı uygulamaz (her zaman döndürmelidir `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Bu programın kod yolları numaralandırır.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Bir döküm bir dosyaya yazar.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program, bir işlem bir veya daha fazla programlarını oluşur ancak belirli bir çalışma zamanı mimaride çalışan iş parçacığı bir kapsayıcıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

