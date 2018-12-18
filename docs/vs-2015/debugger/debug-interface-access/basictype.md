---
title: BasicType | Microsoft Docs
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
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 633fb76a8177f239b988554a5d15bee09e00c2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745031"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Simgenin temel türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Öğeleri  
 btNoType  
 Belirtilen hiçbir temel türü.  
  
 btVoid  
 Temel türü bir `void`.  
  
 btChar  
 Temel türü bir `char` (C/C++ türü).  
  
 btWChar  
 Temel türü olan geniş karakter (Unicode) (`WCHAR`).  
  
 btInt  
 Temel türü `signed int` (C/C++ türü).  
  
 btUInt  
 Temel türü `unsigned int` (C/C++ türü).  
  
 btFloat  
 Temel türü olan bir kayan noktalı sayı (`FLOAT`).  
  
 btBCD  
 Temel türü, ikili dosya kodlanmış bir ondalık (`BCD`).  
  
 btBool  
 Temel türü olan bir Boole değeri (`BOOL`).  
  
 btLong  
 Temel türü bir `long int` (C/C++ türü).  
  
 btULong  
 Temel türü bir `unsigned long int` (C/C++ türü).  
  
 btCurrency  
 Para birimi temel türüdür.  
  
 btDate  
 Temel türü, tarih/saat (`DATE`).  
  
 btVariant  
 Temel türü olan bir değişken türü yapısı (`VARIANT`).  
  
 btComplex  
 Temel türü karmaşık bir sayıdır.  
  
 btBit  
 Temel bir bit türüdür.  
  
 btBSTR  
 Temel türü olan temel ya da ikili bir dize (`BSTR`).  
  
 btHresult  
 Temel türü bir `HRESULT`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu sabit listesi değerleri tarafından döndürülen [Idiasymbol::get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: cvconst.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri ve yapıları](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol::get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)



