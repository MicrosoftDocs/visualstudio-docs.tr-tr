---
title: Hızlı Eylemler, ampuller ve tornavidalar
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7089a9a654d1c346fefcca119f74a87d89f323b8
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349380"
---
# <a name="quick-actions"></a>Hızlı Eylemler

Hızlı Eylemler, kolayca yeniden düzenleme sağlar, oluşturmak veya aksi halde kodu tek eylemle değiştirin. Hızlı eylemler için kullanılabilir C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)ve Visual Basic kod dosyalarında. Bazı eylemler bir dile özgü olan ve diğer tüm diller için geçerlidir.

Hızlı eylemler için kullanılabilir:

- Bir kod düzeltmesini uygulayın bir [Çözümleyicisi kod](../code-quality/roslyn-analyzers-overview.md) kuralı ihlali
- [Bastır](../code-quality/use-roslyn-analyzers.md) kod Çözümleyicisi Kuralı ihlali
- Geçerli bir yeniden düzenleme (örneğin, [satır içi geçici değişken](../ide/reference/inline-temporary-variable.md))
- Kod oluşturma (örneğin, [bir yerel değişken ekleme](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring).

Ampul kullanarak hızlı Eylemler uygulanabilir ![ampul](media/light-bulb-icon.png) veya tornavida ![tornavida simgesi](media/screwdriver-icon.png) simgeleri veya basarak **Ctrl** + **.** imlecinizi bir eylem kullanılabilir kod satırına olduğunda. Gördüğünüz hata ampul ![hata ampul simgesini](media/error-light-bulb-icon.png) hata belirten bir kırmızı dalgalı çizgi yoktur ve Visual Studio, bu hata için bir düzeltme sahiptir.

Herhangi bir dilde üçüncü taraflara özel tanılama ve öneriler, örneğin bir SDK'ın bir parçası olarak sağlayabilir ve Visual Studio ampuller bu kurallara dayalı vurgulamasında kullanılır.

## <a name="icons"></a>Simgeler

Hızlı eylem kullanılabilir olduğunda görüntülenen simge, kullanılabilir düzeltme veya yeniden düzenleme tür gittiğinin belirtisini verir. *Tornavida* ![tornavida simgesi](media/screwdriver-icon.png) simgesi gösterir yalnızca kodunu değiştirmek kullanılabilir eylemleri vardır, ancak bunları mutlaka kullanmamalısınız. *Sarı bir ampul* ![ampul](media/light-bulb-icon.png) simgesi gösterir kullanılabilir eylemler, *gereken* kodunuzu geliştirmek için yapın. *Hata ampul* ![hata ampul simgesini](media/error-light-bulb-icon.png) simgesi gösterir, kodunuzdaki bir hatayı düzeltir bir eylem yoktur.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya tornavida görmek için

- Bir düzeltme varsa, bir hatanın konumda fare geldiğinizde ampuller kendiliğinden görünür.

   ![Ampul fare vurgulama ile](../ide/media/vs2015_lightbulb_hover.png)

- Giriş işaretini bir hızlı eylem kullanılabilir kod satırına taşıdığınızda ampuller ve tornavidalar düzenleyicinin sol kenar boşluğunda görünür.

- Tuşuna **Ctrl**+**.** Hızlı Eylemler ve yeniden düzenlemeler kullanılabilir bir listesini görmek için herhangi bir yerde bir satıra.

## <a name="to-see-potential-fixes"></a>Olası düzeltmeleri görmek için

Ampul yanındaki ya da aşağı oku seçin veya **olası düzeltmeleri göster** kullanılabilir hızlı eylemlerin bir listesini görüntülemek için bağlantı.

![Genişletilmiş ampul](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da kod üretimi](../ide/code-generation-in-visual-studio.md)
- [Yaygın Hızlı Eylemler](../ide/common-quick-actions.md)
- [Kod stilleri ve hızlı Eylemler](../ide/code-styles-and-quick-actions.md)
- [Yazma ve yeniden düzenleme kod (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring)