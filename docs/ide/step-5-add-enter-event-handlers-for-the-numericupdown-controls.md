---
title: '5. adım: NumericUpDown denetimleri için Enter olay işleyicileri ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e05d6cc201819d37e77587529ffd79a740003a10
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747925"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>5. adım: NumericUpDown denetimleri için Enter olay işleyicileri ekleme
Bu öğreticinin beşinci bölümünde, ekleyeceksiniz <xref:System.Windows.Forms.Control.Enter> girmek için olay işleyicileri için test sorunları bir biraz daha kolay yanıtlar. Bu kodu seçin ve her geçerli değeri temizleyin <xref:System.Windows.Forms.NumericUpDown> test alanın seçtiği ve farklı bir değer girmesini başlatır hemen denetim.

> [!NOTE]
>  Bu konuda bir öğretici serisi kodlama temel kavramları hakkında bir parçasıdır. Öğretici genel bakış için bkz: [Eğitmen 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Varsayılan davranış doğrulamak için

1.  Programınızı çalıştırma ve test başlatın.

     İçinde **NumericUpDown** Denetim toplama problemi için imleci yanına yanıp sönen **0** (sıfır).

2.  Girin **3**ve denetimini gösterir Not **30**.

3.  Girin **5**ve unutmayın **350** görünür ancak değişikliklerini **100** bir saniye sonra.

     Bu sorunu gidermek önce neler hakkında düşünün. Neden göz önünde bulundurun **0** girdiğiniz zaman kayboluyor kaydetmedi **3** ve neden **350** değiştirildi **100** ancak bunun hemen.

     Bu davranış garip görünebilir ancak kodu mantığını verilen mantıklıdır. Seçtiğinizde **Başlat** düğmesi, kendi **etkin** özelliği ayarlanmış **yanlış**, düğmesi devre dışı görünüyorsa ve kullanılamıyor. Programınızı geçerli seçim (odak), bir toplama problemi NumericUpDown denetimi sonraki en düşük TabIndex değeri içeriyor denetimine değiştirir. Kullandığınızda **sekmesini** anahtar NumericUpDown denetimi gitmek için imleç otomatik olarak girdiğiniz numaraları sol tarafındaki ve sağ tarafında görünür neden olan denetim başlangıcında konumlandırıldı. Bir sayı belirttiğinizde, değerinden daha yüksek olan **MaximumValue** girdiğiniz numarayı 100 olarak ayarlanmışsa özelliği, bu özelliğin değeri ile değiştirilir.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>NumericUpDown denetimi için Enter olay işleyicisi ekleme

1.  İlk seçin **NumericUpDown** ("sum" adlı) denetim form üzerinde ve ardından **özellikleri** iletişim kutusunda, seçin **olayları** araç çubuğunda simge.

     **Olayları** sekmesinde **özellikleri** iletişim kutusu tüm form üzerinde seçtiğiniz öğe (işlemek için) yanıtlayabilir olayları görüntüler. NumericUpDown denetimi seçtiğinden tüm listelenen olaylar için ilgilidir.

2.  Seçin **Enter** olayı girin `answer_Enter`ve ardından **Enter** anahtarı.

     ![Özellikleri iletişim kutusu](../ide/media/express_answerenter.png)
**özellikleri** iletişim kutusu

     Yeni bir Enter olay işleyicisi için NumericUpDown denetimi toplam eklediğiniz ve işleyici adlı **answer_Enter**.

3.  Yöntem için **answer_Enter** olay işleyicisi, aşağıdaki kodu ekleyin.

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     Bu kod karmaşık görünebilir, ancak şimdi adım adım bakarsanız anlayabilirsiniz. İlk olarak, yöntem üstünde arayın: `object sender` C# veya `sender As System.Object` Visual Basic'te. Bu parametre gönderen olarak bilinen, olay tetikleme, nesneye başvuruda bulunur. Bu durumda, gönderen NumericUpDown denetimi nesnesidir. Bu nedenle, yönteminin ilk satırında gönderen yalnızca herhangi bir genel nesnesi, ancak özellikle bir NumericUpDown denetimi olmadığını belirtin. (Her NumericUpDown denetimi bir nesnedir, ancak her nesne NumericUpDown denetimi.) NumericUpDown denetimi adlı **answerBox** Bu yöntemde, yalnızca toplam tüm form NumericUpDown denetimleri için kullanılacağından NumericUpDown denetim. Bu yöntem answerBox değişkeninde bildirmek için kapsamı bu yöntem yalnızca için geçerlidir. Diğer bir deyişle, değişken, yalnızca bu yöntemi içinde kullanılabilir.

     Sonraki satıra answerBox başarıyla dönüştürüldü doğrular (bir nesneden bir NumericUpDown denetimi cast). Dönüştürme başarısız olduysa, değişkenin değerini olurdu `null` (C#) veya `Nothing` (Visual Basic). Üçüncü satır, NumericUpDown denetimi görünür yanıt uzunluğunu alır ve bu uzunluğuna göre denetimindeki geçerli değeri Dördüncü satır seçer. Şimdi, test alanın denetimi seçtiğinde, Visual Studio seçilecek geçerli yanıt neden olur. Bu olay tetikler. Farklı bir yanıt girmek test alanın başlar başlamaz, önceki yanıt temizlenir ve yeni yanıtı ile değiştirilir.

4.  İçinde **Windows Form Tasarımcısı**, fark seçin **NumericUpDown** denetim.

5.  İçinde **olayları** sayfasında **özellikleri** iletişim kutusu, aşağı kaydırın **Enter** olay, satırın sonundaki aşağı açılan okunu seçin ve ardından `answer_Enter`eklediğiniz olay işleyicisi.

6.  Ürün ve sayının NumericUpDown denetimleri için önceki adımı yineleyin.

7.  Programınızı kaydetmek ve ardından çalıştırın.

     Seçeneğini belirlediğinizde bir **NumericUpDown** denetimi, mevcut değeri otomatik olarak seçilir ve farklı bir değer girmesini başlattığınızda sonra temizlenir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [6. adım: çıkarma problemi ekleme](../ide/step-6-add-a-subtraction-problem.md).

-   Eğitmen önceki adıma dönmek için bkz: [4. adım: CheckTheAnswer() yöntemi ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md).
