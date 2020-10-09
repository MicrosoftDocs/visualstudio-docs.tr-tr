---
title: Karakter kümesinde geçersiz Aralık (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12624d1a0256360ef1e4538a14100923c7de8af8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862578"
---
# <a name="invalid-range-in-character-set-javascript"></a>Geçersiz karakter kümesi aralığı (JavaScript)
Geçersiz karakter kümesi aralığı olan bir normal ifade oluşturmaya çalıştınız. Karakter kümeleri yalnızca-z veya 0-9 gibi tek karakterlerden oluşmalıdır. bir karakter kümesinde \w gibi karakter sınıfları dahil edilemez. Aralıktaki ilk karakter, aralıktaki ikinci karakterden önce de gelmelidir. Örnek:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Normal ifade karakter kümesini oluşturmak için yalnızca tek karakterler kullanın ve doğru sırada olduklarından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Normal Ifade nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Normal Ifade sözdizimi (JavaScript)](/previous-versions/1400241x(v=vs.100))