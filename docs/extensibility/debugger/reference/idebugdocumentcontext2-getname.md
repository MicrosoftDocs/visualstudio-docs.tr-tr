---
description: Bu belge bağlamını içeren belgenin görüntülenebilen adını alır.
title: 'IDebugDocumentContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96f0130b09a98c4064f53337aaa2e54ad7ed887b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066613"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Bu belge bağlamını içeren belgenin görüntülenebilen adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>Parametreler
`gnType`\
'ndaki [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) numaralandırmasından döndürülecek ad türünü belirten bir değer.

`pbstrFileName`\
dışı Dosyanın adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem genellikle, belge adı belge adının kendisini depolamak üzere yazılmadığı sürece (örneğin gösterildiği gibi), çağrı [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) yöntemine iletilir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CDebugContext` [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
