---
title: '8. adım: oyuncunun kazandığını doğrulamak için yöntem ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 278d8d71378c0d14047fe8e012fed21951101548
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306640"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8. Adım: Oyuncunun Kazandığını Doğrulamak için Yöntem Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyuncu eklemeniz gerekir. Bu nedenle oyun bitmeli; bu bir `CheckForWinner()` oyuncunun kazanıp kazanmadığını doğrulamak için yöntem.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için  
  
1.  Ekleme bir `CheckForWinner()` kodunuz alt kısmına yöntemi aşağıda `timer1_Tick()` olay işleyicisi, aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]  
  
     Başka bir yöntem kullanır `foreach` döngü Visual C# veya `For Each` TableLayoutPanel içindeki her bir etiketi Git, Visual Basic'te döngü. Eşitlik işlecini kullanır (`==` Visual C# ve `=` Visual Basic'te) arka plan ile eşleşip eşlemediğini doğrulamak için her bir etiketin simge rengini denetlemek için. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda, programın kullandığı bir `return` deyimi yöntemin geri kalanını atlayın. Döngü tüm etiketleri çalıştırmadan alır, `return` anlamına gelen form üzerindeki simgelerin tümü eşleştirilmiş olan ifade. Program oyuncunun galibiyetini kutlayan bir MessageBox gösterir ve ardından formun çağırır `Close()` da oyunu sonlandırmak için yöntemi.  
  
2.  Ardından, etiketin tıklama sahip yeni bir olay işleyicisi çağırma `CheckForWinner()` yöntemi. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. Seçilen ikinci simgenin rengini ayarladığınız satırı arayın ve sonra çağrı `CheckForWinner()` aşağıdaki kodda gösterildiği gibi hemen yöntemi.  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]  
  
3.  Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program kutlama amaçlı bir MessageBox görüntüler (aşağıdaki resimde gösterildiği gibi) ve sonra da kutuyu kapatır.  
  
     ![MessageBox ile eşleştirme oyunu](../ide/media/express-tut4step8.png "Express_Tut4Step8")  
MessageBox ile eşleştirme oyunu  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [9. adım: diğer özellikleri deneyin](../ide/step-9-try-other-features.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [adım 7: Keep Pairs Visible](../ide/step-7-keep-pairs-visible.md).



