---
title: 'Idebugdynamicfieldcomplus:: GetTypeFromPrimitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a0e559fbdf2824d334903a668bbdef8dbb6fff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731282"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Temel türü verilen bir türü alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetTypeFromPrimitive(
   DWORD         dwCorElementType,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromPrimitive(
   uint            dwCorElementType,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametreler
`dwCorElementType`\
'ndaki Temel türü temsil eden [CorElementType numaralandırmasındaki](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) değer.

`ppType`\
dışı Türü temsil eden [IDebugField 'ı](../../../extensibility/debugger/reference/idebugfield.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
