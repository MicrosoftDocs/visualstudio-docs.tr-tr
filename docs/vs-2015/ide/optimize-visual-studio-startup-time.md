---
title: Başlatma süresini iyileştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a17b8955d6c81c182523a7616f927eabd8703632
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050189"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio Başlangıç süresini iyileştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İdeal olarak, Visual Studio her zaman mümkün olan en kısa sürede başlatılır. Bunların başlangıçta otomatik olarak yüklemek için ancak Visual Studio uzantıları ve açık aracı penceresi başlangıç zamanı olumsuz etkileyebilir. **Visual Studio performansını Yönet** penceresi yalnızca hangi uzantıları ve özellikleri, Visual Studio Başlangıç süresini etkileyen görmenizi sağlar, ancak ayrıca hızlı bir şekilde nasıl hakkında daha fazla denetime sahip yükleme davranışlarını belirlemenize olanak tanır Visual Studio başlatılır.

## <a name="control-startup-behavior"></a>Başlangıç davranışını denetimi

Başlangıç zamanı genişletme önlemek için Visual Studio 2017 başlangıç sırasında uzantıları yükleme-isteğe bağlı-yüklemede yaklaşımı kullanarak önler. Bu, hemen Visual Studio başlatmaz, bunun yerine bir gerektiğinde temelinde başlatma işleminden sonra zaman uyumsuz olarak açmak sonra uzantıları açmayın anlamına gelir. Ayrıca, önceki bir Visual Studio oturumu açık sol araç pencereleri başlangıç zamanını yavaşlatabileceği için Visual Studio Başlangıç süresini etkileyen önlemek için daha akıllı bir şekilde araç pencereleri açılır.

Visual Studio yavaş başlatma algılarsa, yavaşlama neden olan uzantı veya araç penceresinin için uyarı bir açılır ileti görüntülenir. İleti bir bağlantı da sağlar. **Visual Studio performansını Yönet** iletişim kutusunda, başlangıç performansı etkileyen uzantıları ve araç pencerelerini listeler. Bu iletişim kutusunu başlatma performansını artırmak için uzantı ve araç penceresi ayarlarını değiştirmenize olanak tanır.

![-Visual Studio performansını Yönet açılan](../ide/media/vside-perfdialog-popup.PNG "Visual Studio performansını Yönet - açılan menüsü")

**Visual Studio performansını Yönet** iletişim kutusunda iki kategorisi vardır: **uzantıları** ve **aracı Windows**.

### <a name="control-extensions"></a>Denetim uzantıları
Bir uzantıyı Visual Studio Başlangıç yavaşlatıyor uzantısı görünür **Visual Studio performansını Yönet iletişim** kutusuna uzantı türleri birini seçtiğinizde. Başlangıç zamanı üzerindeki etkisi (altında listelenen **etkisi** bölümü) olan edilemeyecek kadar yüksek, her zaman başlangıçta uzantısı seçerek devre dışı bırakmak seçebileceğiniz **devre dışı** düğmesi. Uzantı sonraki oturumlar için Uzantı Yöneticisi'ni veya Visual Studio performansını Yönet iletişim kutusunu kullanarak yeniden etkinleştirebilirsiniz.

![Visual Studio performansını - uzantıları Yönet](../ide/media/vside-perfdialog-extensions.PNG "Visual Studio performansını Yönet - uzantıları")

Başlangıç uzantılarını yanı sıra yük çözümleri yüklediğinizde veya bir kullanıcı yazdığında uzantıları da devre dışı bırakabilirsiniz. Yalnızca ilişkili uzantıların listesini görmek için senaryo seçin.

### <a name="control-tool-windows"></a>Denetimi Araç pencereleri
Araç penceresi Visual Studio Başlangıç yavaşlatıyor, varsayılan davranışını (size hiçbir avantajı başlangıç hızı sağlar) adresindeki bırakın seçebilirsiniz veya iki davranışları birini seçerek davranışını geçersiz kılabilirsiniz:

- **Başlangıçta pencere gösterme:** bu seçeneği belirlerseniz, Visual Studio'da açtığınızda belirtilen araç penceresi her zaman içinde önceki bir oturum açma sol bile kapatılacak. Araç penceresi menüsünden açabilirsiniz.
- **Otomatik Gizle penceresi başlangıçta:** araç penceresini önceki bir oturumda açık bırakıldı durumunda, bu seçeneğin belirlenmesi araç penceresi başlatma önlemek için başlangıçta aracını pencerenin Grubu Daralt. Araç penceresi hala kullanılabilir ancak Visual Studio Başlangıç süresini artık olumsuz etkiler çünkü araç penceresi genellikle kullanırsanız, iyi bir seçimdir.

![Araç pencereleri - Visual Studio performansını Yönet](../ide/media/vside-perfdialog-toolwindows.PNG "Visual Studio performansını Yönet - araç pencereleri")

Daha sonra fikrinizi değiştirirseniz, bu seçeneklerin hiçbirini döndürebilirsiniz **Visual Studio performansını Yönet** iletişim kutusu. Açmak için **Visual Studio performansını Yönet** Seç iletişim kutusu, menü çubuğunda, **yardımcı**, **Visual Studio performansını Yönet**.
