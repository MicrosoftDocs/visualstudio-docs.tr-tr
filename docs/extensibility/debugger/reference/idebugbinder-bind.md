---
description: Bu yöntem, simgenin geçerli değerini içeren bellek bağlamını veya nesnesini alır.
title: 'Idebugciltçi:: bind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 859ee8d474b25533d990c92e4c4f038d2a62f987
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067445"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Bu yöntem, simgenin geçerli değerini içeren bellek bağlamını veya nesnesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`pContainer`\
'ndaki Tarafından başvurulan alt öğe içeren [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `pField` .

`pField`\
'ndaki Simgeyi temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

`ppObject`\
dışı `IDebugObject` Simgenin örneğini temsil eden öğesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
