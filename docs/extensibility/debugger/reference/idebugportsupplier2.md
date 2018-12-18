---
title: IDebugPortSupplier2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4aa26aa37b40c0e483342e6eb93cbac15bbbfc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119480"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Bu arabirim bağlantı noktalarına oturum hata ayıklama Yöneticisi'ni (SDM) sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Özel bir bağlantı noktası sağlayıcı bağlantı noktası tedarikçi temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı `CoCreateInstance` bir bağlantı noktası tedarikçi ile `GUID` (Bu, bu arabirimi sağlamak için tipik bir şekilde) bu arabirimini döndürür. Örneğin:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Çağrı [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) tarafından kullanılan geçerli bağlantı noktası tedarikçi temsil eden bu arabirimi döndürür [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) bağlantı noktası oluşturulan bağlantı noktası tedarikçi temsil eden bu arabirimini döndürür.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) listesini temsil `IDebugPortSupplier` arabirimleri ( `IEnumDebugPortSuppliers` öğesinden arabirimi elde [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), bağlantı noktası sağlayıcıların tümünü temsil eden kayıtlı ile[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Hata ayıklama altyapısı genellikle bir bağlantı noktası tedarikçi ile etkileşime girmez.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugPortSupplier2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Bağlantı noktası sağlayıcı adını alır.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Bağlantı noktası tedarikçi tanımlayıcısını alır.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Bir bağlantı noktası listesinden bir bağlantı noktası tedarikçi alır.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Zaten mevcut bağlantı noktalarını numaralandırır.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Bir bağlantı noktası tedarikçi yeni bağlantı noktaları ekleme desteklediğini doğrular.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Bir bağlantı noktası ekler.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Bir bağlantı noktası kaldırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bağlantı noktası sağlayıcı adı ve kimliği ile kendini tanıtmak, eklemek ve bağlantı noktalarını kaldırın ve bağlantı noktası tedarikçi sağlayan tüm bağlantı noktaları numaralandırır.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)