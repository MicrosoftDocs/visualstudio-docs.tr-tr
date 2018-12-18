---
title: Yük testi oluşturma ve çalıştırma
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a5782985406d9b2daa53c1fd6ecefb3f31cc0104
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055776"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>İzlenecek yol: Oluşturma ve birim testlerini içeren bir yük testi çalıştırma

Bu izlenecek yolda, birim testleri içeren bir yük testi oluşturun.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu izlenecek yol, oluşturma ve ardından Visual Studio Enterprise'ı kullanarak yük testi çalıştırma adımları. Bir yük testi, web performans testleri ve birim testlerini kapsayıcıdır. Yük testleri ile oluşturduğunuz **Yeni Yük Testi Sihirbazı**.

Yük testi, istenen yük benzetimini oluşturacak şekilde değiştirilebilen birçok çalışma zamanı özellikleri de sunar. Bu kılavuzda, kullandığınız **Yeni Yük Testi Sihirbazı** bir yük testi için birim testleri ekleme.

Bu kılavuzda, aşağıdaki görevleri tamamlamayacaksınız:

-   Birim testleri kullanan bir yük testi oluşturun.

-   Bazı yük testi ayarlarını değiştirin.

-   Bir yük testi çalıştırın.

-   Bölümündeki adımları gerçekleştirdikten [izlenecek yol: oluşturma ve çalıştırma için birim testleri yönetilen kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) web içeren bir basit C# sınıf kitaplığı oluşturmak için performans ve yük bazı birim testlerinin ile testi.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı'nı kullanarak birim testleri içeren bir yük testi oluşturma

### <a name="to-start-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı'nı başlatmak için

1.  İçinde oluşturduğunuz Banka çözümünü açın [izlenecek yol: yönetilen kod oluşturma ve çalıştırma için birim testleri](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2.  İçinde **Çözüm Gezgini**, banka çözümü düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni proje**.

     **Yeni Proje Ekle** iletişim kutusu görüntüler.

3.  İçinde **Yeni Proje Ekle** iletişim kutusunda **Visual C#** ve **Test**. Şablonlar listesinden seçin **Web performansı ve yük testi projesi** ve **adı** alanına `BankLoadTest`. Seçin **Tamam**.

     BankLoadTest web performans ve yük testi projesi çözüme eklenir.

4.  Açık kısayol menüsünden Yeni BankLoadTest web performans ve yük testi projesinin seçin **Ekle**ve ardından **yük testi**.

5.  **Yeni Yük Testi Sihirbazı** başlatır.

6.  **Hoş Geldiniz** sayfasının **Yeni Yük Testi Sihirbazı** ilk sayfa verilmiştir.

7.  Seçin **sonraki**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Yük testi senaryosunun ayarlarını düzenlemek için

1.  İçinde **yük testi senaryosu için bir ad girin** metin kutusunda, **ScenarioSample**.

     A *senaryo* bir gruplandırma mekanizmasıdır. Bir test kümesinden ve bu testlerin yük altında çalıştırmak için özellikleri oluşur.

2.  Ayarlama **profili düşünme süresi** için `Use normal distribution centered on recorded think times`. Düşünme süreleri bir kullanıcının sonraki sayfaya geçmeden önce bir web sayfasında düşünerek geçirdiği zamanı temsil eder.

1.  Seçin **sonraki** işiniz bittiğinde.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Testi senaryosunun yükleme düzeni ayarını düzenlemek için

1.  Seçin **Adım yük**.

    > [!NOTE]
    > İki tür yük düzeni arasında seçim yapabilirsiniz: sabit ve adım. Her tür yükleme testinde, ancak bu kılavuzun amacıyla seçin işlevi sahip **Adım yük**.

2.  Ayarlama **başlangıç kullanıcı sayısı** öğesini 10 kullanıcı.

3.  Ayarlama **adım süresi** 10 saniyedir.

4.  Ayarlama **adım kullanıcı sayısı** 10 kullanıcı/adım için.

5.  Ayarlama **en yüksek kullanıcı sayısı** ila 100 kullanıcı.

6.  Seçin **sonraki**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Senaryoya ilişkin test karışım modeli seçmek için

1.  Altında **nasıl test karışımını modellenmesi**seçin **toplam test sayısına göre**.

2.  Seçin **sonraki**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Birim testlerini senaryoya eklemek için

1.  Sonraki adım **testler eklemek için bir yük testi senaryosu ve test karışımını düzenleme**.

2.  Seçin **Ekle** testleri seçmek için.

3.  Seçin **CreditTest** listelenen birim testleri **kullanılabilir testler** bölmesinde, tüm web performans testleri ve birim testleri web performansı ve yük testi projesi listeler.

4.  Eklemek için oku seçin **CreditTest** birim testine **Seçili testler** bölmesi.

5.  3 ve 4 için **DebitTest** ve **FreezeAccountTest** birim testleri.

6.  Üç birim testini eklemeyi bitirdiğinizde, seçin **Tamam**.

     Test karışımı sunulur.

7.  Altındaki kaydırıcıyı **dağıtım** için **CreditTest** test dağıtımını ayarlamak için biraz sağa doğru. Diğer kaydırıcıların otomatik olarak sola taşı ve böylece dağılım % 100 oranında kalır dikkat edin.

8.  Seçin **sonraki**.

### <a name="to-select-network-mix-for-test-scenario"></a>Test senaryosuna ilişkin ağ karışımı seçmek için

1.  Ağ bant genişliği karışımına eklenecek LAN bağlantı türünü seçin.

     Daha fazla ağ türü ekleyebilirsiniz. Test dağıtımını ve ağırlığını ayarlamak için kaydırıcıları kullanın.

2.  Seçin **sonraki**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Yük testi çalıştırması sırasında sayaç kümeleriyle izlemek üzere bilgisayarları belirtmek için

1.  Seçin **sonraki**.

     Sayaç kümeleri hakkında daha fazla bilgi için bkz: [sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testinde belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Yük testi çalıştırma ayarını düzenlemek için

1.  Seçin **yük testi süresi** ve ardından **çalışma süresi** için 2 dakika *duman testi* yük testi.

     Yük testlerinizi oluştururken her şeyin doğru bir şekilde yapılandırıldığını ve kısa ve hafif bir yük testi çalıştırarak beklendiği gibi çalışır durumda olduğunu doğrulamak için iyi bir uygulamadır. Bu işlem olarak bilinir *duman testi*.

2.  Seçin **son**. Yük testi içinde açılır **Yük Testi Düzenleyicisi'ni**.

## <a name="run-the-load-test"></a>Yük testi çalıştırma
 Yük testini oluşturduktan sonra Banka uygulamanızın yük benzetimine nasıl nasıl yanıt vereceğini görüntülemek için çalıştırın. Bir yük testi çalışırken, gördüğünüz **Yük Testi Çözümleyicisi** penceresi.

### <a name="to-run-the-load-test"></a>Yük testini çalıştırmak için

1.  Açık bir yük testi ile **Yük Testi Düzenleyicisi'ni**, yeşil **Test çalıştırması** araç çubuğu düğmesi. Yük testiniz çalışmaya başlar.

2.  Testi benzetiminiz herhangi bir eşiği aşarsa, ağaç denetimi düğümlerinde eşik ihlali gösteren simgeler görünür. Hatalar bir kırmızı halka yer paylaşımına, uyarılar bir sarı üçgen yer paylaşımına sahiptir. Eşiği aşan bir sayaç bulabilirsiniz ve simgeyi grafiğin üzerine sürükleyerek grafik. Test çalıştırılırken bunu yapabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir yük testi senaryosunda dahil etmek için hangi testlerin belirlemek için test karışımını düzenle](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)