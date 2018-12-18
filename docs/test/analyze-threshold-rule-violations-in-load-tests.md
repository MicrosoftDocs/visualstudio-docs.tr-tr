---
title: Yük testlerindeki eşik kuralı ihlallerini çözümleme
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: be0784197c03aa3117d559cd4aa99797027c8170
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061817"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Yük testi çözümleyicisini kullanarak Yük testlerindeki eşik kuralı ihlallerini çözümleme

Eşik kuralları belirli bir performans sayaçları ile ilişkili olan ve bir performans sayacı aşıldı veya set değerin altına altına düştü ihlallerini gösterir. Bir yük testi çalıştırdığınızda, daha önce ayarladığınız eşik kuralları için oluşan ihlallerini analiz edebilirsiniz.

Herhangi bir ihlal oluştuysa, bir **Eşik ihlallerini** köprü bulunur **Yük Testi Çözümleyicisi** durum çubuğu ve oluşan ihlallerinin sayısını belirtir. Eşik ihlalleri tablosunu görüntülemek için köprüyü seçin. Ayrıca Eşik ihlallerini görüntüleyebilirsiniz **sayaçları** penceresinde ve grafik üzerinde.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Eşik ihlallerini Tablo görünümü

 Eşik ihlalleri tablosunu ilk 1.000 ihlalleri görüntüler. Aşağıdaki tablo şu sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Zaman|İhlalin gerçekleştiği süre boyunca yük test edin.|Evet|
|Bilgisayar|İhlalin gerçekleştiği test edilen bilgisayar adı. **Not:** donanımlarını üzerinde yük testlerini çalıştırdığınızda bu önemlidir.|Evet|
|Kategori|İhlalin gerçekleştiği performans sayacı kategorisi.|Evet|
|Sayaç|İhlalin gerçekleştiği performans sayacının adı.|Evet|
|Örnek|Performans sayacı örneği üzerinde ihlali oluştu.|Evet|
|İleti|Eşik ihlali açıklayan ileti. Örneğin, **Kritik Eşik değeri 0 5 değerini aşıyor**.|Evet|

> [!NOTE]
> Tablo, sütun üst bilgilerini seçerek sıralayabilirsiniz.

 Daha fazla bilgi için [yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümlemek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Eşik ihlallerini Sayaçlar panelini görüntüle

 Eşik ihlallerini görüntüleyebilirsiniz **sayaçları** panelinde Yük testiniz için performans sayaçları listeler ağaç. Simgeleri **sayaçları** paneli iletişim Eşik ihlalleri. Simgesi aşağıdakilerden biri olabilir:

 Simgesi aşağıdakilerden biri olabilir:

 ![Eşik ihlali yok](../test/media/icon_ltest_1.gif) Eşik ihlali yok.

 ![Kritik Eşik ihlalinin son aralığı](../test/media/icon_ltest_2.gif) Son aralıkta bir Kritik Eşik ihlali oluştu.

 ![Önceki bir aralıkta bir Kritik Eşik ihlali](../test/media/icon_ltest_3.gif) Önceki bir aralıkta bir Kritik Eşik ihlali oluştu.

 ![Uyarı eşiği ihlalinin son aralığı](../test/media/icon_ltest_4.gif) Uyarı eşiği ihlalinin son aralıkta oluştu.

 ![Uyarı eşiği ihlalinin önceki aralığı](../test/media/icon_ltest_5.gif) Önceki bir aralıkta bir uyarı eşik ihlali oluştu.

 İsteğe bağlı olarak, Eşik ihlalleri grafikte de görüntülenebilir. Eşik ihlali gerçekleştiği veri noktasının yanındaki grafik üzerindeki eşik simgesi görünür.

 Sayaç ağaçta kök düğümü kadar belirli bir sayaç düğümünden eşik ihlali simgesine yayılır. Bu bir ihlali nedeniyle ağaç genişletilmemiş ağaçta görünür olmayabilir sayacı uyarır.

## <a name="view-threshold-violations-on-the-graph"></a>Grafikte Eşik ihlallerini görüntüle

 Eşik İhlallerini Grafikte görüntüleyebilirsiniz. Benzer şekilde **sayaçları** paneli, simgeler grafikte Eşik ihlallerini iletişim kurar. Grafikte eşik ihlali gerçekleştiği veri noktasının yanındaki simge görünür. Grafikte görünmeyen bir sayaçta eşik ihlali meydana gelirse, bu grafiğe ondan sürükleyerek ekleyebileceğiniz **sayaçları** grafiğe paneli.

 Daha fazla bilgi için [Çözümle yük testi sonuçlarını grafik görünümünde](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testi içinde belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümleyin](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)