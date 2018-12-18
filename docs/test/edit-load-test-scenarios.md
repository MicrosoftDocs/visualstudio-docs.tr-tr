---
title: Yük testi senaryoları
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 865be7c7c6371f92f85d853a7dde045274fc5efb
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896542"
---
# <a name="edit-load-test-scenarios"></a>Yük testi senaryolarını düzenleme

Bir yük testi *senaryo* yük düzeni, test karışımını, tarayıcı karışımı ve ağ karışımını belirtir. Senaryoları, karmaşık, gerçekçi iş yükleri benzetimi yapmak için testleri yapılandırmanıza olanak tanırlar için önemlidir.

Örneğin, kullanılan bir Internet ön uç tarafından eş zamanlı müşterilerin gelen birçok bağlantı hızıyla ve farklı tarayıcılar kullanarak yüzlerce bir e-ticaret sitesini test. Aynı site, ürünleri güncelleştirmek ve istatistikleri görüntülemek için şirket içi çalışanlar tarafından kullanılan bir yönetim işlevi de olabilir. Bu dahili kullanıcılar genellikle aynı tarayıcı ve yüksek hızlı LAN bağlantısı kullanarak siteye erişir. Farklı senaryolarda kullanıcıların bu iki farklı grubunun özelliklerini saklamak isteyeceksiniz. Her senaryo, bir sanal kullanıcı türü içerebilir. Bu durumda, sanal müşterileri temsil edecek bir yük testi senaryosuna yapılabilir ve başka bir senaryo, bir Web sitesinin iç sanal kullanıcılarını temsil etmek için yapılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Senaryo Bileşenleri

Herhangi bir ilk yapılandırma seçenekleri ve bir yük testi oluşturduğunuzda, belirttiğiniz ayarlar daha sonra değiştirilebilir **Yük Testi Düzenleyicisi**. Bir yük testine yeni senaryolar ve çalıştırma ayarları sayaç kümeleri de ekleyebilirsiniz.

![Yük testi senaryoları](../test/media/loadtesteditinscenarios.png)

Senaryoları aşağıdaki bileşenleri içerir:

|Terim|Tanım|
|-|-|
|Tarayıcı karışımı|Sanal kullanıcıların çeşitli web tarayıcıları bir Web sitesine erişir benzetimini yapar.|
|Yük düzeni|Bir yük testi ve yeni kullanıcıların başlatılma oranını sırasında etkin olan sanal kullanıcı sayısını belirtir. Örneğin: adım, sabit ve hedef temelli.|
|Test karışımı modeli|Bir yük testi senaryosunda belirli bir testi çalıştıran sanal kullanıcının olasılığını belirtir. Örneğin: TestA çalıştırmak için % 20 olasılık ve TestB'yi çalıştırmak için % 80 olasılık. Test karışımı modeli her bir senaryo için testinizin hedefini yansıtmalıdır.|
|Test karışımı|Test karışımı seçimini senaryoyu oluşturan web başarım ve birim testleri ve bu testlerin dağıtımını ' dir.|
|Ağ karışımı|Sanal kullanıcıların çeşitli ağ bağlantıları bir Web sitesine erişir benzetimini yapar. Ağ karışımı LAN, kablolu modem ve diğer seçenekleri içeren seçenekler sunar.|

Kullanarak düzenleyebileceğiniz diğer bazı özellikleri senaryosunda **Yük Testi Düzenleyicisi**. Daha fazla bilgi için [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Senaryonuza yapay insan etkileşimi duraklamaları ekleyin:** Düşünme süreleri, insanların bir Web sitesiyle etkileşimleri ile arasında beklemesine neden olan insan davranışını benzetmekte kullanılır. Düşünme süreleri, bir web performans testindeki istekleri ve bir yük testi senaryosunda test tekrarları arasında oluşur. Bir yük testinde Düşünme süreleri kullanarak daha kesin yükleme benzetimleri oluşturmak yararlı olabilir.|-   [Web sitesi insan etkileşimi gecikmelerini benzetmek için Düşünme zamanlarını düzenleme](../test/edit-think-times-in-load-test-scenarios.md)|
|**Senaryonuz için sanal kullanıcı sayısını belirtin:** yük deseni özellikleri benzetimli kullanıcı yükünün yük testi boyunca nasıl ayarlandığını belirlemek için yapılandırabilirsiniz. Üç yerleşik yükleme düzeni Al: Sabit, adım ve hedef temelli. Yük desenini seçin ve yük testi hedefleriniz için uygun düzeylere özellikleri ayarlayın.|-   [Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Bu senaryoda bir testi çalıştıran sanal kullanıcı olasılığını yapılandırın:** bir yük testi senaryosunda belirli bir testi çalıştıran sanal kullanıcı olasılığını belirleyen test karışımını kullanabilirsiniz. Bu, yükü daha gerçekçi bir benzetimini sağlar. Uygulamalarınız boyunca yalnızca bir iş akışı sahip olmak yerine, son kullanıcıların uygulamalarınızla nasıl etkileşmeleri hakkında daha yakın bir benzetim olan birkaç iş olabilir.|-   [Metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Bir Web performans veya birim testi bir yük testi senaryosu ekleyip:** ekleyebilir veya bir yük testi senaryosunda web performans veya birim testi kaldırın. Bir yük testi, her biri bir veya daha fazla web performans testleri içeren bir veya daha fazla senaryo içerir.|-   [Test karışımını düzenleyin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryonuz için istenilen ağ karışımını yapılandırın:** ağ karışımını kullanarak, bir yük testi senaryosunda daha gerçekçi bir biçimde Ağ Yükü benzetimi. Yükleme, tek tek ağ türü yerine farklı yapıda ağ türlerinin karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşmeleri hakkında daha yakın bir benzetim oluşturursunuz. Ağ karışımı modeli senaryonun hedeflerini yansıtmalıdır.|-   [Sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Senaryonuz için uygun Web tarayıcı karışımını seçin:** tarayıcı karışımını kullanarak, bir yük testi senaryosunda daha gerçekçi bir web yükü benzetimi yapabilir. Yükleme tek tarayıcı yerine türdeş olmayan bir karışımını kullanarak oluşturulur. Uygulamalarınızla kullanılacak tarayıcıların daha yakın bir yaklaşığını oluşturursunuz.|-   [Web tarayıcısı türlerini belirtme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryonuz için test yineleme ayarlarını yapılandır:** yükleme testi düzenleyiciyi ve Özellikler penceresini kullanarak test yineleme ayarlarını yapılandırmak için bir yük testi senaryosu düzenleyebilirsiniz. Varsayılan olarak, bir senaryo yok en yüksek test yinelemeleri ile ayarlanır. İsteğe bağlı olarak senaryo ve bunlar arasında beklenecek süreyi en yüksek yineleme sayısı da yapılandırabilirsiniz.|-   [Senaryolar için test yinelemelerini yapılandırma](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Senaryonuz için gecikme ayarlarını yapılandırma:** kullanma **Yük Testi Düzenleyicisi** ve **özellikleri** penceresinde, bir yük testinde bir senaryoyu başlatmadan önce bir gecikme belirleyebilirsiniz. Bir örneği olduğunda kullanmak isteyebilirsiniz **başlama zamanını ertele** özelliği olan başka bir senaryonun tükettiği öğeleri oluşturmaya başlamak için bir senaryoya ihtiyaç duyduğunuzda. Üretim senaryosunun bazı verileri doldurmasına etkinleştirmek için tüketim senaryosunu geciktirebilirsiniz.|-   [Configureng senaryo başlatma gecikmelerini](../test/configure-scenario-start-delays.md)|
|**Bir yük testi senaryosunda kullanılacak uzak makineleri belirtin:** bir yük testi oluşturduktan sonra hangi test aracılarını dahil etmek istediğiniz belirtmek için yük testi senaryonuzun özelliklerini düzenleyebilirsiniz. Daha fazla bilgi için [Test denetleyicileri ve test aracılarını](configure-test-agents-and-controllers-for-load-tests.md).|-   [Nasıl yapılır: belirtin test aracılarını kullanmak için](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testlerini düzenleme](../test/edit-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)