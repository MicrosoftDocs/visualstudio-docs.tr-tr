---
description: Bu yöntem, ölçüm olarak bilinen bir kayıt defteri değerini ayarlar.
title: 'IDebugEngine2:: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec947a97506283b6d26f0e4cb26b06afb183dd57
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087892"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Bu yöntem, ölçüm olarak bilinen bir kayıt defteri değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parametreler
`pszMetric`\
'ndaki Ölçüm adı.

`varValue`\
'ndaki Ölçüm değerini belirtir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Ölçüm, bir hata ayıklama altyapısının davranışını değiştirmek veya desteklenen işlevselliği tanıtmak için kullanılan bir kayıt defteri değeridir. Bu yöntem, çağrıyı [hata ayıklama işlevi Için SDK yardımcılarını](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) uygun biçimine iletebilir `SetMetric` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
