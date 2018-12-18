---
title: IDebugBinder | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3514d280b6718fc670f3bdac35b6bbacbbf2b09c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105102"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  Visual Studio 2015'te ifade değerlendiricisi uygulama bu şekilde kullanım dışıdır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bu arabirim, genellikle bir bellek bağlamı veya sembolün geçerli değeri içeren nesne simge sağlayıcısı tarafından döndürülen bir simge alanı bağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bu arabirim ifade değerlendirme destekler ve hata ayıklama altyapısı (DE) tarafından uygulanmalıdır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim ifade değerlendirme aşamasında kullanılır ve genellikle uygulamasında kullanılan [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugBinder`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Bağlama](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Bellek bağlamı veya sembolün geçerli değeri içeren nesneyi alır.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bir nesnenin çalışma zamanı türü belirler.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Bir nesne konumu veya bellek adresi bellek bağlamına dönüştürür.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Alır bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) işlev parametreleri oluşturmak için kullanılan nesne.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Kesin türü için bir değişken alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim ifade değerlendiricisi tarafından kullanılan nesneleri ağaçları ayrıştırma döndürür. İfade değerlendirici ifade sembolleri örneklerine dönüştürmek için Sembol sağlayıcısını kullanarak bir ifade ayrıştırır [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), her simge türü ve konumu kaynak kodundaki açısından açıklar. [Bağlamak](../../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemi dönüştürür `IDebugField` nesneleri [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) bağlanmak veya bir simge bağı nesneleri yazın bellekte gerçek bir değer. Bunlar `IDebugObject` nesneleri sonra depolanır sonraki değerlendirme için ayrıştırma ağacı.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade değerlendirme arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)