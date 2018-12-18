---
title: Bir Gözcü penceresi ifadesini değerlendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47e875f4d288c896ace377e2844192aa5c3be275
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232109"
---
# <a name="evaluate-a-watch-window-expression"></a>Gözcü penceresi ifadesini değerlendirme
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için bkz: [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Yürütme durakladığında Visual Studio hata ayıklama altyapısı kendi izleme listesindeki her bir ifadenin geçerli değerini belirlemek için (DE) çağırır. DE (EE) ifade değerlendiricisi'ni kullanarak her bir ifade değerlendirir ve Visual Studio görüntüler değeriyle **Watch** penceresi.  
  
 Bir izleme listesi ifade nasıl değerlendirilir genel bir bakış aşağıdadır:  
  
1.  Visual Studio DE'ın çağıran [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ifadeleri değerlendirmek için kullanılan bir ifade içeriği almak için.  
  
2.  İzleme listesi içinde her bir ifade için Visual Studio çağırır [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ifade metin ayrıştırılmış bir ifadeye dönüştürmek için.  
  
3.  `IDebugExpressionContext2::ParseText` çağrıları [ayrıştırma](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) üretebilir ve metin ayrıştırma asıl işi yapmak için bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesne.  
  
4.  `IDebugExpressionContext2::ParseText` oluşturur bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesne ve puts `IDebugParsedExpression` içine bir nesne. Bu ben`DebugExpression2` Visual Studio'ya döndürülen nesne.  
  
5.  Visual Studio çağrıları [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ayrıştırılmış ifade değerlendirilemiyor.  
  
6.  `IDebugExpression2::EvaluateSync` Çağrı başarılı [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) gerçek değerlendirmesi yapmak ve üretmek için bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Visual Studio'ya döndürülen nesne.  
  
7.  Visual Studio çağrıları [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) ardından izleme listesinde görüntülenen ifade değeri elde edilir.  
  
## <a name="parse-then-evaluate"></a>Ayrıştırma sonra değerlendir  
 Karmaşık bir ifade ayrıştırma değerlendirme daha çok daha uzun sürebilir olduğundan bir ifade değerlendirme işlemi iki adımlamayla ayrılmıştır: 1) ifade ayrıştırma ve (2) ayrıştırılmış ifadeyi değerlendirir. Bu şekilde, birden çok kez değerlendirme oluşabilir, ancak yalnızca bir kez ayrıştırılacak ifade gerekiyor. Ara ayrıştırılmış ifade içinde EE döndürüldüğü bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) sırayla kapsüllenmiş ve DE döndürülen nesne bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesne. `IDebugExpression` Nesne için tüm değerlendirmesi erteler `IDebugParsedExpression` nesne.  
  
> [!NOTE]
>  Bir EE rağmen bu Visual Studio varsayar, bu iki adımlı işleme uyması gerekli değildir; EE ayrıştırabilir ve aynı adımda değerlendirme zaman [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrılır (MyCEE örnek, örneğin işleyişi budur). Dilinizi karmaşık ifadeleri biçimlendiriyorsa ayrıştırma adım değerlendirme adımdan ayırmak isteyebilirsiniz. Çoğu ifadeleri izlerken bu Visual Studio hata ayıklayıcısında performans artırabilir gösterilir.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Örnek İfade değerlendirme uygulaması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 İfade değerlendirme adım adım MyCEE örnek kullanır.  
  
 [Bir Gözcü ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Bir başarılı ifade ayrıştırma sonra ne olacağını açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)  
 İfade değerlendirici (EE) hata ayıklama altyapısı (DE) çağırdığında, geçirilen bağımsız değişkenler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)