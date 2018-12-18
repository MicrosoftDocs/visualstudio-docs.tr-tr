---
title: '3. adım: her etikete rasgele simge atama'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 593d778247e3c1e6b9a09358c82b5fd7139cfbb9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672918"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3. adım: her etikete rasgele simge atama
Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için simgeler rasgele formunuzdaki etiket denetimlerine kullanarak Ata bir `AssignIconsToSquares()` yöntemi.

## <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1.  Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük yoktur: `foreach` Visual C# ve `For Each` Visual Basic'te. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

2.  Ekleme `AssignIconsToSquares()` önceki adımda gösterildiği yöntemi. Eklediğiniz kodun hemen altına koyabilirsiniz [2. adım: rasgele nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Daha önce bahsedildiği gibi var. yeni bir öğe, `AssignIconsToSquares()` yöntemi: bir `foreach` döngü Visual C# ve `For Each` Visual Basic'te. Kullanabileceğiniz bir `For Each` döngü aynı eylemi birden çok kez yapmak istediğiniz zaman. Her etiket için aynı deyimleri yürütmek istiyorsunuz, bu durumda, <xref:System.Windows.Forms.TableLayoutPanel>, aşağıdaki kod ile açıklandığı gibi. İlk satırı adında bir değişken oluşturur `control` , her denetimi birer birer denetim üzerinde yürütülen Döngüdeki deyimler olduğunu depolar.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    >  "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     `AssignIconsToSquares()` Yöntemi TableLayoutPanel içindeki her etiket denetiminde yinelenir ve bunların her biri için aynı deyimleri yürütür. Bu deyimler eklediğiniz listeden rasgele bir simge çeker [2. adım: rasgele nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (İşte bu listeye dahil iki her simge, böylece için rastgele bir çift simge atanan olacaktır etiket denetimleri.)

     Daha yakından içinde çalışan kodu `foreach` veya `For Each` döngü. Bu kod burada tekrar üretilmektedir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     İlk satırı dönüştürür **denetimi** değişken adında bir etikete **iconLabel**. Sonraki satır bir `if` dönüştürme emin olmak için denetler deyimidir. Dönüştürme işe, deyimleri `if` deyimi çalıştırın. (Önceki öğreticilerden hatırlayabileceğiniz `if` deyimi belirttiğiniz her tür koşulu değerlendirmek için kullanılır.) İlk satırı `if` deyimi adlı bir değişken oluşturur **; randomnumber &** simgeler listesindeki öğelerden birine karşılık gelen rasgele bir sayı içerir. Bunu yapmak için kullandığı <xref:System.Random.Next> yöntemi <xref:System.Random> daha önce oluşturduğunuz bir nesne. `Next` Yöntemi rasgele sayıyı döndürür. Bu satır ayrıca kullanan <xref:System.Collections.Generic.List%601.Count> özelliği **simgeler** rasgele sayının seçileceği aralığı belirlemek için liste. Sonraki satır simge, liste öğelerine atar <xref:System.Windows.Forms.Label.Text> etiketin özelliği. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, son satırında `if` deyimi forma eklenmiş olan simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Bkz: [adım ı: Visual Studio hata ayıklayıcısı ile bunu nasıl?](https://msdn.microsoft.com/vstudio/ee672313.aspx) veya [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md) daha fazla bilgi için.

3.  Oyun tahtasını simgelerle doldurmak için çağrılacak ihtiyacınız `AssignIconsToSquares()` program başlar başlamaz yöntemi. Visual C# kullanıyorsanız, yalnızca çağrının altına bir deyim ekleyin `InitializeComponent()` yönteminde **Form1**_Oluşturucusu_, böylece formunuz gösterilmeden önce kendini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Bkz: [oluşturucular (C# programlama Kılavuzu)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) veya [oluşturucuları ve yıkıcıları kullanma](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) daha fazla bilgi için Visual Basic'te.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Visual Basic için ekleme `AssignIconsToSquares()` yöntem çağrısını `Form1_Load` yöntemi böylece kod aşağıdaki gibi görünür.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4.  Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.

5.  Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin.

     ![Eşleştirme oyunu rasgele simgeleri içeren](../ide/media/express_tut4step3.png) game rasgele simgeleri içeren eşleştirme

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları oyuncudan gizlemek için her bir etiketin ayarlayabilirsiniz **ForeColor** aynı renge özelliğine kendi **BackColor** özelliği.

    > [!TIP]
    >  Etiket gibi denetimleri gizlemenin bir diğer yolu ayarlamaktır kendi **görünür** özelliğini **False**.

6.  Simgeleri gizlemek için kod içinde derleme dışı bırakılan satırı açıklama işaretlerini kaldırın ve programı durdurmak `For Each` döngü.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7.  Menü çubuğunda, **Tümünü Kaydet** programınızı kaydetmek için düğmesini ve ardından çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Sonraki öğretici adımına gitmek için bkz: [4. adım: her etikete click olay işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).

-   Önceki öğretici adımına dönmek için bkz: [2. adım: rasgele nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
