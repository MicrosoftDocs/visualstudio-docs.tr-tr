---
title: IDebugProperty2 | Microsoft Docs
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
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc5e780bb5e211b8900a22b181749e0376c6f242
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742616"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, yığın çerçeve özelliği, bir program belge özelliği veya diğer bir özelliği temsil eder. Genellikle bir ifade değerlendirme sonucu özelliğidir.  
  
> [!NOTE]
>  Bu kullanım "özelliğinin" ile bir sınıfın üye değişkeni anlamı olsa da karıştırılmamalıdır bir `IDebugProperty2` böyle bir varlık temsil edebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE belirli bir değer türünü temsil etmek için bu arabirimi uygular. Örneğin, değer, bellek veya kayıtları ve değerlerinin listesini görüntülemek için kullanılan bir bellek bağlamında ifade değerlendirme sonucu bir sayısal değer olabilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) değerlendirme sonucunu temsil eder Bu arabirimi elde edilir. `IDebugExpression2::EvaluateAsync` Bu arabirim göndererek döndürür bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) sırayla çağırır SDM arabirimine [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) özelliği almak için.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) ilişkili betik belge sağlamak için bu arabirimi döndürür.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) işlevinin dönüş değerini göstermek için bu arabirimi döndürür.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) programın bir ad veya bir bellek bağlamı gibi çeşitli özelliklerini temsil etmek için bu arabirimi döndürür.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) yığın çerçevesinde yerel değişkenler gibi çeşitli özelliklerini temsil etmek için bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugProperty2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Doldurur bir [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapı özelliği tanımlar.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Bir dizedeki bir özelliğin değerini ayarlar.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Belirli bir başvuru değerinden özelliğin değerini ayarlar.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Bir özellik alt numaralandırır.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Bir özelliğin üst döndürür.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Bir özelliğin en çok türetilen özelliği tanımlayan özellik döndürür.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Bir özelliğin değerini oluşturan bellek bayt döndürür.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Bir özellik değeri için bellek bağlamını döndürür.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Özellik değeri bayt cinsinden boyutunu döndürür.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Bu özelliğin değerine bir başvuru döndürür.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Genişletilmiş bir özellik bilgilerini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliği tarafından temsil edilen bir `IDebugProperty2` arabirimi, bir ad, bir tür ve adresi olan bir değer olarak zorlayıcı olabilir. Daha fazla genel Koşulları'nda bir `IDebugProperty2` üst ve alt düğümleri ile hiyerarşik bir yapısı olan herhangi bir şeyi temsil edebilir.  
  
 Yalnızca sürece geçerli yığın çerçevesi, örneğin çözülebilecek genellikle geçici bir özelliğidir. Diğer yandan, bir başvuru tarafından temsil edilen bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) arabirimi bağlanabilmesini değeri bellekte kaldığı sürece.  
  
 IDE kullanabilirsiniz `IDebugProperty2` göz atın ve çalışma zamanında özellikleri değiştirme kullanıcılara bildirmek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

