---
description: Sağlama toplamı baytlarını alır.
title: 'IDiaSourceFile:: get_checksum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8aac5b35c98b8bb5b11bc623a274949ee32d9229
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147599"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Sağlama toplamı baytlarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametreler
 `cbData`

'ndaki Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

dışı Sağlama toplamı baytlarının sayısını döndürür. Bu parametre olamaz `NULL` .

 `data`

[in, out] Sağlama toplamı baytları ile doldurulmuş bir arabellek. Bu parametre ise `NULL` , `pcbData` gereken bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sağlama toplamı baytları oluşturmak için kullanılan sağlama toplamı algoritmasının türünü öğrenmek için [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) yöntemini çağırın.

 Sağlama toplamı genellikle kaynak dosyanın görüntüsünden oluşturulur, böylece kaynak dosyadaki değişiklikler sağlama toplamı baytlarında değişikliklere yansıtılır. Sağlama toplamı baytları dosyanın yüklü görüntüsünden oluşturulmuş bir sağlama toplamıyla eşleşmiyorsa, dosyanın hasar görmüş veya ile oynanmış olarak kabul edilmesi gerekir.

 Tipik sağlama toplamı 32 bayttan fazla değil, ancak bir sağlama toplamı en büyük boyut olduğunu varsaymaz. `data` `NULL` Sağlama toplamını almak için gereken bayt sayısını almak için parametresini olarak ayarlayın. Ardından uygun boyutun bir arabelleğini ayırın ve bu yöntemi yeni arabellekle bir kez daha çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
