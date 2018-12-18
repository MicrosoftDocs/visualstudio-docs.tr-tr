---
title: Yük testi için senaryo Başlat gecikmelerini yapılandırma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e3c090fbcbc1a322574a5b0eca06ce917594348b
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896555"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Yük testlerinde Senaryo Başlatma Gecikmelerini Yapılandırma

Yük Testi Düzenleyicisi'ni kullanarak bir yük testinde bir senaryo başlatılmadan önce bir gecikme belirtin ve **özellikleri** penceresi.

Örneğin, kullanmak isteyebilirsiniz **başlama zamanını ertele** başka bir senaryonun tükettiği öğeleri oluşturmaya başlamak için bir senaryo gerekiyorsa özelliği. Üretim senaryosunun bazı verileri doldurmasına etkinleştirmek için tüketim senaryosunu geciktirebilirsiniz.

Yalnızca günün belirli bir saatinde Çalıştır bir senaryo sahip olabileceğiniz başka bir örnektir. Bu nedenle, bunun benzetimini gerçekleştirmek için senaryo, başlangıcı geciktirmek istiyorsanız.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Senaryonun gecikme başlangıcı zamanı belirtin

Değiştirmek için Yük Testi Düzenleyicisi'ni kullanarak bir yük testinde bir senaryoya başlamadan önce bir gecikme belirtebilirsiniz **başlama zamanını ertele** özelliğinde **özellikleri** penceresi.

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

 Bir örnek kullanmak isteyebileceğiniz bir örneğinin **başlama zamanını ertele** özelliği başka bir senaryonun tükettiği öğeleri oluşturmaya başlamak için bir senaryoya ihtiyaç olduğunda. Üretim senaryosunun bazı verileri doldurmasına etkinleştirmek için tüketim senaryosunu geciktirebilirsiniz.

 Yalnızca belirli bir süre günün sonunda çalıştırılan bir senaryo sahip olabileceğiniz başka bir örnektir. Bu nedenle, bunun benzetimini gerçekleştirmek için senaryo, başlangıcı geciktirmek istiyorsanız.

> [!NOTE]
> Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Bir senaryo için gecikme başlangıcı zamanı belirtmek için

1. Bir yük testi açın.

     Yük Testi Düzenleyicisi görünür. Yük testi ağacında görüntülenir.

2. Yük testi **senaryoları** klasöründe gecikme başlangıç zamanı belirtmek istediğiniz senaryoyu düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Kategoriler ve özellikler bu senaryonun görüntülenen **özellikleri** penceresi.

4. Metin kutusunda **başlama zamanını ertele** özelliği, yük testi sonra beklenecek süreyi belirten bir zaman değeri başlar yük testi çalıştırdığınızda senaryoyu başlatmadan önce türü.

    > [!NOTE]
    > Varsa değerini **Isınma sırasında devre dışı bırak** senaryosu için özelliği **True**, ardından **başlama zamanını ertele** özellikleri zaman değeri, Isınma sonra uygulanır Dönem. Hangi senaryoları kullanarak Isınma içinde bulunan denetleyebilirsiniz **Isınma sırasında devre dışı bırak** senaryo özelliği.

5. Özellik değiştirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Ardından, yeni kullanarak yük testi çalıştırabilirsiniz **başlama zamanını ertele** değeri.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Etkinleştirme ve bir senaryo Isınma dönemi boyunca olmasından devre dışı

**Isınma sırasında devre dışı bırak** özelliği ayarlanmış kullanarak **özellikleri** penceresi. Yük testi senaryosu özelliklerini düzenleme, Yük Testi Düzenleyicisi tarafından ayarlanır.

 **Isınma sırasında devre dışı bırak** özellik, senaryo çalıştırın veya belirtilen Isınma dönemi sırasında çalışmayabilir belirtmek için kullanılır **başlama zamanını ertele** özelliği. Daha fazla bilgi için önceki yordamda gözden [gecikme başlangıç zamanı senaryonun belirtin](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Etkinleştirme veya devre dışı bir senaryoya yönelik Isınma dönemi

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2. Yük testi **senaryoları** klasörü, Isınma davranışını değiştirmek istediğiniz senaryoyu düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Senaryonun kategoriler ve özellikler görüntülenir **özellikleri** penceresi.

     İçinde **Isınma sırasında devre dışı bırak** özelliği seçin **True** veya **False.**

4. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni kullanarak yük testlerini çalıştırabilirsiniz **Isınma sırasında devre dışı bırak** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Test aracıları yapılandırmak ve test denetleyicilerini yük testleri için](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)