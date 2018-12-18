---
title: '8. adım: Kodu Göster bir resim düğme olayı işleyicisi yazma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6172188fb7d06122cdcc178889b2a5b37ca1bb0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933553"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>8. Adım: Resim Göster Düğmesi Olay İşleyicisi için Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda yaptığınız **resim Göster** şöyle çalışan düğmesi:  
  
- Bir kullanıcı bu düğmeyi seçtiğinde program açılır bir **açık dosya** iletişim kutusu.  
  
- Bir kullanıcı bir resim dosyasını açarsa, program o resmi PictureBox içinde gösterir.  
  
  IDE kod yazmanıza yardımcı olacak, IntelliSense adında güçlü bir araç vardır. Kodun girerken IDE, girdiğiniz kısmi sözcükler için önerilen tamamlamaları içeren bir kutu açar. Sonra yapmak istediğinizi belirlemeye çalışır ve otomatik olarak öğeyi listeden seçtiğiniz son atlar. Yukarı veya aşağı taşımak için okları veya seçimleri daraltmak için de mektup yazmaya devam edebilirsiniz. İstediğiniz seçeneği gördüğünüzde, seçmek için SEKME tuşunu seçin. Alternatif olarak, gerekli değilse, önerileri yok sayabilirsiniz.  
  
  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo")bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 4 Resim Görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205215) veya [öğretici 1: Resim Görüntüleyici C# ' - oluşturma Video 4](http://go.microsoft.com/fwlink/?LinkId=205203). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.  
  
### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Bir resim düğme olayı işleyicisi Göster kod yazmak için  
  
1.  Windows Forms Tasarımcısı'na gidin ve çift **resim Göster** düğmesi. IDE hemen kod tasarımcısına gider ve imlecinizi içine taşır `showButton_Click()` daha önce eklemiş olduğunuz yöntemi.  
  
2.  Türü bir `i` ikisi arasındaki boş bir satıra küme ayraçları {}. (Visual Basic'de Private Sub arasında boş bir satıra yazın... ve End Sub.) Bir **IntelliSense** penceresi açılır ve aşağıdaki resimde gösterildiği gibi.  
  
     ![Visual C ile IntelliSense&#35; kod](../ide/media/express-ifintellisense.png "Express_IfIntellisense")  
Visual C# koduna sahip IntelliSense  
  
3.  **IntelliSense** penceresi sözcüğünü vurgulamalıdır **varsa**. (Aksi takdirde, bir küçük harf girin `f`, ve onu.) Biraz nasıl fark *araç ipucu* yanındaki kutusunda **IntelliSense** penceresi görünür açıklamasıyla birlikte **IF için kod parçacığı deyimi**. (Visual Basic'te araç ipucu ayrıca bunun bir kod parçacığı olduğunu bildiren ancak biraz farklı ifadesi.) Kod parçacığını kullanmak için bu nedenle eklemek için TAB tuşuna basın, istediğiniz **varsa** kodunuzla. Daha sonra yeniden kullanmak için SEKME tuşunu seçin **varsa** kod parçacığı. (Başka bir yerden seçerseniz ve **IntelliSense** penceresi kaybolursa, üzerinden geri alın **miyim** ve yeniden yazın ve **IntelliSense** penceresi yeniden açılır.)  
  
     ![Visual C&#35; kod](../ide/media/express-highlighttrue.png "Express_HighlightTrue")  
Visual C# kodu  
  
4.  Ardından, IntelliSense açmak için daha çok kod girmek için kullandığınız bir **Dosya Aç** iletişim kutusu. Bir kullanıcı seçerseniz, **Tamam** düğmesi, PictureBox, kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlarda kodu nasıl gireceğiniz gösterilmektedir ve çok sayıda adımları olmasına rağmen yalnızca birkaç tuş vuruşları olur:  
  
    1.  Seçili metnin başlangıç **true** kod parçacığında. Tür `op` üzerine yazmak. (Visual Basic'te, bir harfle başlar, bu nedenle `Op`.)  
  
    2.  **IntelliSense** penceresi açılır ve görüntüler **openFileDialog1**. Seçmek için SEKME tuşunu seçin. (Visual Basic'te, gördüğünüz şekilde ilk bir harf ile başlar **OpenFileDialog1**. Emin **OpenFileDialog1** seçilir.)  
  
         Hakkında daha fazla bilgi edinmek için `OpenFileDialog`, bkz: [OpenFileDialog](http://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).  
  
    3.  Bir nokta (`.`) (birçok Programcı bunu nokta olarak adlandırır.) Hemen sonra bir nokta yazdığınız için **openFileDialog1**e **IntelliSense** penceresi açılır; tamamının dolu **OpenFileDialog** bileşenin özellikleri ve yöntemleri. Bu görünen, aynı özelliklerdir **özellikleri** Windows Form Tasarımcısı'nda seçtiğinizde penceresi. Bileşenin bir şeyler (bir iletişim kutusu açmak gibi) yöntemleri de seçebilirsiniz.  
  
        > [!NOTE]
        >  **IntelliSense** penceresi gösterebilir size hem özellikleri hem de yöntemleri. Ne gösterilmekte olduğunu belirlemek için her öğe sol tarafındaki simgeye bakın **IntelliSense** penceresi. Her özelliğin yanında her yöntemin yanında bir blok resmi ve İngiliz anahtarı (veya spanner) resmi görürsünüz. Ayrıca her olayın yanında bir Şimşek simgesi vardır. Bu resimler aşağıdaki gibi görüntülenir.  
  
         ![Yöntem simgesi](../ide/media/express-iconmethod.png "Express_IconMethod")  
Yöntem simgesi  
  
         ![Özellik simgesi](../ide/media/express-iconproperty.png "Express_IconProperty")  
Özellik simgesi  
  
         ![Olay simgesi](../ide/media/express-iconevent.png "Express_IconEvent")  
Olay simgesi  
  
    4.  Yazmaya başlayın `ShowDialog` (büyük/küçük harf IntelliSense için önemsizdir). `ShowDialog()` Yöntemi gösterilir **açık dosya** iletişim kutusu. Pencerenin vurguladıysa **ShowDialog**, SEKME tuşunu seçin. Ayrıca, "ShowDialog" vurgulayın ve Yardımı almak için F1 tuşuna basın.  
  
         Hakkında daha fazla bilgi edinmek için `ShowDialog()` yöntemi bkz [ShowDialog yöntemi](http://msdn.microsoft.com/library/c7ykbedk.aspx).  
  
    5.  Kullandığınızda, bir yöntem bir denetim veya bileşen üzerinde (olarak adlandırılan *bir yöntemi çağırmak*), parantezler eklemeniz gerekir. Bu nedenle açılış ve kapanış ayraçlarını hemen "g sonra" girin `ShowDialog`: `()` şimdi "openFileDialog1.ShowDialog()" gibi görünmelidir.  
  
        > [!NOTE]
        >  Yöntemler, tüm önemli bir parçasıdır ve Bu öğreticide, yöntemleri kullanmak için birkaç yol göstermiştir. Bir bileşenin yöntemini nasıl aradığınız gibi şeyler yapmak için söylemek için çağırabilirsiniz **OpenFileDialog** bileşenin `ShowDialog()` yöntemi. Programınız bir anda, gibi şeyler yapmak için kendi yöntemlerinizi oluşturabilirsiniz adlı `showButton_Click()` bir kullanıcı bir düğmeyi seçtiğinde bir iletişim kutusu ve resim açan yöntemi.  
  
    6.  Visual C# için bir alan ekleyin ve ardından iki eşittir işareti ekleyin (`==`). Visual Basic'te bir alan ekleyin ve ardından tek bir eşittir işareti (`=`). (Visual C# ve Visual Basic farklı eşitlik operatörleri kullanır.)  
  
    7.  Başka bir alan ekleyin. Bunu yaptığınızda hemen başka **IntelliSense** penceresi açılır. Yazmaya başlayın `DialogResult` ve eklemek için SEKME tuşunu seçin.  
  
        > [!NOTE]
        >  Bir yöntem çağırmak için kod yazdığınızda, bazen bir değer döndürür. Bu durumda, **OpenFileDialog** bileşenin `ShowDialog()` yöntemi, bir DialogResult değeri döndürür. DialogResult, iletişim kutusunda ne olduğunu söyleyen özel bir değerdir. Bir **OpenFileDialog** bileşen, kullanıcı seçme içinde sonuçlanabilir **Tamam** veya **iptal**, bu nedenle kendi `ShowDialog()` yöntemi döndürür ya da DialogResult.OK veya DialogResult.Cancel döndürür.  
  
    8.  DialogResult değeri açmak için bir nokta yazın **IntelliSense** penceresi. Harfini girmek `O` ve eklemek için TAB tuşunu **Tamam**.  
  
         Hakkında daha fazla bilgi edinmek için `DialogResult`, bkz: [DialogResult](http://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).  
  
        > [!NOTE]
        >  Kodun ilk satırı tamamlanmış olmalıdır. Visual C# için aşağıdaki olmalıdır.  
        >   
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`  
        >   
        >  Visual Basic için aşağıdaki olmalıdır.  
        >   
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`  
  
    9. Şimdi bir daha fazla kod satırı ekleyin. Bunu yazabilirsiniz (veya kopyalayıp yapıştırın), ancak bunu eklemek için IntelliSense kullanmayı düşünün. Daha fazla, IntelliSense ile kendi kodunuzu yazma daha hızlı bir şekilde bilgi sahibisiniz. Son `showButton_Click()` yöntemi aşağıdaki gibi görünür. (Seçin **VB** kod Visual Basic sürümünü görüntülemek için sekmesinde.)  
  
         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sonraki öğretici adımına gitmek için bkz: [9. adım: gözden geçirme, açıklama ve Test kodunuzu](../ide/step-9-review-comment-and-test-your-code.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [7. adım: bilgisayarınızı forma Ekle iletişim kutusu bileşenleri](../ide/step-7-add-dialog-components-to-your-form.md).



