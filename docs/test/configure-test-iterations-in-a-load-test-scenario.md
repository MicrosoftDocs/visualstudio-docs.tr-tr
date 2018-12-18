---
title: Yük testi için test yinelemelerini yapılandırma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, sceanrios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 28bc6d6cb35397d49868c0603f7beb17f9138c2d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055693"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Bir yük testi senaryosunda test yinelemelerini yapılandırma

Yük Testi Düzenleyicisini kullanarak yük testi senaryosunun test yineleme ayarlarını yapılandırmak için düzenlemek ve **özellikleri** penceresi. Varsayılan olarak, bir yük testi senaryosuna en yüksek test yinelemeleri belirtmeden ayarlanır. En yüksek yineleme sayısı senaryosunda ve bunlar arasında beklenecek süreyi yapılandırma seçeneğiniz vardır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Bir senaryo için en yüksek test yinelemeleri belirtin

Belirtebileceğiniz maksimum sayısını değiştirmek için Yük Testi Düzenleyicisini kullanarak testlerinizi çalıştırmak için bir senaryo için istediğiniz **en yüksek Test Yinelemeleri** özelliğinde **özellikleri** penceresi.

**En yüksek Test Yinelemeleri** özelliği en fazla senaryo için çalışacak test yineleme sayısını denetler. Yalnızca olarak için **Test Yinelemeleri** özelliği yük testinde çalışma ayarları, bu en yüksek şirketteki tüm kullanıcıların tüm aracılar üzerinde değil bir kullanıcı ayarı başına.

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

 Sıralı test karışımı için tek seferde tüm testleri Karıştır aracılığıyla bir yineleme olur. Diğer tüm test karışımları için her test yürütme bir yineleme olarak sayılır. Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

 Yük testi süresi tabanlı yük testi ve süresi yineleme sayısı tamamlanmadan önce sona, test yine durdurulur. Yineleme tabanlı test ve test yinelemeleri senaryo yinelemeler önce karşılandığından, test durur. Kullanarak süresi yapılandırılan **çalışma süresi** özelliğinde **özellikleri** penceresi bir çalışma ayarında bir yük testi ile ilişkili.

 Senaryo yineleme sayısı karşılandığında senaryoyu çalışmayı durdurur, ancak herhangi bir etkin senaryolar çalışmaya devam eder.

> [!NOTE]
> İlgili bir özellik **benzersiz** hangi ilerler sırayla verileri, satır satır, ancak yalnızca bir kez her kayıt için bir web test verisi kaynağı özelliği. Daha fazla bilgi için [web performans testine veri kaynağı Ekle](../test/add-a-data-source-to-a-web-performance-test.md).

 **En yüksek Test Yinelemeleri** özelliği, çeşitli durumlarda kullanışlıdır. Bazı yük test yineleme tabanlı yük test edicileri süre tabanlı test tercih ederken yürütmek tercih eder.

 ![Test Yinelemeleri bir senaryoda belirtme](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>En yüksek test yinelemeleri belirtmek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi görünür. Yük testi ağacında görüntülenir.

3. Yük testi **senaryoları** klasörü, en fazla test yinelemesi sayısını belirtmek istediğiniz senaryoyu düğümünü seçin.

4. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Kategoriler ve özellikler bu senaryonun görüntülenen **özellikleri** penceresi.

5. Metin kutusunda **en yüksek Test Yinelemeleri** özelliği, bir yük testi çalıştırdığınızda, senaryo için çalıştırılacak testlerin sayısını belirten bir değer yazın.

    > [!NOTE]
    > Bir değer için 0'ı kullanarak **en yüksek Test Yinelemeleri** özellik yok en fazla yineleme belirtir.

6. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Ardından, yeni kullanarak yük testi çalıştırabilirsiniz **en yüksek Test Yinelemeleri** değeri.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Bir senaryo için test yinelemeleri arasındaki Düşünme süreleri belirtebilirsiniz

**Test Yinelemeleri Arasındaki Düşünme süresi** özelliği kullanılarak ayarlanır **özellikleri** Yük Testi Düzenleyicisi'nde yük testi senaryosu özelliklerini düzenlerken penceresi.

**Test Yinelemeleri Arasındaki Düşünme süresi** özelliği, bir test yineleme başlamadan önce beklenecek saniye miktarı belirtmek için kullanılır.

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz: [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Test yinelemeleri arasındaki düşünme süresi belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2. Yük testi **senaryoları** klasörü, düşünme süresi için belirtmek istediğiniz senaryoyu düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Senaryonun kategoriler ve özellikler görüntülenir **özellikleri** penceresi.

4. İçin değer **Test Yinelemeleri Arasındaki Düşünme süresi** özelliği, bir sonraki test yineleme başlamadan önce beklenecek saniye sayısını temsil eden bir sayı girin.

5. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni kullanarak yük testlerini çalıştırabilirsiniz **Test Yinelemeleri Arasındaki Düşünme süresi** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Test aracıları yapılandırmak ve test denetleyicilerini yük testleri için](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Web sitesi insan etkileşimi gecikmelerini benzetmek için Düşünme zamanlarını düzenleme](../test/edit-think-times-in-load-test-scenarios.md)