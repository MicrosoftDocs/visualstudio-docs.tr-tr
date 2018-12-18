---
title: Beklenen &#39;@&#39; | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856853"
---
# <a name="expected-3939"></a>Beklenen &#39;@&#39;
Kullanarak koşullu derleme deyimleri ile kullanılmak üzere bir değişken oluşturmaya çalıştı `@set` deyimi, ancak değil yerleştirin bir at işareti "**@**" önce değişken adı.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Ekleme bir at işareti "**@**" hemen önce değişken adı. Örneğin:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [@set Deyimi](../../javascript/reference/at-set-statement-javascript.md)   
 [Koşullu derleme](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Koşullu Derleme Değişkenleri](../../javascript/advanced/conditional-compilation-variables-javascript.md)