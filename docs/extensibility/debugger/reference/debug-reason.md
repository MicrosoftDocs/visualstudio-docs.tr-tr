---
description: İşlemin neden hata ayıklama için başlatıldığına ilişkin belirtir.
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db5d6697f222015cc4f6dbedbc6258e00c9b285f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096258"
---
# <a name="debug_reason"></a>DEBUG_REASON
İşlemin neden hata ayıklama için başlatıldığına ilişkin belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Alanlar
`DEBUG_REASON_ERROR`\
Belirli olmayan bir hata oluştu (diğer nedenlerden hiçbiri uygun olmadığında bu varsayılan koşul olarak kullanılır).

`DEBUG_REASON_USER_LAUNCHED`\
İşlem kullanıcının isteğiyle başlatılmıştı.

`DEBUG_REASON_USER_ATTACHED`\
Zaten çalışan işlem, Kullanıcı tarafından öğesine eklendi.

`DEBUG_REASON_AUTO_ATTACHED`\
İşlem başlatıldığı zaman otomatik olarak eklendi.

`DEBUG_REASON_CAUSALITY`\
*Tam zamanında* (JIT) hata ayıklama olayı nedeniyle işlem başlatıldı.

## <a name="remarks"></a>Açıklamalar
[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) yönteminden döndürüldü.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
