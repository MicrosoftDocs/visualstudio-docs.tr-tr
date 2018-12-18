---
title: Örnek yerel öğeler uygulaması | Microsoft Docs
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
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ca64ed08060df3a03dbb178fc636ca243e1e48d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756821"
---
# <a name="sample-implementation-of-locals"></a>Örnek Yerel Öğeler Uygulaması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio yerel öğeler için bir ifade değerlendiricisi (EE) nasıl alacağını genel bir bakış şu şekildedir:  
  
1.  Visual Studio hata ayıklama altyapısının (DE) çağıran [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) almak için bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) yığın çerçevesinin yerel öğeler de dahil olmak üzere tüm özellikleri temsil eden nesne.  
  
2.  `IDebugStackFrame2::GetDebugProperty` çağrıları [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) kesme noktası içinde gerçekleştiği yöntemi tanımlayan bir nesne elde edilir. Sembol sağlayıcısı DE sağlar ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), bir adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) ve bir bağlayıcı ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` çağrıları [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) ile sağlanan `IDebugAddress` nesne almak için bir [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) belirtilen adresi içeren bir yöntemi temsil eden.  
  
4.  `IDebugContainerField` Arabirimi için sorgulanır [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) arabirimi. Yöntemin Yereller için erişim sağlayan bu arabirimidir.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` bir sınıf oluşturur (adlı `CFieldProperty` örnekteki) uygulayan `IDebugProperty2` yöntemin Yereller temsil eden arabirim. `IDebugMethodField` Nesne bu yerleştirilir `CFieldProperty` ile birlikte nesne `IDebugSymbolProvider`, `IDebugAddress` ve `IDebugBinder` nesneleri.  
  
6.  Zaman `CFieldProperty` nesne başlatılır, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) üzerinde çağrılır `IDebugMethodField` nesne elde etmek için bir [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) yöntemi görüntülenebilir tüm bilgileri içeren yapısı .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` döndürür `CFieldProperty` nesnesinin bir `IDebugProperty2` nesne.  
  
8.  Visual Studio çağrıları [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) döndürülen üzerinde `IDebugProperty2` filtre nesnesiyle `guidFilterLocalsPlusArgs`. Bu döndürür bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) yöntemin yerel öğeler içeren nesne. Bu numaralandırma çağrıları tarafından doldurulur [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) ve [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio çağrıları [sonraki](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) almak için bir [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) her yerel yapısı. Bu yapı için bir işaretçi içeren bir `IDebugProperty2` yerel arabirimi.  
  
10. Visual Studio çağrıları [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yerel'ın adı, değeri ve türü elde etmek her yerel için. Görüntülenen bilgileri budur **Yereller** penceresi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [GetMethodProperty Uygulama](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Bir uygulamasını açıklar [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Yerel Öğeleri Numaralandırma](../../extensibility/debugger/enumerating-locals.md)  
 Hata ayıklama altyapısı (DE) yerel değişkenler veya bağımsız değişkenleri numaralandırmak için bir çağrı nasıl kolaylaştırdığını açıklar.  
  
 [Yerel Özellikleri Alma](../../extensibility/debugger/getting-local-properties.md)  
 Ne DE adı, türü ve bir veya daha fazla yerel öğeler değerini almak için bir çağrıda açıklar.  
  
 [Yerel Değerleri Alma](../../extensibility/debugger/getting-local-values.md)  
 Değerlendirme bağlamı tarafından verilen bir bağlayıcı nesnesi hizmetleri gerektirir yerel değer alınırken açıklanır.  
  
 [Yerel Öğeleri Değerlendirme](../../extensibility/debugger/evaluating-locals.md)  
 Yerel öğeler nasıl değerlendirildiği açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)  
 İfade değerlendirici (EE) DE çağırdığında, geçirilen bağımsız değişkenler sağlar.  
  
 [MyCEE örnek](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 İfade değerlendiricisi MyC dil oluşturmak için bir uygulama yaklaşım gösterilmektedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Öğeleri Görüntüleme](../../extensibility/debugger/displaying-locals.md)

