---
description: . Exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.
title: 'Ialoadcallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed83b79dea8f488be79a2161968876c9aa2a9a11
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148285"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
. Exe dosyasında bir hata ayıklama dizini bulunduğunda çağırılır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parametreler
 `fExecutable`

[in] `TRUE` hata ayıklama dizini bir yürütülebilir dosyadan (. dbg dosyası yerine) okunmalıdır.

 `cbData`

'ndaki Hata ayıklama dizinindeki verilerin bayt sayısı.

 `data[]`

'ndaki Hata ayıklama diziniyle doldurulmuş bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Dönüş kodu genellikle yok sayılır.

## <a name="remarks"></a>Açıklamalar
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemi, yürütülebilir dosyayı işlerken bir hata ayıklama dizini bulduğunda bu geri aramayı çağırır.

 Bu yöntem,. pdb dosyasında bulunenden farklı hata ayıklama bilgilerini desteklemek için istemcinin yürütülebilir ve/veya hata ayıklama dosyasına ters mühendislik gerçekleştirmesine yönelik ihtiyacı ortadan kaldırır. Bu verilerle istemci, kullanılabilir hata ayıklama bilgileri türünü ve çalıştırılabilir dosyada veya. dbg dosyasında bulunup bulunamayacağını algılayabilir.

 Bu geri aramaya gerek kalmaz çünkü `IDiaDataSource::loadDataForExe` Yöntem, sembolleri sağlamak için gerektiğinde. pdb ve. dbg dosyaları saydam bir şekilde açar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
