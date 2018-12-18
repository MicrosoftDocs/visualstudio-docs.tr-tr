---
title: BREAKRESUMEACTION listelemesi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791879"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION Listelemesi
Bir kesme noktası devam etmek için yolları açıklanmaktadır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Uygulama durdurur.|  
|BREAKRESUMEACTION_CONTINUE|Çalışmaya devam eder.|  
|BREAKRESUMEACTION_STEP_INTO|Bir yordam adımları.|  
|BREAKRESUMEACTION_STEP_OVER|Adım bir yordam boyunca.|  
|BREAKRESUMEACTION_STEP_OUT|Adımlar geçerli yordamın dışında.|  
|BREAKRESUMEACTION_IGNORE|Durumu ile çalışmaya devam eder.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Sonraki belge adımları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)