---
title: '&#39;dönüş&#39; deyimi işlev dışı | Microsoft Docs'
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
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846524"
---
# <a name="39return39-statement-outside-of-function"></a>&#39;dönüş&#39; deyimi işlev dışı
Kullanılan bir `return` kodunuzun genel kapsamda deyimi. `return` Deyimi yalnızca bir işlev gövdesinin içinde görünmelidir.  
  
 Bir işlev ile çağırma `()` işleci bir ifadedir. Tüm ifadeler değerlere sahip; `return` deyimi, işlev tarafından döndürülen değerin belirtmek için kullanılır. Genel formu şöyledir:  
  
```  
  
return [ expression ];  
```  
  
 Zaman `return` deyimi yürütüldüğünde, *ifade* değerlendirilir ve işlev değeri olarak döndürdü. Herhangi bir ifade ise **tanımlanmamış** döndürülür.  
  
 Bir işlevin yürütülmesini durdurur `return` deyimi yürütüldüğünde, işlev gövdesinde yine de kalan diğer deyimler olsa bile. Bu kuralın istisnası, **dönüş** ifade oluştuğu yer bir **deneyin** bloğu ve karşılık gelen **son** engellenmesi, kod  **Son olarak** blok işlevi döndürmeden önce yürütülecek.  
  
 Bir işlev verir, çünkü çalıştırmadan işlev gövdesinin sonuna ulaştığında, bir `return` açıklamadır, döndürülen değer **tanımlanmamış** değeri (yani işlev sonucu daha büyük bir ifadenin bir parçası olarak kullanılamaz ).  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kaldırma `return` deyimi ana gövdesinden kodunuzun (genel kapsamlı).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [return deyimi](../../javascript/reference/return-statement-javascript.md)   
 [İşlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [caller Özelliği (İşlev)](../../javascript/reference/caller-property-function-javascript.md)