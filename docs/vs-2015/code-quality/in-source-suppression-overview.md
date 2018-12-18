---
title: Kaynak bastırmaya genel bakış içindeki | Microsoft Docs
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
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 844681d079e5565aab9eceadb73f7d8a61cbb2c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209046"
---
# <a name="in-source-suppression-overview"></a>Kaynak Bastırmaya Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak gizleme özelliği ekleyerek yönetilen kodda Kod Analizi ihlallerini görmezden mı olduğunu **SuppressMessage** ihlallerine neden bir kod kesimlerini özniteliği. **SuppressMessage** yalnızca derleme zamanında code_analysıs derleme simge tanımlanmışsa, yönetilen kod derlemenizin IL meta verilerde bulunan conditional özniteliği bir özniteliktir.  
  
 C + +/ CLI, öznitelik eklemek için üst bilgi dosyasında CA_SUPPRESS_MESSAGE veya CA_GLOBAL_SUPPRESS_MESSAGE makrolarını kullanın.  
  
 Kaynak gizlemeleri yayın derlemelerinde kaynak gizleme meta verileri yanlışlıkla sevkiyat önlemek için kullanmamanız gerekir. Kaynak gizleme işlem maliyetini nedeniyle, kaynak gizleme meta veriler dahil ederek uygulamanızın performansını da düşebilir.  
  
> [!NOTE]
>  El kod bu öznitelikler kendiniz erişiminiz yok. Daha fazla bilgi için [nasıl yapılır: menü öğesini kullanarak uyarıları bastırma](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Menü öğesi, C++ kodu için kullanılamıyor.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage özniteliği  
 Kod Analizi uyarı olarak sağ tıkladığınızda **hata listesi** ve ardından **iletileri gösterme**, **SuppressMessage** özniteliği, kodunuzda veya çok eklenir Projenin genel dosyası.  
  
 **SuppressMessage** özniteliği şu biçime sahiptir:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Konum:  
  
-   **Kural kategorisi** -kategori kural tanımlanır. Kod Analizi kural kategorileri hakkında daha fazla bilgi için bkz: [yönetilen kod uyarıları için Kod Analizi](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Kural Kimliği** -kural tanımlayıcısı. Hem bir kural tanımlayıcısı için kısa ve uzun ad desteği içerir. CAXXXX kısa adıdır; uzun CAXXXX:FriendlyTypeName adıdır.  
  
-   **Gerekçe** -iletisini engelleme nedenini belge için kullanılan metin.  
  
-   **İleti kimliği** -bir sorun için her iletinin benzersiz tanımlayıcısı.  
  
-   **Kapsam** -hedef üzerinde uyarı engellenir. Hedef belirtilmemişse, özniteliğin hedef ayarlanır. Desteklenen kapsamları aşağıdakileri içerir:  
  
    -   Modül  
  
    -   Ad Alanı  
  
    -   Kaynak  
  
    -   Tür  
  
    -   Üye  
  
-   **Hedef** - üzerinde uyarı engellenir hedef belirtmek için kullanılan tanımlayıcı bir. Bir öğe tam adı içermelidir.  
  
## <a name="suppressmessage-usage"></a>SuppressMessage kullanımı  
 Kod çözümleme uyarıları hangi düzeyde gizlenir örneği **SuppressMessage** özniteliği uygulanır. Bunun amacı, sıkı bir şekilde kod gizleme bilgileri eşleştiği ihlalin gerçekleştiği sağlamaktır.  
  
 Kural kategorisi ve kural adı isteğe bağlı okunabilir bir temsilini içeren bir kural tanımlayıcısı genel formu gizleme içerir. Örneğin,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Kaynak gizleme meta veriler en aza indirmek için katı Performans nedeniyle varsa, kural adı bırakılabilir. Kural kategorisi ve kural kimliği birlikte yeterince benzersiz kural tanımlayıcısı oluşturur. Örneğin,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Bakım sorunları nedeniyle bu biçim önerilmez.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Bir yöntem gövdesi içinde birden çok ihlalleri gizleme  
 Öznitelikleri yalnızca bir yöntem uygulanabilir ve yöntem gövdesinde eklenemiyor. Ancak, bir yöntem içinde bir ihlalin birden çok defa geçmelerine ayırt etmek için ileti kimliği olarak tanımlayıcısını belirtin.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Oluşturulan kod  
 Yönetilen kod derleyicileri ve bazı üçüncü taraf araçları hızlı kod geliştirme kolaylaştırmak için kod oluşturur. Kaynak dosyalarında görünür, derleyicinin ürettiği kodu ile işaretlenmiş genellikle **GeneratedCodeAttribute** özniteliği.  
  
 Kod Analizi uyarıları ve hataları üretilen kod için engellenip engellenmeyeceğini seçebilirsiniz. Bu tür uyarılar ve hatalar gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: üretilen kod için uyarıları bastır](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Kod Analizi yoksayar Not **GeneratedCodeAttribute** zaman uygulandığı bütünleştirilmiş tamamını veya tek bir parametre. Bu durum nadiren oluşur.  
  
## <a name="global-level-suppressions"></a>Genel düzeyi Gizlemelerinin  
 Yönetilen kod analizi aracı inceler **SuppressMessage** derleme, modül, tür, üye veya parametre düzeyinde uygulanan öznitelikler. Ayrıca, kaynakları ve ad alanlarına karşı ihlalleri tetikler. İhlalleri genel düzeyde uygulanması gerekir ve kapsamına ve hedef. Örneğin, aşağıdaki ileti bir ad alanı ihlali engeller:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Ad alanı kapsamında bir uyarıyla gizlediğinizde, ad karşı uyarı bastırır. Ad alanı içindeki türleri karşı uyarı engellemez.  
  
 Açık bir kapsam belirterek herhangi bir gizleme ifade edilebilir. Bu gizlemeleri genel düzeyde bulunmalıdır. Bir tür tasarlayarak üye düzeyinde gizleme belirtemezsiniz.  
  
 Genel düzeyi gizlemelerinin açıkça sağlanan kullanıcının kaynağa eşlenmiyor derleyicinin ürettiği kodu başvuran iletilerinin gösterilmemesini tek yoludur. Örneğin, aşağıdaki kod bir ihlali derleyici yayılan bir oluşturucu karşı engeller:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Hedef, her zaman tam öğe adı içerir.  
  
## <a name="global-suppression-file"></a>Küresel bir gizleme dosyası  
 Küresel bir gizleme dosyası genel düzeyi gizlemelerinin ya da bir hedef belirtmeyin gizlemeleri gizlemeleri tutar. Örneğin, derleme düzeyi ihlalleri gizlemeleri bu dosyada depolanır. Ayrıca, proje düzeyi ayarları bir formun arkasındaki kod için kullanılabilir olmadığından bazı ASP.NET gizlemeleri bu dosyada depolanır. Küresel bir gizleme oluşturulur ve projeniz için seçtiğiniz ilk kez eklendi **proje gizleme dosyası** seçeneği **iletileri gösterme** Hata Listesi penceresindeki komutu. Daha fazla bilgi için [nasıl yapılır: menü öğesini kullanarak uyarıları bastırma](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.CodeAnalysis>



