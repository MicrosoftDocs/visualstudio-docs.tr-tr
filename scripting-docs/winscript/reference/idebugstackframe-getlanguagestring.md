---
title: IDebugStackFrame::GetLanguageString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724ca98278eb8885d29aad1799f822ac57251597
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794408"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Dil kısa veya uzun metinsel açıklaması döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fLong`  
 [in] Bayrak, burada `TRUE` uzun açıklama döndürür ve `FALSE` kısa bir açıklaması döndürür.  
  
 `pbstrLanguage`  
 [out] Dil açıklaması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, `fLong` olan `FALSE`, bu yöntem yalnızca yığın çerçevesi ile ilişkili dilinin adı sağlar. Zaman `fLong` olan `TRUE`, bu yöntem bir tam ürün açıklama sağlayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugstackframe arabirimi](../../winscript/reference/idebugstackframe-interface.md)