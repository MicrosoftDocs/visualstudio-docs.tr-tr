---
title: Visual Studio'yu ilk kez oluşturma kullanarak C# konsol uygulaması
titleSuffix: ''
description: Visual Studio'da C#, adım adım ile basit bir Hello World konsol uygulaması oluşturmayı öğrenin.
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a1d7b165466f686549273394c204e4ab31c06b46
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158612"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Hızlı Başlangıç: Visual Studio'yu ilk kez oluşturma kullanarak C# konsol uygulaması

Bu 5-10 dakikalık bir giriş Visual Studio tümleşik geliştirme ortamı (IDE), konsolda çalışan basit bir C# uygulaması oluşturacaksınız.

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulaması projesi oluşturacaksınız. Proje türü bile herhangi bir şey ekledik önce ihtiyacınız olacak tüm şablon dosyaları ile birlikte gelir!

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.

3. İçinde **yeni proje** iletişim kutusunun sol bölmesinde, **C#** ve ardından **.NET Core**. Orta bölmede seçin **konsol uygulaması (.NET Core)**. Ardından Projeyi adlandırın *HelloWorld*.

   ![Konsol uygulaması (.NET Core) proje şablonunu yeni proje iletişim kutusunda Visual Studio IDE](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Görmüyorsanız **konsol uygulaması (.NET Core)** projesinin şablon **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu.

   ![Yeni Proje iletişim kutusundan açık Visual Studio yükleyicisi bağlantıyı seçin](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET Core çoklu platform geliştirme** iş yükü ve ardından **Değiştir**.

     ![.NET core çoklu platform geliştirme iş yükünü Visual Studio yükleyicisi](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Uygulama oluşturma

C# projesi şablonu seçin ve projenizi adlandırın sonra Visual Studio sizin için basit bir "Hello World" uygulaması oluşturur. 

(Bunu yapmak için çağrı <xref:System.Console.WriteLine%2A> "Hello World!" sabit dizesini görüntülemek için yöntemi Konsol penceresinde.)

   ![Şablondan varsayılan Merhaba Dünya kodu görüntüleme](../ide/media/csharp-console-helloworld-template.png)

Basarsanız **F5**, programın hata ayıklama modunda çalıştırabilir. Ancak, konsol penceresinde kapatılmadan önce yalnızca bir süre görünür olur.

(Çünkü böyle `Main` yöntemi, tek bir deyim yürütüldükten sonra ve uygulama sona şekilde sonlandırır.)

### <a name="add-some-code"></a>Kod ekleyin

Tuşuna kadar konsol penceresini kapatmaz, böylece uygulamayı duraklatmak için biraz kod ekleyelim **ENTER**.

1. Çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine%2A> yöntemi:

   ```csharp
   Console.ReadLine();
   ```

1. Bu kod Düzenleyicisi'nde şuna benzer olduğunu doğrulayın:

   ![Merhaba Dünya uygulaması duraklatmak için kod ekleyin](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Seçin **HelloWorld** uygulamayı hata ayıklama modunda çalıştırmak için araç çubuğunda. (Ya da basabilirsiniz **F5**.)

   ![Araç çubuğunda uygulamayı çalıştırmak için Hello World düğmesini seçin](../ide/media/csharp-console-hello-world-button.png)

1. Uygulamanız konsol penceresinde görüntüleyin.

   ![Konsol penceresi gösteren Merhaba Dünya!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Uygulamayı kapatın

1. Tuşuna **ENTER** konsol penceresini kapatın.

1. Kapat **çıkış** Visual Studio'daki bölmesi.

   ![Visual Studio çıktı bölmesini kapatın](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio’yu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıcı tamamladığınızda Tebrikler! C# ve Visual Studio IDE hakkında biraz öğrenilen umuyoruz. Daha fazla bilgi için şu öğretici ile devam edin.

> [!div class="nextstepaction"]
> [Visual Studio'da C# konsol uygulaması ile çalışmaya başlama](tutorial-csharp-console.md)
