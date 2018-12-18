---
title: Kodu çözülecek URI geçerli bir kodlamada değil | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841825"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Kodu çözülecek URI geçerli bir kodlamada değil
Düzensiz biçimlendirilmiş bir URI (Tekdüzen Kaynak Tanımlayıcısı) kod çözme çalışıldı. URI, özel bir sözdizimi vardır; bir URI ile kullanılabilmesi için çoğu alfasayısal olmayan karakter kodlanmış olması gerekir. Kullanabileceğiniz `encodeURI` ve `encodeURIComponent` bir normal bir URI oluşturmak için yöntemleri [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dize.  
  
 Tam bir URI bileşenlerini ayırıcıları ve bir dizi oluşur. Genel formu şöyledir:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Açılı ayraçlar adlarında bileşenleri temsil eder ve ":", "/", ";" ve "?" ayırıcı olarak kullanılan ayrılmış karakterler.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Geçerli bir URI'leri çözmeye çalıştığınız emin olun. Normal çözülemiyor [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dizeleri gibi geçersiz karakterler içeriyor olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [decodeURI işlevi](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent İşlevi](../../javascript/reference/decodeuricomponent-function-javascript.md)