---
title: Yayımlama veya bir bulut hizmeti dağıtmak hazırlama
description: Bulut ve depolama hesabı Hizmetleri'ni ayarlama ve Azure uygulamanızı yapılandırmak için yordamlar hakkında bilgi edinin.
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 7485a03eb61d248517c1a0cdef782bceafcd2741
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056886"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bulut hizmeti yayımlamaya veya dağıtmaya hazırlanma

Bir bulut hizmeti projesini yayımlamak için bu makalede açıklandığı gibi aşağıdaki hizmetleri ayarlamanız gerekir:

* A **bulut hizmeti** rollerinizi Azure ortamında çalıştırmayı ve 
* A **depolama hesabı** Blob, kuyruk ve tablo hizmetlerine erişim sağlar.

## <a name="create-a-cloud-service"></a>Bulut hizmeti oluşturma

Bir bulut hizmeti rollerinizi Azure ortamında çalışır. Bir bulut hizmeti Visual Studio veya aracılığıyla oluşturabilir [Azure portalında](https://portal.azure.com/) izleyen bölümlerde açıklandığı gibi.

### <a name="create-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bir bulut hizmeti oluşturma

1. Önceden oluşturulmuş bir bulut hizmeti projesi ile proje Seç sağ **Yayımla**.
1. Gerekirse, Microsoft veya Azure aboneliğinizle ilişkili kuruluş hesabıyla oturum açın ve ardından **sonraki** ilerletmek için **ayarları** sayfası.
1. A **bulut hizmeti oluşturma ve depolama hesabı** iletişim kutusu görüntülenir (Aksi takdirde, seçin **Yeni Oluştur** gelen **bulut hizmeti** listesi).
1. URL'niz parçası oluşturur ve benzersiz olmalıdır, bulut hizmeti için büyük küçük harf duyarsız bir ad girin. Ayrıca bir bölge veya benzeşim grubu seçin ve bir çoğaltma seçeneğini seçin.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Azure portalı üzerinden bir bulut hizmeti oluşturma

1. Oturum [Azure portalında](https://portal.azure.com/).
1. Seçin **bulut Hizmetleri (Klasik)** sayfanın sol tarafındaki.
1. Seçin **+ Ekle**, ardından (DNS adı, abonelik, kaynak grubunu ve konumu) gerekli bilgileri sağlayın. Bu noktada, daha sonra Visual Studio'da olmadığından bir paketini karşıya yüklemek gerekli değildir.
1. Seçin **Oluştur** tıklayarak işlemi tamamlar.

## <a name="create-a-storage-account"></a>Depolama hesabı oluşturma

Depolama hesabı Blob, kuyruk ve tablo hizmetlerine erişim sağlar. Visual Studio aracılığıyla bir depolama hesabı oluşturabilirsiniz veya [Azure portalında](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Visual Studio'dan bir depolama hesabı oluşturma

1. İçinde **Çözüm Gezgini** önceden oluşturulmuş bir bulut hizmeti projesi ile bulun **bağlı hizmetler** rolü projesi, sağ tıklatın ve seçme içinde düğüm **bağlı hizmet Ekle**. (Visual Studio 2015'te sağ **depolama** düğümünü seçip alt **depolama hesabı oluştur**.)
1. İçinde **bağlı hizmetler** göründüğünde, liste seçin **Azure depolama ile bulut depolama**.
1. Görüntülenen Azure depolama iletişim seçin **+ oluştur yeni depolama hesabı**, aboneliğiniz için bir ad belirtin, bir iletişim kutusu getirir fo hesabı, bir fiyatlandırma katmanı, kaynak grubunu ve konumu.
1. Seçin **Oluştur** bitirdiğinizde. Yeni depolama hesabı, aboneliğinizdeki kullanılabilir depolama hesaplarının listesi görüntülenir.
1. Bu hesap ve seçin seçin **Ekle**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Azure Portalı aracılığıyla bir depolama hesabı oluşturma

1. Oturum [Azure portalında](https://portal.azure.com/).
1. Seçin **+ yeni** sol üstteki.
1. Seçin **depolama** altındaki "Azure marketi," ardından **depolama hesabı - blob, dosya, tablo, kuyruk** sağından.
1. (Adı, dağıtım modeli ve benzeri. gerekli bilgileri sağlayın
1. Seçin **Oluştur** tıklayarak işlemi tamamlar.

## <a name="configure-your-app-to-use-the-storage-account"></a>Depolama hesabı kullanmak için uygulamanızı yapılandırın

Bir depolama hesabı oluşturduktan sonra Visual Studio'dan otomatik olarak bağlanmak URL'leri ve erişim anahtarları da dahil olmak üzere proje için hizmet yapılandırması güncelleştirir.

Bir bulut hizmeti Visual Studio kullanarak oluşturduysanız **bağlı hizmet Ekle**, açarak bağlantıları kontrol edebilirsiniz `ServiceConfiguration.Cloud.cscfg` ve `ServiceConfiguration.Local.cscfg`.

Bir bulut hizmeti Azure portalından oluşturduysanız, aynı adımları izleyin [Visual Studio'dan bir depolama hesabı oluşturma](#create-a-storage-account-from-visual-studio) ancak mevcut bir hesabı yeni bir tane oluşturmak yerine. Visual Studio, daha sonra sizin için yapılandırmayı güncelleştirir.

Yapılandırma ayarları el ile kullanın özellik sayfaları Visual Studio'da bulut hizmeti projenizi geçerli rol için (role sağ tıklayıp **özellikleri**). Daha fazla bilgi için [bir depolama hesabı bağlantı dizesi yapılandırma](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Erişim anahtarları hakkında

Azure portal, her bir Azure depolama hizmetleri ve hesabınız için birincil ve ikincil erişim anahtarlarını kaynaklara erişmek için kullanabileceğiniz URL'leri gösterir. Depolama Hizmetleri karşı yapılan isteklerin kimliğini doğrulamak için bu anahtarları kullanın.

İkincil erişim tuşunu, depolama hesabınız için birincil erişim anahtarı ile aynı erişim sağlar ve bir yedek olarak birincil erişim anahtarınızı tehlikeye girdiği oluşturulur. Buna ek olarak, erişim anahtarlarınızı düzenli aralıklarla yeniden önerilir. Birincil anahtarı yeniden oluşturmak, ikincil anahtarı yeniden oluşturmak, birincil anahtar yeniden oluşturuldu kullanacak şekilde değiştirebilirsiniz ikincil anahtarını kullanmak için bir bağlantı dizesi ayarı değiştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'dan Azure'a yayımlama uygulamaları hakkında daha fazla bilgi için bkz [Azure araçlarını kullanarak bir bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).
