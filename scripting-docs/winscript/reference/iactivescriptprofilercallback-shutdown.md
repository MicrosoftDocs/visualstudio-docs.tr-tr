---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793517"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Profil oluşturma bir komut dosyası altyapısı durduruldu her profil oluşturucu nesne bildirmek için çağrılır. Bu şekilde, profil oluşturucu nesnesi gerekli olursa, temizleme yordamları çağırabilirsiniz. Komut dosyası altyapısı kapatılıyor veya çağrı zaman bu yöntem aynı zamanda komut dosyası altyapısı tarafından çağrılır [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) başarısız olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hrReason`  
 [in] Kapatma nedeni. Komut dosyası altyapısı kapatma olmadığını `S_OK` geçirilir. Varsa çağrısı [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) HRESULT hata döndürür, HRESULT geçirilir. Aksi takdirde, bu değer alındığı [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri komut dosyası altyapısı tarafından göz ardı edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptprofilercallback arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)