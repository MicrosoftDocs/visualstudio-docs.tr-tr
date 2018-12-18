---
title: 'Nasıl yapılır: özel başlangıç sayfası yükseltme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: d5750b620003053ce6af4dd9df38784f77a46200
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062725"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Nasıl yapılır: Visual Studio özel başlangıç sayfası yükseltme
Visual Studio 2010 yükseltebilir veya Visual Studio 2012 özel başlangıç sayfasına Visual Studio 2015 için aşağıda listelenen adımları izleyin.

> [!WARNING]
>  Bu yordamda yükseltilmiş özel başlangıç sayfası ile oluşturulan hesaptır [özel başlangıç sayfası](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) şablonunda Visual Studio Galerisi. Başlangıç sayfanızı yükseltilmesi gereken diğer özelliklerini olabilir.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Özel başlangıç sayfası, Visual Studio 2015'e yükseltmek için

1.  Visual Studio 2015 ve Visual Studio 2015 SDK yüklü olduğundan emin olun. VSSDK dan indirebileceğiniz [Microsoft Visual Studio 2013 SDK'sı](http://go.microsoft.com/?linkid=9863867).

2.  Özel şablon projenizi açın. Yükseltilecek projedir bildiren bir ileti görürsünüz. Tıklayın **Tamam** ve yükseltmenin tamamlanması için bekleyin.

3.  Başlangıç sayfası proje hem denetimi projesi için proje özelliklerinde, hedef Framework'ü en az olduğundan emin olun. .NET Framework 4.5.

4.  Başlangıç sayfası proje için proje özellikleri hata ayıklama kategorisinde devenv.exe Visual Studio 2015 sürümüne yolunu ayarlayın.

5.  Her iki proje için proje başvuruları, Microsoft.VisualStudio.Shell.11.0 yönelik başvuruları kaldırmanız ve Microsoft.VisualStudio.Shell.14.0 başvurular ekleyin.

6.  StartPage.xaml ile XML Düzenleyicisi'ni açın ve aşağıdaki değişiklikleri yapın:

    1.  Ad alanlarını güncelleştirin. Aşağıdaki satırları değiştirin:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         şu şekilde:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7.  MyControl.xaml açın ve ad alanı başvurusu `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` için `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .