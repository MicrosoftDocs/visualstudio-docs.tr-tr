---
title: İfade değerlendirme arabirimleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be9582f965fe1d8a00c97548dbc5f458ae4e1198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107406"
---
# <a name="expression-evaluation-interfaces"></a>İfade değerlendirme arabirimleri
> [!IMPORTANT]
>  Visual Studio 2015'te ifade değerlendiricisi uygulama bu şekilde kullanım dışıdır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendirme arabirimi şunlardır [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama SDK.  
  
## <a name="discussion"></a>Tartışma  
 Bu arabirimleri sırasında kesme modu çağrı yığını ifadelerinde değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı ifade değerlendiricisi için (EE) uygulanır.  
  
 Tablodaki her bir arabirime aşağıdaki listeden uygulayabilirsiniz bileşen gösterir:  
  
-   Altyapısı (DE) hata ayıklama  
  
-   İfade değerlendirici (EE)  
  
-   Visual Studio (VS)  
  
|Arabirim|Tarafından uygulanan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Bir değişken için sayısal bir diğer adı temsil eder.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Bir değişken için sayısal bir diğer adı temsil eder ve bir ifade değerlendiricisi diğer uygulama etki alanı almak için (EE) sağlar.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Bir dizi nesneyi temsil eder.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Yönetilen dizi nesnesi temsil eder ve bir ifade değerlendiricisi dizisi için temel dizin (alt sınırlarını) belirlemek için (EE) sağlar.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|GİZLE|Bağlamalar bellekte gerçek adresleri simgeleri debug bağlayıcı temsil eder.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|GİZLE|Aynı [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi türleri, diğer adlar ve özel görselleştiriciler erişim ancak sağlar.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|İfade değerlendirici temsil eder.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Bir ifade değerlendiricisi (EE), Gelişmiş bir sürümünü temsil eder.|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Bir ifade değerlendiricisi (EE) içeren bir Gelişmiş ayrıştırıcı ağacı temsil eder.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Bir işlevi temsil eder.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Bir işlevi temsil eder ve geliştirir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|GİZLE|Hata Ayıklayıcı'nın çıktı penceresinde bir ileti görüntülemek bir ifade değerlendiricisi (EE) sağlar.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Yönetilen kod nesneyi temsil eder.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Herhangi bir simge temsil eden temel arabirim bellek adresine bağlı.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Aynı [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi ancak ek bilgilere erişim sağlar.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Değerlendirilecek hazır bir ayrıştırılmış ifadesi temsil eder.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Bir işaretçi temsil eder.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Bir işaretçi bir ayrıştırma ağacı temsil eder ve genişleten **IDebugPointerObject** arabirimi.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bir tür değeri türü Görselleştirici aracılığıyla değiştirme olanağı sağlar.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Özel görüntüleyicileri ve türü görselleştiriciler erişim sağlar.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Oluşturma olanağı sağlayan bir [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) nesnesi.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Bir koleksiyonunu temsil eder [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Bir CLR ifade değerlendiricisi yazma](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)