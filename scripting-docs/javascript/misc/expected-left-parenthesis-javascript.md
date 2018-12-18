---
title: Beklenen &#39;(&#39; (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31f611c2dc387a4aec574a3d5f8525b7b298d39d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942289"
---
# <a name="expected-3939-javascript"></a>Beklenen &#39;(&#39; (JavaScript)
Bir ifadeyi parantez kümesi içinde içine erişmeyi denedi, ancak açma parantezinden içermiyordu. Bazı ifadeler açılış ve kapanış ayraçlarını kümesi içinde içine alınması gerekir. Aşağıdaki örnekte ayraç dikkat edin.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değerlendirme ifadeye sol ayraç ekleyin.