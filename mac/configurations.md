---
title: Derleme Yapılandırmalarını Anlama
description: Bu makalede, çeşitli Mac derleme yapılandırmalarını Visual Studio'da açıklanır.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 7f130f5dec77e0a1965c68cf71e642fdb636832f
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296183"
---
# <a name="understanding-build-configurations"></a>Derleme yapılandırmalarını anlama

## <a name="project-build-configurations"></a>Proje derleme yapılandırmaları

Projeleri birden çok yapılandırmalara sahip eğilimindedir ve bunlar arasında geçiş derleme zamanında farklı çıkış izin verir. Örneğin, bir hata ayıklama yapılandırması hata ayıklama sembolleri, işlev adları, parametrelerin veya çöken bir uygulamanın yığın izlemesi değişkenlerinden gidermek hata ayıklayıcı izin vererek çıkarır. Bu ek bilgiler geliştirme sırasında kullanışlı olsa da, bir inflated dosya boyutuna yol açar ve dağıtım için ideal değildir.

Her platform için kendi yapı belirli yapılandırmasına sahip değil.

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Proje yapılandırmaları yakındır çözüm yapılandırmaları bir projenin tamamı için özel yapılandırmalar oluşturmak için kullanılır. Kullanarak **yapılandırma eşlemeleri** sekmesinde altında **Yapı > yapılandırmaları** öğesi atayabilirsiniz her çözüm öğesi için bir hedef yapılandırma de gösterildiği gibi Aşağıdaki görüntüde:

![Yapılandırma eşleme seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırmaları hakkında daha fazla bilgi için bkz. [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) James Montemagno tarafından video.

## <a name="run-configuration"></a>Çalıştırma yapılandırma

Xamarin Studio önceki sürümlerinde, projesi olarak ayarla seçeneğine seçebilirsiniz bir **başlangıç projesi**, Çalıştır/genel Çalıştır/Hata Ayıkla komutunu kullanırken hataları ayıklanmakta proje olduğu. Bu proje panelindeki projenin adı için bir kalın yazı tarafından belirtilir.

Bir başlangıç projesi ayarlama yerine Mac için Visual Studio'da ayarlayabileceğiniz bir _çalıştırma yapılandırmasını_. Çalıştırma yapılandırmaları, araç, aşağıda gösterildiği gibi yapı yapılandırması Seçici yanındaki aşağı açılan listede sunulur:

![Yapılandırma açılan çalıştırın](media/projects-and-solutions-image8.png)

Bir çalıştırma yapılandırma, bir ad ve bir projede farklı amaçlar için tanımlanmış birkaç yapılandırma ile yürütme seçeneklerini kümesidir. Çalıştırma yapılandırmaları proje düzeyinde tanımlanmış ve kadar gerekli eklemek mümkündür ancak varsayılan otomatik olarak yürütülebilir her proje için oluşturulur. Belirli proje türleri otomatik olarak ek çalıştırma yapılandırmaları oluşturun. Örneğin, watchOS projelerine oluşturmak için kullanabileceğiniz  _bakış ve bildirim yapılandırma._

Yapılandırmaları (Bu durumda yapılandırmaları .csproj dosyasında depolanır) diğer geliştiricilerle paylaşılan veya (durumda .user dosyasında depolanır yerel olarak) tutulur.

### <a name="android-run-configurations"></a>Android çalışma yapılandırmaları

Android projeleri için çalıştırma yapılandırmaları hangi etkinlik, hizmet veya çalıştırılırken veya hata ayıklanırken proje başlatmak için yayın alıcısı belirtmenizi sağlar. Intent ek verileri aktarmak ve bileşenlerinizin farklı başlatma koşulları altında test edebilmek için hedefi bayraklarını ayarlayın.

Dışındaki etkinlikleri `MainLauncher` gerekecek `Exported=true` fiziksel bir cihazda hata ayıklama için etkinlik özniteliği eklenemiyor veya tanımladığınız amaç filtreleri.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Çalışma yapılandırmaları bulunabilir veri örnekleri

Aşağıdaki listede, içinde çalıştırma yapılandırmaları dahil edilebilir veri bazı örnekleri verilmiştir:

* Normal .NET projesi
    * Farklı bir başlangıç uygulaması
    * Başlangıç bağımsız değişkenleri
    * Çalışma dizini
    * Ortam değişkenleri
    * Mono çalışma zamanı seçenekleri (yalnızca üzerinde Mono çalıştırılırken kullanılması için)
* Android projesi
    * Giriş noktası (etkinlik, hizmet, alıcı)
    * Hedefi bağımsız değişkenleri ve veri
* iOS projesi
    * Mod (Normal, arka planda getirme)
* iOS uzantı projesi
    * Başlangıç uygulaması: varsayılan veya özel
* WatchKit proje
    * Mod (tek bakışta, bildirim)
    * Bildirim yükü

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows için Visual Studio) olarak derleme yapılandırmalarını anlama](/visualstudio/ide/understanding-build-configurations)