---
description: Belirtilen türde ve boyutta bir dizi oluşturur.
title: 'IDebugTypeFieldBuilder2:: CreateArrayOfType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 954e30fc79ea6e581bc9f39dd17433f976b422ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083511"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
Belirtilen türde ve boyutta bir dizi oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateArrayOfType (
   IDebugField*  pTypeField,
   DWORD         rank,
   IDebugField** pArrayOfTypeField
);
```

```csharp
int CreateArrayOfType (
   IDebugField     pTypeField,
   uint            rank,
   out IDebugField pArrayOfTypeField
);
```

## <a name="parameters"></a>Parametreler
`pTypeField`\
'ndaki Dizinin tutacağız öğelerin türü.

`rank`\
'ndaki Dizideki öğe sayısı.

`pArrayOfTypeField`\
dışı Yeni diziyi temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnelerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)
