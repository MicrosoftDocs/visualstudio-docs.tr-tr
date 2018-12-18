---
title: Bir Yük Testi Senaryosunda Sanal Ağ Türlerini Belirtme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 586038d325f17d37167166a361ee214d959ba2ab
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894683"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Bir yük testi senaryosunda sanal ağ türlerini belirtme

*Ağ karışımı* yük testi senaryosunda daha gerçekçi yükleme benzetimi yapmak için bir yol sağlar. Yükleme, tek tek ağ türü yerine farklı yapıda ağ türlerinin karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşmeleri hakkında daha yakın bir benzetim oluşturursunuz.

Ağ karışımı çalıştıran sanal kullanıcının olasılığını belirtir. bir verilen *ağ profili*. Ağ bant genişliği uygulama katmanında bir simülasyon ağ profilidir. Gecikme süresi benzetimini değil.

Bir yük testi oluşturduğunuzda, bu durumun benzetimini yapmak isteyebileceğiniz yükü birden fazla türde bağlantı oluşturuluyor. Ağ karışımı, ağ türlerinden sunar. Farklı ağlarda benzetimi yapılır. Seçeneğini belirlediğinizde bir seçenek gibi `Cable-DSL 1.5Mbps`, bekleme süresini teste seçili bant genişliği benzetimini yapmak için eklenmiş.

Ağ karışımı diğer karışımı seçenekleri gibi çalışır. Bir ağ türü rastgele ilişkili ağ karışımını temel alarak bir sanal kullanıcıyla seçilir. Kullanıcının test karışımında belirtilen olasılığa dayalı bir belirli ağ türü kullanılarak çalıştırılır.

Ağ karışımı belirledikten sonra ekleme ve ağ türlerini kaldırın. Karıştırma denetimini kullanarak ağ karışımını dağıtımını da değiştirebilirsiniz.

Karıştırma denetimini dağıtım senaryosunda ağların kolayca ayarlamanıza olanak tanır.

Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Gerçek ağ öykünmesi

Visual Studio yazılım tabanlı gerçek ağ öykünmesi yük testleri de dahil olmak üzere tüm test türleri için kullanır. Gerçek ağ öykünmesi ağ paketlerinin doğrudan düzenlenmesiyle ağ koşullarının benzetimini yapar. Gerçek ağ öykünücü Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri gerçek ağ öykünmesine dahil edilir:

-   (Gecikme) ağ üzerinden gidiş-dönüş süresi

-   Kullanılabilir bant genişliği

-   Sıraya alma davranışı

-   Paket kaybı

-   Paketlerin yeniden sıralanması

-   Hata yayılmaları.

Gerçek ağ öykünmesi aynı zamanda IP adresleri veya TCP, UDP ve ICMP gibi protokollere dayanan ağ paket filtrelemelerinde esneklik sağlar.

Gerçek ağ öykünmesi ağ tabanlı uygulama geliştiriciler ve test edenler tarafından istenen sınama ortamına öykünmek, başarımı değerlendirmek, değişikliğin etkilerini öngörmek veya teknoloji iyileştirmesi hakkında kararlar için kullanılabilir. Donanım test yataklarıyla karşılaştırıldığında gerçek ağ öykünmesi çok daha ucuz ve daha esnek bir çözüm ' dir.

## <a name="to-add-new-networks-to-a-scenario"></a>Bir senaryo için yeni ağlar eklemek için

1.  Bir senaryo için ağ karışımını belirleme işlemi sırasında seçin **Ekle**.

     Yeni bir ağ giriş kılavuza eklenir.

    > [!NOTE]
    > Görüntülenecek **Ağ Karışımını Düzenle** iletişim kutusu, varolan bir senaryoyu sağ tıklayın ve ardından **Ağ Karışımını Düzenle**.

2.  İçinde **ağ türü** sütununda, yeni giriş için oku seçin. İstediğiniz ağ türünü seçin.

3.  (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4.  Ağları eklemeyi tamamladığınızda, seçin **Tamam**.

## <a name="to-remove-networks-from-a-scenario"></a>Ağları senaryodan kaldırmak için

1.  Bir yük testi açın.

2.  Bir ağ kaldırın ve istediğiniz senaryoyu **Ağ Karışımını Düzenle**. **Ağ Karışımını Düzenle** iletişim kutusu görüntülenir.

3.  Kılavuz ağ seçin ve sonra **Kaldır**.

4.  (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5.  Ağları kaldırma işlemini tamamladığınızda, seçin **Tamam**.

## <a name="about-the-mix-control"></a>Karışım denetimi hakkında

 Karıştırma denetimini testleri, tarayıcı türleri veya bir yük testi senaryosuna ağ türleri arasında dağıtılmış yük yüzdesi ayarlamanıza olanak tanır. Yüzde değerleri ayarlamak için kaydırıcıları hareket ettirin. Ağ türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli bir ağ profili çalıştıran sanal kullanıcının olasılığını belirtir.

 Bir kaydırıcı taşıdığınızda, tüm kullanılabilir öğeleri yüzde değerlerini değiştirin. İkiden fazla öğe varsa, ekleme veya kaldırma miktarı diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, ekleme veya kaldırma miktarı yalnızca kilidi kalan tüm öğeleri uygulanır.

 **Dağıt** düğmesi tüm öğeler arasında eşit yüzde değerlerini ayırmak için kullanılır. Örneğin, üç öğeye sahipseniz seçme **Dağıt** yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.

 Yüzde değerlerini doğrudan yazmak mümkündür **%** Kaydırıcıları kullanmak yerine sütun. Bir yüzde değeri doğrudan giriyorsanız, diğer öğeler otomatik olarak ayarlar değil.

> [!NOTE]
> Toplam % 100 eklemez veya girilen yüzde değerleri kaydırıcılar devre dışı **%** ondalıksa sütun.

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam % 100 değilse, yüzde değerlerini oldukları gibi kabul etmek için veya geri gidip onları ayarlamanız istenir. Oldukları gibi bunları kabul etmeyi seçerseniz, % 100 olarak dağıtılır.  Örneğin, iki öğeniz varsa ve el ile bunları %80 ve % 40 olarak ayarlarsanız, ilk öğeye (120 bölünmüş 80) % 66.67 ayarlayın ve ikinci öğe %33.33 (40 120 bölünmüş) ayarlayın.