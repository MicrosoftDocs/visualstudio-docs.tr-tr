---
description: Kesme noktasının bağlantısı kesildi sebebini sağlar.
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13f723c6395b8b271d6f097d811c5a31569c5853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067705"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Kesme noktasının bağlantısı kesildi sebebini sağlar.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Alanlar
`BPUR_UNKNOWN`\
Nedeni bilinmiyor.

`BPUR_CODE_UNLOADED`\
Kesme noktasını içeren kod kaldırıldı.

`BPUR_BREAKPOINT_REBIND`\
Kesme noktası farklı bir konuma yeniden bağlıydı. Bu durum, kesme noktası taşırken veya kesme noktası artık geçerli olmayan bir dosyaya bağlandığında, düzenleme ve devam etme işlemlerinden sonra gerçekleşebilir.

`BPUR_ BREAKPOINT_ERROR`\
Kesme noktasının bağlandıktan sonra hatalı olduğu belirlendi. Bu durum, koşulları artık geçerli olmayan yönetilen kesme noktaları olur.

## <a name="remarks"></a>Açıklamalar
[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) yöntemi tarafından döndürüldü.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
