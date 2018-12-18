---
title: IActiveScript::SetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793295"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Komut dosyası altyapısı belirli bir duruma koyar. Bu yöntem bir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan temel olmayan iş parçacığı tarafından çağrılabilir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ss`  
 [in] Komut dosyası altyapısı verilen durumuna ayarlar. Tanımlanan değerlerden biri olabilir [SCRIPTSTATE numaralandırması](../../winscript/reference/scriptstate-enumeration.md) numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_FAIL`|Komut dosyası altyapısı Başlatıldı durumuna geçişi desteklemez. Ana bilgisayar gerekir bu komut dosyası altyapısı atmak ve oluşturma, başlatma ve aynı sonucu elde etmek için yeni bir komut dosyası motoru yük.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya) ve bu nedenle başarısız oldu.|  
|`OLESCRIPT_S_PENDING`|Yöntem başarıyla sıraya alındı, ancak durumu henüz değişmemiştir. Ne zaman durum değişiklikleri site çağrılır geri aracılığıyla [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yöntemi.|  
|`S_FALSE`|Yöntem başarılı oldu, ancak komut dosyası zaten belirtilen durumda olmadığını.|  
  
## <a name="remarks"></a>Açıklamalar  
 Altyapısı durumları komut dosyaları hakkında daha fazla bilgi için komut dosyası altyapısı durumları bölümüne bakın [Windows komut dosyası motorları](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)