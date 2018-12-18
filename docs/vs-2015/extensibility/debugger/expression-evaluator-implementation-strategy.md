---
title: İfade değerlendiricisi uygulama stratejisi | Microsoft Docs
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
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 757e74a9dde1c580a6116342948edd4eb42f9ca3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737891"
---
# <a name="expression-evaluator-implementation-strategy"></a>İfade Değerlendiricisi Uygulama Stratejisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendiricisi (EE) hızlı bir şekilde oluşturmak için bir yaklaşım ise ilk yerel değişkenlerle göstermek için gerekli en düşük kod uygulamak için **Yereller** penceresi. Fark yararlıdır her satırında **Yereller** penceresi adı, türü ve yerel bir değişken değerini görüntüler ve üç tarafından temsil edilen bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesne. Adı, türü ve yerel bir değişken değerini örneğinden alınabilen bir `IDebugProperty2` çağırarak kendi [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi. Yerel değişkenlerle görüntüleme hakkında daha fazla bilgi için **Yereller** penceresinde görmek [görüntüleme Yereller](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Tartışma  
 Uygulanmasıyla bir olası uygulama dizisini başlatır [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Ayrıştırma](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ve [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemleri Yereller görüntülenecek uygulanması gerekir. Çağırma `IDebugExpressionEvaluator::GetMethodProperty` döndürür bir `IDebugProperty2` bir yöntemi temsil eden nesne: diğer bir deyişle, bir [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesne. İçinde kendilerini yöntemleri görüntülenmez **Yereller** penceresi.  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yönteminin uygulanmasını sonraki. Hata ayıklama altyapısı (DE) geçirerek yerel değişkenleri ve bağımsız değişkenler listesini almak için bu yöntemi çağıran `IDebugProperty2::EnumChildren` bir `guidFilter` bağımsız değişkeni `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` çağrıları [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ve [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), tek bir sabit listesi sonuçları birleştirme. Bkz: [görüntüleme Yereller](../../extensibility/debugger/displaying-locals.md) daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Yerel Öğeleri Görüntüleme](../../extensibility/debugger/displaying-locals.md)

