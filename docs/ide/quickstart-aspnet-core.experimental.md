---
title: Bir ASP.NET Core web uygulaması oluşturunC#
description: Visual Studio'da C# ve ASP.NET Core, adım adım ile basit bir Hello World web uygulaması oluşturmayı öğrenin.
ms.custom: mvc
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ab4ce9393e922dec6677d37d7679e1a400a2b5fc
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158885"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Hızlı Başlangıç: İlk ASP.NET Core web uygulamanızı oluşturmak için Visual Studio

Bu 5-10 dakikalık bir giriş Visual Studio'nun nasıl kullanılacağını, bir ASP.NET projesi şablonunu ve C# programlama dilini kullanarak basit bir "Hello World" web uygulaması oluşturacaksınız.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

### <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme

Visual Studio'yu önceden yüklediyseniz, en son sürümü çalıştırdığınızdan emin olun. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için bkz. [en son sürüme Visual Studio 2017 güncelleştirme](../install/update-visual-studio.md) sayfası.

### <a name="choose-your-theme-optional"></a>(İsteğe bağlı) temanızı seçin

Bu hızlı başlangıç öğreticisinde, koyu Tema kullanan ekran görüntüleri içerir. Koyu tema kullanmayan ancak öğrenmek istiyorsanız [Düzenleyicisi ve Visual Studio IDE'yi kişiselleştirme](quickstart-personalize-the-ide.md) öğrenmek için sayfa nasıl.

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir ASP.NET Core web uygulaması projesi oluşturacaksınız. İşte nasıl.

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.

1. Sol bölmesinde **yeni proje** iletişim kutusunda **Visual C#** ve ardından **.NET Core**. Orta bölmede seçin **ASP.NET Core Web uygulaması**. Ardından dosyanızı adlandırın `HelloWorld` ve **Tamam**.

1. İçinde **yeni ASP.NET Core Web uygulaması** iletişim kutusunda **ASP.NET Core 2.0** veya üzeri üstteki açılan menüden ve ardından **Web uygulaması**.

   > [!NOTE]
   > Görmüyorsanız **ASP.NET Core 2.0** veya daha sonra üstteki açılan menüden Visual Studio'nun en son sürümü çalıştırdığınızdan emin olun. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için bkz. [en son sürüme Visual Studio 2017 güncelleştirme](../install/update-visual-studio.md) sayfası.

   ![Visual Studio'da C# ASP.NET Core projesi oluşturma işlemini gösterir animasyonlu .gif dosyasını görüntüleyin](../ide/media/csharp-aspnet-animated-create-project.gif)

   Hemen sonra Visual Studio proje dosyanızı açar.

   > [!NOTE]
   > Görmüyorsanız **.NET Core** projesinin şablon kategorisi **açık Visual Studio yükleyicisi** sol bölmede bağlantı. (Görünen ayarlarınıza bağlı olarak, görmek için kaydırmanız gerekebilir.)
   >
   > ![Visual Studio yükleyicisi yeni proje iletişim kutusundan açın](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio Yükleyicisi'ni başlatır. Seçin **ASP.NET ve web geliştirme** iş yükü ve ardından **Değiştir**.
   >
   > ![ASP.NET iş yükü VS yükleyicisi](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Yeni iş yükünü yüklemek devam etmeden önce Visual Studio'yu kapatın gerekebilir.)

## <a name="create-and-run-the-app"></a>Oluşturma ve uygulama çalıştırma

Ardından, oluşturun ve "Hello World" web uygulamanızı çalıştırın. İşte nasıl.

1. Visual Studio içinde **Çözüm Gezgini**, genişletme **sayfaları** klasör. Ardından, **About.cshtml**.

   ![Çözüm Gezgini'nden About.cshtml dosyayı seçin](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya adında bir sayfaya karşılık gelen **hakkında** web uygulamasında, bir web tarayıcısında çalışan.

   ![Web uygulaması hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

1. Visual Studio Kod Düzenleyicisi'nde okumak için "ek bilgileri" metni değiştirme "**Merhaba Dünya!**".

1. İçinde **Çözüm Gezgini**, genişletme **About.cshtml**ve ardından **About.cshtml.cs**.

1. Okunacak "uygulama açıklaması" ileti metni değiştirme "**iletime nedir?**".

1. Seçin **IIS Express** veya basın **Ctrl**+**F5** uygulamayı çalıştırın ve bir web tarayıcısında açın.

   ![Oluşturmayı ve Visual Studio'da C# ASP.NET Core web uygulaması çalıştırmayı gösteren animasyon .gif dosyasını görüntüleyin](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Yazan bir hata iletisi alırsanız **web sunucusu için 'IIS Express' bağlanılamıyor**, veya bir SSL sertifikası ilgili bir hata iletisi Visual Studio'yu kapatın. Ardından, Visual Studio kullanarak açma **yönetici olarak çalıştır** sağ tıklayın veya bağlam menüsünde seçenek. Ardından, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında doğrulayın **hakkında** sayfa güncelleştirilmiş metni içerir.

1. Web tarayıcısını kapatın.

Bu hızlı başlangıcı tamamladığınızda Tebrikler! C#, ASP.NET Core ve Visual Studio IDE (tümleşik geliştirme ortamı) hakkında biraz öğrenilen umuyoruz.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi için şu öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [C# ve Visual Studio'da ASP.NET kullanmaya başlama](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web uygulamanızı Azure App Service'e yayımlama](..//deployment/quickstart-deploy-to-azure.md)
