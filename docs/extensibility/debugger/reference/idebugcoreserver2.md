---
title: IDebugCoreServer2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce3e4c0c933527a5db754dcd96de97283e6e8260
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107572"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Bu arabirimi temsil eder ve ağ üzerindeki bir makinede bir sunucudan bilgi almak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Visual Studio bir sunucu temsil etmek için bu arabirimi uygular. Visual Studio her örneği bu arabiriminin bir örneğini oluşturur.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Özel bir bağlantı noktası tedarikçi çağrıda bu arabirimin aldığı [olay](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Hata ayıklama altyapısı bu arabirimi yapılan bir çağrı üzerinden dolaylı olarak elde edebilirsiniz [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (döndüren [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), türetilmiş bir arabirim `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugCoreServer2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Bir makine özniteliklerini ve adını alır.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Bir makine adını alır.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Mevcut bir bağlantı noktası tedarikçi bir makinede alır.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Bir makine üzerinde zaten bir bağlantı noktası alır.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tüm bağlantı noktaları için bir numaralandırıcı bir makinede oluşturur.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tüm bağlantı noktası tedarikçileri için bir numaralandırıcı bir makinede oluşturur.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Makine yardımcı programlar için bir makine alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, Visual Studio tarafından ağdaki makinelerde çalışan işlemler göz atmak için de kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)