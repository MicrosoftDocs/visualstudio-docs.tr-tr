---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794630"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Dize ve işlemin dönüş değeri olarak ifade değerlendirme sonucunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phrResult`  
 [out] İşlemin dönüş değeri.  
  
 `pbstrResult`  
 [out] İfade değerlendirme sonucu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_PENDING`|İşlem devam ediyor bekliyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir dize ve işlem olarak ifade değerlendirme sonucunu döndürür `HRESULT`.  
  
 Bu yöntem `S_OK` ve `phrResult` döndürür `E_ABORT` varsa `Abort` işlemi durdurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugexpression arabirimi](../../winscript/reference/idebugexpression-interface.md)