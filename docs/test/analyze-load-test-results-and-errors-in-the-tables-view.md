---
title: Yük testi sonuçlarını ve hatalarını çözümleme
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f77653f8a099f66d751880c412e1532d4a23e656
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068571"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Yük testi sonuçlarını ve hatalarını Yük Testi Çözümleyicisinin Tablo görünümünde çözümleyin

Yük testi sonuçlarını görüntülemek, verileri analiz etmek için farklı şekillerde sağlayan farklı bölmeler görüntüleyebilirsiniz. Verileri, zaman içinde nasıl değiştiğini görmek için bir grafik olarak görüntüleyebileceğiniz veya verileri ayrıntılı tablo olarak görüntüleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tablo görünümüne geçmek için seçin **tabloları** üzerinde **yük testi** araç çubuğu. Farklı tablolar arasında geçiş yapmak için kullanın **tablo** tablo kılavuz yukarıda araç çubuğundaki aşağı açılan listesinde. Tablo Görünümü'nde, aynı anda en fazla dört tabloları görüntüleyebilirsiniz. Daha fazla bilgi için [kutucuk yük testi tabloları](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) bu konuda.

Performans sayaçları için bir tabloda gösterilen Çoğu sayısal değer tüm yük testi bunların toplamı olur. Adlandırılmış sütunlar **son** bir özel durum ve en son örnekleme aralığının değeri temsil eder.

> [!NOTE]
> Adlandırılmış sütunlar **son** yalnızca bir yük testi yürütülürken kullanılabilir. Bu sütunlar bir yük testi tamamlandıktan sonra kullanılabilir değil.

Üzerinde sıralama yapmak istediğiniz sütunun başlığını seçerek birçok tabloları sıralayabilirsiniz. Varsayılan olarak, tüm kullanılabilir sütunları bazı tablolar görüntülemez. Sütunları varsa, tablolar, sütunlar ekleyebilirsiniz. Sütun eklemek için tablonun sağ tıklayın ve ardından **sütunları Ekle/Kaldır**.

> [!NOTE]
> Ek çözümleme için Excel gibi diğer uygulamalara bir tablodan veri kopyalayabilirsiniz.

## <a name="the-load-test-tables"></a>Yük testi tabloları

Aşağıdaki tabloda, yük testi çalışmaları çözümlemek için kullanılabilir olan tabloları listeler.

|Tablo adı|Açıklama|
|-|-|
|Hatalar|Yük testi çalıştırması sırasında oluşan hataların listesini görüntüler. Daha fazla bilgi için [hataları tablosu](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) bu konuda, ve [Çözümle yük testi sonuçları](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Sayfaları|Yük testi çalıştırması sırasında erişilen sayfalarının bir listesini görüntüler. Yalnızca bir yük testi tamamlandıktan sonra bu tabloya bazı veriler kullanılabilir. Daha fazla bilgi için [nasıl yapılır: web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|İstekleri|Bir yük testi sırasında verilen tek tek isteklerin ayrıntılarını görüntüler. Bu, tüm HTTP isteklerini ve resimler gibi bağımlı istekleri içerir. Daha fazla bilgi için [Requests tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) bu konuda.|
|SQL izleme|SQL izleme sonuçlarını görüntüler. Bu tabloda yalnızca bir yük testi tamamlandıktan sonra ve yalnızca SQL izleme test sırasında kullanıldıysa kullanılabilir. Daha fazla bilgi için [SQL izleme verileri tablo](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) bu konuda.|
|Testler|Görüntüler Ayrıntılar bireysel testler için bir yük testi sırasında çalıştırın. Daha fazla bilgi için [testler tablosu](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) bu konuda.|
|Eşikleri|Yük testi çalıştırması sırasında gerçekleşen bir eşik kuralı ihlallerini listesini görüntüler. Daha fazla bilgi için [eşik kuralı ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|İşlemler|Bir yük testi çalıştırması sırasında gerçekleşen işlemleri listesini görüntüler. Daha fazla bilgi için [işlem tablonuzu](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) bu konuda.|
|Aracılar|Yalnızca Yük testinizi test denetleyicisi ve test aracıları kullanıyorsa görüntüler. Yük testi çalıştırması sırasında kullanılan aracılarının listesini görüntüler. Aracıları tablo, kaç tane test aracısı ve bu istekleri kaç tanesinin başarısız istekleri içerir. Ayrıca, aracıları tabloyu test aracısı yük testleri test karışımında ve bunlardan testlerin sayısı içeren kaç başarısız oldu.|
|Test ayrıntıları|Yük testi için test karışımını dahil testler için ayrıntıları görüntüler. Ayrıntılar, test, test, senaryoyu test başlangıç zamanı, test çalıştırmak için geçen süre ve test geçti veya başarısız belirten test sonucu uzunluğunu adını içerir. Test başarısız olursa, bir bağlantı bulunur **ayrıntıları** sütun. Web Performans Testi Düzenleyicisi için vurgulanan başarısız istekle alacak bağlantıyı seçebilirsiniz.|

## <a name="collect-percentile-data"></a>Yüzdelik veri topla

 Bazı yük testi tabloları yüzde birlik veri ve yanıt sürelerini üzerindeki ağ öykünme göre gruplara ayrılmış içeren ek sütunlar içerebilir. Varsayılan olarak, bu verileri toplanmaz. Yüzdelik veri yalnızca sonuçları veritabanına kaydetme ve yerel olarak değil kaydettiğinizde kullanılabilir. Daha fazla bilgi için [yönetme yük testi sonuçları yük testi sonuçları deposunda](../test/manage-load-test-results-in-the-load-test-results-repository.md). Ayrıca, bu verileri toplamak için **Yük Testi Düzenleyicisi**altında **çalıştırma ayarları** belirli çalıştırma ayarını düğüm değiştirmek için düğümü seçin. İçinde **özellikleri** penceresinde için **Zamanlama Ayrıntıları Deposu** özelliği, select **StatisticsOnly** veya **AllIndividualDetails**. Daha fazla bilgi için [nasıl yapılır: web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>İstekler tablosu

 **İstekleri** tablo, bir yük testi sırasında verilen tek tek isteklerin ayrıntılarını görüntüler. Bu, tüm HTTP isteklerini ve resimler gibi bağımlı istekleri içerir. Bir istek birçok testleri ve senaryoya dahil olduğundan tablo, test ve senaryoya göre istekleri listeler.

 Aşağıdaki tablo sütunları listeler **istekleri** tablosu:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|**İstek**|İsteğin URL'si. Örneğin, *home.html*, veya *turuncu arrow.gif*.|Evet|
|**Senaryo**|Senaryonun adı.|Evet|
|**Test**|Testin adı.|Evet|
|**Toplam**|Çalıştırılan yük testi sırasında verilen bu web performans testi isteği toplam sayısı. Toplam başarılı ve başarısız istekler dahildir, ancak önbelleğe alınmış istekler web sunucusuna verilmediği içermez.|Evet|
|**Geçirilen**|İstek verilen ve geçirilen sayısı.|Hayır|
|**Başarısız**|İstek verilen ve başarısız sayısı. Bu sütun girişleri köprü olarak gösteriliyor. Hataları ayrı ayrı bir listesini görüntülemek için herhangi bir köprüye seçebilirsiniz **yük testi hataları** iletişim kutusu. Daha fazla bilgi için [Çözümle yük testi sonuçları](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Evet|
|**Önbelleğe alınmış**|Toplam istek önceden önbelleğe alınmış sayısı.|Hayır|
|**İsteği/sn**|Yük testi çalıştırması sırasında istek saniye oranı.|Hayır|
|**Geçirilen/sn**|Bu istek, geçirilen bu isteğin örnekleri için yük testi sırasında saniye oranı.|Hayır|
|**Saniye başına başarısız oldu**|Bu istek, başarısız olan bu isteğin örnekleri için yük testi sırasında saniye oranı.|Hayır|
|**İlk bayta kalan süre**|Yanıtı ilk baytı almanın ortalama süresi isteğin web sunucusuna gönderilen zamandan itibaren ölçülür. Saniye birimleridir.|Hayır|
|**Yanıt süresi**|Bir istek için tüm yanıt almak için ortalama süresi isteğin web sunucusuna gönderilen zamandan itibaren ölçülür. Saniye birimleridir.|Evet|
|**İçerik uzunluğu**|Ortalama isteğe yanıt içeriği uzunluğu. Bayt birimleridir.|Evet|

## <a name="the-tests-table"></a>Testler tablosu

 **Testleri** tablo, bir yük testi sırasında bireysel testler için ayrıntıları görüntüler. Bir test pek çok senaryoda eklenebilir olduğundan tablo, testleri test ve senaryoya göre listeler.

 Aşağıdaki tablo sütunları listeler **testleri** tablo.

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|**Test**|Testin adı.|Evet|
|**Senaryo**|Senaryonun adı.|Evet|
|**Toplam**|Test senaryosunda çalıştırılma sayısı. Bu, test başarılı ve başarısız olma sayısı içerir.|Evet|
|**Geçirilen**|Test senaryosunda çalıştırın ve geçirilen sayısı.|Evet|
|**Başarısız**|Testin senaryoda çalıştırın ve başarısız olma sayısı. Bu sütun girişleri köprü olarak gösteriliyor. Hataları ayrı ayrı bir listesini görüntülemek için herhangi bir köprüye seçebilirsiniz **yük testi hataları** iletişim kutusu. Daha fazla bilgi için [Çözümle yük testi sonuçları](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Evet|
|**Testleri/sn**|Test yük testi çalıştırması sırasında saniye oranı.|Evet|
|**Geçirilen/sn**|Bu test, geçirilen bu test örnekleri için yük testi sırasında saniye oranı.|Hayır|
|**Saniye başına başarısız oldu**|Bu testi, başarısız olan bu test örnekleri için yük testi sırasında saniye oranı.|Hayır|
|**Test süresi**|Yük testi çalıştırması sırasında testi yürütmek için geçen ortalama süre. Saniye birimleridir.|Evet|
|**%90 test süresi**|Test süresi 90. yüzdebirlik değeri.|Hayır|
|**%95 test süresi**|Test süresi 95. yüzdebirlik değeri.|Evet|
|**İstekleri ve Test**|Testi varsa bir web performans testindeki istekleri ortalama sayısı.|Hayır|

## <a name="the-transactions-table"></a>İşlem tablosu

 **İşlemleri** tablo, bir yük testi çalıştırması sırasında gerçekleşen işlemleri listesini görüntüler. İşlem bir web performans testi içinde tanımlanan işlemlere ya da bir birim testi içinde tanımlanan sayaçlara başvurur bakın. İşlem, veritabanı işlemlerine başvurmaz.

 Aşağıdaki tablo sütunları listeler **işlemleri** tablo.

> [!NOTE]
> Tüm sütunları görüntülemek için etkin çalışma ayarı ile ilişkili Zamanlama Ayrıntıları Deposu özelliğini etkinleştirmeniz gerekir. Daha fazla bilgi için [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Sütun|Açıklama|Zamanlama Ayrıntıları olmadan da görünür|
|-|-|-|
|**İşlem**|İşlemin adı.|Evet|
|**Senaryo**|Senaryonun adı.|Evet|
|**Test**|Testin adı.|Evet|
|**Toplam**|Yük testi çalıştırması sırasında gerçekleştirilen işlemlerin toplam sayısı.|Evet|
|**İşlem süresi**|Yük testi çalıştırması sırasında işlem yürütme süresi. Web performans testleri için süresi hesaplamaya dahil düşünün. Saniye birimleridir.|Hayır|
|**Yanıt süresi**|Yük testi içinde web performans testi işlemi için yanıt süresi. Yanıt süresi Düşünme zamanlarını içermez, yanıt süresi farklı işlem süresi'nden, işlem sırasında gerçekleşen zaman. Saniye birimleridir.|Hayır|
|**Ortalama İşlem süresi**|Ortalama işlem süresi. Bu süre Düşünme süreleri de dahildir. Örneğin, üç taleplere sahip ve her bir Düşünme süresi vardır, bu kez içerecektir olanlar Düşünme süreleri ve yürütmek için gerçek süre ister.|Hayır|
|**Ortalama Yanıt süresi**|Yük testi içinde web performans testi işlemi için ortalama yanıt süresi. Yanıt süresi Düşünme zamanlarını içermez, yanıt süresi farklı işlem süresi'nden, işlem sırasında gerçekleşen zaman. Saniye birimleridir.|Hayır|
|**En az yanıt süresi**|Bu, Düşünme zamanlarını içermez.|Hayır|
|**En yüksek yanıt süresi**|Bu, Düşünme zamanlarını içermez.|Hayır|
|**ORTANCA yanıt süresi**|Bu, Düşünme zamanlarını içermez.|Hayır|
|**% 90 yanıt süresi**|İşlem süresi 90. yüzdebirlik değeri. Bu, Düşünme zamanlarını içermez. **Not:** bu Visual Studio Team System 2008 Test Yükleme kullanılan Aracısı, farklı **%90 işlem süresi** değeri.|Hayır|
|**% 95 yanıt süresi**|95. yüzdebirlik işlem süresi için. Bu, Düşünme zamanlarını içermez. **Not:** bu Visual Studio Team System 2008 Test Yükleme kullanılan Aracısı, farklı **%95 işlem süresi** değeri.|Hayır|
|**% 99 yanıt süresi**|İşlem süresi 99. yüzdebirlik değeri. Bu, Düşünme zamanlarını içermez.|Hayır|
|**Std sapma yanıt süresi**|Bu, Düşünme zamanlarını içermez.|Hayır|

## <a name="the-errors-table"></a>Hataları tablosu

 Bir yük testi çalıştırdığınızda oluşan hataları analiz edebilirsiniz. Hataları analiz etme ve testlerinizi ayarlama yük test işleminin önemli bir parçasıdır. Herhangi bir hata oluştuysa, bir **hataları** köprü yük testi durum çubuğunda görünür ve oluşan hataların sayısını belirtir. Hatalar tablosunu görüntülemek için köprüyü seçin.

 Hata türü ve alt hata türüne göre grupları bir yükleme sırasında oluşan hatalar test tablo. Ayrıca bir **toplam** gerçekleşen tüm hataların toplam sayısını belirten bir tablo satır.

 Hataları tablo şu sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Tür|Hata türü. Örneğin, HTTP hatası.|Evet|
|SubType|Hatanın alt türü. Örneğin, LoadTestException.|Evet|
|Sayısı|Bu türdeki yük testi sırasında oluşan hataları sayısı. Bu sütun girişleri köprü olarak gösteriliyor. Hataları ayrı ayrı bir listesini görüntülemek için herhangi bir köprüye seçebilirsiniz.|Evet|
|Son ileti|Hatayı açıklayan ileti. Örneğin, 404 - bulunamadı.|Evet|

 Daha fazla bilgi için [yük testi tablolarla çalışma](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Hata listesinde detaya gidin

Hata türü ve alt hata türüne göre gruplandırır tablo. Hataları ayrı ayrı tablosunu görüntülemek için görüntü **yük testi hataları** iletişim kutusu. İletişim kutusunu görüntülemek için köprü seçin **sayısı** hataları tablosunda sütun. İletişim kutusu doldurulur hataları tablosunda bir satıra sağ tıklayıp seçerek görüntüleyebilirsiniz **hataları**.

> [!NOTE]
> Herhangi bir hata türüne ve alt birleşimini yalnızca ilk 1.000 örnekleri toplanır. Görüntülediğinizde **yük testi hataları** iletişim kutusu, en fazla hata ilk 1.000 örnekler göreceksiniz.

**Yük testi hataları** tablo şu sütunları içerir:

|Sütun|Açıklama|
|-|-|
|**saat**|Hatanın gerçekleştiği süre boyunca yük test edin.|
|**Aracı**|Hatanın gerçekleştiği aracı bilgisayar adı. Test denetleyicileri ve test aracılarını kullanarak yük testi çalıştırdığınızda, bu önemlidir. Daha fazla bilgi için [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Web performans adını test, bir hata oluştu.|
|**Senaryo**|Hatanın gerçekleştiği Senaryo adı.|
|**İstek**|Hatanın gerçekleştiği istek URL'si.|
|**Türü**|Hata türü. Örneğin, HTTP hatası.|
|**Alt tür**|Hatanın alt türü. Örneğin, LoadTestException.|
|**Metin**|Hata iletisi metni görüntülenir. Örneğin, 404 - bulunamadı.|
|**Yığın**|Bu sütundaki boş veya word girişler **yığın** köprü olarak biçimlendirilir. Hatanın bir yığın izlemesini görüntülemek için köprüyü seçebilirsiniz.|
|**Ayrıntıları**|Bu sütundaki boş veya word girişler **TestLog** köprü olarak biçimlendirilir. Bu bağlantı, yük testi hataları yalıtmaya yardımcı olabilir. Örneğin, seçme **TestLog** bir web performans testi isteği hatası bağlantısını için Web Performans Test Sonuçları Görüntüleyicisi'ndeki web performans test sonuçları açın ve istek hatası vurgulayın.|

> [!NOTE]
> Tablo, sütun üst bilgilerini seçerek sıralayabilirsiniz.

## <a name="the-sql-trace-data-table"></a>SQL izleme verileri tablo

Daha sonra çözümlemek için bir yük testi sırasında izlenecek SQL izleme verilerini toplayabilir. İzleme verilerini toplamak, test edilen SQL Server veritabanında saklı yordamlar ve en yavaş çalışan sorguları belirlemenize olanak tanır.

SQL izleme etkin olduğunda izleme verilerini içeren yük testi çalıştırması sırasında bir dosya oluşturulur. Bu veriler yük testi sonuçları Store test çalışmasının sonunda otomatik olarak kaydedilir ve izleme dosyası silindi. İzleme verilerini analiz **SQL İzleme** yük testi tamamlandıktan sonra tablo.

### <a name="to-view-sql-trace-data"></a>SQL izleme verilerini görüntülemek için

1. Yük Testi Çözümleyicisi'nde seçin **tabloları** araç çubuğundaki tablo kılavuzunu görüntülendiğinden emin olun.

2. İçinde **tablo** aşağı açılan liste kutusunda **SQL İzleme**.

3. Kılavuzda çalıştırma sırasında toplanan izleme verileri görüntülenir. Tablo, en yavaş üst süreye göre sıralanmış yavaş çalışan SQL işlemleri listeler. Genellikle, **süresi** incelemek için ilk sütunda bir sütundur. Milisaniye cinsinden veriler görüntülenir.

   Görüntülenen sütunları aşağıdaki gibidir:

    - **Olay sınıfı**

    - **Süresi**

    - **CPU**

    - **Okur**

    - **Yazar**

    - **TextData**

    - **startTime**

    - **EndTime**

   Bu sütunlarda belirtilen veri dışında SQL olaylarını izlemek istiyorsanız, Visual Studio'dan ayrı SQL Profiler aracını kullanarak kendi özel SQL izleme ayarlayabilirsiniz.

## <a name="tile-load-test-tables"></a>Kutucuk yük testi tabloları

Yük testi sonuçlarını görüntülemek, verileri ayrıntılı tablo olarak görüntüleyebilirsiniz. Tablo görünümüne geçmek için seçin **tabloları** üzerinde **yük testi** araç çubuğu. Kullanılabilir tablolar **hataları**, **sayfaları**, **istekleri**, **SQL İzleme**, **testleri**,  **Eşikleri**, ve **işlemleri**. Daha fazla bilgi için [yük testi tablolarla çalışma](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Tablo Görünümü'nde çakışmadan aynı anda en fazla dört tabloları görüntüleyebilirsiniz.

### <a name="to-tile-tables"></a>Kutucuğa tabloları

1. Üzerinde **Yük Testi Çözümleyicisi** araç seçin **tabloları**.

     Tablo görünümü açılır. Varsayılan düzen iki yatay Panel ' dir.

2. Üzerinde **Yük Testi Çözümleyicisi** araç seçin **Düzen** düğmesine tıklayın ve sonra aşağıdaki seçeneklerden birini seçin:

    - **Tek bir Panel**

    - **İki yatay panel**

    - **Üç yatay panel**

    - **Dört yatay panel**

3. Farklı tablolar arasında geçiş yapmak için her panelinde Tablo Kılavuz Yukarıdaki açılan listeyi kullanın.

    > [!NOTE]
    > Aynı tabloda birden fazla panelde görüntülenemiyor. Zaten başka bir panel içinde görüntülenen bir tabloya bir bölmede görüntülenen tablo değiştirirseniz panellerin tabloları geçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: erişim yük testi sonuçlarını çözümleme](../test/how-to-access-load-test-results-for-analysis.md)
- [Grafik görünümünde yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Eşik kuralı ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testi sonuçları deposu içindeki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)