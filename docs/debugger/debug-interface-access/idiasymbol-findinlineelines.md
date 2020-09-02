---
title: 'IDiaSymbol:: findInlineeLines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45fbc94460eef4e8b5bde2d9a0537c6e75e96756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464557"
---
# <a name="idiasymbolfindinlineelines"></a>IDiaSymbol::findInlineeLines
Bir istemcinin, Bu sembolde doğrudan veya dolaylı olarak, satır numarası bilgileri üzerinden yineleme yapmasına izin veren bir sabit listesi alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT findInlineeLines ( 
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `ppResult`

dışı `IDiaEnumLineNumbers` Alınan satır numaralarının listesini içeren bir nesnesi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)