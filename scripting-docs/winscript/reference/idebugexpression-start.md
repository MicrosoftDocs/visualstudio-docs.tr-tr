---
title: IDebugExpression::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794435"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
İfade değerlendirme başlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdecb`  
 [in] İfade değerlendirme tamamlandığında belirten için geri çağırma. Bu parametre ise `NULL`, hiçbir olaylar ve kullanarak, istemci ifadesi durumu yoklaması gerekir `QueryIsComplete`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ifadesi değerlendirmesi başlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Idebugexpression arabirimi](../../winscript/reference/idebugexpression-interface.md)