---
title: İçin&#39;t sahip &#39;sonu&#39; döngü dışında | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928561"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>İçin&#39;t sahip &#39;sonu&#39; döngü dışında
Kullanmaya çalıştığınız **sonu** anahtar sözcüğü bir döngü dışında. **Sonu** anahtar sözcüğü, bir döngü sonlandırmak için kullanılır veya `switch` deyimi. Döngü gövdesinde gömülü olması gerekir veya `switch` deyimi. Ancak, bir **etiket** break anahtar sözcüğü izleyebilirsiniz.  
  
```  
break labelname;  
```  
  
 Yalnızca etiketli biçiminde ihtiyacınız **sonu** kullanırken anahtar sözcüğü iç içe döngüleri veya `switch` deyimlerini ve en içtekiyle olmayan bir döngüden gerek.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Emin **sonu** anahtar sözcüğü, kapsayan bir döngü veya switch deyimi içinde görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [break deyimi](../../javascript/reference/break-statement-javascript.md)   
 [Program akışı denetimi](../../javascript/controlling-program-flow-javascript.md)   
 [Komut Dosyalarınızda Sorun Giderme](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)