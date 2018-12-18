---
title: Ijsdebugframe::getdocumentpositionwithname yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794570"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName Metodu
Bu kullanıcı düzeyinde belge yığın çerçevesinde geçerli konumunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pDocumentName`  
 [out] Statik betikler için belge için bir URL. Dinamik betikler için komut dosyası (örneğin, eval kod, işlev kodunu vb.) türünü içeren bir adı döndürülür.  
  
 `pLine`  
 Belgenin içinde 1 tabanlı satır konumu [out].  
  
 `pColumn`  
 Belgenin içinde 1 tabanlı satır konumu [out].  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugframe arabirimi](../../winscript/reference/ijsdebugframe-interface.md)