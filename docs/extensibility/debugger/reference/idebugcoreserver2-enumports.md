---
description: Tüm kullanılabilir bağlantı noktalarının listesini alır.
title: 'IDebugCoreServer2:: TRTs | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::EnumPorts
helpviewer_keywords:
- IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9de3b76aabc3e432695b734bcd5db5cf22314c3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058709"
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
Tüm kullanılabilir bağlantı noktalarının listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumPorts( 
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPorts( 
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Tüm bağlantı noktası tedarikçilerinin tüm bağlantı noktalarının listesini içeren bir [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
