---
title: 'İzlenecek yol: Yapılandırma ve kullanma özel bir kural kümesi | Microsoft Docs'
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
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5976ee0c0fbfc4befe97f2ab25c46744a8267134
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906058"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>İzlenecek Yol: Özel bir Kural Kümesini Yapılandırma ve Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, özelleştirilmiş kullanmak üzere yapılandırıldıklarını Kod Analizi araçları nasıl kullanacağınızı gösterir *kural kümesi* üzerinde bir sınıf kitaplığı. Eski kod bölünemez şekilde düzeltilen sorunlar için tarama gibi belirli bir gereksinimi karşılamak için alternatif bir kural kümeleri seçimi yapabilir veya çözümünüz için belirtilen proje türü için ilişkili bir kural kümesini seçebilirsiniz. Her iki durumda da kural kümelerini de bunları proje gereksinimlerinizi ince özelleştirilebilir.  
  
 Bu izlenecek yolda, bu işlemleri adım:  
  
-   Bir sınıf kitaplığı oluşturun.  
  
-   Seçin **Microsoft temel tasarım yönerge kuralları** Kod Analizi kural kümesi.  
  
-   Kendi kodunuzu sınıfına ekleyin.  
  
-   Kod analizini Çalıştır.  
  
-   Kural kümesi özelleştirin.  
  
-   Kod Analizi çalıştırmak ve nasıl özelleştirme davranışı works kural kümesi bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], veya [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Kural Kod Analizi ile kümeleri kullanma  
 İlk olarak, bir basit sınıf kitaplığı oluşturun.  
  
#### <a name="create-a-class-library"></a>Bir sınıf kitaplığı oluşturma  
  
1. Üzerinde **dosya** menüsünde tıklatın **yeni** ve ardından **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunun **proje türleri**, tıklayın **Visual C#**.  
  
3. Altında **Visual C#** seçin **sınıf kitaplığı**.  
  
4. İçinde **adı** metin kutusunda, **RuleSetSample** ve ardından **Tamam**.  
  
   Ardından, seçersiniz **Microsoft temel tasarım yönerge kuralları** kural kümesi ve projenizi kaydedin.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Kod Analizi kural kümesi seçin  
  
1. Üzerinde **Çözümle** menüsünde tıklatın **RuleSetSample için Kod Analizi yapılandırma**.  
  
    Kod Analizi için yapılandırma ayarlarını görünür.  
  
2. İçinde **bu kural kümesini Çalıştır** aşağı açılan listesinden **Microsoft tüm kurallar**.  
  
    Mevcut kuralı kümeleri hakkında daha fazla bilgi için bkz. [kod çözümleme kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md).  
  
    Dosya menüsünde **seçili öğeleri Kaydet** seçtiğiniz kural kümesi hakkında bilgi ve ayarları ile proje dosyası güncelleştirilemedi.  
  
   > [!TIP]
   >  Gerçek bir durumda, Kod Analizi ile hedeflemek için hangi sorunların öncelik için kullanılacak bir başlamak alışkanlıktır **önerilen Minimum kurallar** kural kümesi ve istenen sorunları düzeltin ve artımlı olarak ekleyin Daha fazla kural veya kural bulmak ve ek sorunları düzeltmek için ayarlar.  
  
   Sonra CA1704 ihlallerini göstermek için kullanılan sınıf kitaplığı için bazı kodlar ekleyeceksiniz "Tanımlayıcıları yazıldığından" Kod Analizi kural. Daha fazla bilgi için [CA1704: tanımlayıcılar yazıldığından](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Kendi kodunuzu ekleyin  
  
- Çözüm Gezgini'nde Class1.cs dosyasını açın ve varolan kodu aşağıdakiyle değiştirin:  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Text;  
  
  namespace RuleSetSample  
  {  
      public class Class1  
      {  
          //The variable parameter names "a" and "b" will cause  
          //the warning CA 1704 Microsoft.Naming "Consider   
          //providing a more meaningful name" to fire  
          public int AddIntegers(int a, int b)  
          {  
  
              int sum = a + b;  
  
              return (sum);  
          }  
      }  
  }  
  
  ```  
  
  Artık RuleSetSample proje üzerinde kod analizini Çalıştır ve hataları ve uyarıları hata Listesi penceresindeki oluşturulan arayın.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample projede Kod Analizi Çalıştır  
  
1. Üzerinde **Çözümle** menüsünde tıklatın **RuleSetSample kod çözümlemeyi Çalıştır**.  
  
2. Hata Listesi penceresindeki tıklayın **uyarıları** ve ardından **açıklama** uyarıları sıralamak için sütun başlığını alfasayısal olarak.  
  
    Gerçek bir uygulamada, bu noktada, düzeltme değer herhangi bir kural ihlallerini düzeltmek veya isteğe bağlı olarak devre dışı bırakmak veya düzeltme değerinde başarısız olduğunu belirlediyseniz, bir kural bastır. Daha fazla bilgi için [bastır uyarıları kullanarak SuppressMessage özniteliğini](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. CA1704 uyarılar dikkat edin. Şirket bu kural ihlalleri, "parametreleri için daha anlamlı bir ad sağlamayı göz önünde bulundurmanız gereken." belirtin. Kodunuzda bu sorunu çözmek veya, kural bir sonraki yordamda açıklandığı gibi devre dışı bırakabilirsiniz.  
  
   Ardından, kural kümesi CA1704 uyarı dışlanacak özelleştireceğim, "Tanımlayıcılar doğru yazılmalıdır".  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Kural kümesi belirli bir kural devre dışı bırakmak projeniz için özelleştirmek  
  
1. Üzerinde **Çözümle** menüsünde tıklatın **RuleSetSample için Kod Analizi yapılandırma**.  
  
2. İçinde **bu kural kümesini Çalıştır** aşağı açılan listesinde, doğrulayın **Microsoft tüm kurallar** kural kümesi hala vurgulanır ve ardından **açık**. Kural kümesi sayfası görüntülenir.  
  
3. Microsoft.Naming kategorisi düğümünü genişletin ve ardından CA1704 uyarısı seçin.  
  
4. Altında **eylem** sütunundaki **yok.** Bu, CA1704 bir uyarı veya Hata Listesi penceresindeki hata olarak görüntülenmesini önler.  
  
    Artık çeşitli araç çubuğu düğmeleri ile denemeniz için iyi bir zaman olabilir ve filtreleme seçenekleri, bunlarla ilgili bilgi sahibi olma. Örneğin, kullanabileceğiniz **Group By** belirli bir kural veya kural kategorisi bulma içinde yardımcı olmak için aşağı açılan listesi. Kullanabileceğiniz başka bir örnektir **Gizle devre dışı kurallarını** tüm kuralları göstermek veya gizlemek için kural kümesi sayfaları araç çubuğu düğmesini **eylem** sütun kümesine **hiçbiri**. Bu, yine de bunları devre dışı olmasını istediğinizi doğrulamak için kapatmış kuralları için taramak istiyorsanız yararlı olabilir.  
  
5. Görünüm menüsünde, Özellikler penceresinde tıklayın. Tür **My özel kural kümesi** araç penceresinin Ad kutusuna. Bu yeni kural kümesi görünen adını değiştirir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.  
  
6. Üzerinde **dosya** menüsünde tıklayın **Microsoft tüm Rules.ruleset Kaydet** , özelleştirilmiş kuralını kaydetmek için ayarlayın. Projenizin kök klasörüne gidin. İçinde **FileName** metin kutusunda, **MyCustomRuleSet**. Özel kural kümesi, şimdi projenizi ile kullanmak için seçilebilir.  
  
   Oluşturulan, yeni kural kümesi ile artık, yeni kuralınıza ile ayarlayın kullanmak istediğinizi belirtmek için proje ayarlarınızın yapılandırmanız gerekir.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Yeni Kural projenizi ile kullanılmak üzere kümesi belirtin  
  
1. Çözüm Gezgini'nde projeye sağ tıklayın ve ardından **özellikleri**.  
  
2. İçinde **özellikleri** sekmesinde **Kod Analizi**.  
  
    İçinde **bu kural kümesini Çalıştır** aşağı açılan listesinde, tıklayın  **\<Gözat... >**. Kodu projenizin kök klasörüne gidin ve ardından **MyCustomRuleSet.ruleset**. Önceki yordamda oluşturduğunuz yeni bir kural kümesi budur.  
  
3. Üzerinde **dosya** menüsünde tıklatın **Kaydet** proje yapılandırmanızı kaydetmek için. Özel kural kümesi projenizle artık kullanılabilir.  
  
   Son olarak, kod analizi, MyCustomRuleSet kural kümesini kullanarak yeniden çalıştırılır. Hata Listesi penceresine CA1704 performans kuralı ihlaline görüntülemez dikkat edin.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>İkinci kez RuleSetSample proje üzerinde kod analizini Çalıştır  
  
1.  Üzerinde **Çözümle** menüsünde tıklatın **RuleSetSample kod çözümlemeyi Çalıştır**.  
  
2.  ' A tıkladığınızda dikkat Hata Listesi penceresindeki **uyarıları**, CA1704 uyarı ihlalleri "Tanımlayıcılar doğru yazılmalıdır" kuralı için artık bkz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yönetilen kod projesi için kod çözümlemesini yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Kod çözümleme kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md)



