---
title: Bellek ve disk belleği performans kuralları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec1acb6763d408f9f13ec3044e2cd8137d34e634
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237659"
---
# <a name="memory-and-paging-performance-rules"></a>Bellek ve disk belleği performans kuralları
Performans kuralları bellek ve disk belleği kategori uygulama performansı ve yanıt hızını etkileyebilir profil çalıştırmada sayfalama etkinliğini tanımlar.  
  
|||  
|-|-|  
|[DA0014: Aşırı yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Çalıştırma profili oluşturma boyunca son derece yüksek oranda bir disk gelen ve giden etkin bellek Sayfalaması oluştu. Bu düzey genellikle etkisi uygulama performansı ve yanıt hızını oranlarda disk belleği. Bellek ayırma algoritmaları düzeltilmesi tarafından azaltmayı deneyin. Uygulamanızın bellek gereksinimleri göz önünde bulundurun gerekebilir. Daha fazla belleğe sahip bir bilgisayarda yeniden profil çalıştırmayı deneyin. Disk belleği etkinlik miktarı kuralının D0017 üst eşiğini aştığında, bu kural ateşlenir.|  
|[DA0017: Yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Göreceli olarak yüksek oranda bir disk gelen ve giden etkin bellek Sayfalaması çalıştırmak profil boyunca oluştu. Bu düzey genellikle etkisi uygulama performansı ve yanıt hızını oranlarda disk belleği. Bellek ayırma algoritmaları düzeltilmesi tarafından azaltmayı deneyin. Uygulamanızın bellek gereksinimleri göz önünde bulundurun gerekebilir. Daha fazla belleğe sahip bir bilgisayarda yeniden profil çalıştırmayı deneyin.|