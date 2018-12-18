---
title: Sonlandırılmamış açıklama | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fde5d5edd7e81060b088e4940d752aa05e65ded
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868111"
---
# <a name="unterminated-comment"></a>Sonlandırılmayan açıklama
Çok satırlı açıklama bloğu başladı, ancak düzgün bir şekilde, sona ermedi değil. Çok satırlı açıklamalar başlar ile bir "/\*" birleşimi ve geriye doğru ile biten "\*/" birleşimi. Bir örnek verilmiştir:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Çok satırlı yorumlarla sonlandırmak mutlaka "*/".  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açıklama Deyimleri](../../javascript/reference/comment-statements-javascript.md)