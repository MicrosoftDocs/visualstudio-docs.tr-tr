---
title: IObjectIdentity::IsEqualObject | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794735"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Bir nesne geçerli nesneye eşit olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `punk`  
 [in] Geçerli nesneyle Karşılaştırılacak nesne adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Nesneleri eşit.|  
|`S_FALSE`|Nesneleri eşit değildir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulaması `IsEqualObject` yöntemi döndürmelidir `S_OK` nesneleri yalnızca özdeş ise.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iobjectıdentity arabirimi](../../winscript/reference/iobjectidentity-interface.md)