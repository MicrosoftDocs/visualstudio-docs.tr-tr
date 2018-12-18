---
title: IDebugField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2ff92f339568a6a20e2f85a0b2deae9c8db244f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116308"
---
# <a name="idebugfield"></a>IDebugField
Bu arabirim bir alanı başka bir deyişle, bir simge veya türü açıklamasını temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bir simge sağlayıcısı, tüm alanlar için temel sınıf olarak bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, tüm alanlar için temel sınıftır. Dönüş değerine göre [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), bu arabirimi kullanarak daha özel arabirimleri döndürebilir [QueryInterface](/cpp/atl/queryinterface). Ayrıca, birçok arabirimleri dönmesini `IDebugField` çeşitli yöntemlerle nesneleri.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugField`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Simge veya türü görüntülenebilir bilgilerini alır.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Alan türünü alır.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Alan türünü alır.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Alan kapsayıcısını alır.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Adres alanının alır.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Bayt cinsinden bir alan boyutunu alır.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Bir alan hakkında bilgi genişletilmiş.|  
|[Eşittir](../../../extensibility/debugger/reference/idebugfield-equal.md)|İki alan karşılaştırır.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Simge veya türü türü bağımsız bilgilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 C dili için bir tür eşdeğerdir `typedef`.  
  
 Aşağıdaki örnekte C++ dili, `weather` bir sınıf türü ve `sunny` ve `stormy` simgeler şunlardır:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Bir alanı temsil eden bir simge ya da türü çağırarak belirlenebilir [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) inceleyerek [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sonucu. Varsa `FIELD_KIND_TYPE` bit ayarlanmışsa, bir tür alanıdır ve `FIELD_KIND_SYMBOL` bit ayarlanır, bir simge.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)