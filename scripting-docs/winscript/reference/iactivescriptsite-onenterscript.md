---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793550"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Ana bilgisayara komut dosyası altyapısı kod yürütme başladıktan bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut dosyası altyapısı bu yöntem her bir giriş veya deðiþiklik komut dosyası motoruna çağırmanız gerekir. Örneğin, komut dosyasını bir nesne çağırır sonra komut dosyası altyapısı tarafından işlenen bir olay gönderir, komut dosyası altyapısı çağırmalısınız `IActiveScriptSite::OnEnterScript` önce olayı yürütmek ve çağırmalısınız [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) Olay yürütülürken sonra ancak olay harekete nesne dönmeden önce yöntemi. Bu yönteme çağrıları iç içe. Bu yöntem her çağrısına karşılık gelen çağrıyı gerektirir `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)