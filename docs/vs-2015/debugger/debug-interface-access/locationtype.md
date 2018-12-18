---
title: LocationType | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a41eb64cc1a93f39a50187d54ecf556246f31913
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752846"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Konum bilgilerini bir sembol içinde yer alan türünü gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Öğeleri  
 `LocIsNull`  
 Konum bilgileri kullanılamıyor.  
  
 `LocIsStatic`  
 Statik konumdur.  
  
 `LocIsTLS`  
 İş parçacığı yerel depolama alanında konumdur.  
  
 `LocIsRegRel`  
 Kayıt göreli konumu.  
  
 `LocIsThisRel`  
 Konum `this`-göreli.  
  
 `LocIsEnregistered`  
 Bir kayıttaki konumdur.  
  
 `LocIsBitField`  
 Bir bit alanına konumdur.  
  
 `LocIsSlot`  
 Bir Microsoft Ara dil (MSIL) yuvası konumdur.  
  
 `LocIsIlRel`  
 MSIL göreli konumdur.  
  
 `LocInMetaData`  
 Meta verilerde konumdur.  
  
 `LocIsConstant`  
 Bir sabit değer konumdur.  
  
 `LocTypeMax`  
 Bu numaralandırma, konum türleri sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanılabilir özellikler [Idiasymbol](../../debugger/debug-interface-access/idiasymbol.md) sembolün konumu resim dosyası içinde arabirimi bağlıdır. Daha fazla bilgi için [simge konumları](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Bu numaralandırma değerleri için yapılan bir çağrı tarafından döndürülen [Idiasymbol::get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: cvconst.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri ve yapıları](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol::get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)



