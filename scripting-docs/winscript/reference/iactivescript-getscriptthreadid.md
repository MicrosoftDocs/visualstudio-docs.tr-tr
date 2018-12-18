---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792005"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Verilen Win32 iş parçacığı ile ilişkili iş parçacığı için bir komut dosyası altyapısı-tanımlı tanımlayıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwWin32ThreadID` ,  
 [in] Bir çalışan Win32 iş parçacığında geçerli işlem iş parçacığı tanımlayıcısı. Kullanım [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) işlevi şu anda yürütülen iş parçacığı iş parçacığı tanıtıcısı alınamadı.  
  
 `pstidThread` ,  
 [out] Verilen Win32 iş parçacığı ile ilişkili bir betik iş parçacığı tanımlayıcı alan değişkenin adresini. Bu tanımlayıcı yorumu komut dosyası altyapısı kalır ancak Windows iş parçacığı tanımlayıcısı yalnızca bir kopyasını olabilir. Win32 iş parçacığı sona ererse, bu tanımlayıcı atanmamış haline gelir ve bundan sonra başka bir iş parçacığı atanabilir unutmayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya) ve bu nedenle başarısız oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alınan tanımlayıcı, komut dosyası iş parçacığı yürütme denetimi yöntemleri yapılan sonraki çağrılar gibi kullanılabilir [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) yöntemi.  
  
 Bu yöntem bir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan temel olmayan iş parçacığı tarafından çağrılabilir [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)