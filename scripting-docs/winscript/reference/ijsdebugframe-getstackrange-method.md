---
title: Ijsdebugframe::getstackrange yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794516"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange Metodu
Mantıksal JavaScript yığın çerçevesi mutlak bir adres aralığını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStart`  
 [out] Çerçevenin çoğu yığın işaretçisi alt.  
  
 `pEnd`  
 [out] Üst çoğu yığın işaretçi çerçeve.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, birlikte birden çok çalışma zamanları toplanan araya eklemeli Yığın izlemeleri eklemekten için kullanışlıdır. Başlangıç Son yığın işaretçileri birden fazla fiziksel makine yığın çerçevesi (için yorumlanan JavaScript çalışma zamanı çerçeveler) olabilir. Başlat > düşük adresine yığın yüksek olarak büyüdükçe bitmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugframe arabirimi](../../winscript/reference/ijsdebugframe-interface.md)