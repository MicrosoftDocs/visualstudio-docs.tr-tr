---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796421"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Belirtilen dizinde düğümünde olan alt öğesini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `isn`  
 [in] Üst alt dizini.  
  
 `ppsn`  
 [out] Bir işaretçi alan değişkenin adresini `IScriptNode` alt örneğinin arabirimi.  
  
 İçin `IScriptNode` bir Web sayfasını temsil eden nesneler, bu parametre bir betik bloğu içeren bir nesne döndürür.  
  
 İçin `IScriptEntry` bir betik bloğu belirtmek nesneler, bu parametre bir işlevini belirten bir nesne döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin `IScriptEntry` işlev nesnesi belirtin nesneleri ve `IScriptScriptlet` nesneleri, hiç alt öğe girişi olduğundan bu yöntem başarısız olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iscriptnode arabirimi](../../winscript/reference/iscriptnode-interface.md)