---
title: İfade değerlendirme (Visual Studio SDK hata ayıklama) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb5bfe5f5c77e7ba1881f803830e1cb3d357561b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781588"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>İfade Değerlendirme (Visual Studio Hata Ayıklama SDK’sı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kesme modu sırasında IDE programınızın çeşitli değişkenler içeren basit ifadeler değerlendirilmesi mümkün olması gerekir. Bunu yapmak için hata ayıklama altyapısı (DE) ayrıştırma ve bir windows IDE'nin girilen bir ifadeyi değerlendirmek mümkün olması gerekir.  
  
 İfadeleri kullanarak oluşturulan [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi ve bu temsil ortaya çıkan [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi.  
  
 **IDebugExpression2** arabirimi çağrıları ve DE uygulanır, **EvalAsync** döndürülecek yöntemi bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) görüntülemek için IDE, arabirimi IDE içindeki ifade değerlendirmenin sonuçları. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) bir ifade değerini İzle penceresine veya Yereller penceresine yerleştirme için kullanılabilir bir yapıyı döndürür.  
  
 Hata ayıklama paketi veya oturum hata ayıklama Yöneticisi (SDM) çağıran [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) veya [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) almak için bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) temsil eden arabirim Değerlendirme sonucu. `IDebugProperty2` adı, türü ve ifadenin değerini döndüren yöntemler vardır. Bu bilgiler çeşitli hata ayıklayıcı pencerelerinde görüntülenir.  
  
## <a name="using-expression-evaluation"></a>İfade değerlendirme kullanma  
 İfade değerlendirme kullanmak için uygulamanız gereken [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi ve tüm yöntemleri [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) aşağıdaki tabloda gösterildiği gibi arabirim.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Zaman uyumsuz olarak bir ifadeyi değerlendirir.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz bir ifade değerlendirme sona erer.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Zaman uyumlu bir ifadeyi değerlendirir.|  
  
 Zaman uyumlu ve zaman uyumsuz değerlendirme uygulanması gerekir [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi. Zaman uyumsuz bir ifade değerlendirme uygulanmasını gerektirir [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme Denetimi ve Durum Değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)

