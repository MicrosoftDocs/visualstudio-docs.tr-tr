---
description: Bir işlevi temsil eder ve IDebugFunctionObject arabirimini geliştirir.
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 012cd3dd0068fe69aae8898a408435340c6b22ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072851"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir işlevi temsil eder ve [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini geliştirir.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir ifade değerlendirici (EE), bir işlevi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimin yöntemleri **IDebugFunctionObject** türlerini aşağıdaki yollarla erteler:

- **Ihata ayıklama Gevaluate** yöntemi bayraklar alır.

- **CreateObject** yöntemi bayraklar ve bir zaman aşımı alır.

- **CreateStringObjectWithLength** yöntemi bir uzunluk alır.

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Değerlendirme bayrağı ayarları ve zaman aşımı değeri verilen bir Oluşturucu kullanan bir nesne oluşturur.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Belirtilen uzunluğa sahip bir dize nesnesi oluşturur.|
|[Değerlendirmesini](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|İşlevini çağırır ve sonuç değerini bir nesne olarak döndürür.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
