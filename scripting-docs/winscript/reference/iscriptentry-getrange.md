---
title: IScriptEntry::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794867"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Bir giriş uzunluğu ve başlangıç konumunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pichMin`  
 [out] İçin `IScriptEntry` bir betik bloğu belirtmek nesneleri 0 döndürür.  
  
 İçin `IScriptEntry` bir işlev nesnesi belirtin nesneleri geçerli komut dosyası bloğunda işlevi başlangıç konumunu döndürür.  
  
 İçin `IScriptScriptlet` nesneleri, 0 döndürür.  
  
 `pcch`  
 [out] İçin `IScriptEntry` bir betik bloğu belirtmek nesneleri metnin uzunluğunu döndürür.  
  
 İçin `IScriptEntry` bir işlev nesnesi belirtin nesneleri işlev tanımı uzunluğunu döndürür.  
  
 İçin `IScriptScriptlet` nesneleri, giriş uzunluğunu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iscriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)