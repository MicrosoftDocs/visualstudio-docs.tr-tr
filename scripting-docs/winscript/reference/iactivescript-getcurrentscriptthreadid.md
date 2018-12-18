---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791750"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Şu anda yürütülen iş parçacığı için bir komut dosyası altyapısı-tanımlı tanımlayıcı alır. Tanımlayıcı, komut dosyası iş parçacığı yürütme denetimi yöntemleri yapılan sonraki çağrılar gibi kullanılabilir [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstidThread`  
 [out] Geçerli iş parçacığı ile ilişkili bir betik iş parçacığı tanımlayıcı alan değişkenin adresini. Bu tanımlayıcı yorumu komut dosyası altyapısı kalır ancak Windows iş parçacığı tanımlayıcısı yalnızca bir kopyasını olabilir. Win32 iş parçacığı sona ererse, bu tanımlayıcı atanmamış haline gelir ve bundan sonra başka bir iş parçacığı atanabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_POINTER` geçersiz bir işaretçi belirtilmişse.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan temel olmayan iş parçacığı tarafından çağrılabilir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)