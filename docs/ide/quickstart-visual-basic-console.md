---
title: İlk Konsol uygulamanızı Visual Basic ile oluşturma
description: Visual Basic, adım adım ile Visual Studio'da basit bir Hello World konsol uygulaması oluşturmayı öğrenin.
ms.date: 12/10/2017
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.technology: vs-acquisition
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 67a990b98b385cacab89bfa8270d8409f9e9aa5f
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159613"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Hızlı Başlangıç: Visual Basic ile Visual Studio'da ilk Konsol uygulamanızı oluşturma

Bu 5-10 dakikalık bir giriş Visual Studio tümleşik geliştirme ortamı (IDE), konsolda çalışan basit bir Visual Basic uygulaması oluşturacaksınız.

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, Visual Basic uygulama projesi oluşturacaksınız. Proje türü bile herhangi bir şey ekledik önce ihtiyacınız olacak tüm şablon dosyaları ile birlikte gelir!

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.

3. İçinde **yeni proje** iletişim kutusunun sol bölmesinde, **Visual Basic**ve ardından **.NET Core**. Orta bölmede seçin **konsol uygulaması (.NET Core)**. Ardından Projeyi adlandırın *HelloWorld*.

   ![Konsol uygulaması (.NET Core) proje şablonunu yeni proje iletişim kutusunda Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Görmüyorsanız **konsol uygulaması (.NET Core)** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu.

   ![Yeni Proje iletişim kutusundan açık Visual Studio yükleyicisi bağlantısına tıklayın](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET Core çoklu platform geliştirme** iş yükü ve ardından **Değiştir**.

     ![.NET core çoklu platform geliştirme iş yükünü Visual Studio yükleyicisi](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Uygulama oluşturma

Visual Basic projesi şablonu seçin ve projenizi adlandırın sonra Visual Studio sizin için basit bir "Hello World" uygulaması oluşturur. Çağrı <xref:System.Console.WriteLine%2A> "Hello World!" sabit dizesini görüntülemek için yöntemi Konsol penceresinde.

![Şablondan varsayılan Merhaba Dünya kodu görüntüleme](../ide/media/vb-console-helloworld-template.png)

Tıklarsanız **HelloWorld** düğmesi IDE program hata ayıklama modunda çalıştırabilirsiniz.

  ![Programın hata ayıklama modunda çalıştırmak için Merhaba Dünya düğmesine tıklayın](../ide/media/vb-console-hello-world-button.png)

Bunu yaptığınızda, konsol penceresinde kapatılmadan önce yalnızca bir süre için görülebilir. Çünkü böyle `Main` yöntemi, tek bir deyim yürütüldükten sonra ve uygulama sona şekilde sonlandırır.

### <a name="add-some-code"></a>Kod ekleyin

Uygulamayı duraklatmak ve ardından kullanıcı girdisi isteyin biraz kod ekleyelim.

1. Çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine%2A> yöntemi:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Bir tuşa basın kadar bu program duraklatılır.

2. Menü çubuğunda, seçin **derleme** > **Çözümü Derle**.

   Bu, just-in-time (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Tıklayın **HelloWorld** araç çubuğunda.

   ![Araç çubuğundan programı çalıştırmak için Merhaba Dünya düğmesine tıklayın](../ide/media/vb-console-hello-world-button.png)

2. Konsol penceresini kapatmak için herhangi bir tuşa basın.

   ![Konsol penceresinde Hello World gösteren ve devam etmek için herhangi bir tuşa basın](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıcı tamamladığınızda Tebrikler! Visual Basic ve Visual Studio IDE hakkında biraz öğrenilen umuyoruz. Daha fazla bilgi için şu öğreticiyle devam edin.

> [!div class="nextstepaction"]
> [Visual Studio'da Visual Basic ile çalışmaya başlama](tutorial-visual-basic-console.md)
