---
title: Yük Testlerini Çözümlemek için Grafik Görünümü Göstergesini Kullanma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3e379cd3f05063424a7db9905611fa86467bee2d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067200"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Yük testlerini çözümlemek için grafik görünümü göstergesini kullanma

Yük Testi Çözümleyicisinin Grafik görünümü seçili grafik ile ilişkili her performans sayacı bilgileri görüntüleyen bir gösterge paneli içerir.

![Grafik görünümü göstergesi](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki bilgiler, gösterge içinde yer alır:

-   **Grafikte Göster:** belirtmek için onay kutularını kullanın olmadığını belirli bir sayaç çizgi gibi **kullanıcı yükü** veya **Hatası/sn**, grafikte çizilir. Çizgi grafikte çizilmesini istiyorsanız onay kutusunu seçin. Graftan çizim satırı kaldırmak için bir onay kutusunu temizleyin. Çizim satırı kaldırıldığında, sayaç istatistikleri göstergede gösterilecek devam eder.

-   **Aralık:** performans sayacının y ekseni aralığını bu sütunda görüntülenir. Varsayılan olarak, bu değeri otomatik olarak örnek veri değişikliklerini aralığı olarak ayarlar. Otomatik olarak ayarlanan bir aralık her zaman maksimum değerden fazla olan 10 sonraki gücünü olacaktır. Bu, negatif katları içerir. Bir grafik çeşitli sayaçları, her biri farklı bir aralık içerebilir. Bu nedenle, y ekseni ile belirli bir aralık Etiketlenmedi ancak bunun yerine her bir sayacın toplam aralığının yüzde temsil eden 0-100 değerleri ile etiketlenir. Örneğin, 1000 bir aralığı olan bir sayaç için bir veri noktasının y ekseninde 60 600 sayacının değerine karşılık gelir.

    > [!NOTE]
    > Belirli bir değer aralığına kilitleyerek otomatik aralık değeri ayarı kapatabilirsiniz. Aralık kilitlendiğinde aralığını aşan değerleri grafiğin üst kısmında belirtilen en yüksek değer olarak görüntülenir. Kullanım **Çizim Seçenekleri** belirli bir değerin aralığı kilitlemek için iletişim kutusu.

-   **Sayaç:** adlı dört sütun **sayacı**, **örneği**, **kategori**, ve **bilgisayar** birlikte benzersiz olarak Performans sayacı belirleyin.

-   **Renk:** **renk** sütun çizilen satır performans sayacı için renk ve çizgi stilini gösterir. Kullanım **Çizim Seçenekleri** grafikteki bir performans sayacı rengini veya çizgi stilini değiştirme iletişim kutusu. **Çizim Seçenekleri** iletişim kutusu gösterge kısayol menüsünden kullanılabilir.

-   **İstatistikleri:** **Min**, **Max**, **ortalama** ve **son** performans istatistiklerini sütunları göster sayacı. Bu değerler grafı görünür bölgesine görüntülenen verilere karşılık gelir. Örneğin, bir bölgesine yakınlaştırma göstergesi istatistikleri yalnızca yakınlaştırılmış alan için değerleri ücreti yansıtılır. "Son" sütunu en son tamamlanan örnekleme aralıkta performans sayacı değeridir.

    > [!NOTE]
    > Yük testi çalışırken son sütunu, yalnızca Yük Testi Çözümleyicisi'nin göstergede görüntüler.

     Daha fazla bilgi için [nasıl yapılır: grafiğin bir bölgesine yakınlaştırmak](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Bir öğenin göstergede seçilmesi şunları yapar:

-   Gösterge ve grafik kaldırılacak öğe sağlar. Ya da öğeyi sağ tıklatıp seçin **Sil**, veya basın **Sil** anahtarı.

-   Grafiği çizilen satırda vurgulanır.

-   Seçili öğe için verileri görüntülemek veri kılavuzu neden olur.

-   Erişmenizi sağlar **Çizim Seçenekleri** sayaç için iletişim kutusu.

> [!TIP]
> Kullanabileceğiniz **grafik seçenekleri aşağı açılan** düğmesine **Yük Testi Çözümleyicisi** araç çubuğu ve select **Göstergeyi Göster** göstermek veya gizlemek için **gösterge** graf görünümünü ile ilişkili bölmesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: grafiğin bir bölgesine yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Grafik görünümünde yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
