---
title: Azure bulut hizmeti için sabit bir sanal IP adresi korumak nasıl | Microsoft Docs
description: Azure bulut hizmeti sanal IP adresi (VIP) değişmemesini sağlayın öğrenin.
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003695"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Azure bulut hizmeti için sabit bir sanal IP adresi tutma
Azure'da barındırılan bir bulut hizmeti güncelleştirdiğinizde, hizmet sanal IP adresi (VIP) emin olmanız gerekebilir. Birçok etki alanı Yönetimi Hizmetleri, etki alanı adı sistemi (DNS) etki alanı adlarını kaydetmek için kullanın. VIP aynı kalırsa DNS çalışır. Kullanabileceğiniz **Yayımlama Sihirbazı** bulut hizmetinizin VIP'si ne zaman değişmez emin olmak için Azure Araçları, güncelleştirin. Bulut Hizmetleri için DNS etki alanı yönetimi kullanma hakkında daha fazla bilgi için bkz. [Azure bulut hizmeti için bir özel etki alanı adı yapılandırma](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>VIP değiştirme olmadan bir bulut hizmeti yayımlama
Önce Azure'da üretim ortamı gibi belirli bir ortamda dağıtımı yaparken, bir bulut hizmeti VIP'si ayrılır. VIP, yalnızca açıkça dağıtımı silin veya dağıtım dağıtımı güncelleştirme işlemi tarafından örtük olarak silindi değiştirir. VIP korumak için dağıtımınızı silmeniz gerekir değil ve Visual Studio, dağıtımınızı otomatik olarak silmez emin olmanız gerekir. 

Dağıtım ayarlarında belirttiğiniz **Yayımlama Sihirbazı**, çeşitli dağıtım seçenekleri destekler. Yeni bir dağıtımını veya artımlı ya da eşzamanlı bir güncelleştirme dağıtımı belirtebilirsiniz. Güncelleştirme dağıtımının her iki tür VIP korur. Farklı dağıtım türlerinin tanımları için bkz: [Azure uygulaması Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md). Ayrıca, bir hata oluşursa önceki bir bulut hizmeti dağıtımını silinmiş olup olmadığını kontrol edebilirsiniz. Doğru seçeneği ayarlamazsanız, VIP beklenmedik bir şekilde değiştirebilirsiniz.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>VIP değiştirme olmadan bir bulut hizmeti güncelleştirme
1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın. 

2. İçinde **Çözüm Gezgini**, projeye sağ tıklayın. Kısayol menüsünde **Yayımla**.

    ![Yayımla Menüsü](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. İçinde **Azure uygulamasını Yayımla** iletişim kutusunda, dağıtmak istediğiniz Azure aboneliğini seçin. Gerekli ve select oturum **sonraki**.

    ![Azure uygulama oturum açma sayfasına yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Üzerinde **ortak ayarları** sekmesinde, doğrulayın bulutun adını hizmet dağıtım yapıyorsanız, **ortam**, **derleme Yapılandırması**ve **Hizmet yapılandırması** tümü doğrudur.

    ![Azure uygulama ortak ayarlar sekmesinde Yayımla](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Üzerinde **Gelişmiş ayarlar** sekmesinde, doğrulayın **dağıtım etiketi** ve **depolama hesabı** doğrudur. Doğrulayın **hata durumunda dağıtımı Sil** onay kutusu işaretli değildir ve doğrulayın **dağıtım güncelleştirme** onay kutusu seçilidir. Öğenizin **hata durumunda dağıtımı Sil** onay kutusunu olun dağıtım sırasında bir hata oluşursa, VIP kaybolmaz. Seçerek **dağıtım güncelleştirme** onay kutusunu, dağıtımınızı silinmez ve uygulamanızı yeniden yayımladığınızda, VIP kaybı olmadığından emin olun. 

    ![Azure uygulama ayarları, Gelişmiş sekmesini yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Daha fazla rollerinin güncelleştirilmesi için nasıl istediğinizi belirtmek için seçin **ayarları** yanındaki **dağıtım güncelleştirme**. Şunlardan birini seçin **Artımlı güncelleştirme** veya **eşzamanlı güncelleştirme**seçip **Tamam**. Seçin **Artımlı güncelleştirme** uygulama her zaman kullanılabilir olduğunu, uygulamanızın her örneği birbiri ardına güncelleştirmek için. Seçin **eşzamanlı güncelleştirme** uygulamanız aynı anda tüm örneklerini güncelleştirilecek. Eşzamanlı güncelleştirilmesi daha hızlıdır, ancak hizmet uygulamanızın güncelleştirme işlemi sırasında kullanılabilir olmayabilir. İşlemi tamamladığınızda, seçin **sonraki**.

    ![Azure uygulama dağıtım ayarları sayfasında yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. İçinde **Azure uygulamasını Yayımla** iletişim kutusunda **sonraki** kadar **özeti** sayfası görüntülenir. Lütfen ayarlarınızı doğrulayın ve ardından **Yayımla**.
   
    ![Azure uygulama özeti sayfasında yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio kullanarak Azure Uygulama Sihirbazı yayımlama](vs-azure-tools-publish-azure-application-wizard.md)

