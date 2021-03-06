---
title: Kod analizi kural kümesi başvurusu
ms.date: 04/04/2018
description: Visual Studio eski kod analizi 'nde yerleşik kural kümeleri hakkında bilgi edinin. Kural kümelerindeki kaynakları görün. Bu kümeleri özelleştirilmiş kural kümelerinde nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cead2d51a13ce4ec137edcd55c7db91d84b04f7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867782"
---
# <a name="code-analysis-rule-set-reference"></a>Kod analizi kural kümesi başvurusu

Visual Studio 'da yönetilen kod projeleri için eski analizler yapılandırdığınızda, yerleşik *kural kümeleri* listesinden seçim yapabilirsiniz. Bazı kurallar yerleşik kural kümelerinden birine dahildir. Örneğin, temel doğruluk kuralları kural kümesi, Yönetilen Önerilen Kurallar kural kümesindeki kuralları içerir.

> [!NOTE]
> Bu bölümdeki kural kümeleri eski Analize aittir. Kod Çözümleyicisi paketleri için kullanılabilen kural kümeleri hakkında daha fazla bilgi için bkz. [kural kümelerini kod Çözümleyicileri Ile kullanma](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

Bu yerleşik kural kümelerinden birini kullanabilir ya da [bir kural kümesini](../code-quality/how-to-create-a-custom-rule-set.md) proje gereksinimlerinize uyacak şekilde özelleştirebilirsiniz. Özel bir kural kümesinde aynı kuralı içeren birden çok kural kümesi eklerseniz, bu kural özel kural kümesinde yalnızca bir kez görünür.

Bu bölümdeki konular, yerleşik kural kümelerini ve içerdikleri kuralları (veya uyarıları) anlatmaktadır.

| Kural kümesi | Dahil edilen kurallar |
| - | - |
| [Tüm Kurallar](all-rules-rule-set.md) | Tüm kullanılabilir yönetilen ve C++ kurallarını içerir |
| [Temel Doğruluk Kuralları](basic-correctness-rules-rule-set-for-managed-code.md) | Mantık hataları ve çerçeve kullanımı için yönetilen önerilen kuralları ve kuralları içerir |
| [Genişletilmiş Doğruluk Kuralları](extended-correctness-rules-rule-set-for-managed-code.md) | Temel doğruluk kurallarını (Yönetilen Önerilen kuralları içerir) ve mantık hataları ve çerçeve kullanımı için daha fazla kuralı içerir |
| [Temel Tasarım Kılavuzu Kuralları](basic-design-guideline-rules-rule-set-for-managed-code.md) | , Kodun okunmasını, anlaşılmasını ve bakımını kolaylaştırmak için yönetilen önerilen kuralları ve kuralları içerir |
| [Genişletilmiş Tasarım Kılavuzu Kuralları](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Temel tasarım kılavuz kuralları (Yönetilen Önerilen kuralları içerir) ve adlandırmaya odaklanabilecek daha fazla bakım kuralı içerir |
| [Genelleştirme kuralları](globalization-rules-rule-set-for-managed-code.md) | Genelleştirme sorunları için kuralları içerir |
| [Yönetilen Minimum Kurallar](managed-minimum-rules-rule-set-for-managed-code.md) | Kritik yönetilen kod sorunları için dört kural içerir |
| [Yönetilen Önerilen Kurallar](managed-recommended-rules-rule-set-for-managed-code.md) | Yönetilen minimum kuralların yanı sıra kritik yönetilen kod sorunları için daha fazla kural içerir |
| [Karışık Minimum Kurallar](mixed-minimum-rules-rule-set.md) | CLR için C++ kodunda kritik sorunlara yönelik kurallar içerir |
| [Karışık Önerilen Kurallar](mixed-recommended-rules-rule-set.md) | CLR için C++ kodunda karışık minimum kuralların yanı sıra kritik sorunlar için daha fazla kural içerir |
| [Yerel Minimum Kurallar](native-minimum-rules-rule-set.md) | Yerel koddaki kritik sorunlara yönelik kurallar içerir |
| [Yerel Önerilen Kurallar](native-recommended-rules-rule-set.md) | Yerel en düşük kuralları ve yerel koddaki kritik sorunlar için daha fazla kuralı içerir |
| [Güvenlik kuralları](security-rules-rule-set-for-managed-code.md) | Güvenlik açıklarını bulmaya yönelik kuralları içerir |