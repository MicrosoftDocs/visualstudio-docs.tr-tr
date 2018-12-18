---
title: Oluşturulan özel durum yakalanmadı | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788768"
---
# <a name="exception-thrown-and-not-caught"></a>Oluşan özel durum yakalanmadı
Bulunan bir `throw` kodunuzu, ancak deyiminde değil içinde içine bir **deneyin** bloğu veya Hayır ilişkili **catch** hata bloğunun. Özel durumlar içinden **deneyin** kullanarak engelleme **throw** deyimi ve yakalanan dışında **deneyin** ile engelleme bir **catch** deyimi.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Bir özel durum kod içine bir **deneyin** engelleme ve karşılık gelen olduğundan emin olun. **catch** bloğu.  
  
-   Özel durum doğru biçimde catch deyimi bekliyor emin olun.  
  
-   Özel durum işlenemezse, başka bir karşılık gelen catch deyimi olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata nesnesi](../../javascript/reference/error-object-javascript.md)   
 [throw deyimi](../../javascript/reference/throw-statement-javascript.md)   
 [try... catch... finally deyimi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)