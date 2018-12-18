---
title: Yük testi sonuçlarındaki grafiklerde sayaç ekleme ve silme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c4cb68370a743381a13b88c8a5fdc7d61700cb17
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049956"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Nasıl yapılır: Yük Testi Sonuçlarındaki Grafiklerde Sayaç Ekleme ve Silme

Kullanabileceğiniz **sayaçları** paneli performans sayaçları grafiğe eklenecek.

![Grafiğe eklenen sayacı](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Performans sayacı örnekleme aralığı hakkında önemli noktalar**

İçin bir değer seçin **örnek hızı** özelliği yük testinde çalışma ayarları yük testinizin uzunluğuna göre. Varsayılan değer olarak beş saniye gibi küçük bir örnekleme hızı yükleme testi sonuçları veritabanı daha fazla alan gerektirir. Daha uzun yük testleri için örnek hızı artırmak topladığınız veri miktarını azaltır. Daha fazla bilgi için [nasıl yapılır: örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek hızlara ait bazı Kılavuzlar şunlardır:

|Yük testi süresi|Önerilen örnek hız|
|-|-----------------------------|
|\< 1 saat|5 saniye|
|1 - 8 saat|15 saniye|
|8 - 24 saat|30 saniye|
|> 24 saat|60 saniye|

**Yüzdelik veri toplamak için zamanlama ayrıntılarını da dahil olmak üzere dikkat edilmesi gereken noktalar**

Yük testi adlı Düzenleyicisi'nde çalışma ayarlarında bir özelliği yoktur **Zamanlama Ayrıntıları Deposu**. Varsa **Zamanlama Ayrıntıları Deposu** özelliği etkinse, sonra Yük testi sırasında her bir bireysel test, hareket ve sayfa yürütülme zamanı yükleme testi sonuçları deposunda depolanır. Bu, 90'ıncı ve 95 yüzdelik veri gösterilmesini sağlar **Yük Testi Çözümleyicisi** testler, hareketler ve sayfalar tablolarında.

Etkinleştirmek için iki seçeneğiniz vardır **Zamanlama Ayrıntıları Deposu** adlı çalıştırma ayarları özellikleri özelliğinde **StatisticsOnly** ve **AllIndividualDetails**. Her iki seçenek tüm bireysel testler, sayfalar ve hareketler zamanlanır ve bireysel zamanlama verisinden yüzdelik veri hesaplanır. Fark **StatisticsOnly** seçeneğini yüzdelik veri hesaplanır hemen sonra bireysel zamanlama verileri depodan silinir. Bu, zamanlama ayrıntılarını kullandığınızda depodaki gerekli alanı miktarını azaltır. Ancak, İleri düzey kullanıcılar SQL araçları kullanarak zamanlama ayrıntı verilerini farklı yollarla işlemek isteyebilirsiniz. Bu durum söz konusuysa **AllIndividualDetails** seçeneği kullanılmalıdır, böylece zamanlama ayrıntı verileri bu işlem için kullanılabilir. Ayrıca, özelliği ayarlamanız **AllIndividualDetails**, kullanan sanal kullanıcı etkinliğini çözümleyebilirsiniz **sanal kullanıcı etkinliği** içinde grafik **Yük Testi Çözümleyicisi** yük testi çalışmayı tamamladıktan sonra. Daha fazla bilgi için [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Zamanlama ayarları verisini özellikle daha uzun yük testleri için çok büyük olabilir saklamak için yük testi sonuçları deposunda gereken alan miktarı. Bu veriler yük testi yürütmesini bitirene kadar yükleme testi aracısında depolanır çünkü Ayrıca, yük testi sonuçları deposu yük testinin sonunda bu verileri depolamak için uzun zamandır. Yük testi çalışmayı tamamladıktan sonra verilerin depoya saklandığı. Varsayılan olarak, **Zamanlama Ayrıntıları Deposu** özelliği etkin hale getirilir. Bu test ortamınızın sorunu ise, ayarlamak isteyebilirsiniz **Zamanlama Ayrıntıları Deposu** için **hiçbiri**.

Daha fazla bilgi için [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Bir yük testi grafiğinde belirli bir performans sayacına görüntülemek için

1.  Bir yük testi tamamlandıktan sonra veya Yük Testi Çözümleyicisi'nin araç çubuğunda, bir test sonucunu seçin **grafikleri**.

     **Sayaçları** paneli, grafik görünümünde görüntülenir.

    > [!NOTE]
    > Varsa **sayaçları** paneli görünür değilse, seçin **Sayaçlar panelini Göster** araç.

2.  İçinde **sayaçları** panelinden, düğümleri hiyerarşideki grafik şeklinde görüntülenmesini görmek istediğiniz performans sayacı bulana kadar genişletin.

     Örneğin, testleri çalıştığı bir bilgisayarda kullanılabilir bellek görüntülemek için genişletin **bilgisayarlar**bilgisayar düğümünü genişletin ve ardından **bellek**. Göreceğiniz **Kullanılabilir MBayt** sayacı.

3.  Performans sayacı görüntülemek istediğiniz graph'ı seçin.

4.  Performans sayacı seçiminde sağ **sayaçları** seçin ve panel **grafik üzerinde sayaç Göster**.

    > [!TIP]
    > Performans sayacının verileri bir grafikte görüntüleme geçici olarak durdurmak için göstergede performans sayacı için onay kutusunu temizleyin. Bu grafikte eğilim çizgisi görüntülemeden hala çözümlenecek min, Maks ve ortalama istatistikler sağlar. Bu grafik, çakışan birçok performans sayacı çizimleri içeriyorsa sorunları çözümlerken yararlı olabilir. Daha fazla bilgi için [yük testlerini çözümlemek için grafik görünümü göstergesini kullanma](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5.  Graftan performans sayacı verilerini kaldırmak için performans sayacı seçiminde sağ **sayacı** seçin ve gösterge sütunu **Sil**.

     \- veya -

     Grafiği seçip veri satırına sağ **Sil**.

     \- veya -

     Performans sayacını seçin **sayacı** gösterge sütunu verileri çizgi grafikte ve tuşuna **Sil** anahtarı.

    > [!NOTE]
    > Kullanarak bir performans sayacı gösterge ancak grafikte yerleştirmek seçebilirsiniz **gösterge üzerinde Sayaç Ekle** komutu.

## <a name="see-also"></a>Ayrıca bkz.

- [Grafik görünümünde yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Nasıl yapılır: özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)