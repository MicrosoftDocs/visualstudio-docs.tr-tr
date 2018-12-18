---
title: '6. adım: çıkarma problemi ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6960f7ca6db9584af8d43b9cee0d0c6bc810bc7f
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747899"
---
# <a name="step-6-add-a-subtraction-problem"></a>6. adım: çıkarma problemi ekleme
Bu öğreticinin altıncı bölümünde çıkarma problemi ekleme ve aşağıdaki görevleri nasıl gerçekleştireceğinizi öğrenin:

-   Çıkarma değerleri depolar.

-   Soruna yönelik rastgele sayılar oluşturma (ve yanıt 0 ile 100 arasında olduğundan emin olun).

-   Yanıtlar denetler ve böylece yeni çıkarma problemi çok denetler yöntemi güncelleştirin.

-   Zamanlayıcı 's güncelleştirme <xref:System.Windows.Forms.Timer.Tick> olay işleyicisi böylece süresi dolmadan doğru yanıt olarak olay işleyicisi doldurur.

## <a name="to-add-a-subtraction-problem"></a>Çıkarma problemi ekleme

1.  Toplama problemi tamsayı değişkenleri Zamanlayıcı arasındaki formunuza çıkarma problemi iki tamsayı değişkenleri ekleyin. Kod aşağıdaki gibi görünmelidir.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     Yeni tamsayı değişkenlerin adlarındaki —**minuend** ve **subtrahend**— koşulları programlama değil. Yüklenmekte olan numarası (subtrahend) çıkarılır ve subtrahend yüklenmekte olan numarası (minuend) çıkarılır aritmetik geleneksel adlarında olup olmadıklarını. Subtrahend eksi minuend farktır. Değişkenleri, denetimleri, bileşenleri ya da yöntemleri için belirli adları programınızı gerektirmediğinden diğer adlarını kullanabilirsiniz. Adları sayıyla başlayarak değil gibi kurallara uymalıdır, ancak genellikle x1, x2, x3 ve x4 gibi adlar kullanabilirsiniz. Ancak, genel adlar kod okunması zor ve sorunları izlemek neredeyse imkansız kolaylaştırır. Değişken adları benzersiz ve yararlı tutmak için geleneksel adları çarpma için kullanacağınız (multiplicand × çarpanı ürün =) ve bölme (bölünen ÷ bölen sayının =) Bu öğreticide daha sonra.

     Ardından, değiştireceğiniz `StartTheQuiz()` yöntemi için çıkarma problemi rastgele değerler sağlayın.

2.  Aşağıdaki kod sonra "çıkarma sorunu dolgu" açıklama ekleyin.

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Çıkarma problemi için negatif yanıtları önlemek için bu kod kullanır <xref:System.Random.Next> yöntemi <xref:System.Random> biraz farklı bir toplama problemi nasıl mu sınıfı. Ne zaman size `Next()` yöntemi iki değerleri daha büyük veya eşit olduğu ilk değeri ve küçük rastgele bir sayıyı Çekmeleri ikinciden. Aşağıdaki kod, 1 ile 100 arası bir rastgele sayı seçer ve minuend değişkeninde depolar.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Çağırabilirsiniz `Next()` "rasgele Sıralayıcı" daha önce bu öğreticide, birden çok yolla adlı rastgele sınıfının yöntemi. Birden çok yolla çağırabilirsiniz yöntemleri için aşırı yüklü olarak da adlandırılır ve bunları keşfetmek için IntelliSense kullanabilirsiniz. Bakabilir yeniden araç ipucu için IntelliSense penceresinin `Next()` yöntemi.

     ![IntelliSense penceresi araç ipucu](../ide/media/express_overloads.png)
**IntelliSense** penceresi araç ipucu

     Araç İpucu gösterir **(+ 2 overload(s))**, çağırabilirsiniz anlamına `Next()` iki yolla yöntemi. Böylece birbirinden biraz farklı çalıştığını aşırı farklı sayılar veya bağımsız değişken türleri içerir. Örneğin, bir yöntem tek tamsayı bağımsız değişkeni sürebilir ve onun aşırı birini bir tamsayı ve bir dize alabilir. Ne yapmak istiyorsunuz üzerinde göre doğru aşırı seçin. Koda eklediğinizde `StartTheQuiz()` yöntemi, daha fazla bilgi IntelliSense penceresinde görünür girdiğiniz hemen `randomizer.Next(`. Aşırı yükleme geçiş yapmak için seçin **yukarı ok** ve **aşağı ok** anahtarları aşağıdaki çizimde gösterildiği gibi:

     ![Sonraki aşırı&#40; &#41; IntelliSense yönteminde](../ide/media/express_nextoverload.png) için aşırı yükleme **Next()** yönteminde **IntelliSense**

     Bu durumda, minimum ve maksimum değerleri belirttiğinden son aşırı seçin istiyorsunuz.

3.  Değiştirme `CheckTheAnswer()` yöntemi için doğru çıkarma yanıt denetleyin.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     Visual C# ' ta, `&&` olan `logical and` işleci. Visual Basic'te eşdeğer işlecidir `AndAlso`. "Bu işleçlere addend1 ve addend2 toplamı NumericUpDown toplamın değeri eşitse ve minuend subtrahend eksi NumericUpDown fark değeri eşitse." gösterir `CheckTheAnswer()` Yöntemi döndürür `true` yalnızca toplama ve çıkarma sorunları yanıtlarını hem de doğru olması gerekir.

4.  Süresi dolmadan zaman doğru yanıt olarak doldurması Zamanlayıcı'nın onay olay işleyicisi son bölümü aşağıdaki kod ile değiştirin.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5.  Kaydedin ve kodunuzu çalıştırmak.

     Programınızı çıkarma problemi, aşağıda gösterildiği gibi içerir:

     ![Matematik testi çıkarma sorunla](../ide/media/express_addsubtract.png)
**matematik testi** çıkarma problemi ile

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [adım 7: çarpma ve bölme sorunları eklemek](../ide/step-7-add-multiplication-and-division-problems.md).

-   Eğitmen önceki adıma dönmek için bkz: [5. adım: NumericUpDown denetimleri için olay işleyicileri ekleme girin](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
