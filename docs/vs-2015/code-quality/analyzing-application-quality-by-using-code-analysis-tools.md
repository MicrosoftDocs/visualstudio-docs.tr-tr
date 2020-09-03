---
title: Kod analizi araçlarını kullanarak uygulama kalitesini analiz etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8ec0706530cd61653d44533654cf453d25eb42e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919067"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Kod Analiz Araçları ile Uygulama Kalitesini Analiz Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, yönetilen kod [kalitesini analiz etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) yönetilen kod Için Visual Studio kod analizi, Microsoft .NET Framework Tasarım yönergelerine göre ayarlanan programlama ve tasarım kurallarının ihlalleri gibi yönetilen derlemeler hakkında bilgi sağlar. Uyarı iletileri ilgili programlama ve tasarım sorunlarını belirler ve mümkünse sorunun nasıl düzeltileceğini gösteren bilgileri sağlar.

 [Kod analizini kullanarak C/C++ kod kalitesini analiz etme](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) C/C++ Kod Analizi Aracı, geliştiriciler için C/C++ kaynak kodundaki olası arızaların bilgilerini sağlar. Araç tarafından bildirilen yaygın kodlama hataları, arabellek taşmaları, Başlatılmamış bellek, null işaretçi başvurusu ve bellek ve kaynak sızıntılarını içerir.

 [Kod analizi kurallarını gruplandırmak Için kural kümeleri kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Projenize uygulanacak *kural kümelerini* seçin ve oluşturun.

 [Kod Analizi uygulama hataları](../code-quality/code-analysis-application-errors.md) Kod Analizi işlevindeki hataları düzeltir.

 [Takım projesi Iade Ilkeleriyle kod kalitesini geliştirme](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Team Foundation Sürüm Denetimi (TFVC) kullandığınızda, takım projeleriniz için daha iyi kod ve daha verimli grup geliştirmeye yol açabilecek uygulamalar uygulayan iade ilkeleri oluşturabilirsiniz. İade ilkeleri, kodun iade edilene izin verilmesi için takım projesi düzeyinde ayarlanan ve Geliştirici bilgisayarlarında uygulanan kurallardır.

### <a name="code-analysis-for-drivers"></a>Sürücüler için kod analizi
 Kod analizi araçları, sürücü kaynak kodunu sistematik olarak çözümleyerek sürücünüzün kararlılığını ve güvenilirliğini artırmaya yardımcı olabilir.

 [Kod analizi araçlarını kullanarak sürücü kalitesini analiz etme](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Sürücüler için kod analizi, C ve C++ programlarındaki temel kodlama hatalarını algılayan ve (birincil olarak) çekirdek modu sürücü kodundaki hataları algılamak için tasarlanan özel bir modül içeren derleme zamanı statik doğrulama aracıdır. Statik Sürücü Doğrulayıcısı (SDV), Windows çekirdek modu sürücülerinin kaynak kodunu sistematik olarak analiz eden bir statik doğrulama aracıdır. SDV, sürücünün Windows işletim sistemi çekirdekle doğru şekilde etkileşime sahip olup olmadığını belirler.

 [Sürücüler Için kod analizi uyarıları](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings) Sürücü kodunda olası bir hata algılandığında, sürücüler için kod analizinin rapor veren uyarıları açıklar.

## <a name="related-tasks"></a>İlgili görevler
 [Yönetilen kodun ölçüm karmaşıklığı ve Bakımma](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Açıklamayı buraya ekleyin.

 [Kodunuzun birim testi](../test/unit-test-your-code.md) Açıklamayı buraya ekleyin.
