---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793379"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Windows altyapısı komut dosyasına eklenecek ham metni kod kod parçacıklarını sağlar veya çalışma zamanında değerlendirilecek ifade text sağlayan komut dosyası, bunu uygulayan olup `IActiveScriptParse32` arabirimi. VBScript gibi hiçbir bağımsız geliştirme ortamına sahip yorumlanan komut dosyası dilleri için bu alternatif bir mekanizma sağlar (dışında `IPersist*`) komut dosyası motoruna bir kod almak için ve komut dosyası parçalarını çeşitli nesnesine eklemek için olaylar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Kod Resimli komut dosyasına ekler.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Komut dosyası altyapısını başlatır.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Ad alanına bildirimleri ekleme ve uygun şekilde kodu değerlendirme verilen kodu Resimli ayrıştırır.|