---
description: Sabit Listesi dizisinden belirtilen sayıda yığın çerçevesi öğesi alır.
title: 'IDiaEnumStackFrames:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cee13aa9e26de77cf22cf7a51011a567cb14c25
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159162"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Sabit Listesi dizisinden belirtilen sayıda yığın çerçevesi öğesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak numaralandırıcıdaki StackFrame öğelerinin sayısı.

 rgelt

dışı İstenen [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) nesneleriyle doldurulacak bir dizi.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki yığın çerçevesi öğelerinin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla yığın çerçevesi yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
