---
title: SCRIPTLANGUAGEVERSION numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796376"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION Numaralandırması
Sürümleri scripting olası belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Numaralandırma değerleri  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Varsayılan sürümü. Tamsayı değeri 0'dır.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows sürüm 5.7 komut dosyası. Tamsayı değeri 1'dir.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows sürüm 5.8 komut dosyası. Tamsayı değeri 2'dir.|  
|SCRIPTLANGUAGEVERSION_MAX|En yüksek sürüm. Tamsayı değeri 255'tir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası sabitleri, numaralandırmaları ve hata kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)