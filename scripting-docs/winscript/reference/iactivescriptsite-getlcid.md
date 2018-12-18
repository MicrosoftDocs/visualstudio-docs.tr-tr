---
title: IActiveScriptSite::GetLCID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793544"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Ana bilgisayarın kullanıcı arabirimiyle ilişkilendirilmiş yerel ayar tanıtıcısını alır. Komut dosyası altyapısı tanımlayıcı hata dizeleri ve altyapısı tarafından oluşturulan diğer kullanıcı arabirimi öğeleri uygun dilde göründüğünden emin olmak için kullanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `plcid`  
 [out] Komut dosyası altyapısı tarafından görüntülenen kullanıcı arabirimi öğeleri için yerel ayar tanıtıcısını alan değişkenin adresini.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_NOTIMPL`|Bu yöntem uygulanmadı. Sistem tarafından tanımlanan yerel kullanın.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem döndürürse `E_NOTIMPL`, sistem tarafından tanımlanan yerel ayar tanımlayıcısı kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)