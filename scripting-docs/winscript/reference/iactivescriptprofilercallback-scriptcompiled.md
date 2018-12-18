---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793508"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Profil oluşturucu komut dosyası altyapısını nesne derlenmiş bir komut dosyası bildirir. Bu yöntem derlenir her komut dosyası için çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `scriptId`  
 [in] Derlenen betik benzersiz kimliği. Bu kimlik komut dosyası altyapısı tarafından atanır.  
  
 `type`  
 [in] Derlenen komut dosyası türü. Değerleri tanımlanan [profıler_scrıpt_type numaralandırması](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Mevcut ise, bir işaretçi bir `IUnknown` profil oluşturucu için sorgu gerekir arabirimi bir [Idebugdocumentcontext arabirimi](../../winscript/reference/idebugdocumentcontext-interface.md) işaretçi. Aksi takdirde, bu boş olacaktır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri komut dosyası altyapısı tarafından göz ardı edilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca bu ana bilgisayar tarafından destekleniyorsa komut dosyası altyapısı belge bağlamı sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptprofilercallback arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)