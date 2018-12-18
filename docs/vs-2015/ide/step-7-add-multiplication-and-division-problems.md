---
title: '7. adım: Çarpma ve bölme problemleri ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c0c2b069ebb75cbe4547528317544172b1d7ae2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195162"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>7. Adım: Çarpma ve Bölme Problemleri Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu Eğitimin yedinci kısmında çarpma ve bölme soruları ekleyeceksiniz ancak önce bu değişiklik hakkında düşünün. Değerleri depolamayı da içeren ilk adımı düşünün.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Çarpma ve bölme sorunları ekleme  
  
1.  Daha fazla dört tamsayı değişken formuna ekleyin.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2.  Daha önce yaptığınız gibi değiştirebilir `StartTheQuiz()` çarpma ve bölme sorularını için rastgele sayılarla dolduracak şekilde yöntemi.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3.  Değiştirme `CheckTheAnswer()` BT'nin ayrıca çarpma ve bölme sorularını kontrol edecek şekilde yöntemi.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Çarpı işareti (×) kolayca giremezsiniz ve bölme klavyeyi kullanarak oturum açma (bölü;), böylece Visual C# ve Visual Basic bir yıldız işareti (*) için çarpma ve bölme için bir eğik çizgi işareti (/) kabul edin.  
  
4.  Zaman aşımı halinde doğru yanıtı doldurur. böylece, Zamanlayıcının Tick olay işleyicisinin son kısmını değiştirin.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5.  Programınızı kaydedin ve çalıştırın.  
  
     Sınava girenlerin aşağıdaki çizimde gösterildiği gibi sınavı tamamlamak için dört sorusuna yanıt vermeniz gerekir.  
  
     ![Dört Sorulu matematik sınavı](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Dört Sorulu matematik sınavı  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [adım 8: testi özelleştirme](../ide/step-8-customize-the-quiz.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [6. adım: çıkarma problemi ekleme](../ide/step-6-add-a-subtraction-problem.md).



