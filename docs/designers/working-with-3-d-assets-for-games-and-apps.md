---
title: Oyunlar ve uygulamalar için 3B varlıklarla çalışma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c86b5ec3918526f461b39080967d5bc4a8a32e30
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079480"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Oyunlar ve uygulamalar için 3B varlıklarla çalışma

Bu belge, oluşturmak veya 3B modelleri, dokuları ve gölgelendiricileri DirectX tabanlı oyunlar ve uygulamalar için değiştirmek için kullanabileceğiniz Visual Studio Araçları açıklar.

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio'da DirectX uygulaması geliştirme
 DirectX uygulaması, programlama mantığı, DirectX API ve üst düzey gölgelendirme dili (HLSL) programları, zengin, etkileşimli bir multimedya deneyimi sunmak için ses ve 3B görsel varlıklar genellikle birleştirir. Visual Studio, başka bir aracı kullanmak için IDE'den çıkmadan görüntü ve dokuları, 3B modeller ve gölgelendiriciler ile çalışmak için kullanabileceğiniz araçları içerir. Visual Studio Araçları, özellikle oluşturmak için uygun *yer tutucu* kodu test veya üretime hazır varlıkları komisyon önce ve inceleme ve üretime hazır değiştirmeye yönelik prototipleri oluşturmak için kullanabileceğiniz, varlıkları Uygulamanızı hata ayıklama işlemi yaparken varlıklar.

 İşte türde varlıkları hakkında daha fazla bilgi Visual Studio'da çalışabilirsiniz.

### <a name="images-and-textures"></a>Görüntü ve dokuları
 Görüntü ve dokuları rengi ve oyunlar ve uygulamalar, görsel ayrıntıları sağlayın. 3B grafikler, çeşitli biçimlerde, türleri ve geometriler farklı kullanımlarını desteklemek için doku gelir. Örneğin, normal haritalar için daha ayrıntılı aydınlatma, 3B modelleri piksel başına yüzey normal değerler sağlayın ve küp eşlemlerinin sky kutulama, yansıma ve küresel doku eşleme gibi kullanımlar için her yöne doku sağlayın. Doku, farklı ayrıntı düzeyleri en verimli işleme desteklemek için Mipmap sağlayabilir ve farklı renk kanalı ve renk sıralamalarının destekleyebilir. Dokular grafik az ayrılmış bellek kaplar ve gpu erişimi dokular daha verimli bir şekilde yardımcı sıkıştırma biçimlerinin çeşitli içinde depolanabilir.

 Görüntü ve dokuları birçok ortak türlerini ve biçimlerini çalışmak için Visual Studio görüntü Düzenleyicisi'ni kullanabilirsiniz.

### <a name="3d-models"></a>3B modeller
 3B modeller, boşluk ve Şekil oyunlar ve uygulamalar oluşturun. En düşük düzeyde, 3B alanda noktaları konumunu modelleri kodlama — olarak bilinen *köşeler*— çizgiler veya üçgenler model şeklini temsil eden tanımlamak için verileri dizinleme birlikte. Ek veriler bu köşelerde ile ilişkili olabilir — örneğin, renk bilgilerini, normal vektörleri veya uygulamaya özel öznitelikler. Her model nesnesi genelinde öznitelikleri de tanımlayabilirsiniz — Örneğin, hangi gölgelendirici nesnenin yüzeyi veya hangi doku uygulandığı görünümünü hesaplamak için kullanılır.

 Sık kullanılan çeşitli biçimlerde 3B modellerle çalışmak için Visual Studio Model Düzenleyicisi'ni kullanabilirsiniz.

### <a name="shaders"></a>Gölgelendiricileri
 Gölgelendiricileri grafik işlemci birimi (GPU) üzerinde çalışan küçük, etki alanına özgü programlardır. Gölgelendiricileri belirlemek 3B modelleri içine ekrandaki dönüştürülür şekiller ve bu şekiller her pikselin nasıl renklendirilmiştir. Gölgelendirici oluşturma ve nesneyi oyunlarda veya uygulamalarda uygulama nesnesi benzersiz bir görünüm verebilirsiniz.

 Özel görsel efektler HLSL programlama bilmeden oluşturmak için Visual Studio gölgelendirici tasarım gölgelendirici grafik tabanlı bir araçtır, Tasarımcısı'nı kullanabilirsiniz.

> [!NOTE]
> DirectX programlama ile başlama hakkında daha fazla bilgi için bkz. [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). DirectX tabanlı bir uygulamanın hatalarını ayıklama hakkında daha fazla bilgi için bkz. [(DirectX grafiklerinde hata ayıklama) grafik tanılama](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu
 Visual Studio, DirectX 2B ve 3B varlıkları işlemek için kullanır. DirectX 11 Oluşturucu ya da Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) yazılım oluşturucusu seçebilirsiniz. DirectX 11 Oluşturucu, DirectX 11 ve DirectX 10 GPU üzerinde yüksek performanslı, Donanım hızlandırmalı işleme sağlar. WARP Oluşturucu varlıklarınızı çok çeşitli bilgisayarlar çalışma emin olmaya yardımcı olur; bu modern grafik donanımının sahip olmayan bilgisayarlar ve grafik donanımının tümleşik bilgisayarları içerir. WARP hakkında daha fazla bilgi için bkz: [Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) Kılavuzu](http://go.microsoft.com/fwlink/p/?LinkId=224634).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dokularla ve görüntülerle çalışma](../designers/working-with-textures-and-images.md)|Dokular ve görüntüler ile çalışmak için Visual Studio kullanmayı açıklar.|
|[3B modelleriyle çalışma](../designers/working-with-3-d-models.md)|3B modellerle çalışmak için Visual Studio kullanmayı açıklar.|
|[Gölgelendiricilerle çalışma](../designers/working-with-shaders.md)|Visual Studio gölgelendirici Tasarımcısı oluşturmak ve özel gölgelendirici efektleri değiştirmek için nasıl kullanılacağını açıklar.|
|[Oyunlarda veya uygulamalarda 3B varlıklar kullanma](../designers/using-3-d-assets-in-your-game-or-app.md)|Oyunlarda veya uygulamalarda görüntü Düzenleyicisi, Model düzenleyiciyi veya gölgelendirici Tasarımcısı kullanarak oluşturduğunuz varlıkları kullanmayı açıklar.|