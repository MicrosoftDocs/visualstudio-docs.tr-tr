---
title: SCRIPTTHREADSTATE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796331"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE Numaralandırması
Bir iş parçacığı durumu bir komut dosyası motoru belirtir. Bu numaralandırma tarafından kullanılan [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Numaralandırma değerleri  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Belirtilen iş parçacığı şu anda işleme hemen yürütülen kod metni komut dosyalı bir olay Bakım veya bir komut dosyası makrosu çalıştırıyor.|  
|SCRIPTTHREADSTATE_RUNNING|Belirtilen iş parçacığı etkin olarak işleme hemen yürütülen kod metni komut dosyalı bir olay Bakım veya bir komut dosyası makrosu çalıştırıyor.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası sabitleri, numaralandırmaları ve hata kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)