---
title: Takım projesi iade ilkeleri ile kod kalitesini arttırma | Microsoft Docs
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
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c48a4e9cb68997903eed017637c9f00db88261a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299032"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Takım Projesi İade İlkeleriyle Kod Kalitesini Arttırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Team Foundation sürüm denetimi (TFVC) kullandığınızda, takım projeleriniz için iade ilkeleri oluşturabilirsiniz. zorlamak için daha iyi kod ve daha verimli Grup gelişimi yol açan uygulamalar. İade ilkeleri takım projesi düzeyinde ayarlanan ve kod iade edilmesine izin verilmesinden önce Geliştirici bilgisayarlarında mecburi olan kurallardır.  
  
 Bu takım projesi iade ilkeleri belirtebilirsiniz:  
  
-   **Yapılar**: derleme sırasında oluşturulan yapı aralarının bir yeni iadeden önce düzeltilmesi gereken gerektirir.  
  
-   **Değişiklik kümesi açıklamalarını**: kullanıcıların değişiklikler iade edilirken açıklama sağlamanızı gerektirir.  
  
-   **Kod Analizi**: Kod Analizi iade etme önce çalışmasını gerektirir.  
  
-   **İş öğeleri**: iş öğelerinin biri veya daha fazla onay-'ile ilişkili olmasını gerektirir.  
  
> [!IMPORTANT]
>  İade ilkelerini kullanmak için bağlanmalıdır [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|Destekleyici İçerik|  
|----------|------------------------|  
|**İade etme ilkeleri oluşturun ve kullanın:** takım proje ayarlarını kullanarak iade ilkeleri oluşturma [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Ayarlama ve kalite kapıları](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Kod çözümleme iade ilkeleri oluşturup:** standart kod analizi kuralları kümesinden seçebilir veya özel bir grup oluşturabilirsiniz.|[Kod Çözümleme İade İlkeleri Oluşturma ve Kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>İlişkili görevler  
  
|Görev|Destekleyici İçerik|  
|----------|------------------------|  
|**Geliştirme ortamınızı ayarlama:** oluşturabilir veya kod değiştirme önce uygun kaynak kodu kullanarak geliştirme ve test ortamlarınızı ayarlamanız gerekir. Veritabanları ile çalışıyorsanız, ayrıca veritabanlarının çevrimdışı gösterimine erişiminiz olmalıdır.|[Geliştirme ortamlarını ayarlama](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Kod Analizi geliştirme sürecine kullanın:** takım üyeleri, Kod Analizi çözümlemelerini geliştiricinin bilgisayarında çalıştırın. Visual Studio'da geliştiriciler yapılandırmak ve bireysel kod projeleri için Kod Analizi yürütmeleri çalıştırın, görüntüleme ve sorunlarını analiz etmenize bulunan ve Uyarılar için iş öğeleri oluşturun.|[Uygulama Kalitesini Analiz Etme](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Birim testleri oluşturma ve çalıştırma:** birim testleri, C#, Visual Basic .NET ve C++ projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir şekilde geliştiricilere ve test edicilere verin. Birim test bir kez oluşturulabilir ve kaynak kodun hiçbir hatanın emin emin olmak için değiştirildiği her seferde çalıştırın.|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|  
|**İş öğelerini ve kusurları izleyin:** iş öğelerini takım projesi hakkındaki işleri ve bilgileri yönetmek ve izlemek için kullanabilirsiniz. Bir iş öğesi bir veritabanıdır bu kayıt [!INCLUDE[esprfound](../includes/esprfound-md.md)] atamasını ve çalışmanın ilerlemesini izlemek için kullanır. Farklı türlerde iş öğeleri, iş, müşteri gereksinimleri, ürün hataları ve geliştirme görevleri gibi farklı türlerde izlemek için kullanabilirsiniz.|[İş izleme ve iş akışını yönetme &#91;yönlendirildi&#93;](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Dış kaynaklar  
  
### <a name="guidance"></a>Kılavuz  
 [Visual Studio 2012 – bölüm 2 ile sürekli teslimat testi: birim testi: iç testler](http://go.microsoft.com/fwlink/?LinkID=255188)



