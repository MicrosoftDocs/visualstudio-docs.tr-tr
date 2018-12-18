---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796292"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Basit bağlantı noktası nesnesi ve istemcinin havuz arasında bir bağlantı kurar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdisp`  
 [in] İşaretçi `IDispatch` istemci arabiriminde havuz önerisi kullanıcının. İstemcinin havuz basit bağlantı noktasından giden çağrıları alır.  
  
 `pdwCookie`  
 [out] Bu bağlantı benzersiz olarak tanıtan bir döndürülen belirteç işaretçi. Çağıranın bu belirteç daha sonra geçirerek bağlantıyı silmek için kullanan `ISimpleConnectionPoint::Unadvise` yöntemi. Bağlantı başarıyla kuruldu değil, bu değer sıfır olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem basit bağlantı noktası nesnesi ve istemcinin havuz arasında bir bağlantı kurar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isimpleconnectionpoint arabirimi](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)