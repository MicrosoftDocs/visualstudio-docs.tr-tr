---
title: '4. adım: CheckTheAnswer() yöntemi ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ff11913b854ede1c20c0670b89c4ea2f50fd326e
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32064525"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4. adım: CheckTheAnswer() yöntemi ekleme
Bu öğreticinin dördüncü bölümünde bir yöntem yazacaksınız `CheckTheAnswer()`, matematik sorunlara yanıtlar doğru olup olmadığını belirler. Bu konuda bir öğretici serisi kodlama temel kavramları hakkında bir parçasıdır. Öğretici genel bakış için bkz: [Eğitmen 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Visual Basic'te aşağıdaki varsa, kullanacağınız `Function` anahtar sözcüğü her zamanki yerine `Sub` anahtar sözcüğü çünkü bu yöntemi bir değer döndürür. Gerçekten bu basit bir işlemdir: bir alt bir değer döndürmüyor ancak bir işlev desteklemez.  

## <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtlar doğru olup olmadığını doğrulamak için  

1.  Ekleme `CheckTheAnswer()` yöntemi.  
  
     Bu yöntem çağrıldığında, addend1 ve addend2 değerlerini ekler ve toplam değeri sonucu karşılaştırır <xref:System.Windows.Forms.NumericUpDown> denetim. Değerlerin eşit olup olmadığını yöntemi değerini döndürür. `true`. Aksi takdirde, yöntemi bir değeri döndürür `false`. Kodunuzu aşağıdaki gibi görünmelidir.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Ardından, süreölçerini 's yöntemindeki kod güncelleştirerek yanıt kontrol edeceğiz <xref:System.Windows.Forms.Timer.Tick> yeni çağrı için olay işleyicisini `CheckTheAnswer()` yöntemi.  
  
2.  Aşağıdaki kodu ekleyin `if else` deyimi.  

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  

     Yanıt doğruysa, `CheckTheAnswer()` döndürür `true`. Olay işleyicisi Zamanlayıcı durdurur, eklenen kutlama iletisi gösterir ve sonra yapar **Başlat** yeniden kullanılabilir düğmesine tıklayın. Aksi takdirde, test devam eder.  

3.  Programınızı kaydetmek, çalıştırmak, bir test başlatmak ve toplama problemi doğru bir yanıt sağlar.  

    > [!NOTE]
    >  Yanıtınız girdiğinizde, varsayılan değer yanıtınızı girmek için başlatın ya da sıfır el ile silmeniz gerekir önce ya da seçmeniz gerekir. Bu davranış daha sonra Bu öğreticide düzeltmeniz.  

     Doğru yanıt sağladığınızda, bir ileti kutusu açılır ve **Başlat** düğmesi kullanılabilir olur ve Zamanlayıcı durdurur.  

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Öğretici bir sonraki adıma dönmek için bkz: [5. adım: NumericUpDown denetimleri için olay işleyicileri ekleme girin](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Eğitmen önceki adıma dönmek için bkz: [3. adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).
