---
title: IActiveScript::GetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791564"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Komut dosyası altyapısı geçerli durumunu alır. Bu yöntem bir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan temel olmayan iş parçacığı tarafından çağrılabilir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pss`  
 [out] Tanımlanan bir değer alan değişkenin adresini [SCRIPTSTATE numaralandırması](../../winscript/reference/scriptstate-enumeration.md) numaralandırması. Değer çağıran iş parçacığı ile ilişkili komut dosyası altyapısı geçerli durumunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_POINTER` geçersiz bir işaretçi belirtilmişse.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)