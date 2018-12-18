---
title: '5. adım: etiket başvuruları ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ecea1c6a1baf27247b9b01d28e04b6da827a0e3
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747951"
---
# <a name="step-5-add-label-references"></a>5. adım: etiket başvuruları ekleme
Program player seçer hangi etiket denetimleri izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınızı artık hangi etiket denetimi ilk seçilir ve kullanarak, ikinci seçilir izlemek *başvuru değişkenleri*.

## <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1.  Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     Bu başvuru değişkenleri önceki nesneleri eklemek için kullandığınız deyimleri benzer (gibi <xref:System.Windows.Forms.Timer> nesneleri <xref:System.Collections.Generic.List%601> nesneleri ve <xref:System.Random> nesneler) formunuza. Ancak, bu deyimleri olduğundan formda görünmesi iki ek etiket denetimleri neden hiçbir `new` iki deyimleri birini kullanılan anahtar sözcük. Olmadan `new` anahtar sözcüğü, hiçbir nesnesi oluşturulur. İşte bu nedenle `firstClicked` ve `secondClicked` başvuru değişkenler adlandırılır: Bunlar yalnızca izlenmesi (ya da bakın) etiket nesneleri.

     Bir değişken bir nesne izleyen değil, özel bir ayrılmış değerine ayarlanır: `null` Visual C# ve `Nothing` Visual Basic'te. Bu nedenle, program başladığında, her ikisi de `firstClicked` ve `secondClicked` ayarlanır `null` veya `Nothing`, değişkenleri herhangi bir şey izleyen olduğunu olmayan anlamına gelir.

2.  Değiştirme, <xref:System.Windows.Forms.Control.Click> yeni kullanmak için olay işleyicisini `firstClicked` başvuru değişkeni. İşlemdeki son deyim kaldırmak `label_Click()` olay işleyicisi yöntemi (`clickedLabel.ForeColor = Color.Black;`) ve bunların yerine `if` izleyen deyimi. (Açıklama ve tüm eklediğinizden emin olun `if` deyimi.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3.  Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4.  Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program zaten player seçtiyseniz, bunu ilk etiketi izleyen olan `firstClicked` eşit değil `null` Visual C# veya `Nothing` Visual Basic'te. Olduğunda, `if` deyimi denetimleri `firstClicked` eşit olup olmadığını belirlemek için `null` veya `Nothing`, öyle olmadığı ve ifadeler yürütmez bulduğu `if` deyimi. Bu nedenle, aşağıdaki resimde gösterildiği gibi, yalnızca seçilen ilk simgenin rengi siyah olur ve diğer simgeler görünmez.

     ![Bir simge gösteren eşleşen oyun](../ide/media/express_tut4step5.png)
**eşleme oyunu** gösteren bir simge

     Bu durum ekleyerek öğreticinin sonraki adımda düzeltme bir **Zamanlayıcı** denetim.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [6. adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).

-   Eğitmen önceki adıma dönmek için bkz: [4. adım: her etikete Click olay işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).
