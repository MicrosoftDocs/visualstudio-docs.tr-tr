---
title: İlk C# konsol uygulamanızı oluşturmak için Visual Studio 'Yu kullanma
titleSuffix: ''
description: Visual Studio 'da C# ile adım adım bir basit Merhaba Dünya konsol uygulaması oluşturmayı öğrenin.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: e3c6646fca0f0b20f7fb5d5d018c297d1ece920d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945558"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Hızlı başlangıç: ilk C# konsol uygulamanızı oluşturmak için Visual Studio 'Yu kullanma

Visual Studio tümleşik geliştirme ortamına (IDE) bu 5-10 dakikalık bir giriş içinde, konsolunda çalışan basit bir C# uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

3. Sol bölmedeki **Yeni proje** iletişim kutusunda **C#**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından projeyi *HelloWorld* olarak adlandırın.

   ![Visual Studio IDE 'de yeni proje iletişim kutusundaki konsol uygulaması (.NET Core) proje şablonu](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     **Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin.

   ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi Aç bağlantısını seçin](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresi](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil listesinden **C#** öğesini seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması için C# şablonunu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol uygulaması (.NET Core)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Sonra, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio yeni projenizi açar.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

::: moniker range="vs-2017"

C# proje şablonunuzu seçip projenizi adlandırın, Visual Studio sizin için basit bir "Merhaba Dünya" uygulaması oluşturur.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio, projenizde varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end

(Bunu yapmak için, <xref:System.Console.WriteLine%2A> "Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağırır. Konsol penceresinde.)

   ![Şablondan varsayılan Merhaba Dünya kodunu görüntüleme](../ide/media/csharp-console-helloworld-template.png)

**F5** tuşuna basarsanız, programı hata ayıklama modunda çalıştırabilirsiniz. Ancak, konsol penceresi kapanmadan önce yalnızca bir süre görünür.

(Bu davranış, `Main` yöntemi tek ifadesinin yürütüldükten sonra sonlandırdığı ve bu nedenle uygulama sona erdiğinde oluşur.)

### <a name="add-some-code"></a>Kod ekleme

Uygulamayı duraklatmak için, **ENTER** tuşuna basarak konsol penceresinin kapanmaması için bazı kodlar ekleyelim.

1. Yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine%2A> :

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde şöyle göründüğünü doğrulayın:

   ![Merhaba Dünya uygulamasını duraklatmak için kod ekleme](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı hata ayıklama modunda çalıştırmak için araç çubuğunda **HelloWorld** düğmesini seçin. (Veya **F5** tuşuna basabilirsiniz.)

   ![Uygulamayı araç çubuğundan çalıştırmak için Merhaba Dünya düğmesini seçin](../ide/media/csharp-console-hello-world-button.png)

1. Uygulamanızı konsol penceresinde görüntüleyin.

   ![Merhaba Dünya gösteren konsol penceresi!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Uygulamayı kapat

1. Konsol penceresini kapatmak için **ENTER** tuşuna basın.

1. Visual Studio 'da **Çıkış** bölmesini kapatın.

   ![Visual Studio 'da çıkış bölmesini kapatma](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio’yu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! C# ve Visual Studio IDE hakkında biraz bilgi edindiniz. Daha fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Visual Studio 'da C# konsol uygulaması ile çalışmaya başlama](../get-started/csharp/tutorial-console.md)
