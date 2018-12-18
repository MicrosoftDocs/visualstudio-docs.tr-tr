---
title: "Nasıl yapılır: IDE'de gezinme | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea104d08216a4ef7bdb07fc42b5a22eb5352d757
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049625"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Nasıl Yapılır: Visual Studio IDE’de Gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tümleşik geliştirme ortamı (IDE) penceresi penceresinin hareket etmenize izin vermek için tasarlanmış ve dosyaya tercih ya da proje gereksinimlerinize bağlı olarak birkaç farklı yolla olmuştur. Düzenleyicide açık dosyalar arasında geçiş yapmak veya tüm etkin araç pencerelerini IDE içinde dolaşma seçebilirsiniz. Herhangi bir dosya Aç bakılmaksızın, son erişilme sırası düzenleyicisinde için doğrudan geçiş yapabilirsiniz. Bu özellikler, IDE içinde çalışırken üretkenliğinizi artırmaya yardımcı olabilir.

> [!NOTE]
>  İletişim kutuları, adları ve konumları gördüğünüz gibi menü komutlarının Seçenekleri Yardımı'nda, etkin ayarlarınıza ve sürüm bağlı olarak açıklanan nedir öğesinden farklı olabilir. Bu Yardım sayfası ile yazılmıştır **genel geliştirme ayarları** unutmayın. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Klavye Kısayolları
 Visual Studio neredeyse tüm menü komutu bir klavye kısayolu vardır. Ayrıca, kendi özel kısayolları da oluşturabilirsiniz. Daha fazla bilgi için [tanımlama ve özelleştirme klavye kısayolları](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Düzenleyicideki dosyalar arasında gezinme
 Düzenleyicide açık dosyaları arasında gezinmek için çeşitli yöntemler kullanabilirsiniz. Hangi erişim, şu anda açık olan herhangi bir dosya veya sık kullanılan dosyaları için sekmesinde de bunlar her zaman görünür, böylece hızla bulmak için haldeyken IDE Gezgini'ni kullanın sıraya göre dosyalar arasında taşıyabilirsiniz.

 Navigate geri ve İleri gidin, bunlar erişilen, sipariş çok geri ve İleri görüntüleme geçmişiniz Microsoft Internet Explorer için yaptığınız gibi temel düzenleyicide açık olan dosyaları arasında geçiş.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Kullanım sırasına göre açık dosyalar arasında taşımak için

- Açık belgeleri en son dokunulan sırada etkinleştirmek için CTRL + eksi işareti'ya basın.

- Ters sırada açık belgeler etkinleştirmek için CTRL + SHIFT + eksi işareti'ya basın.

  > [!NOTE]
  >  **Geriye doğru gidin** ve **Navigate Forward** üzerinde bulunabilir **görünümü** menüsü.

  Belirli bir dosyayı dosya son erişildiği zaman bağımsız olarak düzenleyicide açık geçebilirsiniz kullanarak **haldeyken IDE Gezgini'ni**, **etkin dosyaların** düzenleyicisinde, liste veya **Windows** iletişim kutusu.

  **Haldeyken IDE Gezgini'ni** Windows uygulama değiştirici gibi çalışır. Menüleri kullanılamaz ve yalnızca kısayol tuşu kullanılarak erişilebilir. İki komutlardan birini erişmek için kullanabileceğiniz **haldeyken IDE Gezgini'ni** (arasında geçiş yapmak istediğiniz düzene bağlı olarak, dosyalar arasında geçiş yapmak için aşağıda).

  ![Visual Studio IDE Gezgini](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` en son erişilen dosyanın taşımanızı sağlar ve `Window.NextDocumentWindowNav` ters sırada taşımanızı sağlar. Genel Geliştirme Ayarları atar CTRL + SHIFT + TAB `Window.PreviousDocumentWindowNav` ve CTRL + TAB `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Kullanmakta olduğunuz bir ayarlar bileşimi bu komutuna atanmış kısayol tuş bileşimi zaten yoksa, kendi özel komut kullanarak atayabilirsiniz **klavye** sayfasının **seçenekleri** iletişim bir kutu. Daha fazla bilgi için [tanımlama ve özelleştirme klavye kısayolları](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Düzenleyicideki belirli dosyalar geçmek için

-   Görüntülemek için CTRL + TAB tuşuna basın **haldeyken IDE Gezgini'ni**. CTRL tuşunu basılı tutun ve sürekli olarak geçiş yapmak istediğiniz dosyayı seçin kadar SEKME tuşuna basın.

    > [!TIP]
    >  Hangi geçtiğiniz sırasını tersine çevirmek için **etkin dosyaların** listesinde, CTRL + SHIFT tuşlarını basılı tutun ve SEKME tuşuna basın.

     \- veya -

-   Düzenleyici sağ alt köşesinde, seçin **etkin dosyaların** düğmesini ve ardından geçmek için listeden bir dosya seçin.

     \- veya -

-   Menü çubuğunda, **penceresi**, **Windows**.

-   Listesinde, görüntülemek ve ardından istediğiniz dosyayı seçin **etkinleştirme**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>IDE'de araç Windows arasında gezinme
 **Haldeyken IDE Gezgini'ni** de sahip olduğunuz aracı windows döngüsü sağlar IDE'de açın. İki komutlardan birini erişmek için kullanabileceğiniz **haldeyken IDE Gezgini'ni** arasında geçiş yapmak istediğiniz düzene bağlı olarak, araç pencereleri arasında geçiş yapmak için. `Window.PreviousToolWindowNav` en son erişilen dosyanın taşımanızı sağlar ve `Window.NextToolWindowNav` ters sırada taşımanızı sağlar. Genel Geliştirme Ayarları atar SHIFT + ALT + F7 `Window.PreviousDocumentWindowNav` ve ALT + F7 `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Kullanmakta olduğunuz bir ayarlar bileşimi bu komutuna atanmış kısayol tuş bileşimi zaten yoksa, kendi özel komut kullanarak atayabilirsiniz **klavye** sayfasının **seçenekleri** iletişim bir kutu. Daha fazla bilgi için [tanımlama ve özelleştirme klavye kısayolları](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE'nin belirli araç penceresine geçin

-   Görüntülemek için ALT + F7'ye basın **haldeyken IDE Gezgini'ni**. ALT tuşunu basılı tutun ve F7'ye geçiş yapmak istediğiniz pencereyi seçene kadar tekrar tekrar basın.

    > [!TIP]
    >  Hangi geçtiğiniz sırasını tersine çevirmek için **etkin aracı Windows** listesinde, SHIFT + ALT tuşları basılı tutun ve F7'ye basın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md) [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md)
