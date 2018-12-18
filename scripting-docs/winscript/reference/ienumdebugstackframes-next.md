---
title: IEnumDebugStackFrames::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e148b5e13bc3d7986451ece11a3a2eada5baa28
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794693"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Belirtilen bir numaralandırma sırası segmentlerinde sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Almak için Segment sayısı.  
  
 `prgdsfd`  
 [out] Bir dizi döndürür `DebugStackFrameDescriptor` alınan kesimleri temsil eden arabirimler.  
  
 `pceltFetched`  
 [out] Numaralandırıcı tarafından alınan kesimleri gerçek sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem numaralandırma sırası segmentlerinde belirtilen sayıda alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ienumdebugstackframes arabirimi](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor yapısı](../../winscript/reference/debugstackframedescriptor-structure.md)