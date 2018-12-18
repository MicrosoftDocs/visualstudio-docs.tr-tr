---
title: ICanHandleException::CanHandleException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793730"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Betik altyapısı çağıran bir belirtilen özel durumu işleyebilir belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pExcepInfo`  
 [in] İşaretçi bir `EXCEPINFO` hiçbir özel durum işleyicisi bulunursa bildirilecek bilgileri içeren yapısı.  
  
 `pvar`  
 [in] Tarafından oluşturulan değer gibi özel durum ile ilişkili bir değere bir `throw` deyimi. Bu parametre olabilir `NULL`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Çağıran özel durumu işleyebilecek|  
|`E_FAIL`|Çağıran özel işleyemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı, `IDispatchEx::InvokeEx`, veya benzer bir yöntem sonuçları bir özel durum, çağıran destekleyen betiğin çağıran zincirindeki komut dosyası altyapısı denetler `ICanHandleException` arabirim ve özel durumu işleyebilecek gösterir. Hiçbir çağıran özel durumu işleyebilecek, betik altyapısı durur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icanhandleexception arabirimi](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)