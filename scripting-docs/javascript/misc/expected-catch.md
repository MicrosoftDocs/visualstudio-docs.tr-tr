---
title: Beklenen &#39; catch &#39; | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788996"
---
# <a name="expected-39catch39"></a>Beklenen &#39; catch &#39;
Özel durum işleme kullanılan **deneyin** engellemek, ancak ilişkili yazmadı **catch** deyimi. Bir özel durum oluşursa, yürütülecek değil kodu ile birlikte edilemeyebilir kod içinde sarmalamak özel durum mekanizması işleme gerektiren bir **deneyin** bloğu. Özel durumlar içinden **deneyin** kullanarak engelleme **throw** deyimi ve yakalanan dışında **deneyin** bir veya daha fazla blok **catch**deyimleri.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İlişkili eklemek **catch** bloğu.  
  
-   Kullanmayı deneyin bir **son** yerine engelleme bir **catch** bloğu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [try... catch... finally deyimi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Hata nesnesi](../../javascript/reference/error-object-javascript.md)