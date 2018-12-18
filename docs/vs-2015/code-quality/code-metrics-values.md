---
title: Kod ölçüm değerleri | Microsoft Docs
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
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 22c42cb215999fcc4415f4d7541b8f4b95ac2d29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782967"
---
# <a name="code-metrics-values"></a>Kod Ölçüm Değerleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod ölçümleri, geliştiricilere, geliştirdikleri daha iyi bir anlayış kod sağlayan yazılım ölçü kümesidir. Kod ölçümleri avantajlarından yararlanarak, geliştiriciler hangi türleri ve/veya yöntemleri yeniden işledi veya daha kapsamlı test anlayabilirsiniz. Geliştirme ekipleri olası riskleri belirlemek, bir proje geçerli durumunu anlamanıza ve yazılım geliştirme sırasında ilerlemeyi.  
  
## <a name="software-measurements"></a>Yazılım ölçümleri  
 Kod ölçümleri sonuçları aşağıda gösterilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hesaplar:  
  
-   **Bakım dizini** – 0 ile 100 arasında göreceli bir kolayca kod bakım temsil eden dizin değeri hesaplar. Yüksek bir değer daha iyi bakım anlamına gelir. Renk kodlu derecelendirmeleri, hızlı bir şekilde kodunuzda sorunlu noktaları tanımlamak için kullanılabilir. Yeşil bir derecelendirme 20 ile 100 arasında ve kod iyi bakım sahip olduğunu gösterir. Sarı bir derecelendirme 10 ile 19 arasında ve kod oldukça sürdürülebilir olduğunu gösterir. Kırmızı derecesi 0 ile 9 arasında bir derecelendirme ve düşük bakım belirtir.  
  
-   **Döngüsel karmaşıklık** – kod yapısal karmaşıklığını ölçer. Program akışını farklı kod yollarında sayısını hesaplayarak oluşturulur. Karmaşık denetim akışı olan bir program daha sürdürülebilir ve daha iyi kod kapsamını elde etmek için daha fazla test gerektirir.  
  
    > [!NOTE]
    >  Bazı durumlarda, bir yöntem için döngüzel karmaşıklığına hesaplanması [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] önceki sürümlerden farklıdır. Daha fazla bilgi için "değişiklikleri, Visual Studio 2010 kod karmaşıklığı hesaplamalar bölümünde" olmadığını [kod ölçümleri sorunlarını giderme](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Devralma derinliği** – sınıf hiyerarşisini köküne genişleten sınıf tanımları sayısını gösterir. Belirli yöntemleri ve alanları tanımlandığı anlamak için olabilir derinde hiyerarşi daha zor veya / ve yeniden tanımlanan.  
  
-   **Sınıf bağlantısından** – ölçer bağlantı parametreleri, yerel değişkenler, dönüş türleri, yöntem çağrılarını, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamalarını, dış türlerinde tanımlanan alanların benzersiz sınıflara ve özniteliği düzenleme. İyi yazılım tasarımı, türleri ve yöntemleri uyumun yüksek olması sahip ve eşlenmesiyle düşük olduğunu belirler. Yüksek bağlantısından yeniden kullanabilir ve diğer türleri, birçok bağımlılıkları nedeniyle korumak zor bir tasarımın belirtisidir.  
  
-   **Kod satırlarını** – yaklaşık kod içinde satır sayısını belirtir. Sayısı IL kodunu alır ve bu nedenle satır kaynak kodu dosyasının tam sayı değil. Çok yüksek bir sayı, bir türün veya yöntemin çok fazla iş yapmak çalışıyor ve bölünmesi gösterebilir. Ayrıca, tür veya yöntem korumak zor olabilir gösterebilir.  
  
## <a name="anonymous-methods"></a>Anonim Yöntemler  
 Bir *anonim yöntem* ada sahip bir yöntem. Anonim yöntemler, en sık temsilcinin parametre olarak bir kod bloğu geçirmek için kullanılır. Ölçümleri sonuçları bir yöntem veya erişimci gibi bir üye olarak bildirilen anonim yöntemi için yöntem bildiren bir üye ile ilişkili. Bunlar, bu yöntemi çağıran bir üye ile ilişkili değildir.  
  
 Kod ölçümleri anonim yöntemler nasıl işler hakkında daha fazla bilgi için bkz. [anonim metotlar ve kod çözümleme](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## <a name="generated-code"></a>Oluşturulan kod  
 Bazı yazılım araçları ve derleyicileri, bir projeye eklenir ve proje Geliştirici görmezsiniz veya değiştirme kod oluşturur. Çoğunlukla, ölçüm değerleri hesaplarken kod ölçümleri oluşturulmuş kodu yoksayar. Bu, hangi geliştirici bakın ve değiştirme yansıtacak şekilde ölçüm değerleri sağlar.  
  
 Geliştirici bakın ve değiştirme kodu olduğundan Windows forms için oluşturulan kodu yok sayıldı değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



