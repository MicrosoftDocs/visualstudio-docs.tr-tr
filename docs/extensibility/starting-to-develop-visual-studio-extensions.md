---
title: Visual Studio uzantıları geliştirmeye başlama | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5d6e84bc526cf597fbfd22bd36b93cd419ba0d6
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349669"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio uzantıları geliştirmeye başlama

Visual Studio uzantısı önce hiçbir zaman yazdıysanız, muhtemelen bazı sorular vardır. Biz burada en yaygın olanlarından bazıları listelediğiniz. Aradığınız bilgileri görmüyorsanız, geri bildirim düğmeleri kullanın (**bu sayfa yardımcı oldu?** ekranın alt kısmındaki), istediğiniz için isteyebilir.

> [!NOTE]
> Bu makale, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio genişletme](/visualstudio/mac/extending-visual-studio-mac).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio uzantıları geliştirme hangi yazılım gerekiyor?

Visual Studio uzantıları geliştirme için Visual Studio SDK'sı Visual Studio yanı sıra yüklemeniz gerekir. Visual Studio SDK normal kurulumunun bir parçası yükleyebilir veya daha sonra yükleyebilirsiniz. Visual Studio SDK'sını yükleme hakkında daha fazla bilgi için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio uzantıları ile ne tür bir şeyler yapabilirim?

Farklı Visual Studio uzantıları imagining için söz konusu olduğunda sky sınırı güçlendirin. Elbette, uzantıların çoğu kod yazma ile yapmak için bir şey vardır ancak, böyle olması gerekmez. Tür uzantıları oluşturabileceğinizi bazı örnekleri aşağıda verilmiştir:

- Visual Studio'da söz dizimi renklendirme, IntelliSense ve derleyici ve hata ayıklama desteği bulunmayan diller için destek

- Çekirdek genişleten üretkenlik araçları, IDE deneyimi ek şablonlar, kodu yeniden düzenleme, yeni iletişim kutuları veya araç pencereleri

- Veri tasarım ya da bulut desteği gibi senaryolar için etki alanına özel tasarımcılar

Uzantıları örnekleri için kullanıma [Visual Studio Market](https://marketplace.visualstudio.com/vs). Birçok uzantının kaynaklanan açık olan ve Market'te kendi GitHub deposunu bağlantılarını içerir.

## <a name="which-visual-studio-features-can-i-extend"></a>Hangi Visual Studio özellikleri miyim uzatabilir miyim?

Teorik olarak, Visual Studio neredeyse tüm parçası genişletebilirsiniz: menüleri, araç çubukları, komutları, windows, çözümler, projeler, düzenleyiciler ve benzeri.

Uygulamada, çoğu kişi, genişletmek istediğiniz özellikleri komutlar, menüler ve araç çubukları, windows, IntelliSense ve projeleri olduğunu bulduk. İlgili bölümlerin bağlantıları aşağıda verilmiştir:

-   [Menüler ve komutlar genişletme](../extensibility/extending-menus-and-commands.md): Visual Studio menüleri ve araç çubukları için kendi öğelerinizi ekleyin. Yeni Visual Studio işlevselliği veya kendi dış yardımcı uygulamalar başlatmak için kullanabilirsiniz. Ayrıca, menü öğeleri için özel kısayolları da sağlayabilir.

-   [Genişletme ve özelleştirme araç Windows](../extensibility/extending-and-customizing-tool-windows.md): mevcut araç pencerelerini genişletme veya kendi araç pencereleri oluşturun. Örneğin, yeni özellikler için ekleyebilirsiniz **özellikleri**, veya ek özellikler eklemek için yeni bir araç penceresi oluşturabilirsiniz.

-   [Düzenleyici ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md): Visual Studio dilleri için sağlanan IntelliSense kendi özelleştirmelerinizi eklemek veya yeni bir programlama dilleri için destek oluşturun. Yeni deyim tamamlama, öneriler ve yeni Hızlıbilgi araç ipuçlarını oluşturabilirsiniz. Ampullerle, yeniden düzenleme önerileri ekleyebilir ve yeni programlama dilleri desteklemek kodu düzeltir.

-   [Projeleri Genişletme](../extensibility/extending-projects.md)

-   [Kullanıcı Ayarlarını ve Seçeneklerini Genişletme](../extensibility/extending-user-settings-and-options.md)

-   [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)

-   [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)

-   [Visual Studio Yalıtılmış Kabuğu](../extensibility/visual-studio-isolated-shell.md)

##  <a name="BKMK_ProjectTemplate"></a> Hangi proje şablonları tarafından VSSDK sağlanır?
 İki ana tür uzantılarının VSPackages ve MEF uzantılarıdır. Genel olarak, VSPackage uzantılarına kullanın veya projeleri komutları ve araç pencerelerini genişletme uzantılar için kullanılır. MEF uzantıları genişletme veya Visual Studio Düzenleyicisi özelleştirmek için kullanılır.

 Visual C# ve Visual Basic uzantıları için menü komutlarını, araç pencereleri ve düzenleyici uzantıları oluşturduğunuz yeni öğe şablonları ile birlikte kullanabileceğiniz boş bir VSIX proje şablonu VSSDK sağlar. Paket proje şablonları, kod parçacıkları ve diğer yapıtlar Bu şablon, dağıtım diğer kullanıcılar için de kullanabilirsiniz.

 C++ için menü komutları, araç pencereleri ve özel düzenleyicilerde eklenecek kodu VSPackage sihirbaz sağlar.

 Yalıtılmış Kabuk şablonu, marka ve kendi olarak dağıtmak Visual Studio Kabuğu sürümünde bir uzantı paketi için kullanılır. Aşağıdaki konular her uzantı türü ile çalışmaya başlama işlemini gösterir:

-   Menü komutları: [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

-   Araç penceresi: [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

-   Düzenleyici uzantıları: [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   Temel VSPackages: [VSPackage içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

-   VSIX proje şablonu: [VSIX proje şablonu ile çalışmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Visual Studio gibi görünmesini uzantım nasıl alabilirim?
 Uzantı için kullanıcı arabirimini tasarlamaya yönelik harika ipuçları alın [Visual Studio kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK kod örnekleri nerede bulabilirim?
 Her biri önceki bölümde listelenen bağlantılara belirli özellikleri uygulamak nasıl gösteren adım adım izlenecek yollar vardır. Açık kaynak github'da VSSDK örnekleri bulabilirsiniz [Visual Studio örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Uzantım nasıl dağıtmak?
 Uzantınızı başka bir bilgisayara yüklemek ya da çift tıklayarak yükleme bir .vsix dosyası olarak arkadaşlarınıza gönderin. VSIX paketlerini hakkında daha fazla bilgi bulabilirsiniz [sevkiyat Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md).

 Visual Studio müşterilerine çok sayıda görünür olmasını sağlayan Visual Studio Market'te, uzantınızı da yayımlayabilirsiniz. Uzantı Marketi paketleme ilişkin bir örnek için bkz [izlenecek yol: Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Market'te yayımlamak için yapmanız gerekenler hakkında daha fazla bilgi için bkz. [Visual Studio için ürün ve](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio’yu Genişletme](/visualstudio/mac/extending-visual-studio-mac)