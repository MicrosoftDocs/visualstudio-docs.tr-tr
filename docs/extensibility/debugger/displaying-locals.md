---
title: Yerel öğeleri görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e1a91de0d2a0f4f4e114ccfc77c6a3ce97084d1
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203387"
---
# <a name="display-locals"></a>Görüntü yerel öğeler
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için bkz: [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Her zaman yürütme yöntemini içeren yöntemi olarak da bilinen veya geçerli yöntemi bağlamında gerçekleştirilir. Yürütme durakladığında Visual Studio hata ayıklama altyapısı yerel değişkenler listesini almak için (DE) ve topluca Yereller yöntemin adı bağımsız değişkeni çağırır. Visual Studio bu Yereller ve değerlerini görüntüler **Yereller** penceresi.  
  
 Yerel öğeleri görüntülemek için DE çağırır [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemi için EE ait olan bir değerlendirme bağlamı, sembol sağlayıcısı (SP), geçerli yürütme adresi ve bir bağlayıcı nesnesi sağlar. Daha fazla bilgi için [değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md). Çağrı başarılı olursa `IDebugExpressionEvaluator::GetMethodProperty` yöntemi döndürür bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) geçerli yürütme adresini içeren yöntemi temsil eden nesne.  
  
 DE çağrıları [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) almak için bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , yalnızca yerel öğeler döndürür ve bir listesini oluşturmak için numaralandırılmış nesnesini [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)yapıları. Her yapı adı, türü ve yerel değerini içerir. Tür ve değer, biçimlendirilmiş dizeler görüntülemek için uygun olarak depolanır. Adı, türü ve değeri genellikle birlikte bir satırında görüntülenen **Yereller** penceresi.  
  
> [!NOTE]
>  **QuickWatch** ve **Watch** windows değişkenleriyle aynı ada, değere ve türü biçimi de görüntüler. Ancak, bu değerleri çağırarak elde edilen [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yerine `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Örnek yerel öğeler uygulaması](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Yerel uygulama işleminde size adım adım örnek kullanır.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)  
 Hata ayıklama altyapısı (DE) ifade değerlendiricisi (EE) çağırdığında, bu üç bağımsız değişken geçirir açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)