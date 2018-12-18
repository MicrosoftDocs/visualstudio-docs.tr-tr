---
title: '6. adım: düğme denetimlerinizi adlandırma'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b11bace93efc253ffcb0f8d2b97ecc57c7462bb8
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748403"
---
# <a name="step-6-name-your-button-controls"></a>6. adım: düğme denetimlerinizi adlandırma
Yalnızca bir tane <xref:System.Windows.Forms.PictureBox> formunuzda. Eklendiğinde, IDE otomatik olarak da adlandırılan **pictureBox1**. Yalnızca bir tane <xref:System.Windows.Forms.CheckBox>, adlandırılmış **checkBox1**. En kısa sürede, biraz kod yazılır ve bu kod onay kutusunu ve PictureBox başvurur. Her bu denetimlerin yalnızca biri, çünkü gördüğünüzde ne anlama geldiğini bilirsiniz **pictureBox1** veya **checkBox1** kodunuzda.

> [!NOTE]
>  Adları Visual Basic'te, herhangi bir denetim adı varsayılan ilk harfini ilk harf olduğundan **PictureBox1**, **CheckBox1**ve benzeri.

 Formunuzda dört düğme vardır ve bunları IDE adlı **button1**, **button2**, **button3**, ve **button4**. Yalnızca geçerli adlarını bakarak hangi düğme bilmiyorsanız **Kapat** düğmesi ve hangisinin olduğuna **resim Göster** düğmesi. İşte bu nedenle daha bilgilendirici adları düğme denetimlerinizi vermek yararlıdır.

 ![video bağlantı](../data-tools/media/playvideo.gif)bu konuda video sürümü için bkz: [Öğreticisi 1: Visual Basic'te - Video 3 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205213) veya [Eğitmen 1: Resim Görüntüleyici C# ' - Video 3 oluşturma](http://go.microsoft.com/fwlink/?LinkId=205202). Bazı menü komutları ve diğer kullanıcı arabirimi öğeleri küçük farklar olduklarından bu videolar Visual Studio'nun önceki bir sürümünü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde geçerli sürümünde Visual Studio çalışır.

## <a name="to-name-your-button-controls"></a>Düğme denetimlerinizi adlandırma için

1.  Form üzerinde seçin **Kapat** düğmesi. (Seçili tüm düğmeleri hala varsa, seçin **Esc** seçimini iptal etmek için anahtar.) Haftasına **özellikleri** görene kadar penceresi **(ad)** özelliği. ( **(Ad)** özelliği olduğunda en üstüne yakın özellikleri alfabetik.) Adına değiştirme **Kapat düğmesi**, aşağıdaki resimde gösterildiği gibi.

     ![Özellikler penceresini kapat düğmesi adla](../ide/media/express_setnameproperty.png)
**özellikleri** penceresiyle **Kapat düğmesi** adı

    > [!NOTE]
    >  Düğmesinin adını değiştirmeyi deneyin, **Kapat düğmesi**, sözcük kapatın ve düğmesi arasında bir boşluk ile IDE bir hata iletisi görüntüler: "özelliğinin değeri geçerli değil." Boşluk (ve diğer birkaç karakterler) denetim adlarında izin verilmiyor.

2.  Diğer üç düğmelere yeniden adlandırma **backgroundButton**, **clearButton**, ve **showButton**. Denetim Seçici açılan listeden seçerek adlarını doğrulayabilirsiniz **özellikleri** penceresi. Yeni düğmesi adları görüntülenir.

3.  Çift **resim Göster** formundaki düğmesi. Alternatif olarak, seçin **resim Göster** düğmesi formda ve ardından **Enter** anahtarı. Bunu yaptığınızda, IDE ek bir sekme adlı ana penceresinde açar. **Form1.cs** (**Form1.vb** Visual Basic kullanıyorsanız). Bu sekme, aşağıdaki resimde gösterildiği gibi formun arkasındaki kod dosyası gösterir.

     ![Visual C ile Form1.cs sekmesini&#35; kod](../ide/media/express_showbuttoncode.png)
**Form1.cs** Visual C# kodu sekmesi

4.  Bu kod parçası, üzerinde odaklanın. (Seçin **VB** Visual Basic kodu Visual Basic sürümünü görüntülemek için kullanıyorsanız, aşağıda sekmesinde.)

     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]

     Adlı kodu aradığınız `showButton_Click()`. İçin kod dosyası açıldığında IDE bu formun kodu eklenen **showButton** düğmesi. Bir formda bir denetim için kod dosyası açtığınızda tasarım zamanında, zaten yoksa denetim için kodu oluşturulur. Olarak bilinen bu kodu bir *yöntemi*, programınızı çalıştırma ve control - bu durumda, seçin ne zaman çalışacağını **resim Göster** düğmesi.

    > [!NOTE]
    >  Bu öğreticide, otomatik olarak oluşturulan Visual Basic kodu ayraçlar arasında her şeyi kaldırarak Basitleştirilmiş `()`. Bu olduğunda, aynı kod kaldırabilirsiniz. Programınız her iki durumda da çalışır. Öğreticiler geri kalanı için mümkün olduğunda otomatik olarak oluşturulan kod basitleştirilmiştir.

5.  Seçin **Windows Form Tasarımcısı** yeniden sekmesinde (**Form1.cs [Design]** Visual C# ' ta, **Form1.vb [tasarım]** Visual Basic'te) ve koddosyasınıaçma**Resmi temizleyin** formun kodda bir yöntem oluşturmak için düğmesi. Bu, kalan iki düğmeleri için işlemi yineleyin. Her zaman IDE yeni bir yöntemi formun kod dosyasına ekler.

6.  Daha fazla yöntem eklemek için kod dosyasını açmak **onay kutusunu** denetim **Windows Form Tasarımcısı** eklemek IDE yapmak için bir `checkBox1_CheckedChanged()` yöntemi. Bu yöntem, her kullanıcı seçer veya onay kutusunu temizler çağrılır.

    > [!NOTE]
    >  Bir programda çalışırken, kod düzenleyicisini arasında genellikle taşıyın ve **Windows Form Tasarımcısı**. IDE projenizde gidin kolay hale getirir. Kullanım **Çözüm Gezgini** açmak için **Windows Form Tasarımcısı** çift tıklatarak *Form1.cs* Visual C# veya *Form1.vb* Visual Basic'te veya menü çubuğunda seçin **Görünüm** > **Tasarımcısı**.

     Aşağıdaki yeni kod, Kod Düzenleyicisi'nde gördüğünüz gösterir.

     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

     Eklediğiniz beş yöntem adlı *olay işleyicileri*, (örneğin, bir kutusunu işaretleyerek veya bir düğmesini seçerek bir kullanıcı) bir olay gerçekleştiğinde her programınızı bunları çağırır.

     Tasarım zamanında IDE içinde bir denetim için kod görüntülediğinizde, bir yoksa Visual Studio denetim için bir olay işleyicisi yöntemi ekler. Örneğin, bir düğme çift tıkladığınızda, IDE için bir olay işleyicisi ekler, <xref:System.Windows.Forms.Control.Click> (düğme kullanıcının seçtiği her adı verilir) olay. Bir onay kutusu çift tıkladığınızda, IDE için bir olay işleyicisi ekler, <xref:System.Windows.Forms.CheckBox.CheckedChanged> (kullanıcı kutusunu seçer veya temizler olduğunda çağrılan) olay.

     Bir denetim için bir olay işleyicisi ekledikten sonra kendisine dilediği zaman dönebilirsiniz **Windows Form Tasarımcısı** denetimi çift tıklatarak veya menü çubuğu seçme **Görünüm**  >  **Kod**.

     Programları derleme ve yöntemler (olay işleyicileri dahil), istediğiniz herhangi bir ad olabilir adları önemlidir. IDE ile olay işleyici eklediğinizde, denetimin adını ve işlenen olay dayalı bir ad oluşturur. Örneğin, adlı bir düğmeye Click olayını **showButton** çağrılır `showButton_Click()` olay işleyicisi yöntemi. Ayrıca, dosyaları açma ve kapama parantez `()` yöntemlerini ele belirtmek için yöntem adından sonra genellikle eklenir. Kod değişken adını değiştirmek istediğiniz karar verirseniz, kodda değişkeni sağ tıklatın ve ardından **yeniden düzenlemeniz** > **yeniden adlandırma**. Bu değişken kodda tüm örneklerini yeniden adlandırılmıştır. Bkz: [yeniden düzenlemeyi yeniden adlandırma](../ide/reference/rename.md) daha fazla bilgi için.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [adım 7: formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md).

-   Eğitmen önceki adıma dönmek için bkz: [5. adım: formunuza denetimler ekleme](../ide/step-5-add-controls-to-your-form.md).
