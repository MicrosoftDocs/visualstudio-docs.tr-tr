---
title: Test ayarlarını kullanarak ağ öykünmesini yapılandırma
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 032eff41f0e6b6366e5eb56dad591a02ebde4984
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065901"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da test ayarlarını kullanarak ağ öykünmesini yapılandırma

Uygulamanızı Visual Studio'dan farklı ağ ortamlarında test etmek için tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Ayrıca, testlerinizi çalıştırdığınızda bir yapay ağ yükünü veya performans sorununu test etmek için de yapılandırılabilir.

> [!WARNING]
> Testlerinizi Öykünülen ağdan daha yavaş türde bir gerçek ağda çalıştırırsanız, test yine daha yavaş ağ hızında çalışır. Öykünme ağ ortamını yalnızca yavaşlatabilir, hızlandıramaz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordam yapılandırma düzenleyicisinden ağ öykünmesini yapılandırmak nasıl açıklar. Bu adımlar, Microsoft Test Yöneticisi ve Visual Studio içinde her iki yapılandırma düzenleyicisine uygulanır.

> [!NOTE]
> Ağ öykünmesi tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi'nde test ayarları için kullanılmaz.

Yönetici ayrıcalıklarına sahip bir hesap, ağ öykünmesi için kullanılmalıdır. El ile testler çalıştıran yerel bir rol için ağ öykünmesi seçtiyseniz, yönetici ayrıcalıklarını kullanarak Microsoft Test Yöneticisi'ni başlatmanız gerekir. Başka bir rol için ağ öykünmesi seçtiyseniz, bu rol için makineye test aracısını Yöneticiler grubunun bir üyesi olan bir kullanıcı hesabı kullandığını doğrulamalısınız. Test aracınız için hesabınızı ayarlama hakkında daha fazla bilgi için bkz. [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Test aracısı için varsayılan hesap olan ağ hizmeti hesabını administrators grubunun bir üyesi değil.

**Gerçek ağ öykünmesi**

Visual Studio tüm test türleri için yazılım tabanlı gerçek ağ öykünmesi kullanır. Bu, yük testlerini içerir. Gerçek ağ öykünmesi ağ paketlerinin doğrudan düzenlenmesiyle ağ koşullarının benzetimini yapar. Gerçek ağ öykünücü Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri gerçek ağ öykünmesine dahil edilir:

- (Gecikme) ağ üzerinden gidiş-dönüş süresi

- Kullanılabilir bant genişliği

- Sıraya alma davranışı

- Paket kaybı

- Paketlerin yeniden sıralanması

- Hata yayılmaları.

Gerçek ağ öykünmesi aynı zamanda IP adresleri veya TCP, UDP ve ICMP gibi protokollere dayanan ağ paket filtrelemelerinde esneklik sağlar.

Gerçek ağ öykünmesi ağ tabanlı geliştiriciler ve test edenler tarafından istenen sınama ortamına öykünmek, başarımı değerlendirmek, değişikliğin etkilerini öngörmek veya teknoloji iyileştirmesi hakkında kararlar için kullanılabilir. Donanım test yataklarıyla karşılaştırıldığında gerçek ağ öykünmesi çok daha ucuz ve daha esnek bir çözüm ' dir.

## <a name="configure-network-emulation-for-your-test-settings"></a>Test ayarlarınız için ağ öykünmesini yapılandırın

Bu yordamdaki adımları gerçekleştirmeden önce Visual Studio'dan test ayarlarınızı açmalı ve ardından gerekir **veri ve tanılama** sayfası.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Test ayarlarınız için ağ öykünmesini yapılandırmak için

1.  Belirli bir ağa benzetmek için kullanılacak rolü seçin.

    > [!NOTE]
    > Yalnızca istemci rol veya sunucu rolünü ağ öykünmesi bağdaştırıcısını yapılandırmanız gerekmez. Her iki roldeki bağdaştırıcıyı kullanmak zorunda değil. Bağdaştırıcı her iki rol arasındaki iletişimi etkileyen ağ gürültüsüne öykünür, bu ikisinde kullanmak zorunda değil. Gerekli olmadıkça sunucu rolündeki ek yükü önlemek ağ öykünmesi bağdaştırıcısı için bir istemci rolü seçmeniz gerekir.

2.  Seçin **ağ öykünmesi** seçip **yapılandırma**.

     Ağ öykünmesini yapılandırmak için iletişim kutusu görüntülenir.

3.  Yanındaki oku seçin **kullanılacak ağ profilini Seç**ve bir testi çalıştırırken öykünmesini istediğiniz ağ türünü seçin (örneğin, **Kablo-DSL 768Kps**).

    > [!WARNING]
    > Testlerinizi Öykünülen ağdan daha yavaş türde bir gerçek ağda çalıştırırsanız, test yine daha yavaş ağ hızında çalışır. Öykünme ağ ortamını yalnızca yavaşlatabilir, hızlandıramaz.

4.  Ağ öykünmesi tanılama veri bağdaştırıcısı test ayarlarında içerir ve yerel makinenizde kullanmayı düşünüyorsanız, daha sonra Ayrıca ağ öykünmesi sürücüsünü makinenizin ağ bağdaştırıcılarından birine bağlamanız gerekir. Ağ öykünmesi sürücüsü işlevi için ağ öykünmesi tanılama veri bağdaştırıcısı için gereklidir. Ağ öykünmesi sürücüsü yüklü ve bağdaştırıcınıza iki şekilde bağlanır:

    -   **Microsoft Visual Studio Test Aracısı ile yüklenmiş ağ öykünme sürücüsü:** Microsoft Visual Studio Test Aracısı hem uzak makinelerde hem de yerel makinenizde kullanılabilir. Visual Studio Test aracısı yüklediğinizde, yükleme işlemi ağ öykünmesi sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

    -   **Microsoft Visual Studio Test Professional ile yüklenmiş ağ öykünme sürücüsü:** ağ öykünmesini ilk kez kullanırken, ağ öykünme sürücüsünü bir ağ kartına bağlamanız istenir.

    > [!TIP]
    > Ayrıca ağ öykünmesi sürücüsü komut satırından yerel makinenizde aşağıdaki komutu kullanarak Visual Studio test aracısı yüklemeden yükleyebilirsiniz: **VSTestConfig NETWORKEMULATION/Install**

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile yapılan testleri (Azure Test planları)](/azure/devops/test/run-manual-tests?view=vsts)