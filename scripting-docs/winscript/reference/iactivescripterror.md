---
title: Iactivescripterror | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a403bf412a0c93a5c435e1a3184202ed68d406ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793328"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Bu arabirimi uygulayan bir nesne geçirilir [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) komut dosyası altyapısı işlenmemiş bir hata karşılaştığında yöntemi. Ana bilgisayar daha sonra oluşan hata hakkında bilgi edinmek için bu nesnede yöntemleri çağırır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Bu hatayla ilgili bilgileri alır.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Bir hatanın oluştuğu konum kaynak kodundaki alır.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Burada bir hata oluştu kaynak dosyasındaki satır alır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası arabirimleri](../../winscript/reference/active-script-interfaces.md)