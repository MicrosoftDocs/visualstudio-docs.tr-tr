---
description: Bölüm için compiland tanımlayıcısını alır.
title: 'IDiaSectionContrib:: get_compilandId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_compilandId method
ms.assetid: 71ef2e63-d095-42b6-88d8-626e3129f0d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04f5420ab149de3382553ea2cc23a04f0a526bd6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157303"
---
# <a name="idiasectioncontribget_compilandid"></a>IDiaSectionContrib::get_compilandId
Bölüm için compiland tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bölüm için compiland tanımlayıcısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
