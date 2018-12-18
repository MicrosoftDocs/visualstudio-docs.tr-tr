---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791891"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Bir komut dosyası iş parçacığı geçerli durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `stidThread`  
 [in] İş parçacığı durumu istendiği tanıtıcısı, veya aşağıdaki özel iş parçacığı tanımlayıcıları:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Temel iş parçacığı; diğer bir deyişle, komut dosyası altyapısını iş parçacığı örneğinin başlatılmasından.|  
|SCRIPTTHREADID_CURRENT|Şu anda yürütülen iş parçacığı.|  
  
 `pstsState`  
 [out] Belirtilen iş parçacığı durumu alan değişkenin adresini. Durumu tarafından tanımlanan adlandırılmış sabit değerleri biri tarafından gösterilen [SCRIPTTHREADSTATE numaralandırması](../../winscript/reference/scriptthreadstate-enumeration.md) numaralandırması. Bu parametre geçerli iş parçacığının tanımlamıyorsa durumu herhangi bir zamanda değişebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan temel olmayan iş parçacığı tarafından çağrılabilir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)