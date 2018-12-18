---
title: İşlev sonucuna atanamaz | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788723"
---
# <a name="cannot-assign-to-a-function-result"></a>İşlev sonucuna atanamaz
İşlev sonucuna bir değer atamaya çalıştı. Bir işlevin sonucu bir değişkene atanabilir, ancak bir değişken olarak kullanılamaz. İşlev için yeni bir değer atamak istiyorsanız, parantez (işlev çağırma işleci) atlayın. Aşağıdaki örnek, bu hatanın oluşturulduğu bir durumu gösterir.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Bir işlev çağrısı sonuç değeri yapabileceğiniz bir şey kullanmayın *atamak*. İşlev çağrısının sonucunu atayabilirsiniz *bir değişkene* rağmen.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Alternatif olarak, işlevi kendisini (ve onun dönüş değeri) bir değişkene atayabilirsiniz.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [JavaScript kodu yazma](../../javascript/writing-javascript-code.md)   
 [İşlevler](../../javascript/functions-javascript.md)