---
title: 'IDiaSymbol:: findChildrenExByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936aa9006fac088efbb155d44ca8e4257ce94302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464571"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Simgenin, belirtilen göreli sanal adreste (RVA) geçerli olan alt öğelerini alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT findChildrenExByRVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `symtag`

'ndaki [SymTagEnum numaralandırmasında](../../debugger/debug-interface-access/symtagenum.md)tanımlandığı şekilde alınacak alt öğelerin sembol etiketlerini belirtir. `SymTagNull`Tüm alt öğelerin alınması için olarak ayarlayın.

 `name`

'ndaki Alınacak alt öğelerin adını belirtir. `NULL`Tüm alt öğelerin alınması için olarak ayarlayın.

 `compareFlags`

'ndaki Ad eşleştirme için uygulanacak karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `address`

'ndaki RVA belirtir.

 `ppResult`

dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 `S_OK`Simgenin en az bir alt öğesi bulunursa veya `S_FALSE` alt öğe bulunmazsa öğesini döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen yerel semboller, canlı Aralık bilgilerini içerir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)