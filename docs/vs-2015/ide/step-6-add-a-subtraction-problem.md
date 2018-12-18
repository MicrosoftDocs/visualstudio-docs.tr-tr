---
title: '6. adım: çıkarma problemi ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 793204bf4a08d09d7ce6e48e37254dd311ac6a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229248"
---
# <a name="step-6-add-a-subtraction-problem"></a>6. Adım: Çıkarma Problemi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu Eğitimin altıncı kısmında bir çıkarma sorusu ekleyin ve aşağıdaki görevleri nasıl gerçekleştireceğinizi öğrenin:  
  
-   Çıkarma değerlerini Store.  
  
-   Sorun için rastgele sayılar üretin (ve yanıtın 0 ile 100 arasında olduğundan emin olun).  
  
-   Yanıtları denetler ve böylece çok yeni bir çıkarma sorusu denetler yöntemi güncelleştirin.  
  
-   Zamanlayıcınızın Tick olayı işleyicisini, Süre dolduğunda olay işleyicisi doğru yanıtı doldurur. böylece güncelleştirin.  
  
### <a name="to-add-a-subtraction-problem"></a>Çıkartma problemi ekleme  
  
1.  Formunuza tamsayı değişkenleri ek sorunun ve Zamanlayıcının arasında çıkartma sorusu için iki tamsayı değişkeni ekleyin. Kod aşağıdaki gibi görünmelidir.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]  
  
     Yeni tamsayı değişkenlerinin adları —**Eksilen** ve **çıkarılan**— programlama terimleri değildir. Bunlar, çıkarılmakta olan sayı (çıkarılan) ile içinden çıkartıldığı sayı (Eksilen) çıkartılır için aritmetikte kullanılan geleneksel adlardır hedeflenmiştir. Fark, Eksilen eksi çıkarılandır vardır. Programınızı değişkenler, denetimler, bileşenler veya yöntemleri için belirli adlar verilmesini gerektirmediği diğer adlar kullanabilirsiniz. Adları basamak ile başlamıyor gibi kurallara uymanız gerekir, ancak genellikle x1, x2 x3 ve x4 gibi adlar kullanabilirsiniz. Ancak genel adlar kodun zor okunmasına ve sorunların neredeyse çözülemez hale. Değişken adları benzersiz ve yararlı tutmak için çarpma geleneksel adlarını kullanmanız gerekir (çarpan × çarpan ürün =) ve bölme (bölü; bölen bölünen sayının =) Bu öğreticinin sonraki bölümlerinde.  
  
     Ardından, değiştireceksiniz `StartTheQuiz()` yöntemini çıkarma sorusu için rastgele değerler sağlayacak.  
  
2.  Aşağıdaki kodu "çıkartma sorusundaki dolgu" yorumundan sonra ekleyin.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]  
  
     Çıkartma sorusu için negatif yanıtları önlemek için bu kodu kullanan `Next()` yöntemi `Random` biraz farklı ek sorunun nasıl yaptığını sınıfı. Size zaman `Next()` yöntemine iki değer değerinden büyük veya eşit ilk değer ve daha az rastgele bir sayı seçer ve ikinci değerden. Aşağıdaki kod, 1 ile 100 arasında rastgele bir sayı seçer ve bunu Eksilen değişkeninde depolar.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]  
  
     Çağırabilirsiniz `Next()` yöntemi `Random` , birden çok yolla bu öğreticinin önceki kısımlarındaki "randomizer" olarak adlandırılan sınıfı. Birden fazla şekilde çağırabileceğiniz yöntemler için aşırı yüklü olarak başvurulur ve bunlarda gezinmek için IntelliSense'i kullanabilirsiniz. Konum yeniden için IntelliSense penceresini araç ipucuna `Next()` yöntemi.  
  
     ![IntelliSense pencere araç ipucu](../ide/media/express-overloads.png "Express_Overloads")  
IntelliSense pencere araç ipucu  
  
     Araç İpucu gösterilmektedir **(+ 2 çağırabileceğiniz**, çağırabileceğiniz anlamına gelen `Next()` iki yolla yöntemi. Böylece birbirinden biraz farklı çalıştığını farklı sayılarda ya da türlerde bağımsız değişkenleri, aşırı yüklemeleri içerir. Örneğin, bunun aşırı yüklerinden biri bir tam sayı ve bir dize alabilir ancak bir yöntem tek bir tamsayı bağımsız değişken alabilir. Ne, bunu yapmak için istediğinize bağlı olarak doğru aşırı yüklemesi'ı seçin. Koda eklediğinizde `StartTheQuiz()` yöntemi, daha fazla bilgi IntelliSense penceresinde görünür, girer girmez `randomizer.Next(`. Aşağıdaki çizimde gösterildiği gibi aşırı yükler arasında gezinmek için Yukarı Ok ve aşağı ok tuşlarını seçin.  
  
     ![Sonraki için aşırı yükleme&#40; &#41; IntelliSense yönteminde](../ide/media/express-nextoverload.png "Express_NextOverload")  
Intellisense'da Next() yöntemi için aşırı yükleme  
  
     Bu durumda, minimum ve maksimum değerleri belirttiğinden, son aşırı yükü seçmek istersiniz.  
  
3.  Değiştirme `CheckTheAnswer()` yöntemini doğru çıkarma yanıtını kontrol edecek şekilde.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]  
  
     Visual C# içinde `&&` olduğu `logical and` işleci. Visual Basic'te, eşdeğer işlecidir `AndAlso`. Bu işleçler "addend1 ve addend2 Toplamı toplam NumericUpDown değeri eşitse göstermeye yardımcı olur ve Eksilen eksi çıkarılan fark NumericUpDown'ının değerine eşitse." `CheckTheAnswer()` Yöntemi döndürür `true` yalnızca toplama ve çıkarma yanıtlar doğru hem de olması gerekir.  
  
4.  Zaman aşımı halinde doğru yanıtı doldurur. böylece, Zamanlayıcının Tick olay işleyicisinin son kısmını aşağıdaki kodla değiştirin.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]  
  
5.  Kaydet ve kodunuzu çalıştırın.  
  
     Programınız aşağıdaki çizimde gösterildiği gibi bir çıkarma sorusu içerir.  
  
     ![Çıkarma Sorulu matematik sınavı](../ide/media/express-addsubtract.png "Express_AddSubtract")  
Çıkarma Sorulu matematik sınavı  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [7. adım: ekleme çarpma ve bölme problemleri](../ide/step-7-add-multiplication-and-division-problems.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [5. adım: ekleme girmek için olay işleyicileri NumericUpDown denetimleri](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).



