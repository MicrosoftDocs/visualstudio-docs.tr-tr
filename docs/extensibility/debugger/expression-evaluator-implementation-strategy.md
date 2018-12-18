---
title: İfade değerlendiricisi uygulama stratejisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0b60a82b9451dfa43f5cd231fd38dd32b1729ed
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233054"
---
# <a name="expression-evaluator-implementation-strategy"></a>İfade değerlendiricisi uygulama stratejisi
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için bkz: [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendiricisi (EE) hızlı bir şekilde oluşturmak için bir yaklaşım ise ilk yerel değişkenlerle göstermek için gerekli en düşük kod uygulamak için **Yereller** penceresi. Fark yararlıdır her satırında **Yereller** penceresi adı, türü ve yerel bir değişken değerini görüntüler ve üç tarafından temsil edilen bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesne. Adı, türü ve bir yerel değişken değeri öğesinden alınan bir `IDebugProperty2` çağırarak kendi [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi. Yerel değişkenlerle görüntüleme hakkında daha fazla bilgi için **Yereller** penceresinde görmek [görüntüleme Yereller](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Tartışma  
 Uygulanmasıyla bir olası uygulama dizisini başlatır [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Ayrıştırma](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ve [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemleri uygulanan, yerel öğeler görüntülenecek. Çağırma `IDebugExpressionEvaluator::GetMethodProperty` döndürür bir `IDebugProperty2` bir yöntemi temsil eden nesne: diğer bir deyişle, bir [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesne. İçinde kendilerini yöntemleri görüntülenmez **Yereller** penceresi.  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yönteminin uygulanmasını sonraki. Hata ayıklama altyapısı (DE) geçirerek yerel değişkenleri ve bağımsız değişkenler listesini almak için bu yöntemi çağıran `IDebugProperty2::EnumChildren` bir `guidFilter` bağımsız değişkeni `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` çağrıları [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) ve [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), tek bir sabit listesi sonuçları birleştirme. Bkz: [görüntüleme Yereller](../../extensibility/debugger/displaying-locals.md) daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Görüntü yerel öğeler](../../extensibility/debugger/displaying-locals.md)