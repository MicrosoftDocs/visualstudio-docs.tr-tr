---
title: IDispatchEx::GetNameSpaceParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12168ddb5f65c62e81a8f724cacf8b3fd4a1b3a9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794603"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Arabirim için ad alanı üst nesnenin alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppunk`  
 Adres bir `IUnknown` ad alanı üst öğenin arabirimin aldığı arabirim işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da başka bir OLE tanımlı hata kodu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idispatchex arabirimi](../../winscript/reference/idispatchex-interface.md)