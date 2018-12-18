---
title: IActiveScript::SetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793265"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Komut dosyası motoru, sizi bilgilendirir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) ana bilgisayarı tarafından sağlanan arabirim site. Diğer önce bu yöntemi çağırabilmeniz [IActiveScript](../../winscript/reference/iactivescript.md) arabirim yöntemleri kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pScriptSite`  
 [in] Bu komut dosyası altyapısı örneği ile ilişkili olması için komut dosyası ana bilgisayarı tarafından sağlanan site adresi. Sitenin benzersiz olarak bu komut dosyası motoru örneğine atanması gerekir; diğer komut dosyası motorları ile paylaşılamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_FAIL`|Belirlenemeyen bir hata oluştu; komut dosyası altyapısı, bir siteyi başlatmak tamamlayamadı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, bir site zaten ayarlanmış).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)