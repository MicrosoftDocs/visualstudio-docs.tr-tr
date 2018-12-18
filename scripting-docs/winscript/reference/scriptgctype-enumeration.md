---
title: SCRIPTGCTYPE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d42187cc7467bea9d777f35bb208c4e42cabb31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796406"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE Numaralandırması
Çöp toplama gerçekleştirmek için türü. Kullanılan [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Numaralandırma değerleri  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Normal çöp toplama yapın. Tamsayı değeri 0'dır.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Ayrıntılı atık toplama yapın. Tamsayı değeri 1'dir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası sabitleri, numaralandırmaları ve hata kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)