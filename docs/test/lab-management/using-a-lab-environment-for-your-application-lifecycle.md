---
title: Devops için bir laboratuvar ortamı kullanma
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 45be33245e559cb5027124b4678984ece076e1cf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061164"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Devops için bir laboratuvar ortamı kullanma

Bir laboratuvar ortamı, uygulama geliştirip test etmek için kullanabileceğiniz sanal ve fiziksel makineler koleksiyonudur. Bir laboratuvar ortamında iş istasyonları, web sunucuları ve veritabanı sunucuları gibi çoklu katman uygulamalarını test etmek için gerekli olan çoklu roller içerebilir. Ayrıca, Laboratuvar ortamınızla birlikte bir yapı-dağıtma-test iş akışı oluşturmaya, dağıtmaya ve uygulamanız üzerinde otomatik testler çalıştırmak sürecini otomatik hale getirmek için kullanabilirsiniz.

* **Otomatik testleri çalıştırmak için bir test planı kullanma** -koleksiyonu adlı otomatikleştirilmiş testler çalıştırabilirsiniz bir *test planı*ve ilerlemeyi görüntüleyebilirsiniz.

* **Yapı-dağıtma-test iş akışı** -çok katmanlı uygulamaların otomatik olarak test etmek için bir yapı-dağıtma-test iş akışı kullanabilirsiniz. Bir yapı başlatır, yapı dosyalarını laboratuar ortamında uygun makinelere dağıtır ve ardından otomatikleştirilmiş testleri gerçekleştiren bir iş akışı buna tipik bir örnektir. Ayrıca, iş akışınızı belirli aralıklarla çalışacak şekilde zamanlayabilirsiniz.

* **Hatta manuel test sırasında tanılama verilerini tüm makinelerden toplama** -aynı anda birden çok makinelerden Tanılama verileri toplayabilirsiniz. Örneğin, bir tek test çalıştırması sırasında IntelliTrace toplama, test etkisi ve bir web sunucusu, bir veritabanı sunucusu ve istemci verilerini diğer tür.

Ortak laboratuvar ortamı topolojilerinin örnekleri şunlardır:

| Topoloji | Açıklama |
|---|---|
|![Yalnızca sunucu topolojisi](../media/topology_backend.png)| Bu laboratuar ortamını sahip bir *sunucu topolojisi*, genellikle sunucudaki sunucu uygulamaları el ile testleri çalıştırmak için kullanılır ve hataları ortamında doğrulamak için kendi istemci makineleri kullanmak için test edici sağlar. Bir arka uç topolojisinde, laboratuar ortamınızda yalnızca sunucularını içerir. Bu tür bir topoloji kullandığınızda, sunuculara genellikle bağlanın laboratuvar ortamında ortam olmayan bölüm olan bir istemci makinesi kullanarak.|
|![Bulut laboratuvar ortamı](../media/topology_cloud.png)| Bu laboratuar ortamını benzer özellikleri sağlar ve olarak özellikleri _sunucu topolojisi_, ancak fiziksel veya sanal bir yerel ortamda; çalışan kurulum süresini azaltabilir, basitleştirmek makineler gereksinimini ortadan kaldırır Bakım ve maliyeti en aza indirin. Birden çok Web siteleri ve sanal makineler, özel ağı ayarlamak hızlı ve kolay bir bulut ortamında Microsoft Azure gibi.|
|![İstemci-sunucu laboratuvar ortamı](../media/topology_clientserver.png)| Bu laboratuar ortamını sahip bir *istemci-sunucu topolojisi*, genellikle istemci ve sunucu bileşenlerini içeren bir uygulamayı test etmek için kullanılır. Bir istemci/sunucu topolojisinde, uygulamanızı test etmek için kullanılan istemci ve sunucu makinelerini, Laboratuvar ortamınızda tümü. Bu topoloji kullandığınızda, testlerinizi etkiler her makineden test verilerini toplayabilir.|

| | |
|---|---|
| ![video kamera simgesini film](../../install/media/video-icon.png) | [Bir video izleyin](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) Laboratuvar ortamlarını test için yönetme. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Bulut ile Azure işlem hatları veya Team Foundation Server derleme ve yayın kullanın

Otomatik test ve yapı-dağıtma-test otomasyonu kullanarak gerçekleştirebileceğiniz [derleme ve yayın](/azure/devops/pipelines/index?view=vsts) Team Foundation Server (TFS) ve Azure Test planları özellikleri. Bazı avantajları şunlardır:

* Bir yapı denetleyicisi veya Test denetleyicisi gerekmez.
* Test aracısı üzerinden bir görevi derleme veya sürüm bir parçası olarak yüklenir.
* Dağıtım adımlarını özelleştirmek kolay bir işlemdir. Artık tek bir betik kullanmak için kısıtlanır. Ayrıca Visual Studio Market olduğu gibi ürün içinde kullanılabilir olan birçok görev yararlanabilirsiniz.
* Test paketlerini sürdürmenize gerek yoktur. Test ikili dosyalarını doğrudan çalıştırabilirsiniz.
* Raporlama deneyimi her derleme veya yayın içinde çalıştırılan testler için daha zengin bir satır içi sahip olursunuz.
* Hangi varlıkları izleyebilirsiniz (sürüm, derleme, iş öğelerini, işlemeleri) şu anda dağıtıldığı ve her ortamda test.
* Özelleştirme ve birden çok test ortamlarını ve üretim için bile kolayca dağıtmak için Otomasyon genişletin.
* Bir iade veya işleme olduğunda veya belirli bir zamanda her gün gerçekleşecek Otomasyon zamanlayabilirsiniz.

Daha fazla bilgi için [kullanım derleme veya yayın Yönetimi](use-build-or-rm-instead-of-lab-management.md).

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Microsoft Test Yöneticisi'nin Visual Studio Laboratuvar Yönetimi özelliklerini kullanma

Oluşturun ve Visual Studio 2017 Enterprise sürümünde kullandığınızda Visual Studio Laboratuvar Yönetimi özellikleriyle laboratuvar ortamları Microsoft Test Yöneticisi'nin yönetin.

Laboratuvar Yönetimi, ortamınızdaki her bir makinede test aracıları otomatik olarak yükler.

Laboratuvar Yönetimi, System Center Virtual Machine Manager (SCVMM) ile birlikte kullanmanız durumunda, laboratuvar ortamları kullandığınızda da bu avantajlar olursunuz:

* **Makine yapılandırmaları hızla yeniden oluşturmak** -tipik bir üretim ortamlarını şekilde yapılandırılmış sanal makine koleksiyonları depolayabilirsiniz. Ardından, depolanmış ortamın yeni bir kopyasını her testi gerçekleştirebilirsiniz.

* **Bir hatanın tam bir koşul yeniden** - başarısız testi, laboratuar ortamınızda durumunun bir kopyasını saklamak ve yapı sonuçlarını ya da bir iş öğesi erişim.

* **Bir laboratuvar ortamı birden çok kopyasını aynı anda çalıştırmak** -adlandırma çakışmaları olmadan Laboratuvar ortamınızdaki birden çok kopyasını aynı anda çalıştırabilirsiniz.

### <a name="standard-environments-and-scvmm-environments"></a>Standart ortamlar hem SCVMM ortamları

Laboratuvar ortamları, Visual Studio Laboratuvar Yönetimi ile oluşturabileceğiniz iki tür vardır: **standart ortamları** ve **SCVMM ortamları**. Ancak, her ortam türünü yeteneklerini farklıdır.

**Standart ortamları:** sanal ve fiziksel makinelerin bir karışımını içerebilir. Üçüncü taraf sanallaştırma çerçeveleri tarafından yönetilen standart bir ortam sanal makineler ekleyebilirsiniz. Ayrıca, standart ortamları bir SCVMM sunucusu gibi ek sunucu kaynaklarını gerektirmez.

**SCVMM ortamları:** yalnızca SCVMM ortamları sanal makineler yalnızca Hyper-V sanallaştırma Framework'te çalıştırabilirsiniz (System Center Virtual Machine Manager), SCVMM tarafından yönetilen sanal makineler içerebilir. Ancak SCVMM ortamlarını standart ortamlarda kullanılabilir olmayan aşağıdaki otomasyon ve yönetim özellikleri sağlar:

- **Ortam anlık görüntülerini:** ortam anlık görüntülerini içeren bir laboratuar ortamında durumunu hızlı bir şekilde, temiz bir ortam geri yükleme veya değiştirilmiş bir ortamın durumu Kaydet. Bir yapı-dağıtma-test iş akışı, kaydetme ve Ortam anlık görüntü geri yükleme işlemini otomatik hale getirmek için de kullanabilirsiniz.

- **Depolanan ortamlar:** bir SCVMM ortamı bir kopyasını depolamak ve söz konusu ortamın birden çok kopyasını dağıtabilirsiniz.

- **Ağ yalıtımı:** ağ yalıtımı, bilgisayar adı çakışmaları olmadan bir SCVMM ortamı birden çok eşdeğer kopyasını aynı anda çalışmasına olanak sağlar.

- **Sanal makine şablonları:** bir sanal makine şablonu adı olan bir sanal makine ve diğer tanımlayıcıları kaldırıldı. Bir VM şablonu SCVMM ortamında dağıtıldığında, Microsoft Test Yöneticisi yeni tanımlayıcılarını oluşturur. Bu, birden çok kopyasını aynı ortamdaki bir sanal makine veya birden çok ortamda dağıtın ve ardından sanal makineleri aynı anda çalıştırmak sağlar.

- **Depolanan sanal makineler:** proje Kitaplığınızda depolanan ve benzersiz tanımlayıcıları içeren bir sanal makine.

> [!NOTE]
> Laboratuvar Yönetimi SCVMM 2016 desteklemez.

SCVMM hakkında daha fazla bilgi için bkz. [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts).

Standart ortamlar hem SCVMM ortamları aynı özelliklerin çoğunu destekler. Ancak, dikkate alınması gereken bazı önemli farklar vardır. Aşağıdaki tabloda, standart ortamlar hem SCVMM ortamları için kullanılabilen özellikler karşılaştırılmıştır.

|Özellik|SCVMM ortamları|Standart ortamları|
|-|------------------------|-|
|**Test etme**|||
|El ile testleri çalıştırma|Desteklenir|Desteklenir|
|Kodlanmış UI ve diğer otomatikleştirilmiş testleri çalıştırma|Desteklenir|Desteklenir|
|Tanılama bağdaştırıcısını kullanarak kapsamlı hataları bildirin|Desteklenir|Desteklenir|
|**Derleme dağıtımı**|||
|Otomatik yapı-dağıtma-test iş akışları|Desteklenir|Desteklenir|
|**Ortam oluşturma ve yönetme**|||
|Sanal makinelerin yanı sıra fiziksel makineleri kullanın|Desteklenmez|Desteklenir|
|Üçüncü taraf sanal makinelerini kullanın|Desteklenmez|Desteklenir|
|Otomatik olarak makinelere test aracısı Laboratuvar ortamına yükleme|Desteklenir|Desteklenir|
|Kaydet ve Ortam anlık görüntülerini kullanarak bir laboratuvar ortamı durumunu dağıtma|Desteklenir|Desteklenmez|
|VM şablonlarından laboratuvar ortamları oluşturun|Desteklenir|Desteklenmez|
|Başlat/Durdur/anlık görüntü ortamı|Desteklenir|Desteklenmez|
|Ortam Görüntüleyici kullanarak ortama bağlanın|Desteklenir|Desteklenir|
|Ağ yalıtımını kullanarak aynı anda bir ortamın birden çok kopyasını çalıştırmak|Desteklenir|Desteklenmez|

### <a name="lab-management-concepts"></a>Laboratuvar Yönetimi Kavramları

Devam etmeden önce bilmeniz bazı ek kavramları şunlardır:

|Terim|Açıklama|
|-|-----------------|
|Laboratuvar Merkezi|Microsoft Test oluşturduğunuz ve Laboratuvar ortamlarını Yöneticisi alan.|
|Azure DevOps projesi Laboratuvar|Bağlanabilmesi için bunları ayarlayın ve sanal makinelerini çalıştırmak için laboratuvar ortamlarını koleksiyonu.|
|Azure DevOps projesi kitaplığı|Bir arşiv depolanan sanal makineler, şablonlar ve projenizin konak grubuna içe saklı laboratuvar ortamları. SCVMM ortamları ile kitaplığınızda öğeleri kullanabilirsiniz; Ancak, bunları doğrudan standart bir ortama ekleyemezsiniz. Kitaplığınızda öğeleri çalıştırılamıyor; Bunun yerine, bunları yeni bir ortamı dağıtmak için kullanın.|
|Dağıtılan ortam|Bağlanmak ve makinelerinde çalıştırın böylece proje Laboratuvarınızı dağıtılan bir laboratuvar ortamı.|

Laboratuvar Yönetimi hakkında daha fazla bilgi için bkz:

* [Laboratuvarınızı Planlama](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Laboratuvarınızı yönetme](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [SCVMM ortamları için ayarlama](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [İzinleri Yönet](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Değişiklik Kurulumu](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Sorun giderme](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Ortamları ayarlama hakkında daha fazla bilgi için bkz:

* [Derleme ve yayın bulut ortamları](use-build-or-rm-instead-of-lab-management.md)
* [Standart laboratuvar ortamları](https://msdn.microsoft.com/library/ee390842.aspx)
* [SCVMM (sanal) ortamları](https://msdn.microsoft.com/library/ee943322.aspx)
* [Bir ağ yalıtılmış ortam oluşturma ve kullanma](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>Ayrıca bkz.

* [Test aracılarını yükleme ve yapılandırma](../../test/lab-management/install-configure-test-agents.md)
* [Visual Studio Laboratuvar Yönetimi Kılavuzu](https://aka.ms/vsarsolutions)
* [Microsoft DevOps blogu](https://blogs.msdn.microsoft.com/devops/)
