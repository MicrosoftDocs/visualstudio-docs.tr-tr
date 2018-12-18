---
title: '5. adım: Ekleme NumericUpDown denetimleri için giriş olay işleyicileri girin | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a87704f7d836da2309e711f3379df01b01c807c2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294495"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>5. Adım: NumericUpDown Denetimleri için Giriş Olay İşleyicileri Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu Eğitimin beşinci kısmında girme sınav sorularının yanıtlarını biraz daha kolay hale getirmek için gir olayı işleyicilerini ekleyeceksiniz. Bu kodu seçin ve her NumericUpDown denetimindeki geçerli değeri sınava seçer ve farklı bir değer girmeye başladığında sürede temizleyin.  
  
> [!NOTE]
>  Bu konu, temel kodlama kavramları hakkındaki bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: bir zaman aşımına matematik sınavı oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-verify-the-default-behavior"></a>Varsayılan davranışı doğrulama  
  
1.  Programınızı çalıştırın ve sınavı başlatın.  
  
     Ek sorunun NumericUpDown denetiminde imleç yanında yanıp söner **0** (sıfır).  
  
2.  Girin `3`, Denetim gösterir Not **30**.  
  
3.  Girin `5`yani **350** görünür ancak değişikliklerini **100** bir saniye sonra.  
  
     Bu sorunu gidermeden önce neler olduğu hakkında düşünün. Neden göz önünde bulundurun **0** girdiğiniz kaybolmadığını `3` ve neden **350** değiştirilecek **100** ancak hemen.  
  
     Bu davranış garip görünebilir ancak kodun mantığı verilen mantıklıdır. Seçeneğini belirlediğinizde **Başlat** düğmesi, kendi **etkin** özelliği **False**, ve düğme soluklaşır ve kullanılamaz. Programınız geçerli seçimi (odağı), ek sorunun NumericUpDown denetimi sonraki en düşük TabIndex değerine sahip denetime değiştirir. Bir NumericUpDown denetimine gitmek için SEKME tuşunu kullandığınızda, imleç otomatik olarak girdiğiniz sayılar sol tarafındaki ve sağ tarafında görünür neden olan denetim başlangıcına yerleştirilir. Bir sayı belirtirseniz değerinden daha yüksek olan **MaximumValue** girdiğiniz sayı 100 olarak ayarlanmışsa özelliği, özelliğin değeriyle değiştirilir.  
  
### <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>NumericUpDown denetimi için bir Enter olay işleyicisi eklemek için  
  
1.  ("Sum" adında) ilk NumericUpDown denetimi form üzerinde ve ardından seçin **özellikleri** iletişim kutusunda **olayları** araç çubuğundaki simgeye.  
  
     **Olayları** sekmesinde **özellikleri** iletişim kutusu (işleyebileceğiniz) formda seçtiğiniz öğenin yanıt verin olayların tümünü görüntüler. NumericUpDown denetimini seçtiğinizden, tüm etkinlikler buna ilişkindir.  
  
2.  Seçin **Enter** olay girin `answer_Enter`ve ardından Enter tuşuna basın.  
  
     ![Özellikleri iletişim kutusu](../ide/media/express-answerenter.png "Express_AnswerEnter")  
Özellikleri iletişim kutusu  
  
     Toplama NumericUpDown denetimi için az önce bir Enter olay işleyicisini eklediniz ve işleyiciyi adlı **answer_Enter**.  
  
3.  Yöntem için **answer_Enter** olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial3Step5_6#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#11)]  
  
     Bu kod karmaşık görünebilir, ancak şimdi adım adım bakarsanız anlayabilirsiniz. Önce yöntemin üstüne bakın: `object sender` C# veya `sender As System.Object` Visual Basic'te. Bu parametre gönderen olarak bilinen, olayı tetiklenmekte olan nesneye başvurur. Bu durumda gönderen nesnesi NumericUpDown denetimidir. Bu nedenle, yöntemin ilk satırında gönderenin herhangi genel amaçlı nesne olmadığının olarak NumericUpDown denetimi değildir belirtin. (Her NumericUpDown denetimi bir nesnedir ancak her nesne bir NumericUpDown denetimidir.) NumericUpDown denetimine **answerBox** Bu yöntemde tüm formunda NumericUpDown denetimleri için kullanılacağından yalnızca toplama NumericUpDown denetimi. Bu yöntemde answerBox değişkeni bildirdiğinizden, kapsamı yalnızca bu yönteme uygulanır. Diğer bir deyişle, değişken, yalnızca bu yöntem içinde kullanılabilir.  
  
     Sonraki satır answerBox başarıyla dönüştürülüp dönüştürülmediğini doğrular (bir nesneden bir NumericUpDown denetimine atama). Dönüştürme başarısız oldu, değişkenin değerini gerekir `null` (C#) veya `Nothing` (Visual Basic). Üçüncü satır NumericUpDown denetiminde görünen yanıt uzunluğu alır ve geçerli değeri bu uzunluğa göre denetim dördüncü satırı seçer. Artık, sınava giren denetimi seçtiğinde, Visual Studio bu da geçerli yanıtın seçilmesine neden olur. Bu olay tetiklenir. Sınava giren farklı bir yanıt girmeye başladıktan hemen sonra önceki yanıt temizlenir ve yeni yanıt ile değiştirilir.  
  
4.  Windows Form Tasarımcısı'nda, farklılık NumericUpDown denetimini seçin.  
  
5.  İçinde **olayları** sayfasının **özellikleri** iletişim kutusu, aşağı kaydırın **Enter** olay satırın sonundaki aşağı açılır oku seçin ve ardından `answer_Enter`eklediğiniz olay işleyicisi.  
  
6.  Ürün ve bölüm NumericUpDown denetimleri için önceki adımı yineleyin.  
  
7.  Programınızı kaydedin ve ardından çalıştırın.  
  
     Bir NumericUpDown denetimini seçtiğinizde, mevcut değer otomatik olarak seçilir ve farklı bir değer girmeye başladığınızda seçilip silinir.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [6. adım: çıkarma problemi ekleme](../ide/step-6-add-a-subtraction-problem.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [4. adım: CheckTheAnswer() yöntemi ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md).



