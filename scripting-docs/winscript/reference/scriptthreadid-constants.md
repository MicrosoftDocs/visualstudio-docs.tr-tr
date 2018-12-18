---
title: SCRIPTTHREADID sabitleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796412"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID Sabitleri
İş parçacığı türünü belirtmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Şu anda yürütülen iş parçacığı.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Temel iş parçacığı; diğer bir deyişle, komut dosyası altyapısını iş parçacığı örneğinin başlatılmasından.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Tüm iş parçacıklarının.|  
  
## <a name="remarks"></a>Açıklamalar  
 `SCRIPTTHREADID` Türü tarafından kullanılan `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, ve `IActiveScript::InterruptScriptThread`, ancak sabitler tarafından yalnızca kullanılabilir `IActiveScript::GetScriptThreadState` ve `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)