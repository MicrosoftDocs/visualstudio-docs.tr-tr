---
title: 'IDebugThread2:: SetThreadName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f49a15486551a91538bebe8fa900d165fdbb78b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911882"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
İş parçacığının adını ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetThreadName ( 
   LPCOLESTR pszName
);
```

```csharp
int SetThreadName ( 
   string pszName
);
```

## <a name="parameters"></a>Parametreler
`pszName`\
'ndaki İş parçacığının adı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacığı adını almak için [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)
