---
title: 'IDiaSession:: Findfilebyıd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 172a02a2b2d818132131b94192af39d45e390254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864259"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Kaynak dosya tanımlayıcısına göre bir kaynak dosyası alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `uniqueId`

'ndaki Kaynak dosya tanımlayıcısını belirtir.

 `ppResult`

dışı Alınan kaynak dosyayı temsil eden bir [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaynak dosya tanımlayıcısı, tüm kaynak dosyalarını benzersiz hale getirmek için DIA SDK dahili olarak kullanılan benzersiz bir değerdir. Bu yöntem genellikle DIA SDK için dahili olarak kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)