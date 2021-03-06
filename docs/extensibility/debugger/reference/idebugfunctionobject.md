---
description: Bu arabirim bir işlevi temsil eder.
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0fabd43fe6f7d8ee8e5cddc6cc655088bf4a9abf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063558"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim bir işlevi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir ifade değerlendirici bu arabirimi bir işlevi temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabiriminin bir özelleştirmesi ve arabirimindeki [QueryInterface](/cpp/atl/queryinterface) kullanılarak elde edilir `IDebugObject` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugObject nesnesinden](../../../extensibility/debugger/reference/idebugobject.md)devralınan yöntemlere ek olarak, `IDebugFunctionObject` arabirim aşağıdaki yöntemleri sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Temel bir veri nesnesi oluşturur.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Oluşturucuyu kullanarak bir nesne oluşturur.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Oluşturucusu olmayan bir nesne oluşturur.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Bir dizi nesnesi oluşturur.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Bir dize nesnesi oluşturur.|
|[Değerlendirmesini](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|İşlevini çağırır ve sonuç değerini bir nesne olarak döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, ifade değerlendiricisi 'nin bir ayrıştırma ağacındaki işlevleri temsil etmesini sağlar. `Create`Bu arabirimdeki Yöntemler, yöntemine giriş parametrelerini temsil eden nesneleri oluşturmak için kullanılır. İşlev daha sonra, işlevin dönüş değerini temsil eden bir nesne döndüren [değerlendir](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) yöntemi çağırarak yürütülür.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
