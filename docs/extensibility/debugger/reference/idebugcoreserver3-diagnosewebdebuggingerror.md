---
description: Otomatik iliştirme neden başarısız olduğunu saptamaya çalışır.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a7e41842842850f7eb9ff4993bba348aea9816f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077713"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Otomatik iliştirme neden başarısız olduğunu saptamaya çalışır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametreler
`pszUrl`\
'ndaki Şu anda kullanılmıyor; her zaman bir null değer olarak ayarlanmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Diğer tipik dönüş kodları aşağıda verilmiştir:

|Kod|Description|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Uzak sunucunun neden hata ayıklamaya başlayamadığını belirleyemiyor.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Büyük olasılıkla yetersiz izinler nedeniyle veya hata ayıklama fiili etkinleştirilmediğinden, uzak sunucuda hata ayıklama yapılamıyor.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web sunucusu kilitlenmiş ve hata ayıklamayı etkinleştirmek için gereken hata ayıklama fiilini engelliyor.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
