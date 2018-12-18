---
title: '7. adım: çiftleri görünür kılma'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e27a5378aacec6af4ca07f13242f24bd665a762e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747860"
---
# <a name="step-7-keep-pairs-visible"></a>7. adım: çiftleri görünür kılma
Oyuncu yalnızca eşleşmeyen simge çiftlerini seçtiği sürece oyun düzgün çalışır. Ancak oyuncu eşleşen bir çift seçtiğinde ne olması gerektiğini bir düşünün. Süreölçer kapatarak simgeleri yerine yapma kayboluyor (kullanarak <xref:System.Windows.Forms.Timer.Start> yöntemi), böylece, artık kullanarak etiketleri izleyen oyun kendisini sıfırlamalıdır `firstClicked` ve `secondClicked` başvuru değişkenleri sıfırlamadan Seçilen iki etiket renklerini.

## <a name="to-keep-pairs-visible"></a>Çiftleri görünür durumda tutmak için

1.  Aşağıdakileri ekleyin `if` ifadesine `label_Click()` yalnızca Zamanlayıcı başladığınız deyimi yukarıdaki kodu sona olay işleyicisi yöntemi. Kodu programa eklerken yakından inceleyin. Kodun nasıl çalıştığını bir düşünün.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     İlk satırı `if` eklediğiniz deyimi player seçer ilk etiketi simgesinde İkinci etiketin simgesinde aynı olup denetler. Simgeler aynıysa, C# veya üç deyimleri içinde süslü ayraçlar arasında üç deyimleri programı yürütür `if` Visual Basic'de deyimini. İlk iki deyimleri sıfırlama `firstClicked` ve `secondClicked` böylece bunlar artık herhangi bir etiket izlemek değişkenleri başvuru. (Bu Zamanlayıcı'nın iki ifadeden tanıyabilir <xref:System.Windows.Forms.Timer.Tick> olay işleyicisi.) Üçüncü deyimi bir `return` program yürütme olmadan yöntemi deyimlerinde kalanını atlayın söyler deyimi.

     Visual C# ile programlama, bazı kodları kullandığını tek bir eşittir işareti fark etmiş (`=`), diğer deyimler iki eşittir işareti kullanırken (`==`). Neden göz önünde bulundurun `=` bazı yerlerde kullanılır ancak `==` farklı konumlarda kullanılır.

     Bu örnek, aradaki farkı gösteren güzel bir örnektir. Parantez içine arasında yer alan kodunu dikkatli bir göz atalım `if` deyimi.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     İlk ifade sonra kod bloğunu, en yakın Ara `if` deyimi.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Bu deyimlerden birincisi iki simgenin aynı olup olmadığını denetler. Visual C# programı kullanır, iki değer karşılaştırıldığında çünkü `==` eşitlik işleci. İkinci ifade gerçekten değeri değişir (adlı *atama*), ayar `firstClicked` başvuru değişkeni eşit `null` sıfırlama. İşte bu nedenle kullandığı `=` atama işleci yerine. Visual C# kullanan `=` değerlerini ayarlamak için ve `==` bunları karşılaştırmak için. Visual Basic kullanan `=` değişkeni ataması ve karşılaştırma için.

2.  Programı kaydedip çalıştırın ve sonra formdaki simgeleri seçmeye başlayın. Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetiklenir ve iki simge de kaybolur. Eşleşen bir çift seçerseniz yeni `if` deyimini yürütür ve return deyiminin simgeler aşağıdaki resimde gösterildiği gibi görünür, kalır, böylece süreölçer başlatır kod atlamak yönteminin neden olur.

     ![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)
**eşleme oyunu** görünür simgesi çiftleri ile

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [adım 8: oyuncunun kazandığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

-   Eğitmen önceki adıma dönmek için bkz: [6. adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).
