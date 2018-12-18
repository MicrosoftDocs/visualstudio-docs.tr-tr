---
title: IEnumDebugStackFrames::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Reset
ms.assetid: 57be2683-5346-4464-bdf5-6fd45b56253a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46ff707795354902c19e9a9c1b425bb960af50bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794513"
---
# <a name="ienumdebugstackframesreset"></a>IEnumDebugStackFrames::Reset
Bir numaralandırma sırasını başlangıç durumuna sıfırlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir numaralandırma dizisi başına sıfırlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ienumdebugstackframes arabirimi](../../winscript/reference/ienumdebugstackframes-interface.md)