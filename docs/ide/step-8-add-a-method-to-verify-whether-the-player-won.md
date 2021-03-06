---
title: '8. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme'
description: Oyuncunun kazandığını tespit etmek için nasıl Yöntem ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 931e39a4f3cf87fe2d147d90f2111c9a9db3faeb
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297008"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme
Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyuncu, oynatıcı WINS 'e göre sona erdirmek `CheckForWinner()` için oyuncunun kazanıp kazanılmadığını doğrulamak üzere bir yöntem eklemeniz gerekir.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1. `CheckForWinner()`Aşağıdaki kodda gösterildiği gibi, kodunuzun altına, olay işleyicisinin altına bir yöntem ekleyin `timer1_Tick()` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)     

     Yöntemi `foreach` `For Each` , içindeki her bir etikette gezinmek Için C# veya Visual Basic içindeki döngüsünde başka bir döngü kullanır <xref:System.Windows.Forms.TableLayoutPanel> . `==` `=` Her etiketin simge rengini denetlemek için, arka planla eşleşip eşleşmediğini doğrulamak üzere eşitlik Işlecini (C# ' ta ve Visual Basic) kullanır. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda program, `return` yöntemin geri kalanını atlamak için bir ifade kullanır. Döngü, ifadeyi yürütmeden tüm etiketleri alırsa `return` , bu, formdaki tüm simgelerin eşleştirildiği anlamına gelir. Program, oyunu kazanmakta olan bir MessageBox gösterir ve ardından `Close()` oyunun sona erdirmek için formun yöntemini çağırır.

2. Sonra, etiketin <xref:System.Windows.Forms.Control.Click> olay işleyicisinin yeni yöntemi çağırmasını sağlayabilirsiniz `CheckForWinner()` . Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. İkinci seçili simgenin rengini ayarladığınız çizgiyi bulun ve ardından `CheckForWinner()` aşağıdaki kodda gösterildiği gibi yöntemi hemen sonra çağırın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program bir kutlama **MessageBox** (aşağıdaki ekran görüntüsünde gösterildiği gibi) görüntüler ve sonra kutuyu kapatır.

     ![MessageBox ile eşleştirme oyunu](../ide/media/express_tut4step8.png)<br/>
***Eşleşen oyun** _ _With * ***MessageBox***

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 9. **[Adım: diğer özellikleri deneyin](../ide/step-9-try-other-features.md)**.

- Önceki öğretici adımına dönmek için bkz. 7. [Adım: çiftleri görünür tut](../ide/step-7-keep-pairs-visible.md).
