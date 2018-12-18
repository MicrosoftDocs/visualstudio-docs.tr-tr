---
title: Ijsdebugframe::evaluate yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794390"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate Yöntemi
Bu yığını çerçevesi bağlamında bir ifadenin değerlendirin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pExpressionText`  
 [in] Değerlendirilecek ifade.  
  
 `ppDebugProperty`  
 [out] Özellik tarayıcısı temsil eden nesne.  
  
 `pError`  
 [out] Bir hata oluşursa hata iletisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki döndürür: S_OK: Değerlendirme başarılı, * ppDebugProperty değerlendirme sonucunu içerir. S_FALSE: Değerlendirme bir hata oluşturur (veya değerlendirme işlem desteklenmiyor) \*pError hata iletisi içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugframe arabirimi](../../winscript/reference/ijsdebugframe-interface.md)