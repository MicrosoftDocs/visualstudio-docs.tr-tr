---
description: Kapsayıcının alanları için bir Numaralandırıcı oluşturur.
title: 'IDebugContainerField:: EnumFields | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63ce34fc9eddec84326982cf7d30fda919817040
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077934"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Kapsayıcının alanları için bir Numaralandırıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parametreler
`dwKindFilter`\
'ndaki Numaralandırılacak alanları seçerek [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sabitlerin birleşimi. Alan türleri, sınıf veya temel gibi depolama türlerini veya yerel, parametre veya "This" işaretçisi gibi belirli bilgileri tanımlayabilir.

`dwModifiersFilter`\
'ndaki Numaralandırılacak alanları seçerek [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) sabitlerin birleşimi. Alan değiştiricileri, genel veya özel gibi erişim izinleri veya sanal, statik veya son gibi depolama bilgileri olabilir.

`pszNameFilter`\
'ndaki Numaralandırılacak alanın adı. Tüm alanlar döndürülürsünüz bu null bir değer olabilir.

`nameMatch`\
'ndaki Aramanın büyük/küçük harfe duyarlı olup olmadığını denetleyen [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) numaralandırmasından bir değer.

`ppEnum`\
dışı Alan listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Alan yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, alan yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `dwKindFilter`, `dwModifiersFilter` Ve `pszNameFilter` parametreleri birleştirilebilir, örneğin, "MyMethod" adlı tüm ortak sanal yöntemleri seçmek için.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
