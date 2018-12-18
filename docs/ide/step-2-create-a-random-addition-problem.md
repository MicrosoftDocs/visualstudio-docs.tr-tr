---
title: '2. adım: rasgele bir toplama problemi oluşturma'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abd70e53c06da53f22bcac4c7f041aaef75bd412
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747873"
---
# <a name="step-2-create-a-random-addition-problem"></a>2. adım: rasgele bir toplama problemi oluşturma
Bu öğreticinin ikinci bölümünde, test zor rasgele rakamlar temelinde matematik sorunları ekleyerek yapın. Adlı bir yöntem de oluşturma `StartTheQuiz()` ve sorunlarını doldurur ve geri sayım süreölçer başlatır. Daha sonra Bu öğreticide çıkarma, çarpma ve bölme problemleri ekleyeceksiniz.

> [!NOTE]
>  Bu konuda bir öğretici serisi kodlama temel kavramları hakkında bir parçasıdır. Öğretici genel bakış için bkz: [Eğitmen 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Rasgele bir toplama problemi oluşturmak için

1.  Form Tasarımcısı'nda formu seçin (**Form1**).

2.  Menü çubuğunda seçin **Görünüm** > **kod**.

     *Form1.cs* veya *Form1.vb* kodu formun görüntüleyebilmesi için kullanmakta olduğunuz programlama dili bağlı olarak görünür.

3.  Oluşturma bir <xref:System.Random> ekleyerek nesne bir `new` deyimi aşağıdaki gibi kod üstüne yakın.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     Formunuz için rasgele nesne eklenmiş ve nesne adlı **rasgele Sıralayıcı**.

     `Random` bir nesne olarak bilinir. Büyük olasılıkla daha önce bu word duymadığınız ve sonraki öğretici programlamada için ne anlama geldiğini hakkında daha fazla bilgi edinin. Şu an için yalnızca kullanabileceğinizi unutmayın `new` düğmeleri, etiketleri, paneller, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms ve hatta forms ve bu öğeleri oluşturmak için deyimleri nesneler olarak adlandırılır. Programınızı çalıştırma, formu başlatan ve arkasındaki kod rastgele bir nesne oluşturur ve onu adları **rasgele Sıralayıcı**.

     En kısa sürede, test için her sorun oluşturur rastgele sayılar depolamak için değişkenleri kullanmalısınız yanıtlar denetlemek için bir yöntem yapı. Bkz: [değişkenleri](/dotnet/visual-basic/programming-guide/language-features/variables/index) veya [türleri](/dotnet/csharp/programming-guide/types/index). Değişkenleri düzgün bir şekilde kullanmak için bunları, adlarını ve veri türlerini listeleme anlamına gelir bildirmeniz gerekir.

4.  İki tamsayı değişken forma ekleyin ve bunları **addend1** ve **addend2**.

    > [!NOTE]
    >  Bir tamsayı değişken int'e C# veya Visual Basic'te bir tamsayı olarak bilinir. Bu tür bir değişken -2147483648 ile 2147483647 arasında bir pozitif veya negatif sayı depolar ve ondalık sayı değil yalnızca tam sayılar depolayabilirsiniz.

     Aşağıdaki kod gösterildiği gibi rasgele nesne eklemek için yaptığınız gibi bir tamsayı değişken eklemek için benzer bir sözdizimi kullanın.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5.  Adlı bir yöntem ekleyin `StartTheQuiz()` ve rasgele nesnenin kullanan <xref:System.Random.Next> etiketler rastgele sayılar göstermek için yöntem. `StartTheQuiz()` sonunda tüm sorunlar doldurun ve süreölçeri başlatmak, bu nedenle bir yorum ekleyin. İşlevi aşağıdaki gibi görünmelidir.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Nokta (.) girin, sonra fark `randomizer` kodda bir IntelliSense penceresi açar ve tüm çağırabilirsiniz rastgele nesnesinin yöntemlerini gösterir. Örneğin, IntelliSense listeler `Next()` şekilde yöntemi.

     ![Next yöntemi](../ide/media/express_randomwhite.png) Next yöntemi

     Bir nesne sonra bir nokta girdiğinizde, IntelliSense özellikleri, yöntemleri ve olayları gibi nesnenin üyelerin listesi gösterilir.

    > [!NOTE]
    >  Kullandığınızda `Next()` yöntemiyle `Random` çağırdığınızda gibi nesne `randomizer.Next(50)`, değerinden 50'dir (0 49 arasında) rastgele bir sayıyı alın. Bu örnekte, aradığınız `randomizer.Next(51)`. Böylece iki rastgele sayı 0 ile 100 arası bir yanıt ekler 51 ve değil 50 kullanılır. 50'ye geçirdiğinizde `Next()` yöntemi, seçtiği bir sayı 49, 0'dan yüksek olası yanıt 98, değil 100 gelir. Her iki tamsayı değişkenlerin yöntemi ilk iki ifadeler, çalıştırdıktan sonra **addend1** ve **addend2**, 0 ile 50 arasında rastgele bir sayı tutun. Bu ekran Visual C# kodunu gösterir, ancak IntelliSense için Visual Basic aynı şekilde çalışır.

     Bu deyimler daha yakın bir göz atın.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Deyimleri kümesi **metin** özelliklerini **plusLeftLabel** ve **plusRightLabel** böylece iki rastgele sayılar görüntüler. Tamsayı 's kullanmalısınız `ToString()` sayıları metne dönüştürmek için yöntem. (Programlamada dize metin anlamına gelir. Etiket denetimleri yalnızca metin, olmayan sayılar görüntülenir.

6.  Tasarım penceresinde ya da çift **Başlat** button, veya onu seçin ve ardından **Enter** anahtarı.

     Test alanın bu düğmesini seçtiğinde, test başlamanız gerekir ve bu davranışı uygulamak için bir Click olay işleyicisi yalnızca ekledik.

7.  Aşağıdaki iki deyimleri ekleyin.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     İlk ifade çağırır yeni `StartTheQuiz()` yöntemi. İkinci ifade ayarlar **etkin** özelliği **startButton** denetimini **False** böylece test alanın düğmesi bir test sırasında seçemezsiniz.

8.  Kodunuzu kaydetmek, çalıştırın ve ardından **Başlat** düğmesi.

     Rasgele bir toplama problemi, aşağıda gösterildiği gibi görünür.

     ![Rasgele bir toplama problemi](../ide/media/express_additionproblem.png) rasgele bir toplama problemi

     Öğreticinin sonraki adımda, toplam ekleyeceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [3. adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).

-   Eğitmen önceki adıma dönmek için bkz: [1. adım: Proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
