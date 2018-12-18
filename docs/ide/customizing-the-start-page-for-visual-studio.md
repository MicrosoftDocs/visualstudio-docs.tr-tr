---
title: Özel başlangıç sayfası yüklemek veya başlangıç öğesini değiştirin
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8f09302a459e31406d69596d43b5c39a67c8268
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064053"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Visual Studio için başlangıç sayfasını özelleştirme

Visual Studio için başlangıç deneyimi gösterildiği gibi birkaç farklı yolla özelleştirebileceğiniz **açık proje** iletişim kutusu veya en son yüklenen çözümü açma. Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

## <a name="to-change-the-startup-item"></a>Başlangıç öğesini değiştirmek için

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

1. Genişletin **ortam**ve ardından **başlangıç**.

1. İçinde **başlangıçta** listesinde, Visual Studio'yu başlattıktan sonra görüntülenecek öğeyi seçin.

## <a name="to-show-a-custom-start-page"></a>Özel başlangıç sayfası göstermek için

Yapabilecekleriniz [kendi özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md) Visual Studio SDK'sını kullanarak veya bir başkası zaten oluşturduğu kullanın. Örneğin, özel başlangıç sayfalarda bulabilirsiniz [Visual Studio Market](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Özel başlangıç sayfası yüklemek için açın *.vsix* dosyası veya kopyalayın ve başlangıç sayfası dosyalarına yapıştırın *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* bilgisayarınızda bir klasör.

### <a name="to-select-which-custom-start-page-to-display"></a>Görüntülenecek hangi özel başlangıç sayfası seçin

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

1. Genişletin **ortam**ve ardından **başlangıç**.

1. İçinde **başlangıç sayfasını Özelleştir** listesinde, istediğiniz sayfayı seçin.

> [!NOTE]
> Özel başlangıç sayfasındaki bir hata Visual Studio'nun çökmesine neden olursa, Visual Studio'yu güvenli modda başlatabilir ve varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz: [safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)