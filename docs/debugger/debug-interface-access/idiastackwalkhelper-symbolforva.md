---
description: Belirtilen sanal adresi içeren simgeyi alır.
title: 'IDiaStackWalkHelper:: symbolForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f75ba05573c5c41baea3ab24ec5b7d06c916c0e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156750"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Belirtilen sanal adresi içeren simgeyi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>Parametreler
 `va`

'ndaki İstenen sembolün içerdiği sanal adres. Simgenin bir `SymTagFunctionType` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırmasından bir değer) olması gerekir.

 `ppSymbol`

dışı Belirtilen adresteki simgeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
