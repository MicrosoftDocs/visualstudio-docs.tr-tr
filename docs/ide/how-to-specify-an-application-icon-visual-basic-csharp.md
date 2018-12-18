---
title: 'Nasıl yapılır: uygulama simgesi (Visual Basic, C#) belirtin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8da1de87031db962ede178a742325d9206e808c3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945226"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl yapılır: uygulama simgesi (Visual Basic, C#) belirtin

`Icon` Özelliği bir proje için simge dosyasını belirtir (*.ico*) derlenmiş uygulama gösterileceği **dosya Gezgini** ve Windows görev çubuğunda.

`Icon` Özelliği, içinde erişilebilir **uygulama** bölmesinde **Proje Tasarımcısı**; projeye kaynaklar veya içerik dosyaları olarak eklenen simgeler listesini içerir.

> [!NOTE]
> Bir uygulama için simge özelliğini ayarladıktan sonra aynı zamanda ayarlayabilirsiniz `Icon` her özellik **penceresi** veya **Form** uygulamadaki. Windows Presentation Foundation (WPF) bağımsız uygulamalar için pencere simgeleri hakkında daha fazla bilgi için bkz: <xref:System.Windows.Window.Icon%2A> özelliği.

## <a name="to-specify-an-application-icon"></a>Uygulama simgesi belirtmek için

1. İçinde **Çözüm Gezgini**, proje düğümüne seçin (değil **çözüm** düğüm).

1. Menü çubuğunda seçin **proje** > **özellikleri**.

1. Zaman **Proje Tasarımcısı** görünen seçin **uygulama** sekmesi.

1. **(Visual Basic)**  &mdash;İçinde **simgesi** listesinde, bir simge seçin (*.ico*) dosyası.

    **C#**&mdash;yakınında **simgesi** listesinde, seçin  **\<Gözat... >** düğmesine tıklayın ve ardından istediğiniz simge dosyasının konumuna göz atın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)