---
title: '3. adım: her etikete rasgele simge atama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ce8047cbdf6d487a1b4ff00ae99c617a9548fca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298785"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3. Adım: Her Etikete Rasgele Simge Atama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için simgeler rasgele formunuzdaki etiket denetimlerine kullanarak Ata bir `AssignIconsToSquares()` yöntemi.  
  
### <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için  
  
1.  Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük yoktur: `foreach` Visual C# ve `For Each` Visual Basic'te. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]  
  
2.  Ekleme `AssignIconsToSquares()` önceki adımda gösterildiği yöntemi. Eklediğiniz kodun hemen altına koyabilirsiniz [2. adım: rasgele nesne ve a List of Icons ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
     Daha önce bahsedildiği gibi var. yeni bir öğe, `AssignIconsToSquares()` yöntemi: bir `foreach` döngü Visual C# ve `For Each` Visual Basic'te. Kullanabileceğiniz bir `For Each` döngü aynı eylemi birden çok kez yapmak istediğiniz zaman. Bu durumda, aşağıdaki kod ile açıklandığı gibi, TableLayoutPanel denetiminizdeki her öğe için aynı deyimleri yürütmek istiyorsunuz. İlk satırı adında bir değişken oluşturur `control` , her denetimi birer birer denetim üzerinde yürütülen Döngüdeki deyimler olduğunu depolar.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]  
  
    > [!NOTE]
    >  "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.  
  
     `AssignIconsToSquares()` Yöntemi TableLayoutPanel içindeki her etiket denetiminde yinelenir ve bunların her biri için aynı deyimleri yürütür. Bu deyimler eklediğiniz listeden rasgele bir simge çeker [2. adım: rasgele nesne ve a List of Icons ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Listeye her simgeden iki tane eklemenizin nedeni budur; böylece rasgele etiket denetimlerine atanmış bir çift simge olur.)  
  
     Daha yakından içinde çalışan kodu `foreach` veya `For Each` döngü. Bu kod burada tekrar üretilmektedir.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]  
  
     İlk satırı dönüştürür `control` değişken adında bir etikete `iconLabel`. Sonraki satır bir `if` dönüştürme emin olmak için denetler deyimidir. Dönüştürme işe, deyimleri `if` deyimi çalıştırın. (Önceki öğreticilerden hatırlayabileceğiniz `if` deyimi belirttiğiniz her tür koşulu değerlendirmek için kullanılır.) İlk satırı `if` deyimi adlı bir değişken oluşturur `randomNumber` simgeler listesindeki öğelerden birine karşılık gelen rasgele bir sayı içerir. Bunu yapmak için kullandığı `Next` yöntemi `Random` daha önce oluşturduğunuz bir nesne. `Next` Yöntemi rasgele sayıyı döndürür. Bu satır ayrıca kullanan `Count` özelliği `icons` rasgele sayının seçileceği aralığı belirlemek için liste. Sonraki satır simge, liste öğelerine atar `Text` etiketin özelliği. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, son satırında `if` deyimi forma eklenmiş olan simgeyi listeden kaldırır.  
  
     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Bkz: [yapmak ı: adım Visual Studio hata ayıklayıcı ile ne nasıl?](http://msdn.microsoft.com/vstudio/ee672313.aspx) veya [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md) daha fazla bilgi için.  
  
3.  Oyun tahtasını simgelerle doldurmak için çağrılacak ihtiyacınız `AssignIconsToSquares()` program başlar başlamaz yöntemi. Visual C# kullanıyorsanız, yalnızca çağrının altına bir deyim ekleyin `InitializeComponent()` yönteminde `Form1` *Oluşturucusu*, böylece formunuz gösterilmeden önce kendini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Bkz: [oluşturucular (C# programlama Kılavuzu)](http://msdn.microsoft.com/library/ace5hbzh.aspx) veya [oluşturucuları ve yıkıcıları kullanma](http://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) daha fazla bilgi için Visual Basic'te.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]  
  
     Visual Basic için ekleme `AssignIconsToSquares()` yöntem çağrısını `Form1_Load` yöntemi böylece kod aşağıdaki gibi görünür.  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  
  
4.  Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.  
  
5.  Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin.  
  
     ![Eşleştirme oyunu rasgele simgeleri içeren](../ide/media/express-tut4step3.png "Express_Tut4Step3")  
Rasgele simgeleri içeren eşleştirme oyunu  
  
     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları oyuncudan gizlemek için her bir etiketin ayarlayabilirsiniz `Forecolor` aynı renge özelliğine kendi `BackColor` özelliği.  
  
    > [!TIP]
    >  Etiket gibi denetimleri gizlemenin bir diğer yolu ayarlamaktır kendi **görünür** özelliğini `False`.  
  
6.  Simgeleri gizlemek için kod içinde derleme dışı bırakılan satırı açıklama işaretlerini kaldırın ve programı durdurmak `For Each` döngü.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]  
  
7.  Menü çubuğunda, **Tümünü Kaydet** programınızı kaydetmek için düğmesini ve ardından çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [4. adım: her etikete bir tıklayın olay işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [2. adım: rasgele nesne ve a List of Icons ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).



