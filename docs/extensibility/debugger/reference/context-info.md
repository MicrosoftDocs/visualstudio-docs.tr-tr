---
description: Bu yapı bir bellek bağlamını veya kod bağlamını açıklar.
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58b524de5d2d230e240ae7338190568ccfe6fb2a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096492"
---
# <a name="context_info"></a>CONTEXT_INFO
Bu yapı bir bellek bağlamını veya kod bağlamını açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların bir birleşimi<strong>.</strong>

`bstrModuleUrl`\
Bağlamın bulunduğu modülün adı.

`bstrFunction`\
Bağlamın bulunduğu işlevin adı.

`posFunctionOffset`\
Kod bağlamı ile ilişkili işlevin satır ve sütun sapmasını tanımlayan [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı.

`bstrAddress`\
Verilen bağlamın bulunduğu koddaki adres.

`bstrAddressOffset`\
Verilen bağlamın bulunduğu koddaki adresin konumu.

`bstrAddressAbsolute`\
Belirtilen bağlamın bulunduğu bellekteki mutlak adres.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) yöntemine yapılan çağrıdan döndürülür.

Bu yapının tipik kullanımı, **bellek** hata ayıklama penceresi desteğidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
