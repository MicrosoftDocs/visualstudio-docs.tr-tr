---
title: Anahtar ifade değerlendiricisi arabirimleri | Microsoft Docs
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
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 616b86ed8a4976ef55437dbe21c044df32b4767a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739926"
---
# <a name="key-expression-evaluator-interfaces"></a>Anahtar İfade Değerlendiricisi Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Değerlendirme bağlamı birlikte ifade değerlendiricisi (EE) yazarken aşağıdaki arabirimleriyle ilgili bilgi sahibi olması gerekir.  
  
## <a name="interface-descriptions"></a>Arabirimi açıklamaları  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Tek bir yöntemi, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), geçerli yürütme noktasını temsil eder, veri yapısını alır. Hata ayıklama altyapısı (DE) geçirir üç bağımsız değişken, bu veri yapısını biridir [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) bir ifadeyi değerlendirmek için yöntemi. Bu arabirim, genellikle sembol sağlayıcısı tarafından uygulanır.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Sahip [bağlama](../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemi bir simge geçerli değerini içeren bellek alanını alır. Tarafından temsil edilen her iki içeren yöntem, verilen bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesi ve tarafından temsil edilen simgenin kendisine bir [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesi `IDebugBinder::Bind` sembolün değerini döndürür. `IDebugBinder` Genel DE uygulanır.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Basit veri türünü temsil eder. Diziler ve yöntemler gibi daha karmaşık türler kullanmak türetilmiş [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) ve [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimleri, sırasıyla. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) yöntemleri veya sınıfları gibi diğer semboller içeren sembolleri temsil eden başka bir önemli türetilmiş arabirimidir. `IDebugField` Arabirimi (ve CIM'in) sembol sağlayıcısı tarafından uygulanan genellikle.  
  
     Bir `IDebugField` nesne bir simgenin türünü ve adını bulmak için kullanılan ve, birlikte olabilir bir [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) nesne, değerini bulmak için kullanılabilir.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Gerçek bitlik bir simgenin çalışma zamanı değerini temsil eder. [Bağlama](../../extensibility/debugger/reference/idebugbinder-bind.md) götüren bir [IDebugField](../../extensibility/debugger/reference/idebugfield.md) temsil eden bir simge ve döndüren bir nesne bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesne. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) yöntemi, bir bellek arabellek sembolün değerini döndürür. Bir DE genellikle bellekte bir özelliğin değerini temsil etmek için bu arabirimi uygular.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Bu arabirim, ifade değerlendiricisi temsil eder. Anahtar yöntemi [ayrıştırma](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), döndüren bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimi.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Bu arabirim, değerlendirilecek hazır ayrıştırılmış bir ifade temsil eder. Anahtar yöntemi [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) IDebugProperty2 bir ifadenin türü ve değeri temsil eden döndürür.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Bu arabirim, değer ve türünü temsil eder ve bir ifade değerlendirme sonucu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)

