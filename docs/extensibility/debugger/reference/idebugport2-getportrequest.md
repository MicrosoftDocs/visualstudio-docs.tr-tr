---
description: Bağlantı noktasını oluşturmak için daha önce kullanılan bir bağlantı noktasının açıklamasını alır (varsa).
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77224f98d953b61529ffed083e7be4cee0ed662f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087489"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Bağlantı noktasını oluşturmak için daha önce kullanılan bir bağlantı noktasının açıklamasını alır (varsa).

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parametreler
`ppRequest`\
dışı Bağlantı noktasını oluşturmak için kullanılan isteği temsil eden bir [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  Bir `E_PORT_NO_REQUEST` bağlantı noktasının bir [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) bağlantı noktası isteği kullanılarak oluşturulup oluşturulmadıysa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
