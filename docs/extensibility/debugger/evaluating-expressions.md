---
title: İfadeleri değerlendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfd6248b06b69fa89d1888467a70718cf98b2a9a
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232474"
---
# <a name="evaluate-expressions"></a>İfadeleri değerlendirme
İfadeler, geçirilen dizelerden oluşturulur **Otolar**, **Watch**, **QuickWatch**, veya **hemen** windows. Bir ifade değerlendirildiğinde değişken veya bağımsız değişken ve değeri türünü ve adını içeren bir yazdırılabilir bir dize oluşturur. Bu dize karşılık gelen bir IDE penceresinde görüntülenir.  
  
## <a name="implementation"></a>Uygulama  
 Bir kesme noktasında bir program durduğunda ifadeler değerlendirilir. İfade tarafından temsil edilen bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) bağlama ve değerlendirme verilen ifade değerlendirme bağlamı içinde hazır ayrıştırılmış bir ifadeyi temsil eden arabirim. Yığın çerçevesinin uygulayarak hata ayıklama altyapısı (DE) sağladığı ifade değerlendirme bağlamının belirler [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi.  
  
 Kullanıcı dizesi verilmiş ve [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi hata ayıklama altyapısı (DE) elde edebilirsiniz bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) için kullanıcı dizesi geçirerek arabirimi [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi. Döndürülen IDebugExpression2 arabirimi ayrıştırılmış ifade değerlendirmesi için hazır içeriyor.  
  
 İle `IDebugExpression2` arabirimini DE üzerinden zaman uyumlu veya zaman uyumsuz bir ifade değerlendirme, bir ifadenin değerini alabilir kullanarak [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Bu değer, birlikte değişken veya bağımsız değişken türü ve ad IDE görüntülenmek üzere gönderilir. Değer, adı ve türü tarafından temsil edilir bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi.  
  
 İfade değerlendirme etkinleştirmek için bir DE uygulamalıdır [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ve [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimleri. Zaman uyumlu ve zaman uyumsuz değerlendirme uygulanması gerekir [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)   
 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)   
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)