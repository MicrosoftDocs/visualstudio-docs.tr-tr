---
title: Profıler_scrıpt_type numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796391"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE Numaralandırması
Betik türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Kullanıcı tarafından yazılan kodu belirtir.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Yürütme sırasında dinamik olarak oluşturulan bir kod belirtir.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Yerel işlevler ve komut dosyası altyapısı tarafından tanımlanan nesneler için komut dosyası türünü belirtir.|  
|PROFILER_SCRIPT_TYPE_DOM|Internet Explorer, örneğin, bir çağrı belge nesne modeli (DOM) içine çağrı belirtir `document.getElementById` yöntemi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası profil oluşturucu sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)