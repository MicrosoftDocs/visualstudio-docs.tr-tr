---
title: '3. adım: geri sayım Zamanlayıcısı ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bbbc5e7de56e3ab03976b1933895035913bb7d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228156"
---
# <a name="step-3-add-a-countdown-timer"></a>3. Adım: Geri Sayım Zamanlayıcısı Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu Eğitimin üçüncü kısmında sınava giren bitirmek kalan saniye sayısını izlemek için bir geri sayım Zamanlayıcısı ekleyeceksiniz.  
  
> [!NOTE]
>  Bu konu, temel kodlama kavramları hakkındaki bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: bir zaman aşımına matematik sınavı oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-add-a-countdown-timer"></a>Bir geri sayım Zamanlayıcısı ekleme  
  
1.  Adlı bir tam sayı değişkeni ekleyin **timeLeft**, önceki yordamda yaptığınız gibi. Kodunuzu aşağıdaki gibi görünmelidir.  
  
     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]  
  
     Şimdi, aslında bir olay başlatır, belirttiğiniz süre miktarını sonra bir Zamanlayıcı gibi saniye sayan bir yöntem gerekir.  
  
2.  Tasarım penceresinde Taşı bir `Timer` denetimi **bileşenleri** formunuza araç kutusu kategorisi.  
  
     Denetim tasarım penceresinin altındaki gri alanda görüntülenir.  
  
3.  Form üzerinde seçin **Süreölçer1** yalnızca eklenen ve Ayarla simgesi kendi **aralığı** özelliğini **1000**.  
  
     Aralık değeri milisaniye olduğundan, bir 1000 değeri Tick olayının her saniye tetiklenmesine neden olur.  
  
4.  Formda, Zamanlayıcı denetimini çift tıklayın veya bunu seçin ve ardından Enter tuşuna basın.  
  
     Kod Düzenleyicisi görünür ve yeni eklediğiniz Tick olay işleyicisinin yöntemini görüntüler.  
  
5.  Aşağıdaki deyimleri yeni olay işleyici yöntemine ekleyin.  
  
     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]  
  
     Zaman belirleyerek aşımına uğrayıp, eklediğiniz üzerinde bağlı olarak, Zamanlayıcı saniyede denetler olmadığını **timeLeft** tamsayı değişkeninin 0'dan büyük. İse, zaman kalıyor. Zamanlayıcı ilk Timeleft'ten 1 çıkarır ve ardından güncelleştirmeleri **metin** özelliği `timeLabel` sınava kaç saniye kaldığını göstermek için denetim.  
  
     Hiçbir zaman kalırsa, Zamanlayıcıyı durdurur ve metnini değiştirir `timeLabel` , denetiminin **saatin yukarı!** Bir mesaj kutusu sınavın ve yanıt açıklanır sunar; bu durumda addend1 ve addend2 ekleyerek tarafından. **Etkin** özelliği `startButton` denetim ayarı `true` sınavı alanın başka bir test başlayabilmesi.  
  
     Az önce eklediğiniz bir `if else` kararlar programların nasıl size deyimi. Bir `if else` deyimi aşağıdaki gibi görünür.  
  
    > [!NOTE]
    >  Aşağıdaki örnek yalnızca gösterim amaçlıdır – projenize eklemeyin.  
  
    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  
  
    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  
  
     Yakından bakın eklediğiniz deyime `else` ek soruya yanıtı göstermek için blok.  
  
     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]  
  
     Deyim `addend1 + addend2` iki değişkendeki değerleri toplar. İlk Kısım (`sum.Value`) kullanan **değer** özelliğini `NumericUpDown` doğru yanıtı görüntülemek için denetim. Aynı özellik daha sonra sınavın yanıtlarını denetlemek için kullanın.  
  
     Sınava girenlerin sayı girebilir, daha kolay kullanarak bir `NumericUpDown` matematik sorularının yanıtları için kullandığınız neden olan denetim. Olası yanıtların tümü 0 ile 100 arası tamsayılardır. Varsayılan değerlerini bırakarak tarafından **Minimum**, **maksimum**, ve **OndalıkBasamaklar** özellikleri, emin sınava girenlerin ondalık girin olamaz, negatif sayılar, veya çok yüksek sayılar. (Sınava girenlerin 3.141 girmek izin vermek istediyseniz ama 3.1415, ayarladığınız, **OndalıkBasamaklar** özelliğini 3.)  
  
6.  Sonuna üç satır ekleyin `StartTheQuiz()` yöntemi, kod aşağıdaki gibi görünür.  
  
     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]  
  
     Artık sınavınız başladığında, **timeLeft** değişkenini 30 ve **metin** özelliği `timeLabel` denetimi, 30 saniye olarak ayarlanır. Ardından `Start()` yöntemi `Timer` denetim geri sayımı başlatır. (Sınav yanıtı henüz denetlemedi; sonraki gelen.)  
  
7.  Programınızı kaydedin, çalıştırın ve ardından **Başlat** formundaki düğmesi.  
  
     Zamanlayıcı saymaya başlar. Zaman zaman sınav sona erer ve yanıtlar görünür. Aşağıdaki çizim sınavı göstermektedir.  
  
     ![Matematik sınavı devam ediyor](../ide/media/express-addcountdown.png "Express_AddCountdown")  
Matematik sınavı devam ediyor  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [4. adım: CheckTheAnswer() yöntemi ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [2. adım: rasgele bir toplama problemi oluşturma](../ide/step-2-create-a-random-addition-problem.md).



