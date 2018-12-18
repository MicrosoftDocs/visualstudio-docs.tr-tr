---
title: ISimpleConnectionPoint::Unadvise | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f926f206bb8a27e6265fd147909a5adb13c3543
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796325"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Üzerinden daha önce oluşturulmuş bir danışma bağlantıyı sonlandırır `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwCookie`  
 [in] Döndürülen gibi sonlandırmak için bağlantı belirteci `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Danışma bir bağlantı sonlandırıldığında bağlantı noktası çağrıları `Release` kaydedilmiş işaretçi yöntemi için bağlantı sırasında `ISimpleConnectionPoint::Advise` yöntemi. Çevirmelerinin çağrısı `AddRef` sırasında gerçekleştirildiği `ISimpleConnectionPoint::Advise` danışma havuz 's çağırdığında bağlantı noktası `QueryInterface`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isimpleconnectionpoint arabirimi](../../winscript/reference/isimpleconnectionpoint-interface.md)