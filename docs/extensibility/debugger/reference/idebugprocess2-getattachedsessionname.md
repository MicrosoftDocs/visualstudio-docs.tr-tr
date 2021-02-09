---
title: 'IDebugProcess2:: Getattachedoturumadı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4692fdbc08655553a829c0f44037221f2e8b410
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907868"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Bu işlemde hata ayıklama yapan oturumun adını alır. IDE, bu bilgileri belirli bir makinedeki belirli bir işlemde hata ayıklama yapan bir kullanıcıya görüntüleyebilir.

> [!NOTE]
> Bu yöntem kullanım dışıdır ve uygulamanın her zaman döndürmelidir `E_NOTIMPL` .

## <a name="syntax"></a>Sözdizimi

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametreler
`pbstrSessionName`\

## <a name="return-value"></a>Dönüş Değeri
 Bu yöntem her zaman döndürmelidir `E_NOTIMPL` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
