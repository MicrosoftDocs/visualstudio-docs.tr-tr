---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793541"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Ana bilgisayar komut dosyası yürütme tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvarResult`  
 [in] Komut dosyası sonucu içeren değişkenin adresini veya `NULL` komut dosyası hiçbir sonuç oluşturduysa.  
  
 `pexcepinfo`  
 [in] Adres bir `EXCEPINFO` betik sonlandırıldı zaman oluşturulan özel durum bilgilerini içeren yapısı veya `NULL` hiçbir özel durum oluşturursa.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemi çağırmadan önce komut dosyası altyapısı çağırır [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) SCRIPTSTATE_INITIALIZED bayrağı ayarlanmış yöntemi tamamlandı. Bu yöntem, ana bilgisayara tamamlanma durumunu ve sonuçlarını döndürmek için kullanılabilir. Olayları ana bilgisayardan indirme dayanır, birçok komut dosyası dillerini ana bilgisayar tarafından tanımlanan ömrü olduğunu unutmayın. Bu durumda, hiçbir zaman bu yöntem çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)