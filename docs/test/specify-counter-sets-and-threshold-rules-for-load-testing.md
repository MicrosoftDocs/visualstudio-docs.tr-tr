---
title: Sayaç kümelerini ve eşik kuralları, yük testi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3cbdd30022b521803662f18b8d3438c6b1ddb37c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057424"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testi içinde belirtin.

Yükleme testleri, performans sayacı verilerini çözümlediğinizde kullanışlı olan adlandırılmış sayaç kümeleri sağlar. Sayaç kümeleri teknoloji ile düzenlenir ve uygulama, ASP.NET, .NET uygulaması, IIS ve SQL içerir. Kullanarak bir yük testi oluşturduğunuzda **Yeni Yük Testi Sihirbazı**, bir başlangıç sayaç kümesini ekleyin. Bu, Yük testiniz için önceden tanımlanmış ve önemli sayaç kümeleri kümesini sunar. Sayaçlarınızı yönettiğiniz **Yük Testi Düzenleyicisi**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testlerinizi Uzak makinelerde dağıtılmışsa, denetleyici ve aracı sayaçları denetleyicisi ve aracısı için eşlenen sayaç kümeleri. Uzak makinede yük testinizde kullanma hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracılarını](configure-test-agents-and-controllers-for-load-tests.md).

Sayaç kümeleri, belirttiğiniz bilgisayarlarda toplanır. Bir sayaç kümesi ve bir yük testi sırasında kullanılan bir bilgisayar arasında bir ilişkilendirmedir bir *sayaç kümesi eşlemesi*. Örneğin, test ettiğiniz web sunucusu, ASP.NET, IIS olabilir ve .NET uygulama sayaç kümesi eşlemelerine.

Varsayılan olarak, performans sayaçları, denetleyici ve aracılar üstünde toplanır. Daha fazla bilgi için [Test denetleyicileri ve test aracılarını](configure-test-agents-and-controllers-for-load-tests.md).

Sayaçları toplamak bilgisayara listesine test altındaki sunucular eklemek önemlidir. Ardından, herhangi bir önemli sistem veri toplanır ve yük testi sırasında izlenir.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için sayaç kümelerini Yönet:** yük testinizi oluşturduktan sonra sayaç kümesi Yük Testi Düzenleyicisi'ni düzenleyebilirsiniz. Sayaç kümelerini yönetme, performans verilerini toplamak istediğiniz bilgisayar kümesini seçme ve atama her bir bilgisayardan toplamak için sayaç kümeleri kümesini içerir. Sayaçlarınızı Yükleme Testi Düzenleyicisi'nde yönettiğiniz.|-   [Nasıl yapılır: sayaç kümelerini Yönet](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Sayaç kümeleri, yük testinize ekleyin:** ile bir yük testi oluşturduğunuzda, **Yeni Yük Testi Sihirbazı**, bir başlangıç sayaç kümesini ekleyin. Bu, Yük testiniz için ön tanımlı sayaç kümeleri kümesini sunar. Bir yük testi oluşturduktan sonra Yük Testi Düzenleyicisi'ni kullanarak mevcut sayaç kümeleri yeni sayaçları ekleyebilirsiniz.|-   [Nasıl yapılır: sayaç kümelerine sayaç ekleme](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Nasıl yapılır: özel sayaç kümeleri ekleme](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Yük testiniz için sayaçlarını kullanarak bir eşik kuralı belirtin:** bir eşik kuralı bir tek performans sayacı üzerinde bir yük testi sırasında sistem kaynak kullanımını izlemek için ayarlanmış bir kuraldır. Sayaç kümesi tanımları, birçok önemli performans sayaçları için önceden tanımlanmış eşik kuralları içerir. Yük testlerindeki eşik kuralları, bir performans sayacı değeri bir sabit değer ya da başka bir performans sayacı değeri ile karşılaştırın.|-   [Nasıl yapılır: bir eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Sayaç kümeleri eşlendi bilgisayarlara kolay adları atayın:** bir kolayca tanınan adı bir bilgisayara uygulanan olanak sağlayan bir bilgisayar etiketleri ekleyebilirsiniz. Etiketler görüntülenir **sayaç kümesi eşlemeleri** Yük Testi Düzenleyicisi'nde ağaç düğümü. Daha da önemlisi, etiketleri görüntülenir rolünü belirlemede yardımcı Excel raporlarını yük testinde, örneğin, "Lab2 içinde Web Sunucu1" bilgisayarında veya "SQL Server2 Phoenix Office".<br /><br /> Daha fazla bilgi için [rapor yük testleri için test karşılaştırmaları veya eğilim analizi sonuçları](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Sayaç kümeleri kullanma

Yük testi araçları, toplamak ve zaman içinde sayaçlarını kullanarak performans verileri grafiği. Sayaç verileri yük testi çalıştırması sırasında kullanıcı tarafından belirtilen aralıklarla toplanır. Daha fazla bilgi için [nasıl yapılır: örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Çalışma zamanında sayaçları görüntüleyebilir veya sonra kullanarak yük testi görüntüleyebilirsiniz *Yük Testi Çözümleyicisi*.

Sayaç verileri sunucusunda ve herhangi bir bilgisayarda bir testin çalıştırıldığı toplanır. Sayaçlar, testlerinizi çalıştırmak Aracı bilgisayarların bir dizi ayarladıysanız, bu bilgisayarlarda de toplanır.

Üç sayaç kategorisi vardır: yüzde, sayıları ve ortalamalar. CPU kullanım yüzdesi, SQL Server kilit sayıları ve saniye başına istek IIS örnek verilebilir.

![Yük Testi Sayaç kümeleri](../test/media/loadtestcountersets.png)

Tek tek HTTP istekleri için performans verilerini bir testi çalıştıran bilgisayar tarafından raporlanır. Aracı bilgisayar gibi. İstekleri için ortalama süre ilk baytı, yanıt süresi ve saniye başına istek sayısı gibi verileri izlemek.

Visual Studio Enterprise, bir web sunucusunda performans verileri koleksiyonunu kolaylaştırmak için yük testleri kullanmak için önceden tanımlanmış, adlandırılmış sayaç kümeleri, ayrıca sağlar. Bu ayarlar, IIS, ASP.NET veya SQL Server çalıştıran bir sunucuya çözümlerken yararlıdır. Yük Testi Düzenleyicisini kullanılarak sayaç varsayılan kümesini sağlanmayan sayaçları eklenebilir. Bu bilgisayarlar kaynak kullanımını izleyebilirsiniz emin olmak için yük testi için bilgisayarları veya test edilen sunucuları eklemek önemlidir. Daha fazla bilgi için [nasıl yapılır: sayaç kümelerini Yönet](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Yük çalıştırmalar sonuçları analiz sık kümesi eşik kuralları ve ölçümün uygulamadaki belirli bir sorun olduğunda anlattığını nasıl yerde toplamak için hangi verilerin öğrenmek için etki alanına özgü belirli bir alanın bilinmesini gerektirir. Daha fazla bilgi için [eşik kuralları hakkında](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Performans sayacı örnekleme aralığı hakkında önemli noktalar

Uygun bir değer seçin **örnek hızı** özelliği yük testinde çalışma ayarları yük testinizin uzunluğuna göre. Varsayılan değer olarak beş saniye gibi küçük bir örnekleme hızı yükleme testi sonuçları veritabanı daha fazla alan gerektirir. Daha uzun yük testleri için örnek hızı artırmak, toplanan veri miktarını azaltır. Daha fazla bilgi için [nasıl yapılır: örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek hızlara ait bazı Kılavuzlar şunlardır:

|Yük testi süresi|Önerilen örnek hız|
|-|-----------------------------|
|\< 1 saat|5 saniye|
|1−8 saat|15 saniye|
|8−24 saat|30 saniye|
|> 24 saat|60 saniye|

## <a name="store-performance-data"></a>Performans verilerini Store

Yük testi sırasında performans sayacı verileri toplanır ve depolanır *Yük Testi Sonuçları Deposu*. Daha fazla bilgi için [Yönet yük testi sonuçları Yük Testi Sonuçları Deposu](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Eşik kuralları hakkında

A *eşik kuralı* bir tek performans sayacı üzerinde bir yük testi sırasında sistem kaynak kullanımını izlemek için ayarlanır bir kuraldır. Sayaç kümesi tanımları, birçok önemli performans sayaçları için önceden tanımlanmış eşik kuralları içerir. Daha fazla bilgi için [yük testlerinde performans sayacı verilerini çözümlemeye yardımcı olmak için kullanım sayacı ayarlar](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Eşik kuralları ve düzeyleri

Eşik kuralları yük testlerinizi oluştururken arasında iki kural türü seçin:

Sabiti Karşılaştır&mdash;performans sayaç değerini sabit değerle karşılaştırın.

Sayaçları Karşılaştır&mdash;bir performans sayacı değeri başka bir performans sayacı değeri ile karşılaştırın.

Eşik kuralları oluşturduğunuzda, kural için düzeyleri de ayarlayın. Uyarı eşiğini ve Kritik Eşik düzeyleri şunlardır. Yük testi çalıştırması görüntülediğinizde, uyarı düzeyi Eşik ihlalleri sarı bir simgeyle gösterilir ve kritik düzey Eşik ihlalleri, kırmızı bir simgeyle gösterilir.

## <a name="the-alert-if-over-property"></a>Uyarı üzerinden özelliği

Ayarlama **aşarsa uyar** özelliğini **True** bir Eşiği aşan bir sorun olduğunu gösterebilir. Örneğin, üzerinde eşik kuralı ayarlarsanız **% işlemci zamanı**, ve değer 90, kullanımı büyük olduğunda uyarı almak istediğiniz **Sabiti Karşılaştır** kural türü için ayarlayın **Kritik Eşik Değer** 90 ve kümesi **aşarsa uyar** için **True**.

Ayarlama **aşarsa uyar** özelliğini **False** eşiğin altında kalan bir sorun olduğunu belirtmek için. Örneğin, üzerinde eşik kuralı ayarlarsanız **İsteği/sn**, ve değer 50 altına kullanım ise uyarı almak istediğiniz **Sabiti Karşılaştır** kural türü için ayarlayın **Kritik Eşik değeri** 50 ve kümesi **aşarsa uyar** için **False**.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Eşik kuralı ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)