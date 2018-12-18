---
title: Nesne bekleniyor | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add25325653627d23eb699ab53c0f2799c8322f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788660"
---
# <a name="object-expected"></a>Nesne bekleniyor
Bir yöntemi veya özelliği bir türde bir nesne üzerinde başka başlatmaya çalıştı `Object`, veya başka bir türünde bir bağımsız değişken geçirildi `Object` zaman bir `Object` gerekli değildi.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yalnızca yöntemi veya özelliği türündeki nesneler üzerinde çağırma `Object`.  
  
-   Nesne olmayan bağımsız değişkeni için hata oluşursa, bir nesne türü geçirmek `Object`.  
  
-   Tanımlanmamış veya null bir başvuru türünde bir nesne yerine çağrılır olup olmadığını denetleyin `Object`.  
  
     Örneğin, aşağıdaki kodda myVar bu hatayı alırsanız:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Bunun yerine bu kodu kullanabilirsiniz:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne nesnesi](../../javascript/reference/object-object-javascript.md)   
 [Nesneler ve diziler](../../javascript/objects-and-arrays-javascript.md)