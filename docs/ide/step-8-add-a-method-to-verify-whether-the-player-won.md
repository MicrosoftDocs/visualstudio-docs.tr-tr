---
title: '8. adım: oyuncunun kazandığını doğrulamak için yöntem ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34b4e8085c3ff3de8037827769331eac83325ff8
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748016"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8. adım: oyuncunun kazandığını doğrulamak için yöntem ekleme
Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Player WINS, eklemeniz gerekir böylece oyun bitmelidir bir `CheckForWinner()` oyuncunun kazandığını doğrulamak için yöntem.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1.  Ekleme bir `CheckForWinner()` , kodunuzu altına yöntemi aşağıda `timer1_Tick()` aşağıdaki kodda gösterildiği gibi olay işleyicisi.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     Başka bir yöntem kullanır `foreach` döngü Visual C# veya `For Each` her etiket gitmesi Visual Basic'te döngü <xref:System.Windows.Forms.TableLayoutPanel>. Eşitlik işleci kullanır (`==` Visual C# ve `=` Visual Basic'te) arka plan eşleşip eşleşmediğini doğrulamak için her etiketin simgenin rengi denetlemek için. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda, program kullanan bir `return` deyimi yöntemi kalanını atlayın. Döngü tüm etiketleri çalıştırmadan alır, `return` tüm form üzerindeki simgelerin eşleştirildiklerinden anlamına gelen deyimi. Program bir MessageBox kazanan üzerinde player kutlayın gösterir ve formun çağırır `Close()` oyun sonuna yöntemi.

2.  Ardından, etiketin sahip <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağırma yeni `CheckForWinner()` yöntemi. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. Satır için ikinci seçilen simgenin rengi ayarladığınız arayın ve ardından çağıran `CheckForWinner()` yöntemi aşağıdaki kodda gösterildiği gibi bundan sonra doğru.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3.  Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandınız, programın bir eklenen kutlama görüntüler **MessageBox** (gösterildiği aşağıdaki resimde) ve ardından kutusunu kapatır.

     ![MessageBox ile eşleme oyunu](../ide/media/express_tut4step8.png)
**eşleme oyunu** ile **MessageBox**

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [adım 9: diğer özellikleri deneme](../ide/step-9-try-other-features.md).

-   Eğitmen önceki adıma dönmek için bkz: [adım 7: çiftleri görünür tut getirin](../ide/step-7-keep-pairs-visible.md).
