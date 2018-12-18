---
title: 'Nasıl yapılır: C/C++ Projeleri için Kod Çözümleme Özelliklerini Ayarlama'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: f2800ce4784f5a8215dfe49b00194925c3cdb588
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920683"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Nasıl yapılır: C/C++ Projeleri için Kod Çözümleme Özelliklerini Ayarlama
Kod çözümleme aracı her yapılandırma projenizin kodda çözümlemek için hangi kuralları kullanacağını yapılandırabilirsiniz. Ayrıca, oluşturulan ve projenize bir üçüncü taraf aracı tarafından eklenen koddan uyarıları gizlemek için Kod Analizi yönlendirebilirsiniz.

## <a name="code-analysis-property-page"></a>Kod çözümleme özellik sayfası
 **Kod Analizi** özellik sayfası, proje için tüm kod çözümleme yapılandırma ayarlarını içerir. Bir proje için Kod Analizi özellik sayfası açmak için **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **özellikleri**. Ardından, genişletin **yapılandırma özellikleri** seçip **Kod Analizi** sekmesi.

## <a name="project-configuration-and-platform"></a>Proje yapılandırması ve platformu
 **Yapılandırma** listesi ve **Platform** listesi için farklı bir proje yapılandırma ve platform birleşimlerini farklı kod çözümleme ayarlarını uygulamak olanak sağlar. Örneğin, bir kural kümesi projeniz için hata ayıklama uygulamak için Kod Analizi oluşturur ve sürüm için farklı bir küme oluşturur yönlendirebilirsiniz.

## <a name="enabling-code-analysis"></a>Kod çözümleme etkinleştirme
 Projeniz için Kod Analizi seçerek etkinleştirmek karar verebilir **etkinleştirme kodu analiz için C/C++ derleme üzerinde**. İle birlikte **yapılandırma** listesinde Örneğin, karar hata ayıklama yapıları ve onu yayımı için derlemeleri Etkinleştir için Kod Analizi devre dışı bırakmak.

 Projenizi yönetilen kodu içeriyorsa, etkinleştirmek veya Kod Analizi seçerek devre dışı bırakmak karar verebilir **etkinleştirmek Kod Analizi derlemede**.

 Kod çözümleme kodunuzun kalitesini geliştirmek ve ortak Tuzaklar önlemenize yardımcı olmak için tasarlanmıştır. Bu nedenle, dikkatlice Kod Analizi devre dışı bırakılıp bırakılmayacağını. Kural kümeleri devre dışı bırakmak daha iyi veya projenize istemediğiniz tek kurallar uygulanabilir.

## <a name="generated-code"></a>Oluşturulan kod
 Geliştiriciler, uygulamaları çabucak geliştirmelerine yardımcı olmak için sık araçlarını kullanın. Bu araçlar, projeye eklenen kodu oluşturabilir. Kod çözümleme oluşturulan kodda bulur kural ihlallerinin görmek isteyebilirsiniz. Bununla birlikte, kod korumak istemiyorsanız, bunları görmek istemeyebilirsiniz.

 **Bastırmak sonuçları oluşturulan kodun** onay kutusunu **genel** Özellikler sayfasında, bir üçüncü taraf aracı tarafından oluşturulan yönetilen koddan Kod Analizi uyarıları görmek istediğiniz isteyip sağlar .

## <a name="rule-sets"></a>Kural kümeleri
 Projenizi yönetilen kodu içeriyorsa, kümeden bir kural seçerek bir kod analizi uygulanacak kuralları seçebilirsiniz **bu kural kümesini çalıştırmak** listesi.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen kod kalitesini analiz etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [C/C++ uyarıları için kod çözümleme](../code-quality/code-analysis-for-c-cpp-warnings.md)