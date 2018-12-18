---
title: Yük testi sonuç grafikleri üzerinde Yakınlaştır
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 558d6429c5d92f833e81074fe928436ab6e7f30e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064899"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Nasıl yapılır: yük testi sonuçlarında grafiğin bir bölgesine yakınlaştırma

Bir yük testi tamamlandıktan sonra yakınlaştırmak ve kaydırmak için grafiğin bir bölgesine yakınlaştırma çubukları kullanabilirsiniz. Yakınlaştırma tarafından ince ayrıntılı olarak yük testi sırasında oluşturulan verileri inceleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yakınlaştırma sırasında çalışan bir test sonuçlarını gözlemeyerek yalnızca zaman, bir Tamamlanan yük testi sonuçlarını analiz kullanılabilir.

Yakınlaştırma denetimini yalnızca görünür **Yük Testi Çözümleyicisi** bir yük testi sonucu yakınlaştırma modunda görüntülediğinizde. Yakınlaştırma modu Grafik görünümünde yük testi tamamlandıktan veya önceden çalışan yük testi yüklenen kurulur. Göstermek veya grafik yakınlaştırma denetimlerini kullanarak Gizle **yakınlaştırma denetimlerini göster** araç.

**Yatay ekseni yakınlaştırma** yük testi sırasında belirli süreler çözümlemek için ayarlanabilir. **Dikey ekseni yakınlaştırma** grafikte yer sayaçları için belirli bir değer aralıklarına çözümlemek için ayarlanabilir.

Her iki **yatay zaman çizelgesi** ve **dikey değer aralığı** yakınlaştırma denetimleri fare kullanılarak ayarlanabilir. **Yatay zaman çizelgesi denetimi** sol ve sağ ok tuşlarını kullanarak da ayarlanabilir. Yakınlaştırma denetimini ayarlamak için ok tuşlarını kullanarak, aynı anda 1 örnekleme aralığı tarafından windows aralığı ayarlayabilirsiniz. Kullanarak **Shift** ve ok tuşları 10 örnekleme aralığının ayarlamalar yapar.

Yakınlaştırma denetimini ok tuşunu kullanarak ayarlamak için önce yakınlaştırma denetimi kullanarak Odaklan **sekmesini** anahtarı. Sol kaydırıcının odağa sahip olduğunda, ok tuşlarını yakınlaştırma pencerenin başlangıç sınır 1 aralığına göre sola veya sağa taşınır. Odağı merkezi kaydırıcısını açık olduğunda, yakınlaştırma penceresi sola veya sağa 1 örnekleme aralığı yakınlaştırma penceresinin boyutunu değiştirmeden kaydırmak için ok tuşlarını kullanabilirsiniz. Ve son olarak, sağ tarafta kaydırıcıyı hareket genişletme veya 1 ile yakınlaştırma penceresinin bitiş aralığını azaltmayı örnekleme aralığı.

Değer aralıkları ve tam zaman çizelgesini göstermek için yatay ve dikey yakınlaştırma denetimlerini döndürmek için kullanabileceğiniz **Yatay Uzaklaştır** seçeneği **Dikey Uzaklaştır** seçeneği veya **Uzaklaştır Her ikisi de** açılır menüde bir seçenek grafikteki.

> [!TIP]
> Kullanabileceğiniz **Yatay Yakınlaştırma Denetimlerini Eşitle** açmasına veya kapatmasına otomatik yatay yakınlaştırma eşitleme için araç çubuğundaki. İle eşitlemede herhangi bir grafiğe geçerli yakınlaştırma da diğer bir grafikler grafikler görünümü üzerinde uygulanır.

![Graf görünümü yakınlaştırma denetimi](../test/media/ltest_zoomcontrol.png)

Önceki çizimde, **Test altındaki sistem** grafik yakınlaştırıldı eşik sorunlarını araştırmak için. Eşik ihlalleri kullanılarak etkinleştirilen **Eşik İhlallerini Grafikte Göster** gelen **grafik seçenekleri** araç çubuğundaki açılan.

Daha fazla bilgi için [Çözümle yük testi sonuçlarını grafik görünümünde](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Grafik görüntüleme

Yakınlaştırma veya uzaklaştırma veya kaydırma bir grafik görüntüsünü değiştirmeden önce grafikleri görüntülemek için bu yordamı izleyin.

Grafikleri görüntülemek için:

1.  Bir yük testi tamamlanana kadar çalıştırın.

2.  Yük testi çalıştırması sonunda seçin **Evet** sonuçları yük testi sonuçlarını görüntüleme yapılıp yapılmayacağının sorulduğu iletişim kutusunda depolar.

     \- veya -

     Daha önce çalıştırılan yük testi ayrıntılarını görüntüleyin. Daha fazla bilgi için [nasıl yapılır: erişim yük testi sonuçlarını analiz](../test/how-to-access-load-test-results-for-analysis.md).

3.  Seçin **grafikleri** graflarınız görüntülenmiyorsa.

4.  Yakınlaştırma çubukları görüntülenmiyorsa seçin **yakınlaştırma denetimlerini göster**.

     İki yakınlaştırma çubukları, her bir grafik için kullanılabilir. Dikey ölçeklendirme denetleyen yakınlaştırma çubuğu grafiği solunda görünür. Grafiğin altında yatay ölçeklendirme özellikleri denetleyen yakınlaştırma çubuğu görünür.

     İki tanıtıcıları her yakınlaştırma çubuğu vardır. Yakınlaştırma çubuğunun her iki ucunda bir dikdörtgen alan işleyicisidir.

## <a name="zoom-and-scroll"></a>Yakınlaştırma ve kaydırma

Görüntülenen birden çok grafik olduğunda, böylece yük testi çalıştırması aynı kısmını görüntüledikleri eşitlenme tutabilirsiniz.

### <a name="to-synchronize-zooming-and-scrolling"></a>Yakınlaştırma ve kaydırma eşitlemek için

1.  Üzerinde **Yük Testi Çözümleyicisi**, seçin **Yatay Yakınlaştırma Denetimlerini Eşitle**.

     Zaman **Yatay Yakınlaştırma Denetimlerini Eşitle** düğmesi seçildiğinde, yakınlaştırma ve kaydırma bireysel bir grafiğin zaman ölçeğini de yakınlaştırıldığını ve diğer grafikleri zaman ölçeğini kaydırır.

2.  Yeniden seçmeniz **Yatay Yakınlaştırma Denetimlerini Eşitle**.

     Zaman **Yatay Yakınlaştırma Denetimlerini Eşitle** düğme seçili değilse, yakınlaştırma ve kaydırma bireysel bir grafiğin zaman ölçeğini yalnızca o grafiği etkiler.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Grafiğin bir bölgesine kaydırma ve yakınlaştırma

1.  Altında bir grafik yakınlaştırma çubuğu üzerinde sol taraftaki tutamacı sağa sürükleyin.

     Bu test çalıştırması ikincisi parçası üzerinde yakınlaştırır. Benzer şekilde, sağ taraftaki tutamacı sola sürükleyerek önceki test çalıştırması kısımlarına yakınlaştırır.

2.  Belirli bir alanı yakınlaştırmak için slayt iki grafiğin merkezine işler.

     Yakın iki birbirine daha kısa, hassas kesimleri yük testinin görüntülemek için ekranı tanıtıcılarıdır.

     Yakınlaştırma çubuğunun orta kısmını seçin ve ardından onu sürükleyerek yük testinde belirli bir noktaya kaydırın.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Seçip sürükleyerek grafiğin belirli bir bölgesine yakınlaştırmak için

1. Yakınlaştırma alanının bir ucunda bulunan bir grafiği seçin.

2. Fare işaretçisi Yakınlaştırma alanının diğer sonuna kadar sürükleyin.

3. Fare düğmesini bırakın.

    Bu, seçip sürükleyerek tanımladığınız alanı büyütür.

   Aşağıdaki yordam, yakınlaştırma çubuğu ucunda ayarlamak zorunda kalmadan hızlıca uzaklaştırmak açıklar.

### <a name="to-zoom-out"></a>Uzaklaştırmak için

1.  Yakınlaştırılmış grafiğe sağ tıklayın.

2.  Kısayol menüsünde **Yatay Uzaklaştır**.

     Bu sürenin tamamı yük testinin çalışma gösterilecek uzaklaştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Grafik görünümünde yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: grafiklerde sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)