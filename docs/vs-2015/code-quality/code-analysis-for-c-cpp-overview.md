---
title: Kod Analizi için C / C++ genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f7261b0bab423aa851b44ec725ca1c2818da9319
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763575"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ İçin Kod Çözümlemesine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ kod çözümleme aracı, geliştiricilere, C/C++ kaynak kodunda olası hatalar hakkında bilgi sağlar. Bellek ve kaynak sızıntıları ve null işaretçiye veya araç tarafından bildirilen genel kodlama hatalarını arabellek taşmaları, başlatılmamış bellek içerir.  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (tümleşik geliştirme ortamı) Tümleştirmesi  
 Analiz aracı kullanmak, geliştiriciler için doğal hale getirmek için tam olarak içinde entegre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Derleme işlemi sırasında kaynak kodu oluşturulan tüm uyarılar hata listesinde görünür. Uyarıya neden olan kaynak koduna gitmek ve nedenini ve sorunun olası çözümleri hakkında daha fazla bilgi görüntüleyebilirsiniz.  
  
## <a name="pragma-support"></a>#pragma desteği  
 Geliştiriciler `#pragma` uyarıları hata olarak değerlendir; etkinleştirmek veya uyarıları devre dışı bırak ve tek tek satırlık bir kod için uyarıları bastırmak için yönergesi. Daha fazla bilgi için [nasıl yapılır: etkinleştirme ve devre dışı bırakmak için kod çözümleme belirli C/C++ uyarıları](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Ek açıklama desteği  
 Ek açıklamalar, Kod Analizi doğruluğunu artırın. Ek açıklamalar, işlev parametrelerinde öncesi ve sonrası koşulları hakkında ek bilgiler sağlar ve dönüş türleri. Daha fazla bilgi için [nasıl yapılır: ek kod __analysis_assume kullanarak bilgilerini belirt](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>İade ilkesinin parçası olarak analiz aracı  
 Tüm kaynak kodu iade etmelerin bazı ilkeleri karşılamasını zorunlu isteyebilirsiniz. Özellikle, çözümleme en son yerel yapı bir adım olarak çalıştırıldığı emin olmanız gerekir. Kod Analizi İlkesi iade etkinleştirme hakkında daha fazla bilgi için bkz. [oluşturma ve kod çözümleme iade ilkelerini kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Ekip Oluşturma entegrasyonu  
 Bir adım olarak kod çözümleme aracı çalıştırmak için derleme sisteminin tümleşik özelliklerini kullanabilirsiniz [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] derleme işlemi. Daha fazla bilgi için [uygulamayı derleyin](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Komut satırı desteği  
 Geliştirme ortamında tam tümleştirme yanı sıra, ayrıca komut satırından, analiz aracı geliştiriciler, aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz:  
  
 `C:\>cl /analyze Sample.cpp`



