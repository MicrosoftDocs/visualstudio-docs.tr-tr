---
title: R kodda hata ayıklama
description: Visual Studio için kesme noktaları da dahil olmak üzere R tam hata ayıklama deneyimi sağlar, ekleme, yığını ve değişkenleri inceleniyor çağırın.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: c89eed2f3e15259489ce43920b912db14ab862a6
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238385"
---
# <a name="debug-r-in-visual-studio"></a>Visual Studio'da R hata ayıklama

R araçları için Visual Studio (RTVS) Visual Studio tam hata ayıklama deneyimini ile entegre olur (bkz [Visual Studio'da hata ayıklamayı](../debugger/debugging-in-visual-studio.md). Bu destek, çalışan işlemlerin, inceleme ve izledikleri değişkenleri ve çağrı yığınını incelemek için ekleme kesme noktaları içerir. Bu makalede daha sonra R ve RTVS özgü hata ayıklama bu yönlerini araştırır.

Hata ayıklayıcı bir R projesini başlangıç R dosyasında diğer proje türleri ile aynıdır için başlangıç: kullanmak **hata ayıklama** > **hata ayıklamayı Başlat**, **F5** anahtar veya **Kaynak başlangıç dosya** hata ayıklama araç çubuğunda: 

![Başlat düğmesi R için hata ayıklayıcı](media/debugger-start-button.png)

Başlangıç dosyasını değiştirmek için Çözüm Gezgini'nde bir dosyaya sağ tıklayın ve seçin **başlangıç R betiği olarak ayarlamak**.

Hata ayıklayıcı "Kaynaklar" Etkileşimli penceresinde başlatma tüm durumlarda, yükleme ve orada etkileşimli pencerenin çıkış gösterildiği gibi çalışan yani:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Dikkat `rtvs::debug_source` işlev, komut dosyası kaynağı için kullanılır. Bu işlev, hata ayıklama hazırlığı kodunuzu değiştirmek RTVS gerektiği için gereklidir. Herhangi bir RTVS kaynak belirleme komutu ve bir hata ayıklayıcısı kullanarak eklendiğinde, Visual Studio otomatik olarak kullanan `rtvs::debug_source`.

Hata ayıklayıcı kullanarak doğrudan etkileşimli penceresinden el ile de ekleyebilirsiniz **R Araçları** > **oturum** > **Attach hata ayıklayıcı** komut, **hata ayıklama** > **R etkileşimli ekleme** komutu, veya **Attach hata ayıklayıcı** etkileşimli pencerenin araç çubuğunda komutu. Bunu yaptıktan sonra kaynak hata ayıklamak istediğiniz dosyaları, sorumluluğundadır. El ile kaynak dosyalarını istiyorsanız, kullandığınızdan emin olun `rtvs::debug_source` ve normal `source` r komutunu

Hata ayıklayıcı ve etkileşimli pencere arasındaki bu bağlantı, arama (ve hata ayıklama) gibi şeyler kolaylaştırır farklı parametre değerleri içeren bir işlev. Örneğin, aşağıdaki işlevi kaynaklı dosyasında (oturuma yüklenmiş anlamına gelir) olduğunu varsayalım:

```R
add <- function(x, y) {
    return(x + y)
}
```

Üzerinde bir kesme noktası ayarlayın, sonra da `return` deyimi. Penceresinde girme şimdi, etkileşimli `add(4,5)` hata ayıklayıcı kesme noktasına durdurur.

## <a name="environment-browser-in-the-interactive-window"></a>Etkileşimli penceresinde ortamı tarayıcı

Hata ayıklayıcıda durduğunda, ayrıca ortamı tarayıcı isteminde durduruldu [etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md). İstemi görünür `Browse[n]>` n, bir sayı.

Ortam tarayıcı özel komutlar destekler:

| Komut | Açıklama |
| --- | --- |
| n | Sonraki: çalıştırır kodda next deyimi dosya (Adımlama olarak aynı). |
| s | adımla: next deyimi işlev çağrısı ise işlevi kapsamı içine Adımlama kod dosyasında next deyimi çalıştırır. |
| F | Son: geçerli işlev kapsamı kalanını çalıştırır ve çağırana (adım ile aynı) döndürür. |
| c, devamı | devam: sonraki kesme programı çalıştırır. |
| Q | çıkar: hata ayıklama oturumu sona erer. |
| Burada | yığını göster: çağrı yığını etkileşimli penceresinde görüntüler. |
| Yardım | Yardımı Göster: kullanılabilir komutlar etkileşimli penceresinde görüntüler. |
| &lt;ifade&gt; | İfade değerlendirme *expr*. |

![Etkileşimli penceresinde ortamı tarayıcı](media/debugger-environment-browser.png)
