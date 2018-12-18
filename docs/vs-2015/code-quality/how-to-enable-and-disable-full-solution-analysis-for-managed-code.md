---
title: 'Nasıl yapılır: yönetilen kod için tam çözüm analizini devre | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: af0aae4020182f6414d44a2004f98a6fc0df23ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221877"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Nasıl yapılır: yönetilen kod için tam çözüm analizini devre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[NOT]
>  Bu konu, yalnızca Visual Studio 2015 güncelleştirme 3 RC ve daha sonra uygulanır.  
  
 *Tam çözüm analizini* çözümünüzdeki ya da açık ve kapalı Visual C# veya Visual Basic dosyalarında çözümünüzdeki açık Visual C# veya Visual Basic dosyaları, yalnızca kod analizi sorunlarına görüp görmediğinizi seçmenize olanak tanıyan bir Visual Studio özelliğidir.  
  
 Tüm dosyalardaki tüm sorunları görmek için kullanışlı olsa da, çözümünüzü çok büyük veya çok sayıda dosya varsa, Visual Studio yavaşlamasına bile dağıtabilir ve notların olabilir.  Gösterilen sorunların sayısını sınırlayabilir ve Visual Studio performansını artırmak için tam çözüm analizini devre dışı bırakabilirsiniz. İsterseniz bu özellik kolayca yeniden etkinleştirebilirsiniz.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Tam çözüm analizini açıp kapatmak için  
  
1.  Visual Studio ana menüsünde **Araçları** &#124; **seçenekleri** görüntülemek için **seçenekleri** iletişim kutusu.  
  
2.  İçinde **seçenekleri** iletişim kutusunda **metin düzenleyici** &#124; **C#** veya **temel** &#124; **Gelişmiş**.  
  
3.  Seçin **tam çözüm analizini etkinleştirme** onay kutusunu tam çözüm analizini etkinleştirme veya devre dışı bırakmak için onay kutusunu temizleyin. Seçin **Tamam** işiniz bittiğinde düğmesi.  
  
     ![Tam çözüm analizi onay kutusunu etkinleştirin. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Sonuçlarını tam çözüm analizini devre dışı bırakma ve etkinleştirme  
 Tam çözüm analizini etkin olduğunda, aşağıdaki ekran görüntüsünde, sonuçlarını görebilirsiniz. Tüm hataları ve Kod Analizi sorunlarıyla *tüm* dosyaların Çözümdeki dosyalar veya açık olup bağımsız olarak görünür.  
  
 ![Tam çözüm analizini etkin. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 Aşağıdaki ekran görüntüsünde, tam çözüm analizini devre dışı bıraktıktan sonra aynı çözümünden alınan sonuçları gösterir. Yalnızca hataları ve içinde kod analizi sorunlarına çözüm dosyalar görünür hata listesinde açın.  
  
 ![Tam çözüm analizini devre dışı. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Otomatik olarak tam çözüm analizini devre dışı bırakma  
 Visual Studio algılarsa 200MB veya daha az sistem belleği için kullanılabilir, etkinleştirildiğinde, otomatik olarak tam çözüm analizini (yanı sıra diğer bazı özellikleri) devre dışı bırakır. Bu meydana gelirse, bu size bildiren bir uyarı görünür. Bir düğme istediğinizde bunu yapmak tam çözüm analizini yeniden etkinleştirmenize olanak tanır.  
  
 ![Uyarı metni tam çözüm analizini askıya](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Ek ayrıntılar  
 Varsayılan olarak, tam çözüm analizini Visual Basic için etkinleştirilir ve Visual C# için devre dışı.  
  
 Visual Studio güncelleştirme 3 RC, önemli ölçüde bellek kullanımını azaltır ve tam çözüm analizini etkin olsa bile, boşta için CPU süresini azaltır bir Gelişmiş kod Çözümleyicisi v2 Tanılama Altyapısı içerir.



