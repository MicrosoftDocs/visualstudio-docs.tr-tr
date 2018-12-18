---
title: Yük Testi Sanal Kullanıcı etkinliğini çözümleme
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ff4d71af450fa6d3f907bb1e1b5b963044e959ff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059914"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisinin Ayrıntılar görünümünde Yük Testi Sanal Kullanıcı etkinliğini çözümleme

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Sanal Kullanıcı Etkinlik Grafiği**

![Sanal Kullanıcı Etkinlik Grafiği](../test/media/virtual_actchart.png)

**Ayrıntıları** görüntülemek görüntüler **sanal kullanıcı aktivite grafiği**, görsel olarak yük testi sırasında tek tek sanal kullanıcıların ne yaptığını analiz etmek için kullanılır. **Sanal kullanıcı aktivite grafiği** , kullanıcı etkinliğinin desenleri görmemizi, yük düzenleri, başarısız olan veya yavaş testleri ilişkilendirmenizi ve diğer sanal kullanıcı etkinliğini isteklerle olanak tanır. **Sanal kullanıcı aktivite grafiği** CPU kullanımı, saniye başına istek bırakmaları artış belirlemenizi de yapabilirsiniz ve hangi test veya sayfaları çalıştırma bırakmaları ve ani değişiklikleri sırasında.

> [!NOTE]
> Kullanmak istediğiniz yük testini çalıştırmadan önce **sanal kullanıcı etkinlik ayrıntıları grafiği**, doğrulamanız gerekir **Zamanlama Ayrıntıları Deposu** özelliği  **AllIndividualDetails** performans Yük Testi Düzenleyicisini kullanarak seçeneği.

 **Ayrıntı göstergesi Panel**

 ![Ayrıntı göstergesi panel](../test/media/ltest_detailslegend.png)

 Ayrıntı göstergesi panel görülebilir **sanal kullanıcı aktivite grafiği**. Ayrıntıları gösterge bölmesinde testler, sayfalar ve işlemleri birkaç farklı ölçütlere göre filtreleme yapmanızı sağlıyor. Örneğin, belirli testleri görünümden kaldır veya tüm başarılı testleri kaldırabilir veya bazı hatalarla başarısız olan testler kaldırın. Ayrıca, günlükleri olmayan tüm testleri de kaldırabilirsiniz.

 Tüm başarısız testleri kırmızı renkte görüntüleyen, başarısız, testleri vurgulayabilirsiniz. Test günlüğü olan testleri de vurgulayabilirsiniz. Günlükleri ile testleri yeşil renkli.

 **Sonuçlar paneli Filtrele**

 ![Sonuçlar paneli Filtrele](../test/media/ltest_filterresults.png)

 Filtre sonuçlar paneli içinde görünen **sanal kullanıcı aktivite grafiği**. Filtre sonuçlar paneli aşağıdakilere göre filtreleyebilirsiniz:

-   **Yalnızca Günlüklü sonuçları göster** yalnızca test test günlüklerinin ilişkili olan sonuçları görüntüler.

-   **Başarılı sonuçları göster** başarılı sonuçları görüntüler.

-   **Hatalı sonuçları göster** hata ayıklamaya yardımcı olabilecek hatalı sonuçları görüntüler.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testinizi çalıştırın:** görüntülemek tamamlanana kadar bir yük testi oluşturup sanal kullanıcı etkinliği verilerini toplamayı etkinleştirmek için yapılandırdıktan sonra test çalıştırmalısınız **sanal kullanıcı aktivite grafiği**.||
|**Sanal kullanıcı etkinliği verilerini içeren yük testi sonuçlarını görüntüleme:** yük testinize yapılandırılmış, oluşturuldu ve çalışması tamamlandıktan sonra sanal kullanıcı etkinliği verilerini kullanarak görüntüleyebilirsiniz **sanal kullanıcı aktivite grafiği** .|-   [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Nasıl yapılır: yük testi sırasında sanal kullanıcıların ne yaptıklarını çözümleme](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Yük testlerinde performans sorunlarını yalıtmak:** kullanabileceğiniz **sanal kullanıcı aktivite grafiği** yük testinizde performans sorunlarını gidermeye yardımcı olmak için.|-   [İzlenecek yol: sorunları yalıtmak için sanal kullanıcı etkinlik grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümleyin](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)