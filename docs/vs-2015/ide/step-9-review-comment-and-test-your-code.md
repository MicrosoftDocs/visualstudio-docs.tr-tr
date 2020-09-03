---
title: '9. Adım: kodunuzu gözden geçirme, açıklama ve test etme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 090aeb83f6d0480c511acd808498953ae6c01940
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851096"
---
# <a name="step-9-review-comment-and-test-your-code"></a>9. Adım: Kodunuzu Gözden Geçirme, Açıklama ve Test Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daha sonra kodunuza bir açıklama eklersiniz. Yorum, programın davranış biçimini değiştirmeyen bir notdur. Kodunuzu okuyan birisinin ne yaptığını öğrenmesini kolaylaştırır. Kodunuza açıklama eklemek için iyi bir önleminizi alarak vardır. Visual C# ' de iki eğik çizgi (//) bir satırı açıklama olarak işaretler. Visual Basic, bir satırı açıklama olarak işaretlemek için tek tırnak işareti (') kullanılır. Bir açıklama ekledikten sonra, programınızı test edersiniz. Projeniz üzerinde çalışırken kodunuzu sık çalıştırmak ve test etmek iyi bir uygulamadır. bu sayede, kod daha karmaşık hale gelmeden önce sorunları önceden yakalayabilir ve çözebilirsiniz. Buna *yinelemeli test*denir.

 Yalnızca bir şey oluşturmuş olabilirsiniz ve henüz yapılmasa da, bir resmi yükleyebilir. Kodunuza bir açıklama eklemeden ve test etmeden önce, bu kavramları sık kullandığınız için kod kavramlarını gözden geçirmek için zaman alın:

- Windows Form Tasarımcısı **resim göster** düğmesine çift TıKLADıĞıNıZDA, IDE programınızın koduna otomatik olarak bir *Yöntem* ekledi.

- Yöntemler, kodunuzun nasıl düzenlenme yöntemleridir: kodunuz birlikte gruplandırılır.

- Çoğu zaman, yöntemin `showButton_Click()` bir iletişim kutusu gösterdiği ve sonra bir resmi yükleyen gibi belirli bir sırada çok sayıda şey yapar.

- Yöntem kod *deyimlerinden*veya kod satırlarından oluşur. Bir yöntemi kod deyimlerini birlikte paketetmenin bir yolu olarak düşünün.

- Bir yöntem yürütüldüğünde veya *çağrıldığında*, yöntem içindeki deyimler sırayla yürütülür ve ilki birinci bir ile başlar.

   Aşağıda bir deyimin örneği verilmiştir.

  ```csharp
  pictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Deyimler, programlarınızın şeyleri yapabilecekleri şeydir. Visual C# ' de, bir ifade her zaman noktalı virgül ile biter. Visual Basic, satırın sonu deyimin sonu olur. (Visual Basic noktalı virgül gerekmez.) Yukarıdaki ifade, `PictureBox` Denetiinizde **OpenFileDialog** bileşeni ile kullanıcının seçtiği dosyayı yüklemesini söyler.

  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) veya [öğretici 1: C# içinde resim görüntüleyici oluşturma-video 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-add-comments"></a>Açıklama eklemek için

1. Aşağıdaki yorumu kodunuza ekleyin.

     [!code-csharp[VbExpressTutorial1Step9_10#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step9_10#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#1)]

    > [!NOTE]
    > **ShowButton** düğinizin Click olay işleyicisi artık tamamlandı ve çalışıyor. Bir deyimden başlayarak kod yazmaya başladıysanız `if` . Bir `if` ifade, programınıza "Bu şeyi denetle ve doğru ise, bu eylemleri yapın." Bu durumda, programınıza **Dosya Aç** iletişim kutusunu açmasını söylersiniz ve Kullanıcı bir dosya seçip **Tamam** düğmesini seçerse, bu dosyayı PictureBox 'a yükleyin.

    > [!TIP]
    > IDE, kod yazmanızı kolaylaştıracak şekilde oluşturulmuştur ve *kod parçacıkları* bunu yapmanın bir yoludur. Kod parçacığı, küçük bir kod bloğuna genişletilmiş bir kısayoldur.
    >
    >  Kullanılabilir tüm parçacıkları görebilirsiniz. Menü çubuğunda **Araçlar**, **kod parçacıkları Yöneticisi**' ni seçin. Visual c# için `if` kod parçacığı **Visual c#** ' de bulunur. Visual Basic için, `if` kod parçacıkları **conditionals ve döngüler**, **kod desenleri**' nde bulunur. Bu yöneticiyi, mevcut parçacıkları taramak veya kendi kod parçacıklarınızı eklemek için kullanabilirsiniz.
    >
    >  Kodu yazarken bir kod parçacığını etkinleştirmek için yazın ve sekme tuşunu seçin. Birçok parçacık, **IntelliSense** penceresinde görünür. bu nedenle, **IntelliSense** penceresinde kod PARÇACıĞıNı seçmek ve sonra IDE 'nin kod parçacığını kullanmasını söylemek için. (IntelliSense parçacığı destekler `if` , ancak `ifelse` kod parçacığını destekler.)

2. Programınızı çalıştırmadan önce, aşağıdaki gibi görünen **Tümünü Kaydet** araç çubuğu düğmesini seçerek programınızı kaydedin.

     ![Tümünü Kaydet araç çubuğu düğmesi](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Tümünü Kaydet düğmesi

     Alternatif olarak, programınızı kaydetmek için menü çubuğunda **Dosya**, **Tümünü Kaydet**' i seçin. Bu, erken ve sık tasarrufu sağlamak için en iyi uygulamadır.

     Çalıştığında, programınız aşağıdaki resim gibi görünmelidir.

     ![Resim görüntüleyici](../ide/media/express-pictureviewerdonerun.png "Express_PictureViewerDoneRun") Resim görüntüleyici

### <a name="to-test-your-program"></a>Programınızı test etmek için

1. F5 tuşunu seçin veya **hata ayıklamayı Başlat** araç çubuğu düğmesini seçin.

2. Yeni yazdığınız kodu çalıştırmak için **bir resim göster** düğmesini seçin. İlk olarak, program açık bir **Dosya** iletişim kutusu açar. Filtrelerinizin, iletişim kutusunun alt kısmındaki **dosya türü** açılan listesinde göründüğünü doğrulayın. Ardından bir resme gidin ve açın. Genellikle **Belgelerim klasörünüzdeki Windows** işletim sistemiyle birlikte gelen örnek resimleri, **Resimlerim \ örnek resimler** klasörü içinde bulabilirsiniz.

    > [!NOTE]
    > **Resim dosyası seç** iletişim kutusunda herhangi bir görüntü görmüyorsanız, \* iletişim kutusunun sağ alt tarafındaki aşağı açılan listede "tüm dosyalar (*.)" filtresinin seçili olduğundan emin olun.

3. Bir resim yükleyin ve PictureBox 'da görünür. Ardından, kenarlıklarını sürükleyerek formunuzu yeniden boyutlandırmayı deneyin. PictureBox 'ın, kendisini formun içine yerleştirilmiş bir TableLayoutPanel içinde yerleştiğinden, resim alanı kendini form kadar geniş olacak şekilde yeniden boyutlandırır ve formun en üstteki %90 ' unu dolduracaktır. TableLayoutPanel ve FlowLayoutPanel kapsayıcılarını şu nedenle kullandınız: Kullanıcı yeniden boyutlandırdığında formunuzu doğru boyutlandırırlar.

     Şimdi, daha büyük resimler resim görüntüleyicinizin kenarlıklarının ötesine geçer. Sonraki adımda, resimlerin pencereye sığması için kod ekleyeceksiniz.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [adım 10: ek düğmeler ve onay kutusu Için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

- Önceki öğretici adımına dönmek için bkz. [8. Adım: resim göster düğmesi olay işleyicisi Için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).
