---
title: 'IDiaPropertyStorage:: ReadDWORD | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b85c8095ca4d730dd74054c976d9a5bf217f1cc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855580"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
`DWORD`Bir özellik kümesindeki değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

'ndaki Okunacak özelliğin tanımlayıcısı ( `PROPID` WTypes. h olarak bir olarak tanımlanır `ULONG` ).

 `pValue`

dışı Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür. `E_INVALIDARG`Özelliğin tür olup olmadığını döndürür `DWORD` .

## <a name="remarks"></a>Açıklamalar
 `DWORD`, Windows tarafından 32 bitlik işaretsiz tamsayı olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)