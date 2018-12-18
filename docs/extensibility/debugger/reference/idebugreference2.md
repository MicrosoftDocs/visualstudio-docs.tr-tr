---
title: IDebugReference2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5d5d8b3ab6e608a2454847fc9ec27e384777bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121505"
---
# <a name="idebugreference2"></a>IDebugReference2
Bu arabirim yığın çerçeve özelliği veya başka bir özellik referansı temsil eder.  
  
> [!NOTE]
>  `IDebugReference2` Gelecekte kullanmak ve tüm yöntemlerinden döndürmelidir için ayrılmış `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE değer belirli bir tür referansı temsil etmek için bu arabirimi uygular. Örneğin, değer, bellek veya kaydeder ve değerlerinin bir listesini görüntülemek için kullanılan bir bellek bağlamı bir ifade değerlendirme sonucu bir sayısal değer olabilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) bu arabirimi elde edilir. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) ve [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) Ayrıca, bu arabirim döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugReference2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Alır [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) bu başvuru açıklar yapısı.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Bu başvuru bir dizeden değerini ayarlar.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Başka bir başvuru bu başvurusundan değerini ayarlar.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Bu başvuru alt numaralandırır.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Bu başvuru üst alır.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Bu başvuru, en çok türetilen referansını alır.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Bu başvuru başvurduğu bellek bayt alır.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Bellek bağlamı için bu başvuru alır.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Bu başvuru bayt cinsinden boyutu alır.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Bu başvuru türünü ayarlar.|  
|[Karşılaştırma](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Bu başvuru başka ile karşılaştırır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu kullanımı "özelliği", bu bir üye değişkenine bir sınıfın anlamını ile rağmen karıştırılmamalıdır bir `IDebugReference2` böyle bir varlık temsil edebilir.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) bir özelliği temsil ederken `IDebugReference2` özelliği, genellikle ayıklanacak programı bir nesneye başvuru başvuru temsil eder.  
  
 Bir özellik ve başvuru arasındaki temel fark, bir adlandırılmamış örneğine başvuruyor ancak bir özelliği bir nesnenin adlandırılmış bir örneğine başvurur ' dir. Örneğin, bir özellik tarafından programın yığınındaki nesneye başvurabilir `"a.b"`. Başka bir özellik aynı nesneye başvurabilir `"c.d"`. Bu özelliğe başvurma şekilde gerektiren `"a.b"` veya `"c.d"` kapsamında olmalıdır. Bu aynı nesneye bir başvurusu adsız; Bu nesne için bellek geçerli olduğu sürece nesne için belirtilebilir.  
  
 Bir `IDebugProperty2` arabirimi zorlayıcı bir adı, türü ve bir adresi olan bir değer olarak. Bir `IDebugReference2`, diğer el, türü ve adresi düşünülebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)