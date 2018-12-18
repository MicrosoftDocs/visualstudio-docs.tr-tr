---
title: Yük Testi Çalıştırma Ayarlarını Yapılandırma
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9aa2defb458fba0d7962813743fa603fe71081e2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053324"
---
# <a name="configure-load-test-run-settings"></a>Yük testi çalıştırma ayarlarını yapılandırma

*Çalıştırma ayarları* bir yük testinin çalışma biçimini etkileyen özellikler kümesidir. Çalıştırma ayarları kategorilere göre düzenlenir **özellikleri** penceresi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir yük testinde çalışma ayarları, ancak tek çalışma etkin olabilir, birden fazla çalışma ayarı olabilir. Diğer çalışma ayarları çalıştıran alternatif bir ayar sonraki testi için kullanmak üzere seçmek için hızlı bir yol sağlar.

İlk çalıştırma ayarı kullanarak bir yük testi oluşturduğunuzda oluşturulan **Yeni Yük Testi Sihirbazı**.

![Yük testi çalıştırma ayarları](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-|
|**Yük testiniz için daha fazla çalıştırma ayarları ekleme:** çalıştırdığınızda oluşturduğunuz çalışma ayarı yanı sıra **Yeni Yük Testi Sihirbazı**, daha fazla çalıştırma ayarları yük testinize altındaki farklı test çalıştırabilmek ekleyebilirsiniz. koşullar.|-   [Nasıl yapılır: bir yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Etkin yük testi ile kullanmak için ayarı çalışma belirlemek:** Yük Testi Düzenleyicisini kullanarak yük testi ile kullanmak istediğiniz çalışma ayarını seçebilirsiniz. Etkin çalışma ayarı, "[etkin]" soneki ile tanımlanır.|-   [Nasıl yapılır: etkin çalışma yük testi için ayarı seçin](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Çalıştırma ayarı Özellikleri Düzenle:** çalıştırmanız düzenleyebileceğiniz özelliklerini gibi şeyler günlüğe kaydetme seçeneklerini ayarlama (daha aşağıda, test, Isınma Süresi, en fazla hata sayısı uzunluğunu belirleyen bakın), örnekleme hızını, bağlantı bildirilen ayrıntıları Modeli (yalnızca web performans testleri), sonuç depolama türü, doğrulama düzeyi ve SQL izleme. Çalıştırma ayarları yük testinizin hedeflerini yansıtmalıdır.|-   [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md)<br />-   [Çalışma ayarı özelliklerini değiştirme](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Yük testi çalışma ayarlarında test yineleme sayısını belirtin:** tüm web başarım ve birim testlerinin yük testlerinizin senaryoların tümünde yapılandırarak çalıştırılacak kaç kez belirtebilirsiniz **Test Yinelemeleri** özellik.|-   [Nasıl yapılır: bir çalışma ayarında test yineleme sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Yük testi çalışma ayarı için örnekleme oranını belirtin:** yapılandırarak Topla performans sayacı verilerini test yük ne sıklıkla belirtebilirsiniz **örnek hızı** özelliği.|-   [Nasıl yapılır: örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zamanlama Ayrıntıları Depolama seçeneği belirtin:** ayrıntılarını yapılandırarak kaydedildi yük testinin nasıl istediğinizi belirtebilirsiniz **Zamanlama Ayrıntıları Deposu** özelliği.|-   [Nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Test kaynak saklama süresini belirtin:** test hızını > Düzeltme > test kaynakları belirli bir süre boyunca koruyarak ayarlayarak döngüsü değişiyorsa **kaynakları saklama süresi** özelliği.|-   [Yük testi hızlandırmak için kaynakların saklanacağı](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Bağlam parametreleri kullanma:** bir dizeyi parametre haline getirmek için bağlam parametreleri kullanabilirsiniz. Örneğin, yük testinizi bir parametreli web sunucusu kullanan bir web performans testi içeriyorsa, farklı bir sunucuya eşleyen çalışma ayarları için bir bağlam parametresi ekleyebilirsiniz.|-   [Nasıl yapılır: bir çalışma ayarına bağlam parametreleri ekleme](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Test günlüğü özelliklerini yapılandırma:** ne sıklıkta çalıştırma ayarları yük testi ile ilişkili olan günlük verileri yazılır yapılandırabilirsiniz. Günlük birkaç gigabayt olabilir çünkü büyük veya karmaşık bir yük testi çalıştırırken bu önemli olabilir.<br /><br /> Hata ayıklama ve uygulamanızı analiz etmenize yardımcı olmak yük testi başarısız olduğunda otomatik olarak kaydedilecek günlük dosyası da yapılandırabilirsiniz.|-   [Yük testi günlüğü ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)|