---
title: BREAKREASON listelemesi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791819"
---
# <a name="breakreason-enumeration"></a>BREAKREASON Listelemesi
Kesilmenin nedenini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|BREAKREASON_STEP|Sürüm modunda dil altyapısıdır.|  
|BREAKREASON_BREAKPOINT|Dil altyapısı açık bir kesme noktası karşılaştı.|  
|BREAKREASON_DEBUGGER_BLOCK|Dil altyapısı hata ayıklayıcı blok başka bir iş parçacığında karşılaştı.|  
|BREAKREASON_HOST_INITIATED|Konak bir sonu istedi.|  
|BREAKREASON_LANGUAGE_INITIATED|Dil altyapısı bir sonu istedi.|  
|BREAKREASON_DEBUGGER_HALT|Hata ayıklayıcı IDE bir sonu istedi.|  
|BREAKREASON_ERROR|Bir yürütme hatası sonu neden oldu.|  
|BREAKREASON_JIT|JIT hata ayıklamayı başlatma işlemi tarafından neden oldu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)