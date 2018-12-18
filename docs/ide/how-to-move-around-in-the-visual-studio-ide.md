---
title: Nasıl IDE'de gezinme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdfae0808ff5daa10f8faa621e6af293543bce66
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060258"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Nasıl yapılır: Visual Studio IDE'de gezinme

Tümleşik geliştirme ortamı (IDE) penceresi penceresinin hareket etmenize izin vermek için tasarlanmış ve dosyaya tercih ya da proje gereksinimlerinize bağlı olarak birkaç farklı yolla olmuştur. Düzenleyicide açık dosyalar arasında geçiş yapmak veya tüm etkin araç pencerelerini IDE içinde dolaşma seçebilirsiniz. Herhangi bir dosya Aç bakılmaksızın, son erişilme sırası düzenleyicisinde için doğrudan geçiş yapabilirsiniz. Bu özellikler, IDE içinde çalışırken üretkenliğinizi artırmaya yardımcı olabilir.

> [!NOTE]
> İletişim kutularında seçenekleri ve adları ve konumları gördüğünüz gibi menü komutları, etkin ayarlarınıza ve sürüm bağlı olarak bu makaledeki açıklanana öğesinden farklı olabilir. Bu makale ile yazılmış **genel** ayarları unutmayın. Ayarlarınızı, örneğin değiştirileceğini **genel** veya **Visual C++** ayarları seçebilirsiniz **Araçları** > **içeri ve dışarı aktarma ayarları**ve ardından **tüm ayarları Sıfırla**.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio neredeyse tüm menü komutu bir klavye kısayolu vardır. Ayrıca, kendi özel kısayolları da oluşturabilirsiniz. Daha fazla bilgi için [tanımlayın ve klavye kısayollarını özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Düzenleyicideki dosyalar gezinme

Düzenleyicide açık dosyaları arasında gezinmek için çeşitli yöntemler kullanabilirsiniz. Hangi erişim, şu anda açık olan herhangi bir dosya veya sık kullanılan dosyaları için sekmesinde de bunlar her zaman görünür, böylece hızla bulmak için haldeyken IDE Gezgini'ni kullanın sıraya göre dosyalar arasında taşıyabilirsiniz.

Geriye doğru gidin ve erişimin sağlandığı ölçütüne göre düzenleyicide açık olan dosyaları ileriye doğru döngü gezinin, çok arka ve gibi Microsoft Internet Explorer geçmişinizi görüntülerken İleri yapın.

### <a name="to-move-through-open-files-in-order-of-use"></a>Kullanım sırasına göre açık dosyalar arasında taşımak için

-   Açık belgeler kullanıcılar en son dokunulan sırada etkinleştirmek için basın **Ctrl**+**-**.

-   Ters sırada açık belgeler etkinleştirmek için basın **Ctrl**+**Shift**+**-**.

    > [!NOTE]
    > **Geriye doğru gidin** ve **Navigate Forward** üzerinde bulunabilir **görünümü** menüsü.

Belirli bir dosyayı dosya son erişildiği zaman bağımsız olarak düzenleyicide açık geçebilirsiniz kullanarak **haldeyken IDE Gezgini'ni**, **etkin dosyaların** düzenleyicisinde, liste veya **Windows** iletişim kutusu.

**Haldeyken IDE Gezgini'ni** Windows uygulama değiştirici gibi çalışır. Menüleri kullanılamaz ve yalnızca kısayol tuşu kullanılarak erişilebilir. İki komutlardan birini erişmek için kullanabileceğiniz **haldeyken IDE Gezgini'ni** (arasında geçiş yapmak istediğiniz düzene bağlı olarak, dosyalar arasında geçiş yapmak için aşağıda).

![Visual Studio IDE Gezgini](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` en son erişilen dosyanın taşımanızı sağlar ve `Window.NextDocumentWindowNav` ters sırada taşımanızı sağlar. **Genel Geliştirme Ayarları** atar **Shift**+**Alt**+**F7** için `Window.PreviousDocumentWindowNav` ve **Alt**  + **F7** için `Window.NextDocumentWindowNav`.

> [!NOTE]
> Kullanmakta olduğunuz bir ayarlar bileşimi bu komutuna atanmış kısayol tuş bileşimi zaten yoksa, kendi özel komut kullanarak atayabilirsiniz **klavye** sayfasının **seçenekleri** iletişim bir kutu. Daha fazla bilgi için [tanımlayın ve klavye kısayollarını özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Düzenleyicideki belirli dosyalar geçmek için

-   Tuşuna **Ctrl**+**sekmesini** görüntülenecek **haldeyken IDE Gezgini'ni**. Basılı **Ctrl** anahtarı ve ENTER tuşuna **sekmesini** kadar art arda, geçiş yapmak istediğiniz dosyayı seçin.

    > [!TIP]
    > Hangi geçtiğiniz sırasını tersine çevirmek için **etkin dosyaların** listesinde, basılı **Ctrl**+**Shift** anahtarları ve ENTER tuşuna **sekmesini**.

    \- veya -

-   Düzenleyici sağ alt köşesinde, seçin **etkin dosyaların** düğmesini ve ardından geçmek için listeden bir dosya seçin.

    \- veya -

-   Menü çubuğunda, **penceresi** > **Windows**.

-   Listesinde, görüntülemek ve ardından istediğiniz dosyayı seçin **etkinleştirme**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Araç Pencereleri IDE içinde gezinme

**Haldeyken IDE Gezgini'ni** de sahip olduğunuz aracı windows döngüsü sağlar IDE'de açın. İki komutlardan birini erişmek için kullanabileceğiniz **haldeyken IDE Gezgini'ni** arasında geçiş yapmak istediğiniz düzene bağlı olarak, araç pencereleri arasında geçiş yapmak için. `Window.PreviousToolWindowNav` en son erişilen dosyanın taşımanızı sağlar ve `Window.NextToolWindowNav` ters sırada taşımanızı sağlar. **Genel Geliştirme Ayarları** atar **Shift**+**Alt**+**F7** için `Window.PreviousDocumentWindowNav` ve **Alt**  + **F7** için `Window.NextDocumentWindowNav`.

> [!NOTE]
> Kullanmakta olduğunuz bir ayarlar bileşimi bu komutuna atanmış kısayol tuş bileşimi zaten yoksa, kendi özel komut kullanarak atayabilirsiniz **klavye** sayfasının **seçenekleri** iletişim bir kutu. Daha fazla bilgi için [tanımlayın ve klavye kısayollarını özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE'nin belirli araç penceresine geçin

-   Tuşuna **Alt**+**F7** görüntülenecek **haldeyken IDE Gezgini'ni**. Basılı **Alt** anahtarı ve ENTER tuşuna **F7** geçmek için istediğinize penceresi tekrar tekrar seçtiğiniz kadar.

    > [!TIP]
    > Hangi geçtiğiniz sırasını tersine çevirmek için **etkin aracı Windows** listesinde, basılı **Shift**+**Alt** anahtarları ve ENTER tuşuna **F7**.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md)