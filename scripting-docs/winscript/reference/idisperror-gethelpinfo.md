---
title: IDispError::GetHelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794558"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Yardım dosyasının yolunu ve hata mümkünse açıklayan konu bağlam Kimliğini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrFileName`  
 [out] Yardım dosyasının tam yolunu içeren dize. Yardım dosyası yok veya bir hata oluştuğunda, dönüş değeri NULL olur.  
  
 `pdwContext`  
 [out] Hata için Yardım içerik kimliği. Yardım dosyası yoksa (varsa `pbstrFileName` null), bu parametre bir anlamı yoktur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Sağlayıcıya özgü bir hata oluştu.|  
|`E_INVALIDARG`|`pbstrFileName`veya `pdwContext` NULL idi.|  
|`E_OUTOFMEMORY`|Sağlayıcı, Yardım dosyası yol döndürmek yeterli bellek ayıramadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, Yardım dosyasının yolunu ve hata mümkünse açıklayan konu bağlam Kimliğini döndürür.  
  
> [!NOTE]
>  Bu yöntem uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idisperror arabirimi](../../winscript/reference/idisperror-interface.md)