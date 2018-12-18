---
title: Hello World uzantısı Öğreticisi | Microsoft Docs
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2122a98778372690990a75269be2f3087653678
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349471"
---
# <a name="create-your-first-extension-hello-world"></a>İlk uzantınızı oluşturun: Hello World

Bu Hello World örnek, Visual Studio için ilk uzantınızı oluşturmada size yol gösterir. Bu öğreticide Visual Studio için yeni bir komut eklerseniz gösterilmektedir.

Bu süreçte şunları öğreneceksiniz nasıl yapılır:

* **[Bir genişletilebilirlik projesi oluşturma](#create-an-extensibility-project)**
* **[Özel komut ekleme](#add-a-custom-command)**
* **[Kaynak kodu değiştirin](#modify-the-source-code)**
* **[Çalıştırın](#run-it)**

Bu örnekte, Visual C# özel menü düğmesi "Deyin. Hello World!" adlı eklemek için kullanacağınız şöyle görünür:

![Hello World komutu](media/hello-world-say-hello-world.png)

> [!NOTE]
> Bu makale, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio genişletilebilirlik kılavuzda](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce yüklediğinizden emin olun **Visual Studio uzantısı geliştirme** ihtiyacınız ve örnek kod VSIX şablonu içeren iş yükü.

> [!NOTE]
> Visual Studio (Community, Professional veya Enterprise) Visual Studio genişletilebilirlik projesi oluşturmak için herhangi bir sürümünü kullanabilirsiniz.

## <a name="create-an-extensibility-project"></a>Bir genişletilebilirlik projesi oluşturma

Adım 1. Gelen **dosya** menüsünü tıklatın **yeni proje**. Ekranın alt kısmında, projenizin adını girin.

Adım 2. Gelen **şablonları** menüsünde tıklatın **Visual C#**, tıklayın **genişletilebilirlik**ve ardından **VSIX projesi**.

![Yeni Proje](media/hello-world-new-project.png)

Başlarken sayfası ve bazı örnek kaynaklar görmelisiniz.

Bu öğreticide bırakın ve kendisine döndürülmesini gerekiyorsa, yeni HelloWorld projeniz bulabileceğiniz **başlangıç sayfası** içinde **son** bölümü.

## <a name="add-a-custom-command"></a>Özel komut ekleme

Adım 1. Bildirim seçerseniz, hangi seçenekleri örneği, meta verileri, açıklama ve sürümü için ayarlarken görebilirsiniz.

Adım 2. ' % S'projesi (çözümü değil) sağ tıklayın. Bağlam menüsünde **Ekle**ve ardından **yeni öğe**.

Adım 3. Seçin **genişletilebilirlik** bölümüne ve ardından **özel komut**.

4. adımı. İçinde **adı** altındaki alan, bu örneği için bir ad verin *Command.cs*.

![özel komut](media/hello-world-custom-command.png)

Yeni komutunuzun listelenen **Çözüm Gezgini** altında **kaynakları** dal. Komutunuz resmi değiştirmek istiyorsanız, PNG ve ICO dosyaları gibi ilgili diğer dosyaları burada bulabilirsiniz budur.

## <a name="modify-the-source-code"></a>Kaynak kodu değiştirin

Bu noktada, eklediğiniz düğmeyi oldukça geneldir. VSCT dosyası ve CS dosyası değişiklik yapmak istiyorsanız değiştirmek zorunda kalırsınız.

* VSCT Burada, Komutlarınızın yeniden adlandırma, yapabilir Visual Studio komut sistemde nereye tanımlamak dosyasıdır. VSCT dosya keşfederken, kod denetimlerin her hangi bir bölümde anlatılmaktadır açıklamalı kod fark edeceksiniz.

* Tıklama işleyicisi gibi eylemler burada tanımlarsınız CS dosyasıdır.

Adım 1. İçinde **Çözüm Gezgini**, yeni komutunuz için VSCT dosyası bulunamıyor. Bu durumda, çağrılacak *CommandPackage.vsct*.

![komut paket vsct](media/hello-world-command-package-vsct.png)

Adım 2. Değişiklik `ButtonText` parametresi `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Adım 3. Geri Git **Çözüm Gezgini** ve bulma *Command.cs* dosya. Değiştirme dizesi `message` komutu için `string.Format(..)` için `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Her dosya için değişikliklerinizi kaydettiğinizden emin olun.

## <a name="run-it"></a>Çalıştırın

Bu gibi durumlarda, kaynak kodu artık Visual Studio deneysel örneğinde çalıştırabilirsiniz.

Adım 1. Tıklayın **Başlat** araç. Bu, projeniz derlenir ve Visual Studio adlı yeni bir örneğini başlatarak, hata ayıklayıcıyı başlatır **deneysel örneğinde**.

Sözcükleri göreceğiniz **deneysel örneğinde** Visual Studio başlık çubuğunda.

![deneysel örneği başlık çubuğu](media/hello-world-exp-instance.png)

Adım 2. Üzerinde **Araçları** menüsü **deneysel örneğinde**, tıklayın **Say Hello World!**.

![Son Sonuç](media/hello-world-final-result.png)

Yeni özel komuttan bir çıktı görmeniz gerekir, bu durumda ekranın ortasında iletişim sağlayan **Merhaba Dünya!** İleti.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio genişletilebilirliği ile çalışmanın temel bilgileri artık bildiğinize göre İşte burada daha fazla bilgi edinebilirsiniz:

* [Visual Studio uzantılarını geliştirmeye başlamak](starting-to-develop-visual-studio-extensions.md) -örnekler, öğreticiler. ve uzantınızı yayımlama
* [Visual Studio 2017 SDK'daki yenilikler](what-s-new-in-the-visual-studio-2017-sdk.md) -Visual Studio 2017'de yeni genişletilebilirlik özellikleri
* [Visual Studio SDK içinde](internals/inside-the-visual-studio-sdk.md) -Visual Studio genişletilebilirlik ayrıntılarını öğrenin