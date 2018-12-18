---
title: 'Nasıl yapılır: C / C++ projeleri için kod çözümleme özelliklerini ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 447bb9dfedc93594c6af014b830bfabc1b7ecf39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752653"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Nasıl yapılır: C/C++ Projeleri için Kod Çözümleme Özelliklerini Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod çözümleme aracı her projenizin yapılandırmasını kodda çözümlemek için hangi kuralları kullanacağını yapılandırabilirsiniz. Ayrıca, oluşturulan ve projenize bir üçüncü taraf araç tarafından eklenen koddan uyarıları bastırmak için Kod Analizi yönlendirebilir.  
  
## <a name="code-analysis-property-page"></a>Kod Analizi özellik sayfası  
 **Kod Analizi** özellik sayfası, proje için tüm kod analizi yapılandırma ayarlarını içerir. Bir proje için Kod Analizi özellik sayfasını açmak için **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **özellikleri**. Ardından, genişletme **yapılandırma özellikleri** seçip **Kod Analizi** sekmesi.  
  
## <a name="project-configuration-and-platform"></a>Proje yapılandırması ve platformu  
 **Yapılandırma** listesi ve **Platform** listesi farklı proje yapılandırma ve platform bileşimleri için farklı kod analizi ayarları uygulamanıza olanak tanır. Örneğin, projeniz için hata ayıklama için bir kural kümesi uygulamak için Kod Analizi yapıları ve sürüm için farklı bir küme oluşturur yönlendirebilir.  
  
## <a name="enabling-code-analysis"></a>Kod analizini etkinleştirme  
 Projeniz için Kod Analizi seçerek etkinleştirip etkinleştirmemeye karar **etkinleştirmek Kod Analizi C/C++ için derleme üzerinde**. İle birlikte **yapılandırma** listesi Örneğin, karar hata ayıklama yapıları ve etkinleştirmek için sürüm derlemeleri için Kod Analizi devre dışı bırakmak.  
  
 Yönetilen Kod projenizi içeren, etkinleştirme veya Kod Analizi seçerek devre dışı karar verebilir **derlemede kod analizini etkinleştir**.  
  
 Kod Analizi, kodunuzun kalitesini ve yaygın görülen tehlikeleri önlemek amacıyla tasarlanmıştır. Bu nedenle, dikkatlice Kod Analizi devre dışı bırakılıp bırakılmayacağını. Kural kümeleri devre dışı bırakmak daha iyi veya projenize istemediğiniz bireysel kuralları uygulanır.  
  
## <a name="generated-code"></a>Oluşturulan kod  
 Geliştiriciler, uygulamaları hızla geliştirmenizi sağlayacak sık araçlarını kullanın. Bu araçlar, projeye eklenen kod oluşturabilirsiniz. Kod Analizi üretilen kodda bulur kural ihlalleri görmek isteyebilirsiniz. Ancak, kodunu korumak istemiyorsanız görmek istemeyebilirsiniz.  
  
 **Bastır sonuçları oluşturulan kodun** onay kutusunu **genel** özellikleri sayfasında, bir üçüncü taraf araç tarafından oluşturulan yönetilen koddan kod çözümleme uyarıları görmek istediğiniz istemediğinizi sağlar .  
  
## <a name="rule-sets"></a>Kural Kümeleri  
 Yönetilen Kod projenizi içeren, bir kural kümesini seçerek bir kod analizi uygulanacak kuralları seçebilirsiniz **bu kural kümesini Çalıştır** listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kod kalitesini analiz etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C/C++ İçin Kod Analizi Uyarıları](../code-quality/code-analysis-for-c-cpp-warnings.md)



