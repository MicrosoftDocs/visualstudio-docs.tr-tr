---
title: İfade değerlendirici mimarisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5110b34c13952e359b494352063a2a277fbdcdde
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232042"
---
# <a name="expression-evaluator-architecture"></a>İfade değerlendirici mimarisi
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için bkz: [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Özel bir dil paketinin Hatalarını Ayıkla, anlamına gelir. Visual Studio Tümleştirme, gerekli bir ifade değerlendirici (EE) arabirimlerini Ayarla gerekir ve bağlayıcı arabirimleri ve ortak dil çalışma zamanı sembol sağlayıcısı (SP) çağırın. SP ve bağlayıcı, geçerli yürütme adresi birlikte ifadelerin değerlendirilme bağlam nesneleridir. Bu arabirimler oluşturmak ve kullanma bilgileri bir EE mimarisini temel kavramlar temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
  
### <a name="parse-the-expression"></a>İfade ayrıştırılamıyor  
 Bir program ayıklanırken ifadeler nedeniyle ama her zaman, hataları ayıklanan programa (kullanıcı tarafından yerleştirilmiş bir kesme noktası veya bir bir özel durumun) bir kesme noktasında durduruldu sayısı için değerlendirilir. Tarafından temsil edilen zaman Visual Studio alır bir yığın çerçevesi şu anda olduğu [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabiriminden hata ayıklama altyapısı (DE). Visual Studio sonra çağıran [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) almak için [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi. Bu arabirim, ifadeleri değerlendirilebilen bir bağlamı temsil eder; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) değerlendirme işlemi için giriş noktasıdır. Bu noktaya kadar tüm arabirimleri DE tarafından uygulanır.  
  
 Zaman `IDebugExpressionContext2::ParseText` olan adlı kesme noktası oluştuğu kaynak dosyanın dili ile ilişkilendirilmiş EE DE başlatır (DE ayrıca SH bu noktada oluşturur). EE tarafından temsil edilen [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimi. Daha sonra DE çağırır [ayrıştırma](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ifade (metin biçiminde) ayrıştırılmış bir ifadeye dönüştürmek için değerlendirme için hazır. Bu ayrıştırılmış ifade tarafından temsil edilen [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi. İfade genellikle ayrıştırılması ve bu noktada değerlendirilmez.  
  
 DE uygulayan bir nesne oluşturur [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi puts `IDebugParsedExpression` içine nesne `IDebugExpression2` nesne ve döndürür `IDebugExpression2` nesnesinden `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluate-the-expression"></a>İfade değerlendirilemiyor  
 Visual Studio ya da çağırır [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ayrıştırılmış ifade değerlendirilemiyor. Bu yöntemlerin ikisi de arama [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` yöntemi çağıran hemen while `IDebugExpression2::EvaluateAsync` yöntemi bir arka plan iş parçacığı aracılığıyla çağırır) ayrıştırılmış ifade değerlendirilip döndürülecek bir [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) ayrıştırılmış ifadenin türü ve değeri temsil eden arabirim. `IDebugParsedExpression::EvaluateSync` Ayrıştırılmış ifade tarafından temsil edilen bir asıl değere dönüştürmek için sağlanan SH, adresi ve Bağlayıcısı'nı kullanan `IDebugProperty2` arabirimi.  
  
### <a name="for-example"></a>Örneğin  
 Çalışan bir program içinde bir kesme noktasına isabet sonra bir değişkende görüntülemek kullanıcının seçtiği **QuickWatch** iletişim kutusu. Bu iletişim kutusu, değişkenin adını, değeri ve türünü gösterir. Kullanıcı, genellikle değeri değiştirebilirsiniz.  
  
 Zaman **QuickWatch** iletişim kutusu gösterilir, incelenmekte değişkeninin adını metin olarak gönderilir [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Bu döndürür bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ayrıştırılmış ifadesi, bu durumda temsil eden bir nesne, değişken. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ardından oluşturmak için çağrılan bir `IDebugProperty2` adının yanı sıra değişken değerini ve türünü temsil eden nesne. Görüntülenen bu bilgilerdir.  
  
 Kullanıcı, değişkenin değeri değişirse [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) program çıktığında kullanılacak şekilde, bellek değişkenin değeri değişir yeni değerle çağrılır çalışıyor.  
  
 Bkz: [görüntüleme Yereller](../../extensibility/debugger/displaying-locals.md) değişkenlerin değerlerini görüntüleme, bu işlemle ilgili daha fazla ayrıntı için. Bkz: [yerel değerinin değiştirilmesi](../../extensibility/debugger/changing-the-value-of-a-local.md) nasıl bir değişkenin değeri değişir hakkında daha fazla bilgi.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)  
 EE DE çağırdığında, geçirilen bağımsız değişkenler sağlar.  
  
 [Anahtar ifade değerlendiricisi arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Değerlendirme bağlamı ile birlikte bir EE yazarken gereken önemli arabirimler açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Yerel öğeleri görüntüleme](../../extensibility/debugger/displaying-locals.md)   
 [Yerel bir değeri değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md)