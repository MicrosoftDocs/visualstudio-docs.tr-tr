---
title: Kodlanmış UI Testleri için En İyi Yöntemler
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed2ab3ff15e94bf0e014b99b6451840e6f26a04e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896030"
---
# <a name="best-practices-for-coded-ui-tests"></a>Kodlanmış UI testleri için en iyi uygulamalar

Bu konuda geliştirme kodlanmış UI testleri için bazı öneriler açıklanmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Önerilen uygulamalar

Esnek bir kodlanmış UI testi oluşturmak için aşağıdaki kılavuzları kullanın.

-   Kullanım **kodlanmış UI Test Oluşturucusu** mümkün olduğunda.

-   Değişiklik yapmayın *UIMap.Designer.cs* doğrudan dosya. Dosyayı değiştirirseniz, dosyadaki değişikliklerin üzerine yazılır.

-   Testinizi kayıtlı yöntemleri bir dizi oluşturun. Bir yöntem kayıt hakkında daha fazla bilgi için bkz: [kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md).

-   Kaydedilen her yöntem, bir tek sayfalı, form veya iletişim kutusu davranmalıdır. Her yeni sayfa, form veya iletişim kutusu için yeni bir test yöntemi oluşturun.

-   Bir yöntem, anlamlı bir yöntem adı yerine varsayılan adı kullanın. Anlamlı bir ad, yöntemin tanımlamanıza yardımcı olur.

-   Mümkün olduğunda, kaydedilen her yöntem için 10'dan az eylemleri sınırlayın. Modüler bu yaklaşım UI değişirse bir yöntem değiştirilecek kolaylaştırır.

-   Her bir onaylama işlemi kullanarak oluşturduğunuz **kodlanmış UI Test Oluşturucusu**, bu otomatik olarak ekler için onay yöntemi *UIMap.Designer.cs* dosya.

-   Kullanıcı Arabirimi (UI) değişirse, onaylama yöntemlerini veya test yöntemlerini yeniden kaydedin veya varolan bir test yöntemi etkilenen bölümleri yeniden kaydedin.

-   Ayrı bir oluşturma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> test altındaki uygulamanız her bir modül için dosya. Daha fazla bilgi için [birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md).

-   UI denetimleri oluşturduğunuzda, test edilen uygulamada anlamlı adlar kullanın. Anlamlı adlar kullanarak otomatik olarak oluşturulan denetim adları için büyük açıklık ve kullanılabilirlik sağlar.

-   Onaylamalar API'SİYLE kodlayarak oluşturuyorsanız kısmında bir onayları yöntemi oluşturma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfının *UIMap.cs* dosya. Onaylama işlemi yürütmek için test yönteminizden bu yöntemi çağırın.

-   API ile doğrudan kod yazıyor olun, oluşturulan sınıflardaki özellikleri ve yöntemleri kullanın *UIMap.Designer.cs* , mümkün olduğunca kodunuzda dosya. Bu sınıflar, iş yapmak daha kolay, daha güvenilir ve daha üretken olmanıza yardımcı olur.

Kodlanmış UI testleri birçok değişiklik kullanıcı arabiriminde otomatik olarak uyum sağlar. Örneğin, bir kullanıcı Arabirimi öğesi konumuna veya rengine değiştiyse, çoğu zaman kodlanmış UI testi hala doğru öğeyi bulur.

Bir test çalıştırması sırasında bir dizi arama özellikleri'ni kullanarak test çerçevesi tarafından kullanıcı Arabirimi denetimleri bulunur. Her denetim sınıfı tarafından oluşturulan tanımlarında arama özellikleri uygulandığı **kodlanmış UI Test Oluşturucusu** içinde *UIMap.Designer.cs* dosya. Arama özellikleri özellik adları ve denetim gibi tanımlamak için kullanılan özellik değerleri ad-değer çiftleri içeren <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, ve <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> denetimin özellikleri. Arama özellikleri değişmeden, kodlanmış UI testi denetimin kullanıcı Arabiriminde başarıyla bulun. Arama özellikleri değiştirilirse, kodlanmış UI testleri denetimleri ve windows kullanıcı Arabiriminde bulmak için buluşsal yöntemler uygulayan bir akıllı eşleştirme algoritmasını sahip. Kullanıcı arabirimini değiştiğinde bulunduklarından emin olmak için önceden tanımlanmış öğeleri arama özelliklerini değiştirmek mümkün olabilir.

## <a name="if-your-user-interface-changes"></a>Kullanıcı arabiriminizi değişirse

Kullanıcı arabirimleri, geliştirme sırasında sık sık değiştirir. Bu değişikliklerin etkisini azaltmak için bazı yollar şunlardır:

-   Bu denetime başvuran kaydedilen yöntemi bulup kullanın **kodlanmış UI Test Oluşturucusu** bu yöntemin eylemleri yeniden kaydetmek için. Varolan eylemlerin üzerine yazmak için yöntem aynı adı kullanabilirsiniz.

-   Bir denetimi artık geçerli olmayan bir onaylama işlemi varsa:

    -   Onaylama içeren yöntemi silin.

    -   Test yönteminin'dan bu yöntem çağrısını kaldırın.

    -   UI denetiminin üzerine artı düğmesi sürükleyerek yeni bir onaylama Ekle, UI haritasını açın ve yeni onaylama Ekle.

Kodlanmış UI testleri nasıl kaydedileceği hakkında daha fazla bilgi için bkz: [kodunuzu test etmek için kullanım UI Otomasyonu](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Bir arka plan işlemi, test önce tamamlanması sürdürebilirsiniz

Sonraki UI eylem ile devam etmeden önce bir işlemin tamamlanmasını beklemeniz gerekebilir. Kullanabileceğiniz bunu yapmanın <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> aşağıdaki örnekte olduğu gibi test, devam etmeden önce beklenecek:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)