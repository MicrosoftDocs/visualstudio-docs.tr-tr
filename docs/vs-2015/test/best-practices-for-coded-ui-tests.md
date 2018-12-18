---
title: En iyi uygulamaları için kodlanmış UI testleri | Microsoft Docs
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
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1a067751662895f99f4caf95d487dc8c8a4672f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903588"
---
# <a name="best-practices-for-coded-ui-tests"></a>Kodlanmış UI Testleri için En İyi Yöntemler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, kodlanmış UI testleri geliştirirken izlenecek en iyi uygulamaları açıklar.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="best-practices"></a>En İyi Yöntemler  
 Esnek bir kodlanmış UI testi oluşturmak için aşağıdaki kılavuzları kullanın.  
  
- Kullanım **kodlanmış UI Test Oluşturucusu** mümkün olduğunda.  
  
- Değişiklik yapmayın `UIMap.designer.cs` doğrudan dosya. Bunu yaparsanız, dosyadaki değişikliklerin üzerine yazılır.  
  
- Testinizi kayıtlı yöntemleri bir dizi oluşturun. Bir yöntem kayıt hakkında daha fazla bilgi için bkz: [kodlanmış UI testleri](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
- Kaydedilen her yöntem, bir tek sayfalı, form veya iletişim kutusu davranmalıdır. Her yeni sayfa, form veya iletişim kutusu için yeni bir test yöntemi oluşturun.  
  
- Bir yöntem, anlamlı bir yöntem adı yerine varsayılan adı kullanın. Anlamlı bir ad, yöntemin tanımlamanıza yardımcı olur.  
  
- Mümkün olduğunda, kaydedilen her yöntem için 10'dan az eylemleri sınırlayın. Modüler bu yaklaşım UI değişirse bir yöntem değiştirilecek kolaylaştırır.  
  
- Her bir onaylama işlemi kullanarak oluşturduğunuz **kodlanmış UI Test Oluşturucusu**, bu otomatik olarak ekler için onay yöntemi `UIMap.Designer.cs` dosya.  
  
- Kullanıcı Arabirimi (UI) değişirse, onaylama yöntemlerini veya test yöntemlerini yeniden kaydedin veya varolan bir test yöntemi etkilenen bölümleri yeniden kaydedin.  
  
- Ayrı bir oluşturma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> test altındaki uygulamanız her bir modül için dosya. Daha fazla bilgi için [birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
- UI denetimleri oluşturduğunuzda, test edilen uygulamada anlamlı adlar kullanın. Bu seçenek, daha fazla anlam ve kullanılabilirlik için otomatik olarak oluşturulan denetim adları sağlar.  
  
- Onaylamalar API'SİYLE kodlayarak oluşturuyorsanız kısmında bir onayları yöntemi oluşturma <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> sınıfının `UIMap.cs` dosya. Onaylama işlemi yürütmek için test yönteminizden bu yöntemi çağırın.  
  
- API ile doğrudan kod yazıyor olun, oluşturulan sınıflardaki özellikleri ve yöntemleri kullanın `UIMap.Designer.cs` , mümkün olduğunca kodunuzda dosya. Bu sınıflar, iş yapmak daha kolay, daha güvenilir ve daha üretken olmanıza yardımcı olur.  
  
  Kodlanmış UI testleri birçok değişiklik kullanıcı arabiriminde otomatik olarak uyum sağlar. Örneğin, bir kullanıcı Arabirimi öğesi konumuna veya rengine değiştiyse, çoğu zaman kodlanmış UI testi hala doğru öğeyi bulur.  
  
  Test çalıştırması sırasında her denetim sınıfı tarafından oluşturulan tanımlarında uygulanan arama özellikleri kümesi kullanarak UI denetimleri test çerçevesi tarafından bulunan **kodlanmış UI Test Oluşturucusu** içinde `UIMap.Designer.cs` dosya. Arama özellikleri özellik adları ve denetim gibi tanımlamak için kullanılan özellik değerleri ad-değer çiftleri içeren <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, ve <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> denetimin özellikleri. Arama özellikleri değişmeden, kodlanmış UI testi denetimin kullanıcı Arabiriminde başarıyla bulun. Arama özellikleri değiştirilirse, kodlanmış UI testleri, denetimleri ve windows kullanıcı Arabiriminde bulmak için buluşsal yöntemler uygulanan bir akıllı eşleştirme algoritmasını sahip. Kullanıcı arabirimini değiştiğinde bulunduklarından emin olmak için önceden tanımlanmış öğeleri arama özelliklerini değiştirmek mümkün olabilir.  
  
## <a name="what-to-do-if-your-user-interface-changes"></a>Kullanıcı arabiriminizi değişirse yapmanız gerekenler  
 Kullanıcı arabirimleri, geliştirme sırasında sık sık değiştirir. Bu değişikliklerin etkisini azaltmak için bazı yollar şunlardır:  
  
- Bu denetim ve kullanım başvuran kayıtlı yöntemi bulun **kodlanmış UI Test Oluşturucusu** bu yöntemin eylemleri yeniden kaydetmek için. Varolan eylemlerin üzerine yazmak için yöntem aynı adı kullanabilirsiniz.  
  
- Bir denetimi artık geçerli olmayan bir onaylama işlemi varsa:  
  
  -   Onaylama içeren yöntemi silin.  
  
  -   Test yönteminin'dan bu yöntem çağrısını kaldırın.  
  
  -   UI denetiminin üzerine artı düğmesi sürükleyerek yeni bir onaylama Ekle, UI haritasını açın ve yeni onaylama Ekle.  
  
  Kodlanmış UI testleri nasıl kaydedileceği hakkında daha fazla bilgi için bkz: [kullanım UI Otomasyon için Test kodunuzu](../test/use-ui-automation-to-test-your-code.md).  
  
## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Test devam etmeden önce tamamlamak bir arka plan işlemi ihtiyacı varsa yapmanız gerekenler  
 Sonraki UI eylem ile devam etmeden önce bir işlemin tamamlanmasını beklemeniz gerekebilir. Kullanabileceğiniz bunu yapmanın <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> aşağıdaki örnekte olduğu gibi test devam etmeden önce beklenecek.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Birden çok UI eşlemesi bulunan büyük uygulamaları sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



