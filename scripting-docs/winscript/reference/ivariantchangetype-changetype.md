---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796415"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Bir değişken değeri alır ve belirtilen bir türe yeni bir değişken oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvarDst`  
 [içinde out] Tarafından temsil edilen değer içeren bir değişken `pvarSrc`, ancak tarafından belirtilen tür ile `vtNew`.  
  
 `pvarSrc`  
 [in] Yeni bir türü değiştirmek için bir değişken değeri.  
  
 `lcid`  
 [in] Bağımsız değişkenler için veya dizelerden dönüştürürken kullanılacak yerel ayar bağlamı.  
  
 `vtNew`  
 [in] Türünü belirtir `pvarDst` olacak.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `pvarDst` Ve `pvarSrc` bağımsız değişkenleri olabilir eşit, özgün değeri; bu durumda üzerine yazılır. Bu yöntem geçirir `pvarDst` için `VariantClear` işlevi, dolayısıyla `pvarDst` geçerli bir değere başlatılması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ivariantchangetype arabirimi](../../winscript/reference/ivariantchangetype-interface.md)