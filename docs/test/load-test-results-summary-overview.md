---
title: Yük Testi Sonuçları Özetine Genel Bakış
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3f5187aabeb0c8e2ef81b0c6b6883b96590d7005
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062615"
---
# <a name="load-test-results-summary-overview"></a>Yük testi sonuçları özetine genel bakış

Bir yük testi çalıştırdıktan sonra sonuçları hızlı bir şekilde anlamak için yükleme testi özetini görüntüleyebilirsiniz. Yükleme testi özetini anahtar sonuçları bir compact ve kolay okunur biçimde sağlar. Ayrıca, yük testinin yazdırabilirsiniz. Bu, proje katılımcılarına sonuçları iletişim kurarken güvenli kılar. Bir yük testi sonucu daha önce çalışan yük testinden açtığınızda, yükleme testi özetini de varsayılan görünümü şu şekildedir. Daha fazla bilgi için [nasıl yapılır: erişim yük testi sonuçlarını analiz](../test/how-to-access-load-test-results-for-analysis.md).

![Özet görünümü](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Yük Testi Özeti

Yükleme testi özetini bölümlere ayrılmıştır. İlk bölüm Özet üst kısmında görünür ve her zaman görünürdür. Yük Testi Özeti görüntülediğinizde, aşağıdaki öğeleri ilk şunlardır:

- Test çalışma bilgisi

- Genel sonuçları

- Anahtar istatistiği: en yavaş 5 sayfa

- Anahtar istatistiği: en yavaş 5 test

- Anahtar istatistiği: en yavaş 5 SQL işlemi

    > [!NOTE]
    > Yalnızca yük testinde SQL izlemeyi etkinse SQL İşlemleri bölmesi görüntülenir.

Kapanış bölümleri Özet sonunda görünür ve yer kazanmak için daraltılmış. Aşağıdaki öğeler, yük testinin sonunda görünür:

- Test Sonuçları

- Sonuçlar sayfası

- İşlem sonuçları

- Test kaynakları altındaki sistem

- Denetleyici ve aracı kaynakları

- Hatalar

## <a name="test-run-information"></a>Test çalıştırması bilgileri

Test çalıştırması bilgileri bölümü, test, başlangıç ve bitiş zamanlarını ve çalıştırdığınız test denetleyicisinin adını da dahil olmak üzere çalışma hakkında genel bilgiler içerir. Bu bölümde Ayrıca, yük testi çalıştırdığınızda eklediğiniz çalıştırma isteğe bağlı bir açıklama içerir.

## <a name="overall-results"></a>Genel sonuçları

Genel sonuçlar bölümü Özet saniye, başarısız isteklerin toplam sayısı, ortalama yanıt süresi ve ortalama sayfa süresi başına istek sayısı dahil olmak üzere test sonuçlarını içerir.

## <a name="key-statistic-top-5-slowest-pages"></a>Anahtar istatistiği: en yavaş 5 sayfa

En yavaş sayfalar bölümü yük testinde ilk 5 en yavaş sayfalar içerir. URL ve ortalama sayfa yükleme süresi her sayfada görüntülenir. Sayfalar, azalan sırada listelenir. Açmak için sayfanın URL'sini seçebileceğiniz **sayfaları** tablo ve daha fazla ayrıntı için bu sayfayı inceleyin. Daha fazla bilgi için [nasıl yapılır: web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Yüzdelik dilim değeri **%95 sayfa süresi (sn)** rapor %95 sayfa bu süresini saniye cinsinden en geç tamamlandı.

## <a name="key-statistic-top-5-slowest-tests"></a>Anahtar istatistiği: en yavaş 5 test

En yavaş 5 test yük testi içinde en yavaş testler bölümü içerir. Her test için test ve ortalama test süresi adı görüntülenir. Testler, azalan sırada listelenir. Açmak için bir test adı seçebileceğiniz **testleri** tablo ve daha fazla ayrıntı için test inceleyin. Daha fazla bilgi için [yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümlemek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Yüzdelik dilim değeri **%95 Test Süresi (sn)** rapor %95 test bu süresini saniye cinsinden en geç tamamlandı.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Anahtar istatistiği: en yavaş 5 SQL işlemi

Yük testinde SQL izlemeyi etkinleştirilirse, en yavaş sorgular ilk 5 en yavaş yük testinde içerir. Her test için işlem ve süreyi adı görüntülenir. Süre (SQL Server 2005) mikrosaniye veya milisaniye (SQL Server 2000 ve öncesi) görüntülenir. Testler süreye göre azalan sırada listelenir. Açmak için bir işlem adını seçebileceğiniz **SQL İzleme** tablo ve daha fazla ayrıntı için bu işlemi denetleyin. Daha fazla bilgi için [SQL izleme verileri tablo](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Test sonuçları

Test sonuçları bölümü, tüm testleri ve yük testi senaryolarında listesini içerir. Testin adını senaryoyu, kaç kez başarısız oldu, çalıştırılma sayısı ve ortalama test süresi görüntülenir. Açmak için bir test adı seçebileceğiniz **testleri** tablo ve daha fazla ayrıntı için test inceleyin. Daha fazla bilgi için [yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümlemek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Daralt ve bölüm başlığının yanındaki oku seçerek bu bölümü genişletin.

## <a name="page-results"></a>Sonuçlar sayfası

Sayfa sonuçları bölümü, yük testinde web sayfalarının bir listesini içerir. URL, senaryo, sayı, ortalama sayfa süresi ve testin adı görüntülenir. Açmak için sayfanın URL'sini seçebileceğiniz **sayfaları** tablo ve daha fazla ayrıntı için bu sayfayı inceleyin. Daha fazla bilgi için [nasıl yapılır: web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Daralt ve bölüm başlığının yanındaki oku seçerek bu bölümü genişletin.

## <a name="transaction-results"></a>İşlem sonuçları

İşlem sonuçları bölümü, yük testi içindeki tüm işlemlerin bir listesini içerir. İşlem, senaryo, test, yanıt süresi, geçen süreyi ve sayı adı görüntülenir. Açmak için bir işlem adını seçebileceğiniz **işlemleri** tablo ve daha fazla ayrıntı için bu işlem inceleyin. Daha fazla bilgi için [yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümlemek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Daralt ve bölüm başlığının yanındaki oku seçerek bu bölümü genişletin.

Yüzdelik değerler, aşağıdaki işlem bilgilerini bildirmek:

-   %90 toplamda işlemlerin tamamlandı küçüktür \<zaman > saniye.

-   %95 toplamda işlemlerin tamamlandı küçüktür \<zaman > saniye.

## <a name="system-under-test-resources"></a>Test kaynakları altındaki sistem

Test kaynakları bölümü altında sistem yükü oluşturulduğu hedef bilgisayarlar kümesi olan bilgisayarların listesini içerir. Bu sayaç kümeleri aracı veya denetleyici dışında topladığınız herhangi bir bilgisayarda içerir. Bilgisayar adı, % işlemci zamanı ve kullanılabilir bellek görüntülenir. Açmak için bir bilgisayar adı seçebileceğiniz **Test altındaki sistem** grafik ve zaman içinde kaynak kullanımını görün. Daha fazla bilgi için [Çözümle yük testi sonuçlarını grafik görünümünde](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Daralt ve bölüm başlığının yanındaki oku seçerek bu bölümü genişletin.

## <a name="controller-and-agent-resources"></a>Denetleyici ve aracı kaynakları

Denetleyici ve aracı kaynakları bölümü testi çalıştırmak için kullanılan bilgisayarların listesini içerir. Bilgisayar adı, % işlemci zamanı ve kullanılabilir bellek görüntülenir. Açmak için bir bilgisayar adı seçebileceğiniz **denetleyicisi ve aracıları** grafik ve zaman içinde kaynak kullanımını görün. Daha fazla bilgi için [Çözümle yük testi sonuçlarını grafik görünümünde](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Daralt ve bölüm başlığının yanındaki oku seçerek bu bölümü genişletin.

## <a name="errors"></a>Hatalar

Hatalar bölümüne yük testi sırasında gerçekleşen tüm hataların listesini içerir. Türünü ve alt hata sayısı ve son ileti görüntülenir. Hata seçebilirsiniz **hataları** tablo ve daha fazla hata ayrıntılarını inceleyin. Daha fazla bilgi için [yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümlemek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Daralt ve bölüm başlığının yanındaki oku seçerek bu bölümü genişletin.

## <a name="print-a-summary"></a>Bir Özet yazdırma

Yükleme testi özetini seçerek yazdırabilir **yazdırma** özeti kısayol menüsünde. Yazdırma ilk seçerek önizleyebilirsiniz **Baskı Önizleme** özeti kısayol menüsünde. Ayrıca, doğrudan önizleme ekranından yazdırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik kuralı ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)