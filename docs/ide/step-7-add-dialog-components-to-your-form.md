---
title: '7. adım: Formunuza iletişim kutusu bileşenleri ekleme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed228c007d41d3c7a0815cb97ea9cd890b3a0c98
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748718"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7. adım: formunuza iletişim kutusu bileşenleri ekleme
Resim dosyaları açmak ve bu adımda, bir arka plan rengi seçin, programı etkinleştirmek için eklediğiniz bir <xref:System.Windows.Forms.OpenFileDialog> bileşeni ve bir <xref:System.Windows.Forms.ColorDialog> formunuza bileşen.

 Bazı yollarını denetiminde gibi bir bileşenidir. Kullandığınız **araç** özelliklerini kullanarak ayarlayın, form ve sizin için bir bileşen eklemek için **özellikleri** penceresi. Ancak bir denetim, bir bileşen formunuza kullanıcı formdaki görebilir görünür bir öğe ekleme değil. Bunun yerine, tetikleyicinin belirli davranışlarını koduyla sağlar. Açılır bir bileşen olan bir **Dosya Aç** iletişim kutusu.

 ![video bağlantı](../data-tools/media/playvideo.gif)bu konuda video sürümü için bkz: [Öğreticisi 1: Visual Basic'te - Video 3 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205213) veya [Eğitmen 1: Resim Görüntüleyici C# ' - Video 3 oluşturma](http://go.microsoft.com/fwlink/?LinkId=205202). Bazı menü komutları ve diğer kullanıcı arabirimi öğeleri küçük farklar olduklarından bu videolar Visual Studio'nun önceki bir sürümünü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde geçerli sürümünde Visual Studio çalışır.

## <a name="to-add-dialog-components-to-your-form"></a>Formunuza iletişim kutusu bileşenleri ekleme

1.  Seçin **Windows Form Tasarımcısı** (**Form1.cs [Design]** veya **Form1.vb [tasarım]**) ve ardından açın **iletişim kutularını** grubu **Araç kutusu**.

    > [!NOTE]
    >  **İletişim kutularını** grubu **araç** açılarak ve dosyaları kaydetme, klasörlere göz atma ve yazı tipleri ve renkler için kullanılan pek çok yararlı iletişim kutuları için açtığınız bileşene sahiptir. Bu projede iki iletişim kutusu bileşenleri kullanın: OpenFileDialog ve ColorDialog.

2.  Adlı bir bileşen eklemek için **openFileDialog1** formunuza, çift **OpenFileDialog**. Adlı bir bileşen eklemek için **colorDialog1** formunuza, çift **ColorDialog** içinde **araç**. (Bir sonraki öğretici adımında kullanın.) Bir alanı altındaki görmelisiniz **Windows Form Tasarımcısı** (altındaki **resim görüntüleyici** form) olan bir simge her eklediğiniz iki iletişim kutusu bileşenleri için aşağıdaki resimde gösterildiği gibi.

     ![İletişim kutusu bileşenleri](../ide/media/express_dialogsadded.png)
**iletişim** bileşenleri

3.  Seçin **openFileDialog1** simgesini ekranın alt kısmındaki alanında **Windows Form Tasarımcısı**. İki özellikleri ayarlayın:

    -   Ayarlama **filtre** (kopyalayın ve yapıştırın) aşağıdaki özellik:

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    -   Ayarlama **başlık** aşağıdaki özelliğine: **bir resim dosyası seçin**

         **Filtre** özellik ayarlarını belirleyin görüntüleyecek dosya türlerini türlerini **Resim Seç** dosya iletişim kutusu.

    > [!NOTE]
    >  Bir örnek görmek için **Dosya Aç** farklı bir uygulama, Aç iletişim kutusunda **not defteri** veya **boyama**ve menü çubuğunda seçin **dosya**  >  **Açık**. Nasıl olduğuna dikkat edin bir **dosya türü** altındaki aşağı açılan listeden. Yalnızca kullanılan **filtre** özelliğinde **OpenFileDialog** , ayarlamak için bileşen. Ayrıca, fark nasıl **başlık** ve **filtre** özellikleri kalın **özellikleri** penceresi. IDE varsayılan değerlerine değiştirilmiş özellikleri göstermek için gerçekleştirir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Öğretici bir sonraki adıma dönmek için bkz: [adım 8: bir resim düğmesi olay işleyicisi Göster için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

-   Eğitmen önceki adıma dönmek için bkz: [6. adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md).
