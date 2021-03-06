---
description: Bir programın yürütmenin belirli bir noktaya ulaştıktan sonra yürütmeyi durdurup durdurmadığını tespit etmek için kullanılır.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a22a0534a464e9899e666550b31ab24503c05d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096531"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Bir programın yürütmenin belirli bir noktaya ulaştıktan sonra yürütmeyi durdurup durdurmadığını tespit etmek için kullanılır.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Alanlar
`CANSTOP_ENTRYPOINT`\
Verilen programın giriş noktasını belirtir.

`CANSTOP_STEPIN`\
Bir işleve adımlamayı belirtir.

## <a name="remarks"></a>Açıklamalar
Programın giriş noktasına ulaştıktan sonra veya bir işlev ya da yönteme adımladıktan sonra durmak gerekirse, oturum hata ayıklama Yöneticisi (SDM) ile onaylamak için [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) yöntemine bir bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
