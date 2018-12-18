---
title: Erişim reddedildi | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9b49f60395a853d7dfda91738ccccaba9d585b46
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295169"
---
# <a name="access-is-denied"></a>Erişim reddedildi
Bir betik konağı geçerli sayfanın dışında bir kaynaktan verilere erişmeye çalıştı. Internet Explorer ve diğer tarayıcılar tarafından izlenen bir aynı çıkış noktası İlkesi, betiklerin yalnızca şema, konak ve bağlantı noktası geçerli sayfasının URL'si ile kaynaklardan veri erişmesine izin verir.  
  
 Örneğin, geçerli sayfa ise `https://employees.mycompany.com`, aşağıdaki URL'lerden verilere erişemezsiniz:  
  
-   `http://data.contoso.com`, HTTPS yerine HTTP kullandığından.  
  
-   `https://somedatasource.com`, farklı bir etki alanı olduğu için.  
  
-   `https://employees.mycompany.com:8888`, farklı bir bağlantı noktasını kullandığından.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Çağırmaya çalıştığınız API JSONP veya güvenli bir şekilde çıkış noktaları arası komut dosyası izin veren iki yaklaşım olan CORS destekleyip desteklemediğini araştırın.  
  
-   REST API'sini çağırmak çalışıyorsanız, bu çağrı, sunucu tarafı kodu yeniden düzenleyin ve ardından, istemci tarafı betikleri için yeni bir REST uç noktasını kullanıma sunar.  
  
     Ek bilgi için aynı çıkış noktası İlkesi, JSONP ve CORS ile ilgili çevrimiçi belgeleri arayın.
