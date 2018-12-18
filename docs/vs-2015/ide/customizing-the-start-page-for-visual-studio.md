---
title: Başlangıç sayfasını özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c426ca146380ce01ec2c1f257c6da5538b941c19
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059778"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Visual Studio için Başlangıç Sayfasını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gösterildiği gibi bazı varsayılan yöntemlerle Visual Studio için başlangıç sayfasını özelleştirebilirsiniz **açık proje** iletişim kutusu veya en son yüklenen çözümü açma. Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

## <a name="customizing-the-default-start-page"></a>Varsayılan başlangıç sayfasını özelleştirme

1.  Menü çubuğunda, **Araçları**, **seçenekleri**.

2.  Genişletin **ortam**ve ardından **başlangıç**.

3.  İçinde **başlangıçta** listesinde, kullanmak istediğiniz özelleştirme için öğeyi seçin.

## <a name="show-a-custom-start-page"></a>Özel başlangıç sayfası gösterme

1.  Özel bir başlangıç sayfası yüklemek için aşağıdaki yöntemlerden birini kullanın:

    -   Buradan yükleyin [Visual Studio Galerisi](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), başka bir Web sitesi veya yerel intranet ağınızdaki bir sayfa.

        > [!NOTE]
        >  Visual Studio'nun önceki bir sürümü için hedeflenen bir sayfayı beğeniyorsanız, Visual Studio SDK kullanarak sayfayı yükseltebilirsiniz. Bkz: [nasıl yapılır: Visual Studio özel başlangıç sayfası yükseltme](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Özel başlangıç sayfası içeren .vsix dosyasını açın, kopyalayın ve başlangıç sayfası dosyalarına yapıştırın **% USERPROFILE % \My Documents\Visual Studio 2015\StartPages** bilgisayarınızda bir klasör.

    -   Visual Studio SDK yüklediyseniz kendi başlangıç sayfanızı oluşturun.

         Bkz: [oluşturarak kendi başlangıç sayfanızı](../misc/creating-your-own-start-page.md).

2.  Menü çubuğunda, **Araçları**, **seçenekleri**.

3.  Genişletin **ortam**ve ardından **başlangıç**.

4.  İçinde **başlangıç sayfasını Özelleştir** listesinde, istediğiniz sayfayı seçin.

> [!NOTE]
>  Özel başlangıç sayfasındaki bir hata Visual Studio'nun çökmesine neden olursa, Visual Studio'yu güvenli modda başlatabilir ve varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz: [safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [başlangıç sayfasının kendi oluşturma](../misc/creating-your-own-start-page.md)
