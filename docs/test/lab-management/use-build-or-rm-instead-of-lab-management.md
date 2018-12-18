---
title: Otomatik test için Azure işlem hatlarını kullanın
ms.date: 10/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7a410601b0d7ab6b6a3901333b062e515555ec2d
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218667"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Azure Test planları yerine Laboratuvar Yönetimi otomatik test için kullanma

Yapı-dağıtma-test Otomasyonu veya otomatikleştirilmiş test için Microsoft Test Yöneticisi ve Laboratuvar Yönetimi kullanırsanız, bu konuda, aynı hedef kullanarak nasıl elde açıklanmaktadır [derleme ve yayın](/azure/devops/pipelines/index?view=vsts) Azure işlem hatları ve takım özellikleri Foundation Server (TFS).

## <a name="build-deploy-test-automation"></a>Yapı-dağıtma-test Otomasyonu

Microsoft Test Yöneticisi ve Laboratuvar Yönetimi, yapı, dağıtım ve uygulamalarınızın test otomatikleştirmek için bir XAML derleme tanımı üzerinde kullanır. XAML derleme bir laboratuvar ortamı, test paketlerini ve test ayarları gibi Microsoft Test Yöneticisi'nde oluşturulan çeşitli yapılar ve yapı denetleyicisi, yapı aracıları, Test denetleyicisi ve Test aracıları gibi çeşitli altyapı bileşenlerini kullanır. Bu amaç elde edin. Aynı Azure işlem hatları veya TFS kullanarak daha az adım ile gerçekleştirebilirsiniz.

| Adımlar | XAML derleme ile | Bir derleme veya yayında |
|-------|----------------------|-----------------|
| Yapıya dağıtmak ve testleri çalıştırmak için makineleri belirleyin. | Standart laboratuar ortamı ile bu makine Microsoft Test Yöneticisi'nde oluşturun. | yok |
| Çalıştırılacak testleri tanımlayın. | Microsoft Test Yöneticisi'nde bir test paketi oluşturun, test çalışmaları oluşturun ve Otomasyon her test çalışmasıyla ilişkilendirme. Testlerin çalıştırılması laboratuvar ortamında makine rolü tanımlayan Microsoft Test Yöneticisi'nde test ayarları oluşturun. | Test planları test yönetmeyi planlıyorsanız otomatik test paketi, Microsoft Test Yöneticisi'nde aynı şekilde oluşturun. Alternatif olarak, doğrudan derlemelerinizi tarafından üretilen test ikililerinin gelen testleri çalıştırmak istiyorsanız, bunu atlayabilirsiniz. Test ayarları her iki durumda da oluşturmaya gerek yoktur. |
| Dağıtım ve test otomatikleştirin. | LabDefaultTemplate.*.xaml kullanarak bir XAML derleme tanımı oluşturun. Derleme, test paketlerini ve laboratuvar ortamı derleme tanımında belirtin. | Oluşturma bir [derleme veya yayın işlem hattı](/azure/devops/pipelines/index?view=vsts) tek bir ortam ile. Komut satırı görevi kullanılarak aynı dağıtım komut dosyası (XAML derleme tanımı) çalıştırın ve Test aracısı dağıtımı ve işlevsel testleri çalıştırma görevini kullanarak otomatikleştirilmiş testleri çalıştırın. Bu görevler için girdi olarak makine ve kimlik bilgilerini bir listesini belirtin. |

Bu senaryo için Azure işlem hatları veya TFS kullanmanın avantajlarından bazıları şunlardır:

* Bir yapı denetleyicisi veya Test denetleyicisi gerekmez.
* Test aracısı üzerinden bir görevi derleme veya sürüm bir parçası olarak yüklenir.
* Dağıtım adımlarını özelleştirmek kolay bir işlemdir. Artık tek bir betik kullanmak için kısıtlanır. Ayrıca Visual Studio Market olduğu gibi ürün içinde kullanılabilir olan birçok görev yararlanabilirsiniz.
* Test paketlerini korumak zorunda değildir. Test ikili dosyalarını doğrudan çalıştırabilirsiniz.
* Raporlama deneyimi her derleme veya yayın içinde çalışan testlerin için daha zengin bir satır içi sahip olursunuz.
* Hangi varlıkları izleyebilirsiniz (sürüm, derleme, iş öğelerini, işlemeleri) şu anda dağıtıldığı ve her ortamda test.
* Özelleştirme ve birden çok test ortamlarını ve üretim için bile kolayca dağıtmak için Otomasyon genişletin.
* Bir iade veya işleme olduğunda veya belirli bir zamanda her gün gerçekleşecek Otomasyon zamanlayabilirsiniz.

## <a name="self-service-management-of-scvmm-environments"></a>SCVMM ortamları Self Servis Yönetimi

[Test Merkezi Microsoft Test Yöneticisi'nde](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) yanı sıra ortam şablonlarını içeren bir kitaplık yönetme isteğe kullanma ortamları sağlama özelliğini destekler bir [SCVMM sunucusu](/system-center/vmm/overview?view=sc-vmm-1801).

Laboratuvar Merkezi Self Servis sağlama özellikleri iki farklı hedeflere sahiptir:

* Altyapıyı yönetmek için basit bir yol sağlar. VM ve ortam şablonlarını yönetme ve otomatik olarak kopyalar ortamlarının birbirinden yalıtmak üzere özel ağlar oluşturma, altyapı Yönetimi örnekleri yoktu.

* Takımlar, test ve dağıtım etkinlikleri sanal makineler'de kullanmak daha basit bir yol sağlar. Kolay kullanım örnekleri olan test senaryolarında bu sanal makinelerin aynı proje güvenlik modeli üzerinden erişilebilir ve tümleşik yapma Laboratuvar ortamını kullanırsınız.

Ancak, daha zengin ortak ve özel bulut gelişimi yönetim sistemleri gibi verilen [Microsoft Azure](https://azure.microsoft.com/) ve [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), altyapı yönetimi özelliklerini bir evrimi yoktur TFS 2017 ve sonraki süreci desteleyen. Bunun yerine kolay gibi bulut altyapılar aracılığıyla yönetilen kaynakların tüketimini odaklanmak devam eder.

(Test veya dağıtım olmaları durumunda Laboratuvar Merkezi ve bunları SCVMM ya da Azure (altyapı yönetimi etkinlikleri olmaları durumunda) veya TFS ve Azure DevOps Hizmetleri yoluyla nasıl gerçekleştirebileceğiniz gerçekleştirdiğiniz tipik etkinlikler aşağıdaki tabloda özetlenmiştir. etkinlikler):

| Adımlar | Laboratuvar Merkezi ile | Bir derleme veya yayında |
|-------|-----------------|-----------------------|
| Ortam şablonlarını içeren bir kitaplık yönetin. | Bir laboratuvar ortamı oluşturun. Sanal makinelerde gerekli yazılımı yükleyin. Sysprep ve depolama ortamı Şablon kitaplığı olarak. | Doğrudan oluşturup sanal makine şablonları veya hizmet şablonları yönetmek için SCVMM Yönetim konsolunu kullanın. Azure kullanırken birini [Azure hızlı başlangıç şablonları](https://azure.microsoft.com/resources/templates/). |
| Bir laboratuvar ortamı oluşturun. | Kitaplıkta bir ortam şablonu seçin ve dağıtın. Sanal makine yapılandırmaları özelleştirmek için gerekli parametreleri belirtin. | Doğrudan şablonlardan VM'ler veya hizmet örnekleri oluşturmak için SCVMM Yönetim konsolunu kullanın. Doğrudan kaynakları oluşturmak için Azure portalını kullanın. Veya bir yayın tanımına sahip bir ortam oluşturun. Azure kullanım görevler veya gelen görevleri [SCVMM Tümleştirme Uzantısı](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) yeni sanal makineler oluşturmak için. Bu tanımın yeni yayın oluşturulması, Laboratuvar Merkezi'nde yeni bir ortam oluşturmaya eşdeğerdir. |
| Makinelere bağlanın. | Laboratuvar ortamı, Ortam Görüntüleyicisi'nde açın. | Sanal makinelere doğrudan bağlanmak için SCVMM Yönetim konsolunu kullanın. Alternatif olarak, uzak masaüstü oturumları açmak için sanal makinelerin DNS adları ve IP adresi kullanın. |
| Bir ortamın bir denetim noktası almak veya bir ortam için temiz bir denetim noktası geri yükleyin. | Laboratuvar ortamı, Ortam Görüntüleyicisi'nde açın. Bir denetim noktası almak veya önceki kontrol noktasına geri yüklemek için seçeneği belirleyin. | SCVMM Yönetim konsolunda, doğrudan sanal makineler bu işlemleri gerçekleştirmek için kullanın. Ya da daha büyük bir Otomasyon bir parçası olarak bu adımları gerçekleştirmek için denetim noktası görevler dahil [SCVMM Tümleştirme Uzantısı](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) bir yayın tanımı ortamının bir parçası olarak. |

## <a name="create-network-isolated-environments"></a>Ağ yalıtımlı ortam oluşturma

Bir ağ yalıtılmış laboratuvar ortamı, ağ çakışmalarına neden olmadan güvenli bir şekilde kopyalanabilir SCVMM sanal makine grubudur. Bu, MTM içinde bir dizi bir dizi sanal makinelerin özel bir ağda yapılandırmak için ağ arabirim kartları ve ağ arabirim kartları başka bir dizi ortak ağdaki sanal makinelerin yapılandırmak için kullanılan yönergeleri kullanarak yapıldı.

Ancak, Azure işlem hatları ve SCVMM ile birlikte TFS derleme ve dağıtım görevi, SCVMM ortamlarını yönetebilir, yalıtılmış sanal ağlar sağlamak için kullanılır ve yapı-dağıtma-test senaryolarını uygulayan. Örneğin, görevin kullanabilirsiniz:

* Kontrol noktalarını oluşturun ve geri yükleme
* Şablon kullanarak yeni sanal makineler oluşturun
* Sanal makineleri başlatıp
* SCVMM özel PowerShell betikleri çalıştırın

Daha fazla bilgi için [yapı-dağıtma-test senaryoları için sanal ağ yalıtımlı ortam oluşturma](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
