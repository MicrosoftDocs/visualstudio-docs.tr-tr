---
title: Oluşturma ve kod çözümleme iade ilkelerini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b2eb5059d5ec027654b1e4de7098c732e897088
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238361"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Kod Çözümleme İade İlkeleri Oluşturma ve Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Team Foundation sürüm denetimi (TFVC) kullandığınızda, .NET Framework ve doğal (C/C++) kod projeleri bir takım projesi için iade Kod Analizi ilkesi oluşturabilirsiniz. Denetim ve kod tabanında denetlenen kodun kalitesini artırmak için kod çözümleme İade İlkesi'ni kullanabilirsiniz.  
  
 İlke, yerel yapı güncel olduğunda ve kod analizini en son kaynak dosyalarında Çalıştır geçirir. En azından kod projesinde etkin Kod Analizi kuralları, takım projesi iade ilkede tanımlanan aynı kuralları içermesi gerekir. Takım Proje ayarlarında hata olarak belirtilen kurallar, kod projesinde hata olarak de belirtilmelidir  
  
> [!IMPORTANT]
>  Kod çözümleme iade ilkeleri web sitesi projeleri için uygulanamaz. Web uygulaması projelerine uygulanabilirler.  
  
 Takım proje ayarlarını kullanarak kod çözümleme iade ilkeleri oluşturma [!INCLUDE[esprscc](../includes/esprscc-md.md)]. İade ilkeleri belirtilir ve bir takım projesi için zorunlu, ancak kod analizi yürütmeleri yapılandırılır ve yerel geliştirme bilgisayarlarda bireysel kod projeleri için çalıştırın. Bu bölümde, bir takım projesi için kod çözümleme iade ilkeleri belirtme ve yönetilen kod için özel kod analizi ilkeleri uygulamak nasıl açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Standart Kod Çözümleme İade İlkeleri Oluşturma veya Güncelleme](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Ayarlamak ve bir takım projesi için Kod Analizi İlkesi değiştirmek için kullandığınız adımları açıklar.  
  
 [Yönetilen Kod için Özel İade İlkelerini Uygulama](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Bir takım projesi iade ilkesi için özel bir kural oluşturmak ve ekip projesinin kod projelerini iade ilkesi ile eşitlemek için kullandığınız adımları açıklar.  
  
 [Kod Çözümleme İade İlkeleri için Sürüm Uyumluluğu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Öğesinin sürümleri arasındaki Kod Analizi giriş kontrol uyumluluk sorunlarını açıklar [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Başvurulan Kod Analizi adlandırma kurallarında gösterilen sözlüğe sözcüklerin ve simgelerin ekleme açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Ayarlama ve kalite kapıları](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Takım Projesi İade İlkeleriyle Kod Kalitesini Arttırma](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)



