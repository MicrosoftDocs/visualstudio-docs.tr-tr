---
title: "' Catch ' bekleniyor | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9950573e7bbeefe3594d77df2ae41c12f77ed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816693"
---
# <a name="expected-catch"></a>'catch' bekleniyor.
Özel durum işleme **TRY** bloğunu kullandınız, ancak ilişkili **catch** ifadesini yazmadınız. Özel durum işleme mekanizması, başarısız olabilecek kodun yanı ve bir özel durum oluşursa, bir **TRY** bloğunun içine sarmalanması gereken kodu gerektirir. Özel durumlar **throw** deyimi kullanılarak **TRY** bloğunun içinden oluşturulur ve bir veya daha fazla **catch** deyimi ile **TRY** bloğunun dışında yakalanır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İlişkili **catch** bloğunu ekleyin.  
  
- **Catch** bloğu yerine **finally** bloğu kullanmayı deneyin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [deneyin... yakala... finally ekstresi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Hata Nesnesi](../../javascript/reference/error-object-javascript.md)