---
title: '2. adım: rasgele bir toplama problemi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47429cb995dd7374276a9e2872d1b80ed452281a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204379"
---
# <a name="step-2-create-a-random-addition-problem"></a>2. Adım: Rasgele bir Toplama Problemi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu Eğitimin ikinci kısmında, sınav zorlu rastgele rakamlara dayanan matematik soruları ekleyerek olun. Adlı bir yöntem de oluşturduğunuz `StartTheQuiz()` ve problemleri dolduran ve geri sayım Zamanlayıcısını başlatır. Bu öğreticide daha sonra çıkarma, çarpma ve bölme sorularını ekleyeceksiniz.  
  
> [!NOTE]
>  Bu konu, temel kodlama kavramları hakkındaki bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: bir zaman aşımına matematik sınavı oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-random-addition-problem"></a>Rasgele bir toplama problemi oluşturma  
  
1.  Form Tasarımcısı'nda (Form1) formunu seçin.  
  
2.  Menü çubuğunda, **görünümü**, **kod**.  
  
     Böylece biçimin ardındaki kodu görüntüleyebilirsiniz Form1.cs veya Form1.vb, kullandığınız, programlama diline göre görünür.  
  
3.  Oluşturma bir `Random` nesne ekleyerek bir `new` ekranın üst kısmında aşağıdaki gibi kod deyimi.  
  
     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]  
  
     Eklediğiniz bir `Random` nesne formunuza ve nesneyi **randomizer**.  
  
     `Random` bir nesne olarak bilinir. Daha önce bu sözcüğü olasılıkla duydunuz ve bir sonraki öğreticide programlama için demek olduğu hakkında daha fazla bilgi edinin. Şimdilik, hemen kullanabileceğiniz unutmayın `new` deyimlerini düğmeler, etiketler, paneller, Openfiledialog'lar, Colordialog'lar, Soundplayer'lar, Random'lar ve hatta biçimler ve bu öğeleri oluşturmak için nesne olarak adlandırılır. Programınızı çalıştırdığınızda form başlatılır ve ardındaki kod, bir `Random` nesne ve onu **randomizer**.  
  
     Yakında yanıtlarını sınavınız her problem için ürettiği rastgele sayıları depolamak için değişkenleri kullanmalısınız denetlemek için bir yöntem oluşturacaksınız. Bkz: [değişkenleri](http://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) veya [türleri](http://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Değişkenleri düzgün kullanmak için bunları, yani adlarını ve veri türlerini listeleme bildirmeniz gerekir.  
  
4.  Forma iki tamsayı değişkeni ekleyin ve bunları **addend1** ve **addend2**.  
  
    > [!NOTE]
    >  Bir tamsayı değişkeni C# veya Visual Basic'te bir tamsayı tamsayı olarak bilinir. Bu türde bir değişken, -2147483648 ile 2147483647 arasında bir pozitif veya negatif sayı depolar ve ondalık değil yalnızca tam sayılara depolayabilirsiniz.  
  
     Benzer bir sözdizimi eklemek için yaptığınız gibi bir tam sayı değişkeni eklemek için kullandığınız `Random` aşağıdaki kodun gösterdiği gibi bir nesne.  
  
     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]  
  
5.  Adlı bir yöntem ekleyin `StartTheQuiz()` kullanan ve `Random` nesnenin `Next()` etiketleri rastgele sayıları göstermek için yöntemi. `StartTheQuiz()` sonunda tüm problemleri doldurun ve süreölçeri başlatacak, bu nedenle bir açıklama ekleyin. İşlev, aşağıdaki gibi görünmelidir.  
  
     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]  
  
     Nokta (.) girdiğinizde, sonra dikkat **randomizer** kodda, bir IntelliSense penceresinin açılır ve tüm gösterir `Random` nesnesinin yöntemlerini çağırabilirsiniz. Örneğin, IntelliSense listeler `Next()` yöntemini aşağıdaki gibi.  
  
     ![Sonraki yöntem](../ide/media/express-randomwhite.png "Express_RandomWhite")  
Next yöntemi  
  
     Bir nesneden sonra bir nokta girdiğinizde, IntelliSense nesnenin üyeleri, özellikler, yöntemler ve olaylar gibi bir listesini gösterir.  
  
    > [!NOTE]
    >  Kullandığınızda `Next()` yöntemiyle `Random` çağırdığınızda gibi nesne `randomizer.Next(50)`, (Başlangıç, 0 ile 49 arasında) 50'den küçük rastgele bir sayı alın. Bu örnekte, aradığınız `randomizer.Next(51)`. Böylece iki rastgele sayı 0 ile 100 arası bir yanıt ekleyecek 51 ve 50 değil kullanılır. 50 geçirirseniz `Next()` yöntemi, bir sayı seçer 0 ile 49 arasında en yüksek olası yanıt 100 değil 98, bu nedenle. Her iki tamsayı değişkenleri, bir yöntemin ilk iki deyim, çalıştırdıktan sonra `addend1` ve `addend2`, 0 ile 50 arasında rastgele bir sayı tutun. Bu ekran Visual C# kodunu göstermektedir, ancak IntelliSense Visual Basic için aynı şekilde çalışır.  
  
     Bu deyimlere daha yakından bakalım.  
  
     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]  
  
     Deyimler **metin** özelliklerini **plusLeftLabel** ve **plusRightLabel** böylece bunlar iki rastgele sayı görüntüler. Bir tamsayının kullanmalısınız `ToString()` sayıları metne dönüştürmek için yöntemi. (Programlamada dize metin anlamına gelir. Etiket denetimleri, sayılar değil yalnızca metin görüntüler.  
  
6.  Tasarım penceresinde, çift tıklayın ya da **Başlat** düğmesini seçin ve ardından Enter tuşuna basın.  
  
     Sınavı alan bu düğmeyi seçtiğinde sınavın başlaması gerekir ve bu davranışı gerçekleştirmek için bir tıklama olayı işleyicisi yalnızca ekledik.  
  
7.  Aşağıdaki iki deyimi ekleyin.  
  
     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]  
  
     İlk deyim yeni çağıran `StartTheQuiz()` yöntemi. İkinci deyim ayarlar **etkin** özelliği **startButton** denetimini **False** böylece sınavı alanın sınav sırasında düğmeyi seçemezsiniz.  
  
8.  Kodunuzu kaydedin, çalıştırın ve ardından **Başlat** düğmesi.  
  
     Rasgele bir toplama problemi, aşağıdaki çizimde gösterildiği gibi görünür.  
  
     ![Rasgele bir toplama problemi](../ide/media/express-additionproblem.png "Express_AdditionProblem")  
Rasgele bir toplama problemi  
  
     Öğreticinin bir sonraki adımda toplamı ekleyeceksiniz.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [3. adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [1. adım: bir proje oluşturup bilgisayarınızı forma etiketler ekleyin](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).



