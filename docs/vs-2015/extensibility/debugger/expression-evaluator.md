---
title: İfade değerlendirici | Microsoft Docs
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
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48763a1e943a63f129c4fa72c0885d0a287b2b31
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736014"
---
# <a name="expression-evaluator"></a>İfade Değerlendirici
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İfade değerlendiricilerini (EE), bunları IDE kesme modundayken, kullanıcı tarafından görüntülenmesine izin verme ayrıştırılamadı ve çalışma zamanında değişkenleri ve ifadeleri değerlendirin dilinin sözdizimi inceleyin.  
  
## <a name="using-expression-evaluators"></a>İfade Değerlendiricilerini kullanma  
 İfadeleri kullanarak oluşturulan [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini aşağıdaki gibi:  
  
1. Hata ayıklama altyapısı (DE) uygulayan [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi.  
  
2. Hata ayıklama paketi alır bir `IDebugExpressionContext2` nesnesinden bir [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi ve çağrıları `IDebugStackFrame2::ParseText` almak için yöntemi bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesne.  
  
3. Hata ayıklama paketi çağrıları [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) yöntemi veya [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ifadenin değerini almak için yöntemi. `IDebugExpression2::EvaluateAsync` Komut/hemen penceresinden çağrılır. Diğer tüm kullanıcı Arabirimi bileşenleri çağırma `IDebugExpression2::EvaluateSync`.  
  
4. İfade değerlendirmesinin sonucu olan bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) adı, tür ve ifade değerlendirme sonucu değerini içeren bir nesne.  
  
   İfade değerlendirme sırasında EE sembol sağlayıcısı bileşenini bilgileri gerektirir. Sembol sağlayıcısı ayrıştırılmış ifade anlama ve tanımlamak için kullanılan bir sembolik bilgi sağlar.  
  
   Zaman uyumsuz bir ifade değerlendirme işlemi tamamlandığında, zaman uyumsuz bir olay tarafından oturum hata ayıklama Yöneticisi (SDM) üzerinden DE IDE ifade değerlendirme tamamlandıktan bildirim gönderilir. Zaman uyumlu bir ifade değerlendirme işlemi tamamlandıktan sonra değerlendirme sonucu çağrısından döndürülen `IDebugExpression2::EvaluateSync` yöntemi.  
  
## <a name="implementation-notes"></a>Uygulama Notları  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hata ayıklama motorlarını beklediğiniz ortak dil çalışma zamanı (CLR) arabirimlerini kullanarak ifade değerlendiricisi ile bahsedeceğiz. Sonuç olarak, bir ifade değerlendiricisi çalıştığını ile [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama motorlarını CLR desteklemesi gerekir (tüm CLR hata ayıklama arabirimleri tam listesi parçası olan debugref.doc içinde bulunabilir, [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcı Bileşenleri](../../extensibility/debugger/debugger-components.md)

