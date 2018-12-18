---
title: IActiveScriptError::GetSourcePosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793346"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Komut dosyası altyapısı bir komut dosyası çalıştırılırken bir hata oluştuğu konum kaynak kodundaki alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwSourceContext`  
 [out] Bağlam tanımlayan bir tanımlama bilgisi alan değişkenin adresini. Bu parametre yorumu konak uygulamaya bağlıdır.  
  
 `pulLineNumber`  
 [out] Kaynak dosyanın hatanın oluştuğu satır numarası alan değişkenin adresini.  
  
 `pichCharPosition`  
 [out] Hatanın oluştuğu karakterin satırda alan değişkenin adresini.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_FAIL` konumu değil alındığında.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescripterror](../../winscript/reference/iactivescripterror.md)