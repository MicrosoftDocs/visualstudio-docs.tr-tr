---
title: Oluşturma bir Windows Forms uygulaması Visual Basic ile
description: Visual Basic, adım adım ile Visual Studio'da bir Windows Forms uygulaması oluşturmayı öğrenin.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 81b44e7053b820e625b5ad61d6e537c95cbf9c03
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159639"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Bir Windows oluşturma Visual Basic ile Visual Studio'da Forms uygulaması

Bu kısa giriş Visual Studio tümleşik geliştirme ortamı (IDE) için bir Windows tabanlı kullanıcı arabirimi (UI) olan basit bir Visual Basic uygulama oluşturacaksınız.

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, Visual Basic uygulama projesi oluşturacaksınız. Proje türü bile herhangi bir şey ekledik önce ihtiyacınız olacak tüm şablon dosyaları ile birlikte gelir.

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.

3. İçinde **yeni proje** iletişim kutusunun sol bölmesinde, **Visual Basic**ve ardından **Windows Masaüstü**. Orta bölmede seçin **Windows Forms uygulaması (.NET Framework)**. Dosya adı `HelloWorld`.

     Görmüyorsanız **Windows Forms uygulaması (.NET Framework)** proje şablonu, / İptal **yeni proje** iletişim kutusu ve üst menü çubuğundan seçin **Araçları**  >  **Araçları ve özellikleri Al**. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** iş yükü, ardından **Değiştir**.

     ![Visual Studio Yükleyicisi'nde .NET core iş yükü](../ide/media/install-dot-net-desktop-env.png)

## <a name="create-the-application"></a>Uygulama oluşturma

Visual Basic projesi şablonu seçin ve dosyanızın adı sonra Visual Studio sizin için bir form açılır. Bir Windows kullanıcı arabirimi biçimidir. "Hello World" uygulaması formu için denetimler ekleyerek oluşturacağız ve ardından size uygulamayı çalıştıracaksınız.

### <a name="add-a-button-to-the-form"></a>Forma bir düğme ekleyin

1. Tıklayın **araç kutusu** araç kutusu çıkış penceresini açmak için.

     ![Araç araç kutusu penceresini açmak için tıklayın](../ide/media/vb-toolbox-toolwindow.png)

     (Görmüyorsanız **araç kutusu** çıkış seçeneği açabilirsiniz, menü çubuğundan. Bunu yapmak için tıklatın **görünümü** > **araç kutusu**. Veya basın **Ctrl**+**Alt**+**X**.)

2. Tıklayın **PIN** simgesini yerleştirmek için **araç kutusu** penceresi.

     ![Araç kutusu penceresini IDE sabitlemek için Raptiye simgesine tıklayın](../ide/media/vb-pin-the-toolbox-window.png)
3. Tıklayın **düğmesi** denetlemek ve ardından form üzerine sürükleyin.

     ![Forma bir düğme ekleyin](../ide/media/vb-add-a-button-to-form1.png)

4. İçinde **Görünüm** bölümünü **özellikleri** penceresinde, tür `Click this`ve tuşuna **Enter**.

     ![Düğmeyi form üzerinde metin ekleme](../ide/media/vb-button-control-text.png)

     (Görmüyorsanız **özellikleri** penceresinde açabilirsiniz, menü çubuğundan. Bunu yapmak için tıklatın **görünümü** > **Özellikler penceresi**. Veya basın **F4**.)

5. İçinde **tasarım** bölümünü **özellikleri** penceresinde adını değiştirmek **Button1** için `btnClickThis`ve tuşuna **Enter**.

     ![Düğmeyi form üzerinde bir işlev ekleme](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Forma bir etiket ekleyin

Bir eylem oluşturmak için bir düğme denetimi ekledik, metni göndermek için bir etiket denetimi ekleyelim.

1. Seçin **etiket** denetimi **araç kutusu** pencere, form üzerine sürükleyin ve altındaki açılan **tıklatın** düğmesi.

2. İçinde **tasarım** bölümünü **özellikleri** penceresinde adını değiştirmek **Label1** için `lblHelloWorld`ve tuşuna **Enter**.

### <a name="add-code-to-the-form"></a>Forma kod ekleyin

1. İçinde **Form1.vb &#91;tasarım&#93;**  penceresinde çift **tıklatın** açmak için düğmeyi **Form1.vb** penceresi.

      (Alternatif olarak, genişletebilirsiniz **Form1.vb** içinde **Çözüm Gezgini**ve ardından **Form1**.)

2. İçinde **Form1.vb** penceresi, arasında **Private Sub** satır ve **End Sub** satır yazın veya yapıştırın `lblHelloWorld.Text = "Hello World!"`.

     ![Forma kod ekleyin](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırın

1. Tıklayın **Başlat** uygulamayı çalıştırmak için düğme.

     ![Uygulamayı çalıştırıp hata ayıklama Başlat'a tıklayın](../ide/media/vb-click-start-hello-world.png)

   Birden fazla işlem gerçekleşir. Visual Studio IDE'de **tanılama araçları** penceresi açılır ve bir **çıkış** penceresi açılır, çok. Ancak IDE dışında bir **Form1** iletişim kutusu görüntülenir. Dahil edilir, **tıklatın** düğme ve metin bildiren **Label1**.

2. Tıklayın **tıklatın** düğmesine **Form1** iletişim kutusu. Dikkat **Label1** metin değişiklikleri **Merhaba Dünya!**.

    ![Label1 metin içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

Bu hızlı başlangıcı tamamladığınızda Tebrikler! Visual Basic ve Visual Studio IDE hakkında biraz öğrenilen umuyoruz. Daha kapsamlı anlamak için delve istiyorsanız, Lütfen bir öğreticide ile devam **öğreticiler** İçindekiler bölümünde.

## <a name="see-also"></a>Ayrıca bkz.

* [Hızlı Başlangıç: Visual Basic ile Visual Studio'da konsol uygulaması oluşturma](quickstart-visual-basic-console.md)
* [Visual Basic IntelliSense hakkında daha fazla bilgi edinin](visual-basic-specific-intellisense.md)
