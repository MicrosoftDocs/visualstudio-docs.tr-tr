---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793652"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Bir özel betik istatistik döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guid`  
 [in] Döndürülecek istatistiği belirtir. Semantiğini belirli bir istatistiği karşılık gelen GUID tamamen tanımlanan altyapısıdır.  
  
 `pluHi`  
 [out] İstatistiğin temsil eden bir 64-bit işaretsiz tamsayıyı yüksek 32 bit.  
  
 `pluLo`  
 [out] İstatistiğin temsil eden bir 64-bit işaretsiz tamsayıyı düşük 32 bit.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Yöntem uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem istatistikleri özel bir ana bilgisayara anlamlı döndürmek bir özel komut dosyası altyapısı sağlar.  
  
> [!NOTE]
>  Bu metot şu anda uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Iactivescriptstats arabirimi](../../winscript/reference/iactivescriptstats-interface.md)