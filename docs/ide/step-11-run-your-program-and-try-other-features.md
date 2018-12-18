---
title: '11. adım: programınızı çalıştırma ve diğer özellikleri deneme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87992bb8ab2557dbca4c8e7e3a94dd99e5de7682
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671930"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>11. adım: programınızı çalıştırma ve diğer özellikleri deneme
Programınız bitti ve çalıştırılmaya hazır. Programınızı çalıştırmak ve arka plan rengini ayarlama <xref:System.Windows.Forms.PictureBox>. Daha fazla bilgi için formun rengini değiştirerek, düğmeleri ve onay kutusunu özelleştirerek ve formun özelliklerini değiştirerek programı iyileştirmeyi deneyin.

 Örnek tamamlanmış bir sürümünü indirmek için bkz [eksiksiz resim görüntüleyici Öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

 ![video bağlantısı](../data-tools/media/playvideo.gif)bu konunun video sürümü için bkz: [öğretici 1: Visual Basic'te - Video 5 resim görüntüleyici oluşturma](http://go.microsoft.com/fwlink/?LinkId=205216) veya [öğretici 1: içinde resim görüntüleyici oluşturma C# -Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). Bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar olduğundan bu videolarda Visual Studio'nun önceki bir sürümü kullanın. Ancak, kavramlar ve yordamlar benzer şekilde Visual Studio'nun geçerli sürümünde çalışır.

## <a name="to-run-your-program-and-set-the-background-color"></a>Programınızı çalıştırmak ve arka plan rengini ayarlamak için

1.  Seçin **F5**, veya menü çubuğunda, **hata ayıklama** > **hata ayıklamayı Başlat**.

2.  Bir resmi açmadan önce seçin **arka plan rengini ayarlamak** düğmesi. **Renk** iletişim kutusu açılır.

     ![Renk iletişim kutusu](../ide/media/express_colordialog.png)
**renk** iletişim kutusu

3.  PictureBox arka plan rengini ayarlamak için bir renk seçin. Yakından bakın `backgroundButton_Click()` nasıl çalıştığını anlamanız için yöntemi.

    > [!NOTE]
    >  Resim URL'sini yapıştırarak Internet'ten yükünü **açık dosya** iletişim kutusu. Arka plan renkleriniz görünsün saydam bir arka plan görüntüsüne bulmaya çalışın.

4.  Seçin **resmi Temizle** temizlendiğinden emin olmak için düğme. Sonra programdan çıkmak **Kapat** düğmesi.

## <a name="to-try-other-features"></a>Diğer özellikleri denemek için

-   Kullanarak form ve düğmelerin rengini değiştirmek **BackColor** özelliği.

-   Düğmeleri ve onay kutusunu kullanarak özelleştirme **yazı tipi** ve **ForeColor** özellikleri.

-   Formunuzun **FormBorderStyle** ve **ControlBox** özellikleri.

-   Formunuzun kullanın **AcceptButton** ve **CancelButton** düğmeler otomatik olarak seçilir, bu nedenle, kullanıcının seçtiği özellikleri **Enter** veya **Esc** anahtarı. Programa **Dosya Aç** kullanıcı seçtiğinde bir iletişim kutusu **Enter** ve kullanıcı seçtiğinde kutuyu kapatın **Esc**.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

-   Visual Studio'da programlama hakkında daha fazla bilgi için bkz. [programlama kavramları](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

-   Visual Basic hakkında daha fazla bilgi için bkz: [Visual Basic ile uygulama geliştirme](/dotnet/visual-basic/developing-apps/index).

-   Görsel hakkında daha fazla bilgi edinmek için C#, bkz: [giriş C# dili ve .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

-   Sonraki eğitime gitmek için bkz: [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

-   Önceki öğretici adımına dönmek için bkz: [adım 10: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
