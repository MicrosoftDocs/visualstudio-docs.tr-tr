---
title: Yük testleri için sanal kullanıcı etkinliğini çözümleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0cac452a7fa4799c986df0f182643ed1b94afbe6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059528"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Nasıl yapılır: sanal kullanıcı etkinlik grafiğini kullanarak yük testi sırasında sanal kullanıcıların ne yaptıklarını çözümleme

Kullanarak yük testi ile ilişkili sanal kullanıcı etkinliğini görüntüleyin **sanal kullanıcı aktivite grafiği**. Grafikteki her satırın tek bir sanal kullanıcı temsil eder. **Sanal kullanıcı aktivite grafiği** tam olarak neyin test sırasında her sanal kullanıcı yürütülmüş gösterir. Kullanıcı Etkinlik düzenlerini görebilir, yük düzenleri, yavaş veya başarısız testleri ilişkilendirin ve diğer sanal kullanıcı etkinliğini isteklerle bakın. **Sanal kullanıcı aktivite grafiği** yalnızca yük testi çalışması bittikten sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordamlar nasıl görüntüleneceğini göstermektedir **sanal kullanıcı aktivite grafiği**nasıl belirli kullanıcının etkinliğini araştırın ve filtrelemeyi kullanma.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarınızda Sanal kullanıcı aktivite grafiği görüntülemek için

1.  Sanal kullanıcı verilerini görüntülemek için öncelikle yapılandırmalısınız **Tüm Bireysel Ayrıntılar** ayarını **Zamanlama Ayrıntıları Deposu** yük testi ile ilişkili olan özellik. Daha sonra Yük testi çalıştırın.

2.  Sonra Yük test çalıştırmaları, test sonuçları Özet sayfasında görüntülenir. Seçin **kullanıcı ayrıntı** araç çubuğunda.

     veya

     Grafik görünümü seçerek açın **grafikleri** araç çubuğunda. Grafiği sağ tıklayın ve ardından **kullanıcı ayrıntılarına Git**.

     Bu seçeneği kullanırsanız **sanal kullanıcı aktivite grafiği** tıklattığınız testin bir parçası için otomatik-yakınlaştırır. İşaretçinizi üzerinde yaklaşık 30 ikinci işareti bulunuyorsa, örneğin, ayrıntı görünümü yaklaşık 30 ikinci işaretleme üzerinde görüntüler **zaman dönemini Yakınlaştır** kısmındaki araç **sanal kullanıcı aktivite grafiği** .

     Ardından, kullanabileceğiniz belirli bir kullanıcının etkinlik ayrıntılarında araştırmak **sanal kullanıcı aktivite grafiği**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Sanal kullanıcı aktivite grafiği, belirli bir kullanıcının etkinlik incelemek için

1. Zaman dönemi aracına yakınlaştırma alt kısmında kullanmak **sanal kullanıcı aktivite grafiği** istediğiniz belirli bir kullanıcı ayrıntılarını incelemek için grafik üzerinde bir alanı seçin.

2. Graftaki bir ayrıntı üzerinde gezdirin. Aşağıdaki bilgiler, araç ipucunda görüntülendiğini görürsünüz:

   - **Kullanıcı Kimliği**

   - **Senaryo**

   - **Test**

   - **URL** (bir test veya işlem göstermez)

   - **Sonucu**

   - **Tarayıcı** (bir test veya işlem göstermez)

   - **Ağ**

   - **Başlangıç saati**

   - **Süresi**

   - **Aracı**

   - **Test günlüğü** (test günlüğü bağlantı)

     > [!NOTE]
     > Seçerseniz, uygulamanızın hata ayıklamaya yardımcı olmak için **Test günlüğü** bağlantı, web testi sonucu veya birim test sonucu açık günlükle ilişkilendirilmiş.

     Ardından, filtreleme ve vurgulama işlemleri bulunan kullanabilirsiniz **sanal kullanıcı aktivite grafiği**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Sanal kullanıcı aktivite grafiği filtreleme seçeneklerini kullanmak için

1. İçinde **ayrıntı göstergesi**, ya da seçmek için açılan listeyi kullanın **Test**, **sayfa**, veya **işlem**.

    **Ayrıntı göstergesi panel**

    ![Ayrıntı göstergesi panel](../test/media/ltest_detailslegend.png)

2. Hatalar, günlükleri, test, arama ve yük testi ile ilişkili aspx sayfaları için onay kutularının işaretini kaldırın veya seçin.

    **Sanal kullanıcı aktivite grafiği** uygun şekilde güncelleştirir.

    **Sanal kullanıcı aktivite grafiği** testler, sayfalar ve işlemleri birkaç farklı ölçütlere göre filtreleme olanağı sağlar. Görünümden belirli testleri kaldırın veya tüm başarılı testleri kaldırın veya bazı hatalarla başarısız testleri Kaldır. Ayrıca, günlükleri olmayan tüm testleri de kaldırabilirsiniz.

    Örneğin, seçebileceğiniz **(hataları vurgula)** tüm hataları grafikte görüntüleyen seçeneği kırmızı renkli. Belirleyebilirsiniz **(Günlüklü sonuçları vurgula)** grafikteki yeşil renkli günlükleri olan tüm test sonuçlarını görüntüleyen seçeneği.

    **Sonuçlar paneli Filtrele**

    ![Sonuçlar paneli Filtrele](../test/media/ltest_filterresults.png)

3. İçinde **sonuçlarını filtreleme**seçin veya aşağıdaki filtre seçenekleri için onay kutularını temizleyin:

   - **Yalnızca Günlüklü sonuçları göster** yalnızca test test günlüklerinin ilişkili olan sonuçları görüntüler.

   - **Başarılı sonuçları göster** başarılı sonuçları görüntüler.

   - **Hatalı sonuçları göster** hata ayıklamaya yardımcı olabilecek hatalı sonuçları görüntüler.

     > [!NOTE]
     > Altında listelenen hata türleri listesi **hatalı sonuçları göster** düğüm daha fazla araştırılması seçerek **tabloları** düğmesine **Web Performans Test Sonuçları Görüntüleyicisi** araç çubuğu. Daha fazla bilgi için [yük testi sonuçlarını ve hatalarını Tablo görünümünde çözümlemek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Sanal kullanıcı aktivite grafiği** uygun şekilde güncelleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [İzlenecek yol: sorunları yalıtmak için sanal kullanıcı etkinlik grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)