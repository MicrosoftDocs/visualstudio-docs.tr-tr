---
title: Yük Testi için Test Denetleyicisi ve Test Aracısı Gereksinimleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8a5cc1f58e0cbdb59458311a1b9a4390bf69bbff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051464"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Test yük test denetleyicisi ve test aracısı gereksinimleri

Bazı test türleri dahil olmak üzere birim, web performansı, yük ve el ile testler Visual Studio ile tümleştirilmiştir. Visual Studio test denetleyicisi kullanarak uzak bilgisayarlarda testleri çalıştırmak için Visual Studio uygulama yaşam döngüsü yönetimi kullanıcıları ve bir veya daha fazla aracı sağlar. Bkz: [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Donanım ve yazılım gereksinimleri

Test denetleyicisi ve test aracısı bilgisayarlarının belirli donanım ve yazılım gereksinimleri vardır. Ayrıca, test denetleyicisini dağıtma ve aracıya sahip bilgisayarlar birden çok dil arasında test etmek istiyorsanız, bu dillerin nasıl destekleneceğini planlamanız gerekir.

### <a name="hardware-requirements"></a>Donanım gereksinimleri

Aşağıdaki tablo, bir test denetleyicisi ve test aracıları dağıtmak için önerilen donanım gereksinimlerini gösterir.

|**Yapılandırma**|**Bileşen**|**CPU**|**HD**|**Bellek**|
|-|-------------------|-|------------|-|
|< 500 sanal kullanıcı|Test aracısı|2.6 GHz|10 GB|2 GB|
|< 1000 sanal kullanıcı|Test aracısı|Çift işlemci 2,6 GHz|10 GB|2 GB|
|N x 1000 sanal kullanıcı|Test aracısı|N aracılarını her çift 2.6 Ghz ile ölçeklendirme|10GB|2GB|
|\< test ortamında 30 bilgisayar. Bu, test edilen aracıları ve sunucuları içerir.|Test denetleyicisi|2.6 GHz|||
|N x 30 bilgisayar test ortamında. Bu, test edilen aracıları ve sunucuları içerir.|Test denetleyicisi|N 2.6 GHz işlemcileri|||

> [!NOTE]
> Sanal kullanıcı sayısı, yaygın olarak teste büyük ölçüde farklılık gösterir. Temsilcilerde varyans bu sapmanın önemli bir nedeni olduğundan *Düşünme süreleri*, veya kullanıcı gecikmeleridir. Daha fazla bilgi için [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme düzenleme kez](../test/edit-think-times-in-load-test-scenarios.md). Bir yük testinde web testleri genellikle daha verimlidir ve birim testlerinden daha fazla yük oluşturur. Geçerli bir normal web uygulamasında 3-5 saniyelik düşünme süreleriyle web testlerini çalıştırmak için önceki tabloda sayılardır.

Burada sunulan yönergeler donanım planlaması için genel kılavuz olarak sağlanır. Test performansını büyük ölçüde test verilerinin miktarına ve test aracılarının sayısına göre değişir. Test aracıları için CPU hızı ve kullanılabilir bellek test yükünü sınırlayacaktır. Test denetleyicilerini, test aracıları sayısına ve testlerde bulunan veri miktarına bağlı olarak daha büyük kaynaklara gerekir.

Visual Studio çalıştıran sunucunun en düşük bant genişliği 1 MB/sn ve en yüksek 350 MS gecikme bir güvenilir ağ bağlantısına sahip olmalıdır. Test aracılarını ve test denetleyicisi arasında güvenlik duvarı olmamalıdır. Test performansınız beklentilerinizi karşılamıyorsa, donanım yapılandırmanızı yükseltmeniz göz önünde bulundurun.

### <a name="additional-hardware-considerations"></a>Ek donanım konuları

Test aracıları testin süresine ve testin boyutuna bağlı olarak test denetleyicilerindeki büyük miktarda veriler oluşturur. Genellikle, test verisinin her 24 saati için ek bir 10 GB için sabit disk depolaması planlamalısınız.

Burada önerilen donanımın yanı sıra, gereksiz güç kaynakları ve gereksiz Fanlar gibi kritik sunucular için ek donanımı göz önünde bulundurmalısınız.

### <a name="language-requirements"></a>Dil gereksinimleri

Karışıklığı önlemek ve işlemi kolaylaştırmak için bir test denetleyicisi ve test aracısı bilgisayarın işletim sistemine ve Team Foundation sunucusu aynı dili kullanacak şekilde yapılandırılması gerekir. Test aracısı ve test denetleyicisi farklı bilgisayarlarda yüklüyse, aynı dili kullanacak şekilde yapılandırılmalıdır. Bu dil Team Foundation Server dağıtımının eşleşen sürece, ancak başka bir dil sürümü Visual Studio'nun İngilizce işletim sisteminde, yükleyebilirsiniz.

## <a name="monitor-agent-resources"></a>Aracı kaynakları izleme

Gözlemleyerek kaynak ihtiyaçlarını belirlemek için aracı makineleri izleyebilirsiniz *QTAgent\*.exe* yürütün ve testleri sırasında ölçek işlemleri. En yaygın sorun üzerinde *QTAgent\*.exe* işlemler olduğu CPU kullanımı. CPU kullanımını sürekli olarak yüksek nineties içinde ise daha sonra aracıyı yoğun olarak yüklendiği göstergesidir. Sonraki genel bellek kullanımı kaynaklanıyor. Testleri zorlu için bu kaynakları izleme, makineler kaynakları artırın veya Testlerinizi farklı dağıtmak belirlemeye yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)