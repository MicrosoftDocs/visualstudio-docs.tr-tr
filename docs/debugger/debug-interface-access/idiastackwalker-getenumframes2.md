---
description: Belirli bir platform türü için yığın çerçeve numaralandırıcısı alır.
title: 'Idiastackdenetçisi:: getEnumFrames2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71af6f8c78f6f4ac0f6008db8a9ecd4ba72df07e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147347"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Belirli bir platform türü için yığın çerçeve numaralandırıcısı alır.

## <a name="syntax"></a>Sözdizimi

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametreler
 `cpuid`

'ndaki [CV_CPU_TYPE_e sabit](../../debugger/debug-interface-access/cv-cpu-type-e.md) listesi numaralandırmasından, Platform türünü belirten bir değer.

 `pHelper`

'ndaki Yardımcı [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) nesnesi.

 `ppEnum`

dışı [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) nesnelerinin bir listesini içeren bir [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yalnızca x86 platformunun yığın çerçeve listesini almak için, [ıdiastackdenetçisi:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) metodunu çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e Numaralandırması](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
