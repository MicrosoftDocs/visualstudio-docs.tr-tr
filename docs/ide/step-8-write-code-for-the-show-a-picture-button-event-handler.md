---
title: '8. adım: bir resim düğme olayı işleyicisi Göster için kod yazma'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2c76a6eb760e55659c7da4df2a1a341426f0c6e
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671813"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>8. adım: bir resim düğme olayı işleyicisi Göster için kod yazma

Bu adımda yaptığınız **resim Göster** şöyle çalışan düğmesi:

- Bir kullanıcı bu düğmeyi seçtiğinde program açılır bir <xref:System.Windows.Forms.OpenFileDialog> kutusu.

- Bir kullanıcı bir resim dosyasını açarsa, program o resmi gösterir <xref:System.Windows.Forms.PictureBox>.

IDE kod yazmanıza yardımcı olacak, IntelliSense adında güçlü bir araç vardır. Kodun girerken IDE, girdiğiniz kısmi sözcükler için önerilen tamamlamaları içeren bir kutu açar. Sonra yapmak istediğinizi belirlemeye çalışır ve otomatik olarak öğeyi listeden seçtiğiniz son atlar. Yukarı veya aşağı taşımak için okları veya seçimleri daraltmak için de mektup yazmaya devam edebilirsiniz. Seçeneği gördüğünüzde, seçmek istediğiniz **sekmesini** anahtarı seçin. Alternatif olarak, gerekli değilse, önerileri yok sayabilirsiniz.

![video bağlantısı](../data-tools/media/playvideo.gif)bu konunun video sürümü için bkz: [öğretici 1: Resim Görüntüleyici oluşturma Visual Basic'te - Video 4](https://msdn.microsoft.com/vstudio/gg315355.aspx). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videoda, Visual Studio'nun önceki bir sürümünü kullanır. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Bir resim düğme olayı işleyicisi Göster için kod yazmak için

1.  Git **Windows Form Tasarımcısı** ve çift **resim Göster** düğmesi. IDE hemen kod tasarımcısına gider ve imlecinizi içine taşır `showButton_Click()` daha önce eklemiş olduğunuz yöntemi.

2.  Türü bir `i` iki ayraçlar arasında boş bir satıra `{ }`. (Visual Basic'te arasında boş bir satıra yazın `Private Sub...` ve `End Sub`.) Bir **IntelliSense** penceresi açılır ve aşağıdaki resimde gösterildiği gibi.

     ![Visual C ile IntelliSense&#35; kod](../ide/media/express_ifintellisense.png)

3.  **IntelliSense** penceresi sözcüğünü vurgulamalıdır `if`. (Aksi takdirde, bir küçük harf girin `f`, ve onu.) Biraz nasıl fark *araç ipucu* yanındaki kutusunda **IntelliSense** penceresi görünür açıklamasıyla birlikte **IF için kod parçacığı deyimi**. (Visual Basic'te araç ipucu ayrıca bunun bir kod parçacığı olduğunu bildiren ancak biraz farklı ifadesi.) Kod parçacığını kullanmak, bu nedenle seçmek istediğiniz **sekmesini** eklemek için anahtar `if` kodunuzla. Ardından **sekmesini** yeniden kullanılacak anahtarı `if` kod parçacığı. (Başka bir yerden seçerseniz ve **IntelliSense** penceresi kaybolursa, üzerinden geri alın `i` ve yeniden yazın ve **IntelliSense** penceresi yeniden açılır.)

     ![Visual C&#35; kod](../ide/media/express_highlighttrue.png)

4.  Ardından, IntelliSense açmak için daha çok kod girmek için kullandığınız bir **Dosya Aç** iletişim kutusu. Bir kullanıcı seçerseniz, **Tamam** düğmesi, PictureBox, kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlarda kodu nasıl gireceğiniz gösterilmektedir ve çok sayıda adımları olmasına rağmen yalnızca birkaç tuş vuruşları olur:

    1.  Seçili metnin başlangıç **true** kod parçacığında. Tür `op` üzerine yazmak. (Visual Basic'te, bir harfle başlar, bu nedenle `Op`.)

    2.  **IntelliSense** penceresi açılır ve görüntüler **openFileDialog1**. Seçin **sekmesini** anahtarı seçin. (Visual Basic'te, gördüğünüz şekilde ilk bir harf ile başlar **OpenFileDialog1**. Emin **OpenFileDialog1** seçilir.)

         Hakkında daha fazla bilgi edinmek için `OpenFileDialog`, bkz: [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

    3.  Bir nokta (`.`) (birçok Programcı bunu nokta olarak adlandırır.) Hemen sonra bir nokta yazdığınız için **openFileDialog1**e **IntelliSense** penceresi açılır; tamamının dolu **OpenFileDialog** bileşenin özellikleri ve yöntemleri. Bunlar görünen, aynı özellikleridir **özellikleri** içinde seçtiğinizde penceresi **Windows Form Tasarımcısı**. Bileşenin bir şeyler (bir iletişim kutusu açmak gibi) yöntemleri de seçebilirsiniz.

        > [!NOTE]
        > **IntelliSense** penceresi gösterebilir size hem özellikleri hem de yöntemleri. Ne gösterilmekte olduğunu belirlemek için her öğe sol tarafındaki simgeye bakın **IntelliSense** penceresi. Her özelliğin yanında her yöntemin yanında bir blok resmi ve İngiliz anahtarı (veya spanner) resmi görürsünüz. Ayrıca her olayın yanında bir Şimşek simgesi vardır. Bu resimler aşağıdaki gibi görüntülenir.

         ![Yöntem simgesi](../ide/media/express_iconmethod.png)

         ![Özellik simgesi](../ide/media/express_iconproperty.png)

         ![Olay simgesi](../ide/media/express_iconevent.png)

    4.  Yazmaya başlayın `ShowDialog` (büyük/küçük harf IntelliSense için önemsizdir). `ShowDialog()` Yöntemi gösterilir **açık dosya** iletişim kutusu. Pencerenin vurguladıysa **ShowDialog**, seçin **sekmesini** anahtarı. Ayrıca "ShowDialog" vurgulayın ve seçin **F1** Yardımı almak için anahtar.

         Hakkında daha fazla bilgi edinmek için `ShowDialog()` yöntemi bkz [ShowDialog yöntemi](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

    5.  Kullandığınızda, bir yöntem bir denetim veya bileşen üzerinde (olarak adlandırılan *bir yöntemi çağırmak*), parantezler eklemeniz gerekir. Bu nedenle açılış ve kapanış ayraçlarını hemen "g sonra" girin `ShowDialog`: `()` şimdi "openFileDialog1.ShowDialog()" gibi görünmelidir.

        > [!NOTE]
        > Yöntemler, tüm önemli bir parçasıdır ve Bu öğreticide, yöntemleri kullanmak için birkaç yol göstermiştir. Bir bileşenin yöntemini nasıl aradığınız gibi şeyler yapmak için söylemek için çağırabilirsiniz **OpenFileDialog** bileşenin `ShowDialog()` yöntemi. Programınız bir anda, gibi şeyler yapmak için kendi yöntemlerinizi oluşturabilirsiniz adlı `showButton_Click()` bir kullanıcı bir düğmeyi seçtiğinde bir iletişim kutusu ve resim açan yöntemi.

    6.  Visual C# için bir alan ekleyin ve ardından iki eşittir işareti ekleyin (`==`). Visual Basic'te bir alan ekleyin ve ardından tek bir eşittir işareti (`=`). (Visual C# ve Visual Basic farklı eşitlik operatörleri kullanır.)

    7.  Başka bir alan ekleyin. Bunu yaptığınızda hemen başka **IntelliSense** penceresi açılır. Yazmaya başlayın `DialogResult` ve **sekmesini** anahtarı ekleyin.

        > [!NOTE]
        > Bir yöntem çağırmak için kod yazdığınızda, bazen bir değer döndürür. Bu durumda, **OpenFileDialog** bileşenin <xref:System.Windows.Forms.CommonDialog.ShowDialog> yöntemi döndürür bir <xref:System.Windows.Forms.DialogResult> değeri. DialogResult, iletişim kutusunda ne olduğunu söyleyen özel bir değerdir. Bir **OpenFileDialog** bileşen, kullanıcı seçme içinde sonuçlanabilir **Tamam** veya **iptal**, bu nedenle kendi `ShowDialog()` yöntemi döndürür ya da `DialogResult.OK` veya `DialogResult.Cancel`.

    8.  DialogResult değeri açmak için bir nokta yazın **IntelliSense** penceresi. Harfini girmek `O` ve **sekmesini** eklemek için anahtar **Tamam**.

         DialogResult hakkında daha fazla bilgi için bkz: [DialogResult](<xref:System.Windows.Forms.DialogResult>).

        > [!NOTE]
        >  Kodun ilk satırı tamamlanmış olmalıdır. Visual C# için aşağıdaki olmalıdır.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  Visual Basic için aşağıdaki olmalıdır.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Şimdi bir daha fazla kod satırı ekleyin. Bunu yazabilirsiniz (veya kopyalayıp yapıştırın), ancak bunu eklemek için IntelliSense kullanmayı düşünün. Daha fazla, IntelliSense ile kendi kodunuzu yazma daha hızlı bir şekilde bilgi sahibisiniz. Son `showButton_Click()` yöntemi aşağıdaki gibi görünür. (Seçin **VB** kod Visual Basic sürümünü görüntülemek için sekmesinde.)

         [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]
         [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Sonraki öğretici adımına gitmek için bkz: [9. adım: gözden geçirme, açıklama ve kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md).

-   Önceki öğretici adımına dönmek için bkz: [7. adım: formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md).
