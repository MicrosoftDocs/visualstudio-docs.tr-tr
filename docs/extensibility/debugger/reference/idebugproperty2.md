---
title: IDebugProperty2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb0cd134d30da277ddc1f984e0cf9e57dd5e4963
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121579"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Bu arabirim yığın çerçeve özelliği, bir program belge özelliği veya başka bir özelliği temsil eder. Özellik genellikle bir ifade değerlendirme sonucudur.  
  
> [!NOTE]
>  Bu kullanımı "özelliği", bu bir üye değişkenine bir sınıfın anlamını ile rağmen karıştırılmamalıdır bir `IDebugProperty2` böyle bir varlık temsil edebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE belirli bir değeri temsil etmek için bu arabirimi uygular. Örneğin, değer, bellek veya kaydeder ve değerlerinin bir listesini görüntülemek için kullanılan bir bellek bağlamı bir ifade değerlendirme sonucu bir sayısal değer olabilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) değerlendirme sonucunu temsil eder Bu arabirimi elde edilir. `IDebugExpression2::EvaluateAsync` Bu arabirim göndererek döndürür bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) sırayla çağırır SDM arabirimine [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) özelliği alınamadı.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) ilişkili betik belge sağlamak için bu arabirimini döndürür.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) bir işlevin dönüş değerini temsil etmek için bu arabirimi döndürür.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) programın bir ad veya bir bellek bağlamı gibi çeşitli özelliklerini temsil etmek için bu arabirimi döndürür.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) yığın çerçevesi yerel değişkenler gibi çeşitli özelliklerini temsil etmek için bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugProperty2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Doldurur bir [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) özelliği tanımlar yapısı.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Bir dizeden bir özelliğin değerini ayarlar.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Verilen başvuru değerinden özelliğin değerini ayarlar.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Bir özelliğin alt numaralandırır.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Bir özelliğin üst öğesini döndürür.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Bir özelliğin en çok türetilen özelliği açıklar özelliği döndürür.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Bir özelliğin değerini oluşturan bellek bayt döndürür.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Bir özellik değeri için bellek bağlamını döndürür.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Özellik değeri bayt cinsinden boyutu döndürür.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Bu özelliğin değeri bir başvuru döndürür.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Bir özelliğin genişletilmiş bilgiler döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliği tarafından temsil edilen bir `IDebugProperty2` arabirim, bir adı, türü ve bir adresi olan bir değer olarak düşünülebilir. Daha fazla genel terimleriyle bir `IDebugProperty2` üst ve alt düğümler ile hiyerarşik bir yapı sahip herhangi bir şeyi temsil edebilir.  
  
 Yalnızca sürece geçerli yığın çerçevesini örneğin son genellikle geçici bir özelliğidir. Diğer yandan, bir başvuru tarafından temsil edilen bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) arabirimi lasts bellek değeri kaldığı sürece.  
  
 IDE kullanabilirsiniz `IDebugProperty2` göz atın ve çalışma zamanında özellikleri değiştirme kullanıcıların izin vermek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)