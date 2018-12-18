---
title: Koşullu derleme kapalı | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914248"
---
# <a name="conditional-compilation-is-turned-off"></a>Koşullu derleme kapalı
Üzerinde koşullu derleme değişken ilk açma koşullu derleme olmadan kullanma girişimi. Üzerinde koşullu derleme bildirir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] derleyici ile @ koşullu derleme değişkenleri olarak başlayan tanımlayıcılar yorumlamak için. Koşullu kodunuzu ifadesiyle başlayarak yapın:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Aşağıdaki deyim, koşullu kodunuzu başlangıcına ekleyin:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koşullu derleme](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Koşullu derleme değişkenleri](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Deyimi](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Deyimi](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Deyimi](../../javascript/reference/at-set-statement-javascript.md)