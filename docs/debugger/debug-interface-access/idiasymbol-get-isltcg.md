---
description: Compiland 'ın, tüm program iyileştirmesine yardımcı olan/LTCG (bağlantı zamanı kodu oluşturma) bağlayıcı anahtarıyla (/CPP/Build/Reference/LTCG-link-Time-Code-Generation) bağlantılı olup olmadığını belirten bir bayrak alır.
title: 'IDiaSymbol:: get_isLTCG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b8306dabe6533287d7d28841ea76f2d6478e4a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160815"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
[Compiland](../../debugger/debug-interface-access/compiland.md) 'ın, tüm program iyileştirmesine yardımcı olan [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation)bağlayıcı anahtarıyla bağlanıp bağlanmadığını belirten bir bayrak alır. Bu anahtar yalnızca yönetilen kod için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 pFlag

dışı `TRUE` `compiland` ' Nin/LTCG bağlayıcı anahtarıyla bağlantılı olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
