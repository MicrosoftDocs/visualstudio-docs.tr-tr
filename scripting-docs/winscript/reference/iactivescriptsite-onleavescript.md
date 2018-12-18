---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793682"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Ana bilgisayar komut dosyası altyapısı kod yürütülmesini döndürdüğünü bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut dosyası altyapısı, komut dosyası altyapısı girilen çağıran bir uygulama denetimi döndürmeden önce bu yöntemi çağırmanız gerekir. Örneğin, komut dosyasını bir nesne çağırır sonra komut dosyası altyapısı tarafından işlenen bir olay gönderir, komut dosyası altyapısı çağırmalısınız [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) olay yürütmeden önce yöntemi ve çağırmalısınız`IActiveScriptSite::OnLeaveScript`olay harekete nesne döndürmeden önce olayı yürütmek sonra. Bu yönteme çağrıları iç içe. Her çağrı için `IActiveScriptSite::OnEnterScript` bu yöntem karşılık gelen çağrıyı gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)