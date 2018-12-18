---
title: Yük testleri için sanal kullanıcı etkinlik grafiğini kullanarak
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8e4584d386cb61aaf7809c8bb5ab748e49543c7e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895931"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>İzlenecek yol: sorunları yalıtmak için sanal kullanıcı aktivite Grafiği'ni kullanma

Bu kılavuzda, yük testinizi çalıştıran tek tek sanal kullanıcı için oluşan hataları yalıtmak için sanal kullanıcı aktivite grafiği kullanmayı öğreneceksiniz.

Sanal kullanıcı aktivite grafiği yük testi ile ilişkili olan sanal kullanıcı etkinliğini görselleştirmenize olanak tanır. Grafikteki her satırın tek bir sanal kullanıcı temsil eder. Sanal kullanıcı aktivite grafiği, tam olarak neyin test sırasında her sanal kullanıcı yürütülmüş gösterir. Bu, kullanıcı etkinlik düzenlerini görerek performans sorunlarını yalıtmak, yük düzenleri, yavaş veya başarısız testleri ilişkilendirin ve diğer sanal kullanıcı etkinliğini isteklerle sağlar. Sanal kullanıcı aktivite grafiği çalışması bittikten sonra yalnızca yüklemeden sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Önkoşullar

-   Visual Studio Enterprise

-   Bu yordamları tamamlayın:

    -   [Bir web performans testini kaydetme ve çalıştırma](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

    -   [Bir yük testi oluşturma ve çalıştırma](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Önceki İzlenecek içinde oluşturulmuş ColorWebApp çözümünü açın

1.  Visual Studio'yu başlatın.

2.  Açık **ColorWebApp** içeren çözüm *LoadTest1.loadtest*. Bu yük testi sonuçları bu konunun önkoşullar bölümünde listelenen üç izlenecek adımlarda yürütülmesi.

     Bu kılavuzda kalan adımlarda ColorWebApp, adlandırılan bir web performans testi adlı bir web uygulaması varsayılır *ColorWebAppTest.webtest'i* ve adlandırılmış test yükü *LoadTest1.loadtest*.

## <a name="run-the-load-test"></a>Yük testi çalıştırma

Sanal kullanıcı etkinliği verilerini toplamak için yük testi çalıştırın.

-   İçinde **Yük Testi Düzenleyicisi**, seçin **çalıştırma** araç çubuğunda. LoadTest1 çalışmaya başlar.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Sanal kullanıcı aktivite grafiği sorunları yalıtmak

Yük testinizi çalıştırın ve sanal kullanıcı etkinliği verilerini toplanan sonra veriler yük testi sonuçlarında kullanarak görüntüleyebileceğiniz **Yük Testi Çözümleyicisi** Ayrıntıları görünümünde **sanal kullanıcı aktivite grafiği** . Ayrıca, kullanabileceğiniz **sanal kullanıcı aktivite grafiği** yük testinizde performans sorunlarını gidermeye yardımcı olmak için.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarında sanal kullanıcı aktivite Grafiği'ni kullanmak için

1.  Sonra Yük testi bittikten çalıştıran, **özeti** yük testi sonuçları sayfası görüntülenir **Yük Testi Çözümleyicisi**. Seçin **grafikleri** araç çubuğunda.

     Graflar görünümü görüntülenir.

2.  Üzerinde **sayfa yanıt süresi** grafiği, bir eşik ihlali simgelerinin sağ tıklayıp **kullanıcı ayrıntılarına Git**.

    > [!NOTE]
    > Kullanabileceğiniz **ayrıntıları** düğmesine **Yük Testi Düzenleyicisi** kullanıcı etkinlik grafiğini çok açmak için araç. Ancak, kullanırsanız **kullanıcı ayrıntılarına Git** seçeneği **sanal kullanıcı aktivite grafiği** otomatik olarak grafiğe sağ tıklanan test yoluna yakınlaştırmak.

     Ayrıntılar görünümü görüntülenir **sanal kullanıcı aktivite grafiği** eşik ihlallerinin gerçekleştiği zaman dilimi üzerine odaklanan.

     Y ekseninde, tek tek sanal kullanıcıların yatay çizimler temsil eder. X ekseni yük testi çalışması için zaman çizelgesi görüntüler.

3.  İçinde **zaman dönemini Yakınlaştır** aracı aşağıdaki **sanal kullanıcı aktivite grafiği**sol ayarlayın ve her ikisi de kadar doğru kaydırıcıları eşik ihlali simgesine kapatın. Bu içindeki zaman ölçeğini değiştirir **sanal kullanıcı aktivite grafiği**

4.  İçinde **ayrıntı göstergesi**, onay kutusunu seçin **(hataları vurgula)**. Eşik ihlali nedeniyle sanal kullanıcı vurgulandığından emin olun.

5.  İçinde **sonuçlarını filtreleme** panelinde, onay kutularını temizleyin **başarılı sonuçları göster** ve **HTTP hatası** ancak **ValidationRuleError**onay kutusu seçili.

     **Sanal kullanıcı aktivite grafiği** 3 saniyeden fazla üzerinde harcanan sanal kullanıcıların görüntüler *Red.aspx* sayfasında önceki yönergelerde yapılandırılmış eşik ihlali belirtildiği gibi.

6.  Fare işaretçisini eşik ihlali için doğrulama kuralı hatası sanal kullanıcıyla temsil eden yatay çizgi üzerine bırakın.

7.  Aşağıdaki bilgileri içeren bir araç ipucu görüntülenir:

    -   **Kullanıcı Kimliği**

    -   **Senaryo**

    -   **Test**

    -   **Sonucu**

    -   **Ağ**

    -   **Başlangıç saati**

    -   **Süresi**

    -   **Aracı**

    -   **Test günlüğü**

8.  Dikkat **Test günlüğü** bir bağlantıdır. Seçin **Test günlüğü** bağlantı.

9. Günlükle ilişkili ColorWebTest öğesini web performans testi açılır **Web Performans Testi Sonuçları Görüntüleyicisi**. Eşik ihlallerinin gerçekleştiği yalıtmanıza olanak sağlar.

     Çeşitli ayarları hem de kullanabilirsiniz **ayrıntı göstergesi** ve **sonuçlarını filtreleme** panelleri, performans sorunlarını ve yük testlerinizi hataları yalıtmaya yardımcı olmak için. Bu ayarlar ile deneme ve **zaman dönemini Yakınlaştır** içinde sanal kullanıcı verilerinin nasıl temsil edildiğini görmek için aracı **sanal kullanıcı aktivite grafiği**.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Nasıl yapılır: Dağıtılmış yük testi için bir test ayarı oluşturun](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)
