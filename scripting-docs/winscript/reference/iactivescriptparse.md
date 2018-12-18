---
title: Iactivescriptparse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793343"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Windows altyapısı komut dosyasına eklenecek ham metni kod kod parçacıklarını sağlar veya çalışma zamanında değerlendirilecek ifade text sağlayan komut dosyası, bunu uygulayan olup `IActiveScriptParse` arabirimi. VBScript gibi hiçbir bağımsız geliştirme ortamına sahip yorumlanan komut dosyası dilleri için bu alternatif bir mekanizma sağlar (dışında `IPersist*`) komut dosyası motoruna bir kod almak için ve komut dosyası parçalarını çeşitli nesnesine eklemek için olaylar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Komut dosyası altyapısını başlatır.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Kod Resimli komut dosyasına ekler.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Ad alanına bildirimleri ekleme ve uygun şekilde kodu değerlendirme verilen kodu Resimli ayrıştırır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası arabirimleri](../../winscript/reference/active-script-interfaces.md)