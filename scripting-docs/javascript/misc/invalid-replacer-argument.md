---
title: Geçersiz değiştirici bağımsız değişken | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 588909bae9c5cf198d3108490111b36d5a2d182b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788684"
---
# <a name="invalid-replacer-argument"></a>Geçersiz değiştirici bağımsız değişken
Çağırmak için bir girişimde bulunuldu `JSON.stringify` geçerli olmayan bağımsız değişkenine sahip. `replacer` Bağımsız değişkeni bir işlevi veya bir dizi olmalıdır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değişiklik `replacer` bağımsız değişkeni bir işlev veya bir dizi.  
  
## <a name="example"></a>Örnek  
 Bu örnek kodda bir çalışma zamanı hatası neden olur `memberfilter` bir işlevi veya dizi yerine bir nesnedir.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JSON nesnesi](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse işlevi](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript çalışma zamanı hataları](../../javascript/reference/javascript-run-time-errors.md)