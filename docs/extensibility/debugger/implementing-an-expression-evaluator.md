---
title: İfade değerlendiricisi uygulama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c5bf8b782d34cb1375f4357cd33f6e47cc22988
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908463"
---
# <a name="implement-an-expression-evaluator"></a>İfade değerlendiricisi uygulama
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için bkz: [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bir ifadenin değerlendirilmesi, hata ayıklama altyapısı (DE), sembol sağlayıcısı (SP), bağlayıcı nesnesi ve ifade değerlendiricisi (EE) arasında karmaşık bir etkileşim özelliği olur. Şu dört bileşen bir başkası tarafından kullanılan ve bir bileşen tarafından uygulanan arabirimler bağlı.  
  
 EE ifade bir dize biçiminde DE tamamlanması ayrıştırır veya onu değerlendirir. EE DE tarafından kullanılan aşağıdaki arabirimlerinden çalıştırır:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  Simgeler ve nesneler değerini almak için DE tarafından sağlanan bağlayıcı nesnesi, EE çağırır. EE DE tarafından uygulanan arabirimler kullanır:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  EE çalıştıran [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` yerel bir değişken, basit bir tür ya da sonra ilgili bilgileri görüntüler. Visual Studio, bir nesne gibi bir ifade değerlendirme sonucu tanımlamak için bir mekanizma sağlar **Yereller**, **izleyin** , veya **hemen** penceresi.  
  
  Bilgi için sorduğunda SP EE için DE tarafından verilir. SP adresleri ve aşağıdaki arabirimlerinden ve bunların türevleri gibi alanlar açıklayan arabirimleri çalıştırır:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE tüm bu arabirimleri kullanır.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [İfade değerlendiricisi uygulama stratejisi](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 İfade değerlendirici (EE) uygulama stratejisi için üç adımlık bir işlemdir tanımlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)