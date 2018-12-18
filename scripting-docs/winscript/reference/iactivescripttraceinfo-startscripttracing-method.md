---
title: Iactivescripttraceınfo::startscripttracing yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793565"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing Yöntemi
Komut dosyası izlemeyi başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSiteTraceInfo`  
 Ana bilgisayarın Iactivescriptsitetraceınfo gösteren bir işaretçi.  
  
 `guidContextId`  
 Bağlam GUID.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş olası değerler şunlardır:  
  
1.  S_OK: başarılı.  
  
2.  E_POINTER: `pSiteTraceInfo` NULL işaretçi.  
  
3.  E_NOTIMPL: uygulanmadı.