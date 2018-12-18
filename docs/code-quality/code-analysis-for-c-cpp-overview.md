---
title: C/C++ İçin Kod Çözümlemesine Genel Bakış
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 35f694d9cc397800249dd9b4acd86bf63d22ad93
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320715"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ genel bakış için Kod Analizi

C/C++ kod çözümleme aracı, C/C++ kaynak kodunuzdaki olası hatalar hakkında bilgi sağlar. Bellek ve kaynak sızıntıları ve null işaretçiye veya araç tarafından bildirilen genel kodlama hatalarını arabellek taşmaları, başlatılmamış belleği içerir. Araç ayrıca denetimleri karşı çalıştırabilirsiniz [C++ temel yönergeleri](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>IDE (tümleşik geliştirme ortamı) Tümleştirmesi

Kod çözümleme aracı, Visual Studio IDE içinde tamamen tümleşiktir.

Derleme işlemi sırasında kaynak kodu oluşturulan tüm uyarılar hata listesinde görünür. Uyarıya neden olan kaynak koduna gitmek ve nedenini ve sorunun olası çözümleri hakkında daha fazla bilgi görüntüleyebilirsiniz.

## <a name="command-line-support"></a>Komut satırı desteğini

Aşağıdaki örnekte gösterildiği gibi ayrıca komut satırından, analiz aracı kullanabilirsiniz:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 sürüm 15.7 ve üzeri** aracı CMake dahil olmak üzere herhangi bir yapı sistemiyle komut satırından çalıştırabilirsiniz.

## <a name="pragma-support"></a>#pragma desteği

Kullanabileceğiniz `#pragma` uyarıları hata olarak değerlendir; etkinleştirmek veya uyarıları devre dışı bırak ve tek tek satırlık bir kod için uyarıları bastırmak için yönergesi. Daha fazla bilgi için [nasıl yapılır: C/C++ projeleri için kod çözümleme özelliklerini ayarlama](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Ek açıklama desteği

Ek açıklamalar, Kod Analizi doğruluğunu artırın. Ek açıklamalar, işlev parametrelerinde öncesi ve sonrası koşulları hakkında ek bilgiler sağlar ve dönüş türleri. Daha fazla bilgi için [nasıl yapılır: ek kod __analysis_assume kullanarak bilgilerini belirt](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>İade ilkesinin parçası olarak analiz aracı

Tüm kaynak kodu iade etmelerin bazı ilkeleri karşılamasını zorunlu isteyebilirsiniz. Özellikle, çözümleme en son yerel yapı bir adım olarak çalıştırıldığı emin olmanız gerekir. Kod Analizi İlkesi iade etkinleştirme hakkında daha fazla bilgi için bkz. [oluşturma ve kod çözümleme iade ilkelerini kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Ekip Oluşturma entegrasyonu

Bir adım olarak kod çözümleme aracı çalıştırmak için derleme sisteminin tümleşik özelliklerini kullanabilirsiniz [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] derleme işlemi. Daha fazla bilgi için [Azure işlem hatları](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: C/C++ için Kod Analizi](quick-start-code-analysis-for-c-cpp.md)
- [İzlenecek yol: C/C++ kod kusurları için analiz edin.](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++ İçin Kod Analizi Uyarıları](code-analysis-for-c-cpp-warnings.md)
- [C++ Temel Yönergeleri denetleyicilerini kullanma](using-the-cpp-core-guidelines-checkers.md)
- [C++ temel yönergeleri denetleyici başvurusu](code-analysis-for-cpp-corecheck.md)
- [Çalıştırılacak C++ Kurallarını Belirtmek için Kural Kümeleri Kullanma](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Kod çözümleme araçları ile sürücü kalitesini analiz etme](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Sürücüleri uyarılar için Kod Analizi](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
