---
title: Bir Gözcü penceresi ifadesini değerlendirme | Microsoft Docs
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
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4dc9a56927ebe1e7b962ab815eb34028ba75350c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801485"
---
# <a name="evaluating-a-watch-window-expression"></a>Gözcü Penceresi İfadesini Değerlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Yürütme durakladığında Visual Studio hata ayıklama altyapısı kendi izleme listesindeki her bir ifadenin geçerli değerini belirlemek için (DE) çağırır. DE (EE) ifade değerlendiricisi'ni kullanarak her bir ifade değerlendirir ve Visual Studio görüntüler değeriyle **Watch** penceresi.  
  
 Bir izleme listesi ifade nasıl değerlendirilir genel bir bakış şu şekildedir:  
  
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
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Örnek İfade Değerlendirme Uygulaması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 İfade değerlendirme adım adım MyCEE örnek kullanır.  
  
 [Bir Gözcü İfadesini Değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Bir başarılı ifade ayrıştırma sonra ne olacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)  
 İfade değerlendirici (EE) hata ayıklama altyapısı (DE) çağırdığında, geçirilen bağımsız değişkenler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

