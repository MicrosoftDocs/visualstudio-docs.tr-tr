---
title: IDebugCoreServer2 | Microsoft Docs
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
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04ce01d03e1c6101fe971e126f57accc77a1a6bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738369"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, temsil ve ağ üzerindeki bir makinede bir sunucudan bilgi almak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Visual Studio, bir sunucu temsil etmek için bu arabirimi uygular. Visual Studio'nun her örneği, bu arabirim bir örneğini oluşturur.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Özel bağlantı noktası sağlayıcısı bir çağrıda bu arabirimin aldığı [olay](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Bu arabirim için bir çağrı aracılığıyla dolaylı olarak bir hata ayıklama altyapısı elde edebilirsiniz [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (döndüren [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), türetilmiş bir arabirim `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugCoreServer2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Bir makine özniteliklerini ve adını alır.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Bir makine adını alır.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Bir makinede var olan bağlantı noktası sağlayıcısı alır.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Bir makinede zaten bir bağlantı noktasını alır.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tüm bağlantı noktaları için bir numaralandırıcı bir makinede oluşturur.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tüm bağlantı noktası sağlayıcıları için bir numaralandırıcı bir makinede oluşturur.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Makine yardımcı programlar bir makine için alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, ağdaki makineler üzerinde çalışan işlemler göz atmak için Visual Studio tarafından da kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

