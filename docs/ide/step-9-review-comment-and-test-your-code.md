---
title: '9. adım: Gözden geçirme, açıklama ve kodunuzu test'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de7ca2509c8489c7a9d541135401949ef3e4b20e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856034"
---
# <a name="step-9-review-comment-and-test-your-code"></a>9. adım: Gözden geçirme, açıklama ve kodunuzu test
Sonraki kod bir açıklama ekleyin. Bir yorum, programın davranışını değiştirmeyen bir nottur. Ne yaptığını anlamak için kodunuzu okuyan kişi için kolaylaştırır. Kodunuza yorumlar eklemek, öğrenmek için iyi bir alışkanlıktır. Visual C# içinde iki İleri eğik çizgi (/ /) satırı bir açıklama olarak işaretler. Visual Basic'te, tek tırnak işareti ('), bir satırı yorum olarak işaretlemek için kullanılır. Bir açıklama ekledikten sonra programınızı test edin. Çalıştırın ve sık yakalayın ve erken önce kod daha karmaşık sorunları düzeltmek için projeler üzerinde çalıştığınız sırada kodunuzu test etmek için iyi bir uygulamadır. Bu adlandırılır *yinelemeli sınama*.

 Çalışır bir şey yalnızca yerleşik ve henüz yapılmaz olsa da, zaten bir resim yüklüyor olabilir. Bir açıklamayı kodunuza ekleyin ve test için önce aşağıdaki kavramları sıkça kullanacağınız için kod kavramlarını gözden geçirmek için zaman ayırın:

- Ne zaman tıklattığınız **resim Göster** düğmesine **Windows Form Tasarımcısı**, otomatik olarak eklenen IDE bir *yöntemi* program kodunuza için.

- Yöntemlerdir nasıl kodunuzu düzenleme şeklinizdir: nasıl kodunuzun gruplandırılma şeklidir.

- Çoğu zaman bir yöntem bir küçük birçok şeyi nasıl gibi belirli bir sırayla yapar, `showButton_Click()` yöntemi bir iletişim kutusu gösterir ve bir resim yükler.

- Bir yöntem kodunu yapılır *deyimleri*, ya da kod satırlarını. Yöntemi, kod deyimlerini paket için bir yol olarak düşünün.

- Bir yöntem yürütüldüğünde veya *adlı*, yöntemdeki deyimler birbiri ardına, ilkinden başlayarak sırayla yürütülür.

   Bir deyim örneği verilmiştir.

  ```csharp
  pictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Deyimleri ne programlarınızın şeyler yaptıran şeydir. Visual C# içinde bir ifade her zaman noktalı virgülle biter. Visual Basic'te, bir satırın sonuna bir deyimin sonudur. (Visual Basic'de noktalı virgül gerekiyor.) Önceki deyim söyler, <xref:System.Windows.Forms.PictureBox> ile kullanıcının seçtiği dosyayı yüklemek için Denetim **OpenFileDialog** bileşeni.

  ![video bağlantısı](../data-tools/media/playvideo.gif)bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 5 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205216) veya [öğretici 1: içinde resim görüntüleyici oluşturma C# -Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.

## <a name="to-add-comments"></a>Yorum eklemek için

1.  Aşağıdaki açıklamayı kodunuza ekleyin.

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

    > [!NOTE]
    >  **ShowButton** düğmenin <xref:System.Windows.Forms.Control.Click> olay işleyicisi artık tamamlandı ve çalışır. Kodu yazmaya başlayarak başlattığınız bir `if` deyimi. Bir `if` deyimdir nasıl programınıza "Bu şeyi denetle ve true ise, şu eylemleri gerçekleştir." Bu durumda programınıza size **Dosya Aç** iletişim kutusu, ve kullanıcı bir dosya seçer ve seçer **Tamam** düğmesi, bu dosyada yük **PictureBox**.

    > [!TIP]
    >  IDE kod yazmanızı kolaylaştırmak amacıyla oluşturulmuştur ve *kod parçacıkları* bunu yapmanın bir yoludur. Bir kod parçacığı, küçük bir kod bloğuna genişletilmiş kısayoldur.
    >
    >  Tüm kullanılabilir kod parçacıkları görebilirsiniz. Menü çubuğunda, **Araçları** > **kod parçacıkları Yöneticisi**. Visual C#, `if` kod parçacığı olan **Visual C#** . Visual Basic'te `if` parçacıkları **Koşullular ve döngüler** > **kod desenleri**. Varolan parçacıklara gözatmak veya kendi parçalarınızı eklemek için bu Yöneticisi'ni kullanabilirsiniz.
    >
    >  Kod yazarken bir parçacığı etkinleştirmek için yazın ve seçin **sekmesini** anahtarı. Birçok Parçacıklar görüntülenir **IntelliSense** seçtiğiniz neden olan bir pencere **sekmesini** tuşunu iki kez: kod parçacığından önce seçilecek **IntelliSense** penceresinde ve bildirmek için kod parçacığını kullanmak için bir IDE. (IntelliSense'i destekler `if` kod parçacığı, ama `ifelse` kod parçacığı.)

2.  Programı çalıştırmadan önce seçerek programınızı kaydedin **Tümünü Kaydet** gibi görünen araç çubuğu düğmesi.

     ![Tüm araç çubuğu düğmesi Kaydet](../ide/media/express_iconsaveall.png)
**Tümünü Kaydet** düğmesi

     Menü çubuğunda, programınızı kaydetmek için alternatif olarak, seçin **dosya** > **Tümünü Kaydet**. Erken ve sıkça kaydetmek iyi bir uygulamadır.

     Çalışırken, programınız aşağıdaki resim gibi görünmelidir.

     ![Resim Görüntüleyicisi](../ide/media/express_pictureviewerdonerun.png)
**Resim Görüntüleyicisi**

## <a name="to-test-your-program"></a>Programınızı test etmek için

1.  Seçin **F5** seçin ya da anahtar **hata ayıklamayı Başlat** araç çubuğu düğmesi.

2.  Seçin **resim Göster** az önce yazdığınız kodu çalıştırmak için düğme. İlk olarak, programı açar bir **açık dosya** iletişim kutusu. Filtrelerinizi göründüğünü doğrulayın **dosya türü** iletişim kutusunun altındaki açılır listede. Ardından bir resme gidin ve açın. Windows işletim sistemi ile gönderilen örnek resimler çoğunlukla olabilir, *Belgelerim* klasöründe *resimlerim\örnek Resimlerim* klasör.

    > [!NOTE]
    >  Herhangi bir görüntü görmüyorsanız **bir resim dosyası seçin** iletişim kutusunda, olduğundan emin olun **tüm dosyalar (*.\*)**  filtre iletişim kutusunun alt sağ tarafındaki aşağı açılan listede seçili.

3.  Bir resim yükleyin ve PictureBox içinde görüntülenecektir. Sonra kenarlıkları sürükleyerek formunuzu yeniden boyutlandırmaya çalışın. PictureBox TableLayoutPanel içine yerleştirmiş olduğundan, böylece form olarak kadar geniş ve formun üst yüzde 90 doldurur kendi kendini formun içine yerleştirildiğini resim alanınız kendi kendini yeniden boyutlandırarak. İşte bu nedenle, kullanılan <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.FlowLayoutPanel> kapsayıcılar: Bunlar formunuzu kullanıcı yeniden boyutlandırdığında doğru boyutta tutun.

     Şimdi, daha büyük resimler, resim görüntüleyicinizin kenarlıklarının dışına gider. Sonraki adımda, resimleri pencereye sığdırmak için kod ekleyeceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Sonraki öğretici adımına gitmek için bkz: [adım 10: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

-   Önceki öğretici adımına dönmek için bkz: [adım 8: bir resim düğme olayı işleyicisi Göster için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).
