---
title: Ienumjsstackframes::Next yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2068bd130e7eb03747b89e2ba107019aa1cd458
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794468"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next Yöntemi
Belirtilen çerçeve sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cFrameCount`  
 [in] Alınacak çerçeve sayısı.  
  
 `pFrames`  
 [out] Çerçeve depolama dizisi.  
  
 `pcFetched`  
 [out] Çerçeve sayısı döndürdü.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ienumjsstackframes arabirimi](../../winscript/reference/ienumjsstackframes-interface.md)