---
title: İşlev geçerli bir prototip nesnesi yok | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788732"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>İşlevin geçerli bir prototip nesnesi yok
Kullanma girişiminde **instanceof** bir nesne bir belirli işlevi sınıfından türetilen ancak nesnenin yeniden tanımlandı belirlemek için `prototype` özelliği olarak ya da `null`, veya bir dış nesne türü (her iki geçersiz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nesneleri). Dış nesne host nesne modeli (örneğin, Internet Explorer'ın belge veya pencere nesnesi) nesneden veya dış COM nesne olabilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İşlevin olun `prototype` özelliği geçerli bir başvurur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [prototype özelliği (nesne)](../../javascript/reference/prototype-property-object-javascript.md)