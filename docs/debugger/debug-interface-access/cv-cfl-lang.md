---
title: CV_CFL_LANG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63426af550894df0e9796babaec91ff5758bbf1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909922"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Bağlantılı modül ve uygulama kaynak kod dilini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## <a name="elements"></a>Öğeleri  
 CV_CFL_C  
 Uygulama dilidir C.  
  
 CV_CFL_CXX  
 C++ uygulama dilidir.  
  
 CV_CFL_FORTRAN  
 Uygulama, FORTRAN dilidir.  
  
 CV_CFL_MASM  
 Uygulama, Microsoft Macro Assembler dilidir.  
  
 CV_CFL_PASCAL  
 Uygulama, Pascal dilidir.  
  
 CV_CFL_BASIC  
 Uygulama, temel dilidir.  
  
 CV_CFL_COBOL  
 Uygulama, COBOL dilidir.  
  
 CV_CFL_LINK  
 Uygulama bağlayıcı tarafından oluşturulan bir modüldür.  
  
 CV_CFL_CVTRES  
 CVTRES aracıyla dönüştürülen bir kaynak modülü uygulamasıdır.  
  
 CV_CFL_CVTPGD  
 Uygulama CVTPGD aracıyla oluşturulan POGO en iyi duruma getirilmiş bir modüldür.  
  
 CV_CFL_CSHARP  
 Uygulama C# dilidir.  
  
 CV_CFL_VB  
 Visual Basic uygulama dilidir.  
  
 CV_CFL_ILASM  
 Uygulama dili Ara dil (diğer bir deyişle, ortak dil çalışma zamanı (CLR) derleme) derlemesidir.  
  
 CV_CFL_JAVA  
 Java uygulama dilidir.  
  
 CV_CFL_JSCRIPT  
 Uygulama, Jscript dilidir.  
  
 CV_CFL_MSIL  
 Uygulama dilidir bir bilinmeyen Microsoft Ara dil (MSIL) kullanarak, büyük olasılıkla bir sonuç [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation) geçin.  
  
 CV_CFL_HLSL  
 Uygulama, yüksek düzey gölgelendirici dili dilidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma değerleri için yapılan bir çağrı tarafından döndürülen [Idiasymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: cvconst.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri ve yapıları](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)