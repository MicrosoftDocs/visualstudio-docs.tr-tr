---
title: Yük testi için bir Web sitesi gerçek dünya kullanımının öykünmesini yapma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 33f44051025310072972ef3c15a1d4a4325c0efe
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896581"
---
# <a name="emulate-expected-real-world-usage-of-a-website-or-application-in-a-load-test-using-a-test-mix-model"></a>Bir Web sitesi veya bir test karışımı modeli kullanarak bir yük testinde uygulamanın beklenen gerçek hayatta kullanımı öykünün

Bir yük testi Web sitesinin veya uygulamanın beklenen gerçek hayatta kullanımı daha doğru bir şekilde tahmin etmek için yük modelleme seçenekleri kullanın. Bir doğru yük modeli dayalı olmayan bir yük testi yanıltıcı sonuçlara neden olabilir çünkü bunu yapmak önemlidir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Test karışımı modeli geliştirmeleri

Yük Testi Düzenleyicisi'ni veya test karışımı modeli Sihirbazı'nı kullanarak bir yük testi senaryosunun test karışımını aşağıdaki türde belirtebilirsiniz. Daha fazla bilgi için [senaryosunda test karışımı modelini değiştirme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Yük testi senaryonuzun aşağıdaki test karışımı modeli seçeneklerinden birini belirtebilirsiniz:

-   **Toplam test sayısı tabanlı:** sanal kullanıcı bir test yinelemesi başlattığında hangi web performans veya birim testi çalıştırma belirler. Yük testi sonunda, belirli bir testin çalışma sayısı, atanan test dağıtımını eşleşti. Bu test karışımı modeli, test karışımını bir IIS günlüğü ya da üretim verilerindeki işlem yüzdeleri dayandırırken kullanın. Daha fazla bilgi için [yüzdesi başlatılan testleri temel alarak](#BasedOnTestsStarted).

-   **Sanal kullanıcı sayısına göre:** belirli bir web performans veya birim testi çalıştıracak sanal kullanıcıların yüzdesini belirler. Yük testi içindeki herhangi bir noktada, belirli bir testi çalıştıran kullanıcıların sayısı, atanan dağıtım eşleşir. Test karışımı yüzdesi belirli bir testi çalıştıran kullanıcıların dayandırırken bu test karışımı modelini kullanın. Daha fazla bilgi için [yüzde tabanlı sanal kullanıcılarda](#PercentageBasedonVirtualUsers).

-   **Kullanıcı adımı tabanlı:** yük testi boyunca, her bir web performans testi veya birim testi belirtilen sayıda kullanıcı, saat başına bir kez çalıştırılır. Bu test karışımı modeli, yük testi boyunca belirli bir hızda testi çalıştırmak için sanal kullanıcıların istediğinizde kullanın. Daha fazla bilgi için [ilerleme test karışımını](#PacingTestMix).

    > [!TIP]
    > Seçtiğinizde **test karışımı yüzdesi** ve seçtiğinizde **yüzde tabanlı sanal kullanıcılarda**? Bazı testler test karışımında diğer testlerden daha uzun bir süreye sahip olduğunuzda, bu iki seçenek arasındaki fark önemlidir. Bu durumda, muhtemelen seçmelisiniz **yüzde tabanlı sanal kullanıcılarda**. Bu seçenek, bir test çalıştırması önlemek yardımcı olur, hangi çok sayıda kullanıcı uzun süreli testler çalıştıran olasılığını artırır. Ancak, tüm testler benzer süreleri varsa, daha güvenli bir şekilde seçebileceğiniz **test karışımı yüzdesi**.

-   **Ardışık düzenine dayanan:** her sanal kullanıcı, testlerin senaryoda tanımlandığı sırada web performans veya birim testleri çalıştırır. Sanal kullanıcı yük testi tamamlanana kadar testler içinde bu sırada dolaşma devam eder. Daha fazla bilgi için [sıralı](#SequentialOrder).

###  <a name="BasedOnTestsStarted"></a> Başlatılan testleri temel alan yüzdesi
 İçin her test karışımında test çalıştırmak için bir sonraki test olarak ne sıklıkta seçildiğini belirleyen bir yüzde belirtebilirsiniz. Örneğin, üç testlere aşağıdaki yüzde değerleri atayabilirsiniz:

- TestA (% 50)

- TestB'yi (%35)

- TestC (% 15)

  Bu ayarı kullanıyorsanız, başlatmak için sonraki test atanan yüzdeyi temel alır. Bunu şu anda her bir testi çalıştıran sanal kullanıcıların sayısını dikkate alarak olmadan.

###  <a name="PercentageBasedonVirtualUsers"></a> Sanal kullanıcı temelli yüzdesi
 Bu model, test karışımını, belirli bir testi çalıştıracak sanal kullanıcıların yüzdesini belirler. Bu model, test karışımını kullanıyorsanız, başlatmak için sonraki test yalnızca atanan yüzdeyi aynı zamanda şu anda belirli bir testi çalıştıran sanal kullanıcıların yüzdesini alır. Yük testi içindeki herhangi bir noktada, belirli bir testi çalıştıran kullanıcıların sayısını mümkün olduğunca yakın atanan dağıtım eşleşir.

###  <a name="PacingTestMix"></a> Test Karışımı İlerlemesi
 Gönderilmemiş test karışımı belirtirseniz, test karışımında test çalıştırması için her test için her sanal kullanıcının oranını ayarlayın. Saat başına sanal kullanıcı başına testler gibi her bir testi bu oranı ifade edilir. Örneğin, aşağıdaki testlere aşağıdaki gönderilmemiş test karışımını atayabilirsiniz:

- TestA: saat başına kullanıcı başına 4 testleri

- TestB'yi: saat başına kullanıcı başına 2 test

- TestC: saat başına kullanıcı başına 0,125 testleri

  Gönderilmemiş test karışımı modeli kullandığınız yük testi çalışma zamanı motoru başlatılan ve testleri gerçek hızı belirtilen oranına eşit veya daha az olmasını garanti eder. Testlerin tamamlanması çok uzun atanan sayı için bir hata döndürülür.

  **Test Yinelemeleri Arasındaki Düşünme süresi** gönderilmemiş test karışımı kullandığınızda ayar geçerli değildir.

#### <a name="apply-distribution-to-pacing-delay"></a>Adım Gecikmesine dağıtımı Uygula
 Değeri **Gecikmesine Dağıtım uygulama** özelliği bir yük testi senaryosunda, true veya false ayarlanabilir:

- **Doğru**: Senaryo değeri tarafından belirtilen tipik istatistiksel dağılımı gecikmeler uygulanacak **saatte kullanıcı başına testler** sütununda **Test Karışımını Düzenle** iletişim. Daha fazla bilgi için [bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Örneğin, sahip olduğunuz varsayılmıştır **saatte kullanıcı başına testler** değerini **Test Karışımını Düzenle** için saat başına 2 kullanıcı test iletişim kutusu. Varsa **Gecikmesine Dağıtım uygulama** özelliği **True**, tipik bir istatistiksel dağılımı testler arasındaki bekleme süresi uygulanır. Testler, saatte 2 test hala çalışır ancak bunlar arasında 30 dakika mutlaka olmaz. 4 dakika sonra 45 dakika sonra ikinci test ilk testin çalıştırabilirsiniz.

- **False**: belirtilen değeri için belirli bir hızda nin testleri çalıştıracağını **saatte kullanıcı başına testler** sütununda **Test Karışımını Düzenle** iletişim. Daha fazla bilgi için [bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Örneğin, sahip olduğunuz varsayılmıştır **saatte kullanıcı başına testler** değerini **Test Karışımını Düzenle** için saat başına 2 kullanıcı test iletişim kutusu. Varsa **Gecikmesine Dağıtım uygulama** özelliği **False**, testlerinizi çalıştırdığınızda, temelde hiçbir yaratmamış olursunuz. Test, 30 dakikada bir çalışır. Bu, saat başına 2 testlerini çalıştırmanızı sağlar.

  Daha fazla bilgi için [nasıl yapılır: kullanıcı adım testi karışım modeli kullanılırken Adım Gecikmesine Dağıtım uygulama](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

###  <a name="SequentialOrder"></a> Sıralı
 Temel bir sıralı test düzeni seçeneğini seçerek senaryosunda testlerin tanımlandığı sırada tüm Testleri Çalıştır her sanal kullanıcı sağlar.

## <a name="test-iterations-property"></a>Test yinelemeleri özelliği
 Çalışma ayarları Özellikler'de Test Yinelemeleri özelliği için bir değer belirtebilirsiniz. Bu değer bir yük testi çalıştırmak için test yinelemeleri sayısıdır. Belirtilen test yineleme sayısını başlatıldıktan sonra hiçbir ek test yineleme ayarlarını yük profillerinden birini rağmen başlatılacak. Belirtilen test yineleme sayısını tamamlandıktan sonra Yük testi sona erer. Daha fazla bilgi için [nasıl yapılır: bir çalışma ayarında test yineleme sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Başlangıç ve sonlandırma testleri
 Her sanal kullanıcının yük testi oturumunun başında ve sonunda çalıştırılacak testleri seçebilirsiniz. Daha fazla bilgi için [bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Testi Başlat**. Bu test, test karışımında testler çalıştırmadan önce her sanal kullanıcı tarafından çalıştırılır.

- **Sonlandırma testini**. Bu test, belirli bir sanal kullanıcı için tüm testler çalıştırıldıktan sonra çalıştırılır.

  Testi başlatma ve sonlandırma testi hakkında aşağıdakileri unutmayın:

- Yineleme sayısı yerine zamanına göre yük testi süresi belirtebilirsiniz. Bu durumda, yük testi çalıştırma süresi tamamlandığında, sonlandırma testi çalıştırılmaz.

- Başlatma testi, birim testi veya bir web performans testi ise, durumu TestContext veya WebTestContext, nesnenin başlangıç testi tamamlandıktan sonra kaydedilir. Bunu daha sonra Başlangıç bağlamı olarak test karışımında test yinelemeleri için kullanılacaktır.

- Yeni kullanıcılar, yeni kullanıcı yüzdesi, senaryo özelliğinde tanımlanan her zaman yürütme başlatma testi, test karışımını testten sonlandırma testi ve bir yineleme.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Bir yük testi senaryosunda dahil etmek için hangi testlerin belirlemek için test karışımını düzenle](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Bir senaryoda test karışımı modelini değiştirme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)