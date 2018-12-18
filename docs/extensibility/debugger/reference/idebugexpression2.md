---
title: IDebugExpression2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114644"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Bu arabirim bağlama ve değerlendirmek için ayrıştırılmış ifade hazır temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) değerlendirilecek hazır bir ayrıştırılmış ifadesi temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) bu arabirimini döndürür. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) döndürür [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi. Yalnızca ayıklanacak program duraklatıldı ve yığın çerçevesi kullanılabilir olduğunda bu arabirimleri erişilebilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugExpression2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bu ifade zaman uyumsuz olarak değerlendirilir.|  
|[Durdurma](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz ifade değerlendirme sona erer.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bu ifade zaman uyumlu olarak değerlendirilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program durdu, oturum hata ayıklama Yöneticisi'ni (SDM) yığın çerçevesi çağrısıyla DE elde [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). SDM sonra çağırır [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) almak için [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi. Bu bir çağrı tarafından izlenir [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) oluşturmak için `IDebugExpression2` değerlendirilecek hazır ayrıştırılmış ifadeyi temsil eden arabirim.  
  
 SDM ya da çağıran [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) gerçekten ifade değerlendirmek ve bir değer üretmek için.  
  
 Bir uygulamasında `IDebugExpressionContext2::ParseText`, DE COM'ın kullandığı `CoCreateInstance` işlevi bir ifade değerlendiricisi örneği ve almak için bir [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimi (örnekte bkz `IDebugExpressionEvaluator` arabirimi). Daha sonra DE çağırır [ayrıştırma](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) elde etmek için bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi. Bu arabirim uygulamasında kullanılan `IDebugExpression2::EvaluateSync` ve `IDebugExpression2::EvaluateAsync` değerlendirmesi gerçekleştirmek için.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)