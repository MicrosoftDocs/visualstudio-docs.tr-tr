---
description: Bir kesme noktası ayarlarken ek bilgi belirtmek için kullanılabilen isteğe bağlı bayraklar sağlar.
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e35e0b219bb77ce722f2e06a260de7ecc837dfb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085331"
---
# <a name="bp_flags"></a>BP_FLAGS
Bir kesme noktası ayarlarken ek bilgi belirtmek için kullanılabilen isteğe bağlı bayraklar sağlar.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Alanlar
`BP_FLAG_NONE`\
Kesme noktası bayrağı olmadığını belirtir.

`BP_FLAG_MAP_DOCPOSITION`\
Hata ayıklama altyapısının (DE), belge konumunu kullanarak kesme noktasını eşlemesi gerektiğini belirtir. Bu yalnızca, Active Server sayfaları (ASP) gibi komut dosyası yönelimli kaynak dosyalarında ayarlanan kesme noktaları için geçerlidir.

`BP_FLAG_DONT_STOP`\
Kesme noktasının hata ayıklama altyapısı tarafından işlenmesi gerektiğini, ancak hata ayıklama altyapısının sonunda durmamalıdır (yani, bir [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) olay nesnesi gönderilmemelidir). Bu bayrak, öncelikle izleneme noktalarıyla kullanılmak üzere tasarlanmıştır.

## <a name="remarks"></a>Açıklamalar
`dwFlags` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapılarının üyesi için kullanılır.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
