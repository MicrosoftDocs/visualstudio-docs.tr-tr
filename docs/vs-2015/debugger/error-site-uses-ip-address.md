---
title: 'Hata: Site IP adresi kullanan | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daa9ed74df46dd6be66a27d09cbbd7c311e03de4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793678"
---
# <a name="error-site-uses-ip-address"></a>Hata: Site IP Adresi Kullanıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklayıcı bir IP adresi kullanarak bir Web uygulaması için otomatik iliştirme çalıştığında bu hata oluşur. Değiştirirseniz böyle **Web sitesi kimliği** için **belirli IP adreslerini kullanan** IIS'de.  
  
 İçin otomatik çalışmaya iliştirme, projeyi yalnızca makine adı yerine belirli bir IP adresi ile oluşturmanız gerekir. Aksi takdirde, hata ayıklayıcı makine adı için IIS debug fiilini göndermek bir hata neden olacak localhost değişecektir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kullanım el ile eklemek yerine (hata ayıklama menüsünden **iliştirme**).  
  
     —veya—  
  
2.  Değişiklik **IIS Web sitesi kimliği** ayarı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



