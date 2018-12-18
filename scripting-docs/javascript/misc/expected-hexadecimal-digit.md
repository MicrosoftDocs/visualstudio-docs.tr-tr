---
title: Beklenen onaltılık basamak | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836183"
---
# <a name="expected-hexadecimal-digit"></a>Beklenen onaltılık basamak
Yanlış bir Unicode kaçış dizisi oluşturduğunuz. Unicode kaçış dizileri \u, tam olarak dört onaltılık basamağın (daha fazla ve en az) geldiği başlar. Unicode onaltılık basamak yalnızca sayı 0-9, A-F büyük harf ve küçük harf a-f içerebilir. Aşağıdaki örnek, doğru biçimlendirilmiş bir Unicode çıkış dizisi gösterir.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Unicode onaltılık basamak \u ile başlamak için yalnızca 0-9, A-F, küçük harf a-f büyük harf sayıları içeren emin olun; ve dört basamak gruplandırılır.  
  
    > [!NOTE]
    >  Bir dizede metin \u kullanın, ardından iki ters eğik çizgi - kullanmak istiyorsanız (\\\u)-ilk ters eğik çizgi kaçış için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../javascript/data-types-javascript.md)