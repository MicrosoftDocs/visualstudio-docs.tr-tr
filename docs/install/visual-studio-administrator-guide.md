---
title: Visual Studio yönetici kılavuzu
titleSuffix: ''
description: Visual Studio bir kuruluş ortamında dağıtma hakkında daha fazla bilgi edinin.
ms.custom: seodec18
ms.date: 05/29/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 358614cae2001f46588bb447d97a863cf19b8036
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159470"
---
# <a name="visual-studio-2017-administrator-guide"></a>Visual Studio 2017 Yönetici Kılavuzu

Kuruluş ortamlarında yüklemeleri bir ağ paylaşımına veya sistem yönetim yazılımının kullanarak son kullanıcılara dağıtmak sistem yöneticileri için yaygındır. Sistem yöneticileri yükleme işlemi sırasında ürün anahtarlarını dağıtmak için yükleme Varsayılanları, önceden yapılandırmak için bir ağ yükleme konumuna oluşturma olanağı sağlayan kurumsal dağıtım desteklemek için Visual Studio Kurulum altyapısı tasarladık, ve ürün yönetmek için başarılı bir dağıtımı sonrasında güncelleştirir. Bu Yönetici Kılavuzu, ağa bağlı ortamlarda kurumsal dağıtım için senaryo tabanlı rehberlik sağlar.

## <a name="deploy-visual-studio-2017-in-an-enterprise-environment"></a>Visual Studio 2017 bir kuruluş ortamında dağıtma

Her hedef bilgisayar karşıladığı sürece Visual Studio 2017 istemci iş istasyonlarına dağıtabilirsiniz [minimum yükleme gereksinimlerini](/visualstudio/productinfo/vs2017-system-requirements-vs). System Center gibi yazılım ya da bir toplu iş dosyası aracılığıyla dağıtıyorsanız olsun, genellikle aşağıdaki adımları izleyerek Git isteyeceksiniz:

1. [Visual Studio ürün dosyalarını içeren bir ağ paylaşımı oluşturmanız](create-a-network-installation-of-visual-studio.md) bir ağ konumuna.

2. [İş yüklerinin ve bileşenlerin seçin](workload-and-component-ids.md) yüklemek istiyorsunuz.

3. [Bir yanıt dosyası oluşturma](automated-installation-with-response-file.md) , varsayılan yükleme seçenekleri içerir. Veya alternatif olarak, [derleme bir yükleme betiği](use-command-line-parameters-to-install-visual-studio.md) yükleme işlemini denetlemek için komut satırı parametreleri kullanan.

4. İsteğe bağlı olarak, [bir toplu lisans ürün anahtarını uygulayan](automatically-apply-product-keys-when-deploying-visual-studio.md) yüklemesinin bir parçası olarak kullanıcılar yazılım ayrı olarak etkinleştirmeniz gerekmez, komut dosyası.

5. Güncelleştirmek için ağ düzeni [kullanıcılarınız için ürün güncelleştirmeleri ne zaman teslim denetim](controlling-updates-to-visual-studio-deployments.md).

6. İsteğe bağlı olarak ayarlanmış kayıt defteri anahtarlarını [istemci iş istasyonları üzerinde önbelleğe alınmış denetim](set-defaults-for-enterprise-deployments.md).

7. Hedef Geliştirici iş istasyonları üzerinde önceki adımlarda oluşturulan betiği yürütmek için tercih ettiğiniz dağıtım teknolojiyi kullanın.

8. [En son güncelleştirmeleri içeren ağ konumunuza Yenile](update-a-network-installation-of-visual-studio.md) Visual Studio, kullandığınız komutunu çalıştırarak güncelleştirilmiş bileşenleri eklemek için düzenli olarak adım 1.

> [!IMPORTANT]
> Bir ağ bağlantısı paylaşımı "kaynak konumu hatırlanır" yüklemeleri bunlar geldiğini unutmayın. Başka bir deyişle, istemci ilk olarak yüklendiği ağ paylaşımına döndürmek bir istemci makinesi onarılması gerekebilir. Böylece, kuruluşunuzda çalışan Visual Studio 2017 istemcileri sahip olmayı beklediğiniz kullanım ömrü hizalar, ağ konumu dikkatle seçin.

## <a name="use-visual-studio-tools"></a>Visual Studio araçlarını kullanma

Yardımcı olacak çeşitli araçlar sunuyoruz [algılamak ve yüklü Visual Studio Örnekleri yönetme](tools-for-managing-visual-studio-instances.md) istemci makinelerinde.

> [!TIP]
> Yönetici Kılavuzu belgelerde ek olarak, iyi bir Visual Studio 2017 kurulumu hakkında bilgi kaynağıdır [sistem durumu Ilgaz'ın blog](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="specify-customer-feedback-settings"></a>Müşteri geri bildirim ayarlarını belirtin

Varsayılan olarak, Visual Studio yüklemesini müşteri geri bildirim sağlar. Grup İlkesi'ni etkinleştirdiğinizde, tek tek bilgisayarlarda müşteri geri bildirimleri devre dışı bırakmak için Visual Studio yapılandırabilirsiniz. Bunu yapmak için aşağıdaki anahtarı kayıt defteri tabanlı bir ilke ayarlayın:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Giriş = **OptIn**

Değer (DWORD) =
* **0** vazgeçti
* **1** kabul

Müşteri geri bildirim ayarları hakkında daha fazla bilgi için bkz. [Visual Studio Müşteri Deneyimi Geliştirme Programı](../ide/visual-studio-experience-improvement-program.md) sayfası.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017'yi Yükleme](install-visual-studio.md)
* [Visual Studio 2017'yi yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
  * [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
  * [İş yükü ve bileşen kimliği başvurusu](workload-and-component-ids.md)
* [Visual Studio'nun ağ tabanlı yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md)
  * [Visual Studio'yu çevrimdışı yükleme için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
* [Visual Studio yanıt dosyası ile otomatikleştirme](automated-installation-with-response-file.md)
* [Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Visual Studio kuruluş dağıtımları için varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md)
* [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
* [Visual Studio'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
