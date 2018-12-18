---
title: IDebugStackFrame::GetDescriptionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdc77aa2ef2f9d7c95b0b82d5195a6a73524f055
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794966"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Yığın çerçevesi kısa veya uzun metinsel açıklaması döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fLong`  
 [in] Bayrak, burada `TRUE` uzun açıklama döndürür ve `FALSE` kısa bir açıklaması döndürür.  
  
 `pbstrDescription`  
 [out] Yığın çerçevesi açıklaması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, `fLong` olan `FALSE`, bu yöntem yalnızca yığın çerçevesi ile ilişkili işlevi adı sağlar. Zaman `fLong` olan `TRUE`, bu yöntem işlev parametrelerini ve diğer ilgili bilgileri de sağlayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugstackframe arabirimi](../../winscript/reference/idebugstackframe-interface.md)