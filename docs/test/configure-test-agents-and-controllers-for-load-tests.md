---
title: Test aracıları yapılandırmak ve test denetleyicilerini yük testleri için
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1f33859522ff42fc85c31261527f17ea0f765199
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068023"
---
# <a name="configure-test-agents-and-test-controllers-for-running-load-tests"></a>Test aracıları yapılandırmak ve test denetleyicilerini yükleme testlerini çalıştırmak için

Visual Studio benzetilmiş yük kullanarak uygulamanız için fiziksel veya sanal makineler oluşturabilirsiniz. Bu makineler, tek bir test denetleyicisi ve bir veya daha fazla test aracıları ayarlanmalıdır. Test denetleyicisi ve test aracıları tek bir bilgisayar başına oluşturabilirsiniz daha fazla yük oluşturmak için kullanabilirsiniz.

> [!NOTE]
> Sitenize aynı anda erişen birçok kullanıcının yükünü oluşturan sanal makineler sağlamak için bulut tabanlı yük testi de kullanabilirsiniz. Bulut tabanlı yük testi hakkında daha fazla bilgi [Azure Test planlarını kullanarak çalışma yük testleri](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Yük Benzetimi Mimarisi

Visual Studio istemci, test denetleyicisi ve test aracılarını yükleme benzetimi mimarisi oluşur.

-   İstemci, geliştirme testleri, testleri çalıştırmak ve test sonuçlarını görüntülemek için kullanılır.

-   Test denetleyicisi, test aracılarını yönetme ve test sonuçlarını toplamak için kullanılır.

-   Test aracıları, sistem bilgileri ve profil oluşturma verilerini test ayarında tanımlanan ASP.NET dahil olmak üzere veri toplamak ve testleri çalıştırmak için kullanılır.

Bu mimari aşağıdaki avantajları sağlar:

- Ek test aracısı test denetleyicisine ekleyerek, yük oluşturmanın ölçeğini genişletebilir yeteneği.

- İstemcisini yüklemeye yönelik esneklik, test denetleyicisi ve test aracısı yazılımını aynı veya farklı bilgisayarlarda. Örneğin:

   **Yerel yapılandırma:**

  - Machine1: Visual Studio, denetleyici, aracı.

    ![Denetleyici ve Aracı'nı kullanarak yerel makine](./media/load-test-configa.png)

    **Tipik Uzaktan yapılandırma:**

  - Machine1 ve 2: Visual Studio (birden çok test eden aynısı kullanabilirsiniz).

  - Makine3: Denetleyici (çok, yüklü aracıları olabilir).

  - Machine4-n: aracısı veya MAKİNE3 denetleyiciyle ilişkili tüm aracıları.

    ![Uzak makinede denetleyicisi ve aracıları kullanma](./media/load-test-configb.png)

Bir test denetleyicisi genellikle birkaç test aracısını yönetir olsa da, bir aracı yalnızca tek bir denetleyici ile ilişkili olabilir. Her test aracısı, geliştiricilerin ekibi tarafından paylaşılabilir. Bu mimari, böylece daha büyük yükleri oluşturmak, test aracıları sayısını artırmak kolaylaştırır.

## <a name="test-agent-and-test-controller-interaction"></a>Test aracısı ve test denetleyicisi etkileşimi

Test denetleyicisi testleri çalıştırmak için bir test ajanı kümesi yönetir. Test denetleyicisi başlangıç testleri, Dur testler, test aracı durumunu izlemek ve test sonuçlarını toplamak için test aracılarıyla iletişim kurar.

### <a name="test-controller"></a>Test denetleyicisi

Test denetleyicisi testleri çalıştırmak için genel bir mimari sağlar ve yük testleri çalıştırmak için özel özellikleri içerir. Tüm test aracılarının testleri başlatana kadar tüm bekler ve test aracıları için test denetleyicisini yük testi gönderir. Tüm test aracılarının hazır olduğunuzda, test denetleyicisi testi başlatmak için test aracıları için bir ileti gönderir.

### <a name="test-agent"></a>Test aracısı

Test aracısı, yeni bir test başlatmak için test denetleyicisinden isteklerini dinleyen bir hizmet olarak çalışır. Test aracısını bir istek aldığında, test aracısı hizmeti, testleri çalıştırmak bir işlem başlatır. Her test aracısı, aynı yük testi çalıştırır.

 Test aracıları ağırlık yönetici tarafından atanır ve bir test aracısın ağırlığı göre yükleme dağıtılır. Test Aracısı 2 700 sanal kullanıcıların benzetimini yapar ancak örneğin, test aracısı 1, 30 ağırlığa sahip ve test aracısını 2 70 ağırlığa sahip ve yük 1000 kullanıcı ayarlanır, sonra test aracısı 1 300 sanal kullanıcı benzetimini yapar. Bkz: [test denetleyicileri ve test aracıları Visual Studio ile yönetme](../test/manage-test-controllers-and-test-agents.md).

 Test aracısını bir test kümesini ve simülasyon parametreleri kümesini girdi olarak alır. Bir anahtar kavram, testleri nerede çalıştıran bilgisayardan bağımsız olmasıdır.

## <a name="test-controller-and-test-agent-connection-points"></a>Test denetleyicisi ve test aracısı bağlantı noktaları

Aşağıdaki çizim, test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktalarını gösterir. Bunu, bu bağlantı noktalarındaki güvenlik kısıtlamalarını yanı sıra gelen ve giden bağlantılar için hangi bağlantı noktalarının kullanılan açıklar.

 ![Contoller test ve test aracısı bağlantı noktaları ve güvenlik](./media/test-controller-agent-firewall.png)

 Daha fazla bilgi için [yapılandırma bağlantı noktaları için test denetleyicileri ve test aracılarını](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Test denetleyicisi ve Aracısı yükleme bilgileri

Yüklemeden ve ortamınız için en iyi performans, yapılandırma yordamları test denetleyicileri ve test aracıları için donanım ve yazılım gereksinimleri hakkında önemli bilgiler için bkz: [yüklemek ve test aracılarıyapılandırma](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Test denetleyicisi ve test aracısı ile birim testleri kullanın

Bir test denetleyicisi ve bir ya da daha fazla aracı yükledikten sonra, yük testleriniz için test ayarında test denetleyicisi ile bir uzaktan yürütme kullanılıp kullanılmayacağını belirtebilirsiniz. Ayrıca, veri ve tanılama bağdaştırıcılarını test ayarında aracıları ile ilişkili rolüyle kullanacak şekilde belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)