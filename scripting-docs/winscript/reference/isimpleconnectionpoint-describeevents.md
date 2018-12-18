---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796361"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Her olay için ad ve DISPID olayların belirtilen aralıkta döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `iEvent`  
 [in] Alınacak ilk olay dizini.  
  
 `cEvents`  
 [in] Alınacak olay sayısıdır.  
  
 `prgid`  
 [out] Olay DISPID değerleri dizisi.  
  
 `prgbstr`  
 [out] Olay adları dizisi.  
  
 `pcEventsFetched`  
 [out] Alınan olayların gerçek sayı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`S_FALSE`|Daha fazla olay bulunmamaktaydı daha istendi. Kullanılamayan olayları DISPID_NULL ve null BSTR ile temsil edilir.|  
|`E_INVALIDARG`|Öğe getirilen.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen olayları aralığında DISPID ve her olay için adı döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isimpleconnectionpoint arabirimi](../../winscript/reference/isimpleconnectionpoint-interface.md)