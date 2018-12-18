---
title: Beklenmeyen niceleyici (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282273"
---
# <a name="unexpected-quantifier-javascript"></a>Beklenmeyen niceleyici (JavaScript)
Normal ifade arama kriterinizi oluştururken bir geçersiz yineleme faktörü ile bir desen öğesi oluşturuldu. Örneğin, deseni  
  
```  
/^+/  
```  
  
 Geçersiz çünkü öğenin ^ (giriş başlangıcına), bir yineleme faktörü sahip olamaz. Aşağıdaki tabloda, yineleme Etkenler olamaz öğeleri listeler.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|^|Giriş başına|  
|$|Konec vstupu|  
|\b|Sözcük sınırı|  
|\B|Sözcük olmayan sınır|  
|*|Sıfır veya daha fazla yinelemeleri|  
|+|Bir veya daha fazla yinelemeleri|  
|?|Sıfır veya bir yinelemeleri|  
|{n}|n yinelemeleri|  
|{n}|n ya da daha fazla yinelemeleri|  
|{n, m}|Bir n-m repetitions, kapsamlı|  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Arama deseni öğeniz yalnızca geçerli yinelemeyi faktörleri içeren emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal ifade nesnesi](../../javascript/reference/regular-expression-object-javascript.md)   
 [Normal ifade söz dizimi (JavaScript)](https://msdn.microsoft.com/library/1400241x)