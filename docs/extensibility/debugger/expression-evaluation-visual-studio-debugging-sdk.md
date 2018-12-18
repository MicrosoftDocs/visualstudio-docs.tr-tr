---
title: İfade değerlendirme (Visual Studio SDK hata ayıklama) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52c897e40b825f85e07b4b4f14796655618280a8
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230740"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>İfade değerlendirme (Visual Studio hata ayıklama SDK)
Kesme modu sırasında birkaç program değişkenleri içeren basit ifadeler IDE değerlendirmelidir. Kendi değerlendirme gerçekleştirmek için hata ayıklama altyapısı (DE) ayrıştırma ve IDE windows birine girilen bir ifadeyi değerlendirir. 
  
 İfadeleri ile oluşturulur [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi ve ortaya çıkan tarafından temsil edilen [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi.  
  
 **IDebugExpression2** arabirimi çağrıları ve DE uygulanır, **EvalAsync** döndürülecek yöntemi bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) görüntülemek için IDE, arabirimi IDE içindeki ifade değerlendirmenin sonuçları. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) değerini, ifadenin yerleştirmek için kullanılan bir yapıyı döndürür bir **Watch** penceresi veya **Yereller** penceresi.  
  
 Hata ayıklama paketi veya oturum hata ayıklama Yöneticisi (SDM) çağıran [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) veya [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) almak için bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) temsil eden arabirim Değerlendirme sonucu. `IDebugProperty2` adı, türü ve ifadenin değerini döndüren yöntemler vardır. Bu bilgiler çeşitli hata ayıklayıcı pencerelerinde görünür.  
  
## <a name="using-expression-evaluation"></a>İfade değerlendirme kullanma  
 İfade değerlendirme kullanmak için uygulamanız gereken [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi ve tüm yöntemleri [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) aşağıdaki tabloda gösterildiği gibi arabirim.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Zaman uyumsuz olarak bir ifadeyi değerlendirir.|  
|[Durdurma](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz bir ifade değerlendirme sona erer.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Zaman uyumlu bir ifadeyi değerlendirir.|  
  
 Zaman uyumlu ve zaman uyumsuz değerlendirme gerektiren uygulama [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi. Zaman uyumsuz bir ifade değerlendirme uygulanmasını gerektirir [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)