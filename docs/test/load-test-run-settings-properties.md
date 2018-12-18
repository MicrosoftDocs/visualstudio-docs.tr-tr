---
title: Yük testi çalıştırma ayarları
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9b0123ba4e6f9565cc31f63a23bb0be0b5bee344
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895502"
---
# <a name="load-test-run-settings-properties"></a>Yük testi çalıştırma ayarları özellikleri

Çalıştırma ayarları yük testinin çeşitli test sonuçları koleksiyon ayrıntı düzeyi ve test çalıştığında toplanan sayaç kümeleri süresi dahil olmak üzere, diğer ayarları belirleyin. Oluşturun ve her bir yük testi için birden çok çalışma ayarlarını depolamak ve ardından test çalıştırması sırasında kullanmak için belirli bir ayar seçin. İlk çalıştırma ayarı kullanarak yük testi oluşturduğunuzda, yük testinize eklenir **Yeni Yük Testi Sihirbazı**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki tablolar, yük testi çalıştırma ayarındaki çeşitli özelliklerini açıklar. Bu özellikler, belirli yük testi gereksinimlerini karşılayacak şekilde değiştirebilirsiniz.

Daha fazla bilgi için [yapılandırma yük testi çalıştırma ayarları](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Genel Özellikler

|Özellik|Tanım|
|-|----------------|
|**Açıklama**|Çalıştırma ayarları açıklaması.|
|**Tür başına en fazla hata**|Yük testi için kaydedilecek türü başına hatalarının sayısı.<br /><br /> Sahip olduğunuz, ancak bunun yapılması ayrıca boyutu ve yük testi sonucu işlem süresi artar, bu sayıyı artırabilirsiniz.|
|**Raporlanan en yüksek istek URL'si**|Benzersiz web performans testi sayısı, bu yük testi sonuçlarında bildirmek URL'leri isteyin.<br /><br /> Sahip olduğunuz, ancak bunun yapılması ayrıca boyutu ve yük testi sonucu işlem süresi artar, bu sayıyı artırabilirsiniz.|
|**En yüksek Eşik ihlalleri**|Bu yük testi için kaydedilecek eşik ihlallerinin sayısı.<br /><br /> Sahip olduğunuz, ancak bunun yapılması ayrıca boyutu ve yük testi sonucu işlem süresi artar, bu sayıyı artırabilirsiniz.|
|**Uygulama etki alanında birim testleri çalıştırma**|Her birim test bütünleştirilmiş kodu birim testleri yük testi içeren bir ayrı uygulama etki alanında çalışmasını olup olmadığını belirleyen bir Boole değeri. True varsayılan ayardır.<br /><br /> Birim testleriniz düzgün çalışması için bir ayrı uygulama etki alanı ya da app.config dosyası gerekmiyorsa, birim testleriniz daha hızlı bir şekilde bu özelliğin değerini ayarlayarak çalışabilir `False`.|
|**Ad**|Gibi çalışma ayarı adı görünür **çalıştırma ayarları** düğümünün **Yük Testi Düzenleyicisi**.|
|**Doğrulama düzeyi**|Bu, en yüksek bir yük testi içinde çalışacak doğrulama kuralı düzeyini tanımlar. Doğrulama kuralları, web performans testi istekleri ile ilişkilidir. Doğrulama kuralı her bir ilişkili doğrulama düzeyi vardır: **yüksek**, **orta**, veya **düşük**. Bu yük testi çalışma ayarı hangi doğrulama kuralları, yük testi içinde web performans testi çalıştırırken çalışacak belirtin. Örneğin, bu ayar çalıştırırsanız ayarlanır **orta**, tüm doğrulama kuralları olarak işaretlenmiş **orta**, veya **düşük** çalıştırılır.|

## <a name="logging-properties"></a>Günlüğe kaydetme özellikleri

|Özellik|Tanım|
|-|----------------|
|**En yüksek Test günlüğü**|Yük testi için kaydedilecek test günlüklerinin sayısını belirtir. Maksimum sayısı için girilen değer test günlüklerinin ulaşıldığında, yük testi günlükleri toplamayı durdurur. Bu nedenle, günlükleri, test, son başında toplanacak. Yük testi tamamlanana kadar çalışmaya devam eder.|
|**Tamamlanmış Testler'in günlükleme sıklığı Kaydet**|Test günlüğü yazılacak sıklığını belirtir. Girilen her test sayısı yetersiz bir test günlüğüne kaydedilecek sayıyı belirtir. Örneğin, on değerinin girilmesi onda, 20, otuzuncu ve benzeri test günlüğüne yazılacağını belirtir. Değer 0 olarak ayarlandığında, hiçbir test günlüğü kaydedilecek belirtir.|
|**Test başarısızlıkları Günlüğü Kaydet**|Belirleyen bir Boole değeri olup olmadığını test günlüklerinin bir yük testi içinde bir test başarısız olursa kaydettiyseniz. Varsayılan, `True` değeridir.<br /><br /> Daha fazla bilgi için [nasıl yapılır: test başarısızlıklarının test günlüklerini kaydedilip kaydedilmediği belirleme](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

 Daha fazla bilgi için [Değiştir yük test günlüğü ayarları](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Sonuçları Özellikleri

|Özellik|Tanım|
|-|----------------|
|**Depolama türü**|Bir yük testinde elde edilen performans sayaçları saklanacağı yol. Seçenekleri aşağıdaki gibidir:<br /><br /> -   **Veritabanı** -içeren bir SQL veritabanını gerektiren bir **yük testi sonuçları Store**.<br />-   **Hiçbiri**.|
|**Zamanlama Ayrıntıları Deposu**|Bu ayrıntılar barındırılacaktır belirlemek için kullanılan **yük testi sonuçları Store**. Üç değerler kullanılabilir:<br /><br /> -   **AllIndividualDetails** - toplamak ve her test, hareket ve sayfa çalıştırılmış veya yük testi sırasında verilen kişisel zamanlama değerlerini depolamak **yük testi sonuçları Store**. Kullanmayı planlıyorsanız gereklidir **sanal kullanıcı aktivite grafiği** içinde **Yük Testi Çözümleyicisi**.<br />     Daha fazla bilgi için [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Hiçbiri** -herhangi bir kişisel zamanlama değerlerini toplamaz. Visual Studio 2013 Update 4 ve sonraki sürümleri için varsayılan değer budur.<br />-   **StatisticsOnly** - toplamak ve her test, hareket ve yürütülen veya yük testi sırasında verilen sayfa için kişisel zamanlama değerlerini depolamak yerine yalnızca istatistiklerini depolamak **yük testi sonuçları Store**.<br /><br /> Daha fazla bilgi için [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>SQL izleme özellikleri

|Özellik|Tanım|
|-|----------------|
|**İzlenen SQL işlemleri'nin en düşük süresi**|Milisaniye cinsinden SQL izleme tarafından yakalanması için bir SQL işleminin en düşük süre. Örneğin, bu, yük altındayken yavaş SQL işlemleri bulmak çalışıyorsanız, hızlı bir şekilde tamamlamak işlemleri yoksay olanak sağlar.|
|**SQL izleme bağlantı dizesi**|İzlenecek veritabanına erişmek için kullanılan bağlantı dizesi.|
|**SQL izleme dizini**|Konum izleme sona erdikten sonra SQL izleme dosyasının nereye yerleştirilir. Bu dizin, SQL Server için yazma izinlerine sahip ve denetleyici için okuma izni gerekir.|
|**SQL izleme etkin**|Bu SQL işlemleri izlemesini sağlar. Varsayılan değer `False` şeklindedir.|

## <a name="test-iterations-properties"></a>Test Yinelemeleri özellikleri

|Özellik|Tanım|
|-|----------------|
|**Test yinelemeleri**|Yük testi tamamlanmadan önce çalıştırılacak testlerin toplam sayısını belirtir. Bu özellik yalnızca özelliği "Test Yinelemeleri Kullan" olduğunda geçerlidir `True`.|
|**Test Yinelemeleri Kullan**|Test Yinelemeleri Kullan ise `True`, yükleme testi yük testi içinde tamamlanmış tek tek testlerin sayısı "Test Yinelemeleri" özelliği tarafından belirtilen sayı ulaşıncaya kadar çalışır. Bu durumda, süre, çalışma süresi ve soğuma süresi olan zamana bağlı ayarları sıcak göz ardı edilir. "Test Yinelemeleri Kullan" ise `False`, tüm zamanlama ayarları uygulamak ve "Test Yinelemeleri" göz ardı edilir.|

 Daha fazla bilgi için [nasıl yapılır: bir çalışma ayarında test yineleme sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Zamanlama özellikleri

|Özellik|Tanım|
|-|----------------|
|**Soğuma süresi**|Test soğuma döneminin süresi ss biçiminde ifade edilir. Yük testi çalışmayı tamamladıktan sonra Yük testi içinde tek tek testlerin hala çalışıyor olabilir. Bekleme dönemi boyunca, bu testler tamamlandıktan veya soğuma döneminin sonuna ulaşılana kadar devam edebilirsiniz. Varsayılan olarak, hiçbir bekleme süresi yoktur ve bireysel testler yük testi çalıştırma süresi ayarına göre tamamlandığında sonlandırılır.|
|**Çalıştırma süresi**|Ss biçimindeki test uzunluğu.|
|**Örnek hızı**|Aralığı ss biçimindeki performans sayacı değerlerini yakalamak.<br /><br /> Daha fazla bilgi için [nasıl yapılır: örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Isınıyor süresi**|Test başına ve veri örnekleri ss biçiminde kaydedilen başlattığınızda arasındaki süre. Bu örnek değerleri kaydetmeden önce belirli bir yük düzeyine ulaşmak için sanal kullanıcı yük adımlamak için sık kullanılır. Isınma süresi sona erdikten içinde gösterilmeden önce yakalanan örnek değerler **Yük Testi Çözümleyicisi**.|

## <a name="webtest-connections-properties"></a>WebTest bağlantıları özellikleri

|Özellik|Tanım|
|-|----------------|
|**WebTest Bağlantı modeli**|Bu, web sunucusu çalıştıran bir yük testi içinde web performans testleri için yük test aracısından bağlantı kullanımını denetler. Üç web performans testi bağlantı modeli seçenekleri kullanılabilir:<br /><br /> - **Kullanıcı başına bağlantı** model gerçek bir tarayıcı kullanarak bir kullanıcının davranışını taklit eder. Internet Explorer 6 ya da Internet Explorer 7 simülasyonu yapıldığında, bir web performans testi çalıştıran her bir sanal kullanıcı web sunucusuna bir veya iki adanmış bağlantıları kullanır. İlk istek web performans testinde verildiğinde, ilk bağlantı kurulur. İkinci bir bağlantı içeren bir sayfada birden fazla bağımlı istek olduğunda kullanılabilir. Bu istekler, iki bağlantı kullanarak paralel olarak verilir. Bu bağlantılar, web performans testinde istekler için yeniden kullanılır. Web performans testi tamamlandığında bağlantıları kapatılır. Bu model bir dezavantajı, aracı bilgisayarında açık tutulması bağlantı sayısı (iki kez kullanıcı yükü en fazla) yüksek olabilir ' dir. Sonuç olarak, bu yüksek bağlantı sayısını desteklemek için gerekli kaynakları tek yük test aracısından kullanıcı yükü sınırlayabilir. Internet Explorer 8 simülasyonu yapıldığında, altı adet eş zamanlı bağlantı desteklenir.<br />- **Bağlantı havuzu** modeli, web sunucusunun birden çok sanal web performans testi kullanıcıları arasında bağlantı paylaşarak kaynaklar üzerinde yük testi aracısı korur. Kullanıcı yükü bağlantı havuzu boyutundan daha büyükse, farklı sanal kullanıcılar tarafından çalıştırılan web performans testleri bir bağlantıyı paylaşır. Bu, bir web performans testini başka bir web performans testi bağlantısı kullanılırken bir isteği bildirmeden önce beklemeniz gerekebilir gelebilir. Yük testi başarım sayacı Ortalama bağlantı bekleme süresi tarafından izlenen bir istek gönderdiğinde, web performans testi ortalama süreyi bekler. Bu sayı, bir sayfa için ortalama yanıt süresi değerinden küçük olmalıdır. Yüklü değilse, bağlantı havuzu boyutu büyük olasılıkla çok küçük.<br />- **Test Yinelemesi başına bağlantı** modeli, her test yinelemesine için adanmış bağlantıları kullanımını belirtir.|
|**WebTest Bağlantı havuzu boyutu**|Bu, yük testi aracısı ve Web sunucusu arasında bağlantı maksimum sayısını belirtir. Bu yalnızca geçerlidir **bağlantı havuzu** modeli.|

##  <a name="change-run-setting-properties"></a>Çalıştırma ayarı Özellikleri Değiştir
 Yük testi farklı koşullar altında çalıştırabilmeniz için daha fazla yük testinize farklı özellik ayarları ile çalışma ayarları ekleyebilirsiniz. Örneğin, yeni bir test ayarı ekleyin ve farklı bir örnek hızı kullanabilir veya bir uzun çalıştırma süresi belirtin. Yalnızca bir çalışma ayarı teker teker kullanabilirsiniz ve etkin olarak işaretleyerek kullanmak için ayarı çalıştırdığınız belirtmeniz gerekir. Bir örnek için bkz. [nasıl yapılır: çalışma ayarları yük testi için etkin seçmek](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

### <a name="to-change-run-settings"></a>Çalıştırma ayarlarını değiştirmek için

1.  Bir yük testi açın.

2.  Genişletin **çalıştırma ayarları** klasör.

3.  Seçin bir **çalıştırma ayarları** düğümü.

4.  Üzerinde **görünümü** menüsünde seçin **Özellikler penceresi**.

     **Özellikler penceresi** görüntülenir ve seçili çalıştırma ayarı özellikleri görüntülenir.

5.  Kullanım **Özellikler penceresi** çalıştırma ayarlarını değiştirmek için. Örneğin, çalışma süresini **00:05:00** testiniz için beş dakika çalıştırılacak.

    > [!NOTE]
    > Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi çalıştırma ayarı özellikleri](../test/load-test-run-settings-properties.md).

6.  Özellikleri değiştirme işiniz bittiğinde, yük testinizi kaydedin. Üzerinde **dosya** menüsünde seçin **Kaydet**.

> [!NOTE]
> Sayaç kümesi eşlemeleri çalışma ayarları, aynı zamanda bir parçasıdır. Daha fazla bilgi için [sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testinde belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)