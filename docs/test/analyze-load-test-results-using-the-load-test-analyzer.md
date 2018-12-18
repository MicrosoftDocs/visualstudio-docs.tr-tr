---
title: Yük testi sonuçlarını çözümleme
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 719163e53b1f8c68850b3f4f211838631a25274a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055614"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Yük Testi Çözümleyicisi kullanarak yük testi sonuçlarını çözümleme

Performans sorunlarını bulmak, hataları belirlemek ve kullandığınızda uygulamanızda geliştirmeleri ölçebilirsiniz **Yük Testi Çözümleyicisi**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu şekilde yük testi sonuçlarını çözümleyin:

-   Bir yük testi çalıştırılırken izleyin.

-   Tamamlandıktan sonra yükleme testini çözümleme.

-   Önceki yükleme testinden sonuçları görüntüleyin.

Ayrıca, iki veya daha fazla katılımcılarıyla paylaşmak eğilim analizi raporları karşılaştırma raporları da oluşturabilirsiniz. Bkz: [raporlama yük testleri için test karşılaştırmaları veya eğilim analizi sonuçları](../test/compare-load-test-results.md).

Visual Studio Enterprise veya komut satırından yük testinizi çalıştırın olup olmadığını ve tek bir bilgisayarda veya uzak bir makine üzerinde yük testi çalışıp şu görevleri gerçekleştirebilirsiniz.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Bir çalışan ve tamamlanmış bir yük testi arasındaki farklar

 Bir yük testi çalıştırdığınızda **Yük Testi Çözümleyicisi** yük testinize ve zaman testin başlatıldığı zaman adı ile birlikte ayrı bir sekmede görüntüler (örneğin, **LoadTest1 [12:40 PM]**). Bir yük testi çalıştığında, performans sayacı verilerini daha küçük bir kümesi bellekte tutulur. Bu veri kümesi, Yük testiniz çalışırken izleyebilirsiniz. Bir yük testi tamamlandıktan sonra veritabanından veri kümesini analiz edebilirsiniz. Hangi verilerin bir yük testi çalıştırdığında ve hangi test yükleme gördüğünüz verileri tamamlandı görüntülenen farklar vardır. Örneğin, yük testi tamamlanana kadar yüzde 90'ını ve yüzde 95 yanıt süresi verilerini hesaplanmaz. Bazı farklılıklar da işlevleri ve verileri çözümlemek kullanılabilen araçların oluşur.

 Yük testi çalıştırdığınızda, iki görünüm mevcuttur: **grafikleri** görünümü ve **tabloları** görünümü. **Grafikleri** görünümü, toplanan grafiği performans sayaçları için sağlar. **Tabloları** görünümü her testler, sayfalar, işlemleri ve toplanan istekleri hakkında bilgi sağlar. Hataları listeleyen bir tablo ayrıca Al

 Yük testi çalıştırması tamamlandığında, varsayılan olarak **özeti** görünümü görüntülenir. Arasında geçiş yapabilirsiniz **özeti**, **grafikleri**, **tabloları**, ve **ayrıntıları** araç çubuğu kullanılarak görünümleri. **Yük Testi Çözümleyicisi** yerleştirilebilir ya da normal Visual Studio pencere düzenleme yöntemlerini kullanarak kayan nokta ayarlayın. Tamamlanan yük testi çalışmaları analiz ederken, birden çok olabilir **Yük Testi Çözümleyici** açık karşılaştırmak için aynı anda farklı yük testi çalıştırır.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testi sonuçlarını erişme:** Yük Testi Düzenleyicisi'nden bir yük testi çalıştırdığınızda, yük testi sonuçları otomatik olarak açmak ve yük testi görüntülenen **Yük Testi Çözümleyicisi**.|-   [Nasıl yapılır: erişim yük testi sonuçlarını çözümleme](../test/how-to-access-load-test-results-for-analysis.md)|
|**Yük testinize analiz Notları Ekle:** çözümlemenizi, Yük testiniz için yorum ekleyebilirsiniz. Açıklamalar, yükleme testi sonucuyla birlikte kalıcı olarak depolanır. Ayrıca girdiğiniz açıklamayı görüntüler **açıklama** yük testi ile ilişkili olan sütun **yönetme testi sonuçlarını Aç ve** Yük Testi Düzenleyicisi iletişim kutusunda.<br /><br /> Daha fazla bilgi için [nasıl yapılır: erişim yük testi sonuçlarını analiz](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Ayrıca, bir Excel raporunu yük test sonuçları oluşturduğunuzda yorumları görüntülenir.<br /><br /> Daha fazla bilgi için [raporlama yük testleri için test karşılaştırmaları veya eğilim analizi sonuçları](../test/compare-load-test-results.md).||
|**Yük testi sonuçlarını çözümleme:** veri yük testinin eriştikten sonra sonuç verileri analiz edebilirsiniz. Sonuçları hızlı bir şekilde anlamak için yükleme testi özetini görüntüleyebilirsiniz. Yükleme testi özetini kısa ve kolay okunur bir biçimde anahtar sonuçları gösterilmektedir.<br /><br /> Yükleme testi özetini yazdırabilir. Bu, proje katılımcılarına sonuçları iletişim kurarken güvenli kılar.<br /><br /> Sonuçlarında grafikler ve Tablolar'ı kullanarak yük testi sonuçlarını ayrıntılarını analiz edebilirsiniz. Bunlar **hataları**, **sayfaları**, **istekleri**, **SQL İzleme**, **testleri**,  **Eşikleri**, ve **işlemleri**.|-   [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)<br />-   [Nasıl yapılır: web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Eşik kuralı ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Grafik görünümünde yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümleyin](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Performans sorunlarını yalıtmak için yük testi sonuçlarınızda Sanal Kullanıcı etkinliğini çözümleme:** sanal kullanıcı aktivite grafiği, bir yük testi sırasında sanal kullanıcıların ne yapmakta olduğunuz görselleştirmek için kullanabilirsiniz. Bu, bir CPU ani veya İsteği/sn bırakmaları yalıtmak ve hangi testler veya sayfaları bu ani ve kaldırma işlemlerine sırasında çalışan belirlemek yardımcı olabilir.|-   [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|