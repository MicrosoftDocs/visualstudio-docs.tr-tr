---
title: IEnumDebugThreads2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125472"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Bu interfac geçerli hata ayıklama oturumunda çalışan iş parçacıkları numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) bir programı iş parçacıklarında listesini temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) bir işlemde çalışan tüm programlar'ın tüm iş parçacıklarının listesini temsil eden bu arabirimi elde edilir. Çağrı [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) bir programı çalışan iş parçacıklarının listesini temsil eden bu arabirimi elde edilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IEnumDebugThreads2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Belirtilen bir numaralandırma sıralı iş parçacığı sayısını alır.|  
|[Atla](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Belirtilen bir numaralandırma dizisi içindeki iş parçacığı sayısı atlar.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Bir numaralandırma sırasını başlangıç durumuna sıfırlar.|  
|[kopya](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Geçerli olarak aynı sıralaması durumu içeren bir numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|İş parçacığı sayısını bir numaralandırıcı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio genellikle güncelleştirmek için bu arabirimi edinir **iş parçacığı** listesinin ilk iş parçacığı çağırmak için elde etmek için de penceresi [yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [devam](../../../extensibility/debugger/reference/idebugprocess3-continue.md), ve [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Devam etmek](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)