---
title: 'Öğretici 1: Resim Görüntüleyici oluşturma'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 966634ee9a71854334bdd5342326c1663b9ad16c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672164"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Öğretici 1: Resim Görüntüleyici oluşturma

Bu öğreticide, bir dosyadan resim yükleyen ve pencerede görüntüleyen bir program oluşturun. Nasıl kullanacağınızı öğrenin **Windows Form Tasarımcısı** düğmeler ve resim kutuları, form üzerindeki özellikleri ayarlamak ve sorunsuz formu yeniden boyutlandırmak için kapsayıcıları kullanma gibi denetimleri Sürüklemeyi için. Ayrıca, kod yazmaya başlayın. Aşağıdakilerin nasıl yapıldığını öğreneceksiniz:

-   Yeni bir proje oluşturun.

-   Test (hata ayıklama) bir uygulama.

-   Bir forma onay kutuları ve düğmeler gibi temel denetimler ekleyin.

-   Düzenleri kullanarak form üzerinde denetimleri yerleştirin.

-   Ekleme **açık dosya** ve **renk** bir forma iletişim kutuları.

-   IntelliSense ve kod parçacıkları kullanarak kod yazın.

-   Olay işleyicisi yöntemleri yazın.

İşiniz bittiğinde, programınız aşağıdaki resim gibi görünecektir:

![Bu öğreticide oluşturduğunuz resim](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

Örnek tamamlanmış bir sürümünü indirmek için bkz [eksiksiz resim görüntüleyici Öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

![video bağlantısı](../data-tools/media/playvideo.gif)bu konunun video sürümü için bkz [: oluşturma Visual Basic'te resim görüntüleyici nasıl musunuz?](http://go.microsoft.com/fwlink/?LinkId=205207) veya [bunu C# içinde resim görüntüleyici: oluşturma nasıl?](http://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır. Visual C# ve Visual Basic hem de Bu öğreticide ele alınmaktadır; bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.
>
> Visual Basic için kod görmek için **VB** sekmesinde kod blokları üstündeki ve Visual C# kodunu görmek için **C#** sekmesi. Visual C++ hakkında bilgi almakla ilgileniyorsanız bkz [başlama](../ide/getting-started-with-cpp-in-visual-studio.md) ve [C++ dil Eğitmeni](http://www.cplusplus.com/doc/tutorial/).
>
> Visual C# veya Visual Basic UWP uygulamaları yazmak için bkz öğrenmekle ilgileniyorsanız [derleme UWP uygulamaları](https://developer.microsoft.com/windows/apps).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[1. adım: bir Windows Forms uygulaması projesi oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Bir Windows Forms uygulaması projesi oluşturarak başlayın.|
|[2. adım: programınızı çalıştırma](../ide/step-2-run-your-program.md)|Önceki adımda oluşturduğunuz Windows Forms uygulama programını çalıştırın.|
|[3. adım: form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md)|Yolu kullanarak formunuzun görünüşünü değiştirin **özellikleri** penceresi.|
|[4. adım: TableLayoutPanel denetimi ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Ekleme bir `TableLayoutPanel` form denetimi.|
|[5. adım: formunuza denetimler ekleme](../ide/step-5-add-controls-to-your-form.md)|Denetimleri gibi ekleme bir `PictureBox` denetimi ve bir `CheckBox` form denetimi. Formunuza düğmeler ekleyin.|
|[6. adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı olarak yeniden adlandırın.|
|[7. adım: formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Ekleme bir `OpenFileDialog` bileşeni ve bir `ColorDialog` formunuza bileşen.|
|[8. adım: bir resim düğme olayı işleyicisi Göster için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazın.|
|[9. adım: Gözden geçirme, açıklama ve kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md)|Gözden geçirin ve kodunuzu test edin. Gerektiği gibi açıklamaları ekleyin.|
|[10. adım: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Diğer düğmelerin ve IntelliSense kullanarak onay kutusu iş yapmak için kod yazın.|
|[11. adım: programınızı çalıştırma ve diğer özellikleri deneme](../ide/step-11-run-your-program-and-try-other-features.md)|Programınızı çalıştırmak ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|
