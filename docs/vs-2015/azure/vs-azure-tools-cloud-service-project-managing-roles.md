---
title: Azure bulut hizmetlerinde rollerini yönetme
description: Ekleme ve Visual Studio ile Azure bulut hizmetlerindeki roller kaldırma hakkında bilgi edinin.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e3a07e92e3be388b43fecd169c89c2c817d66900
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063256"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Visual Studio ile Azure bulut Hizmetleri'nde rollerini yönetme
Azure bulut hizmetinizi oluşturduktan sonra yeni rolleri eklemek veya var olan rolleri kaldırın. Ayrıca, mevcut bir projeyi içeri aktar ve rol dönüştürün. Örneğin, bir ASP.NET web uygulamasını içeri aktarabilir ve bir web rolü olarak belirleyin.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Bir Azure bulut hizmetinde rol ekleme
Aşağıdaki adımlar Visual Studio'da bir Azure bulut hizmeti projesi için bir web veya çalışan rolü eklerken size kılavuzluk.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, proje düğümünü genişletin.

1. Sağ **rolleri** bağlam menüsünü görüntülemek için düğümü. Bağlam menüsünden seçin **Ekle**, geçerli çözümden bir var olan web rolü veya çalışan rolü seçin veya bir web veya çalışan rolü projesi oluşturun. Ayrıca, bir ASP.NET web uygulaması projesi gibi uygun bir projeyi seçin ve bir rol projesi ile ilişkilendiren.

    ![Bir rol için bir Azure bulut hizmeti projesi eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Bir rol bir Azure bulut Hizmeti'nden kaldırılıyor
Aşağıdaki adımlar Visual Studio'da bir Azure bulut hizmeti projesinden bir web veya çalışan rolü kaldırma aracılığıyla Kılavuzu.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, proje düğümünü genişletin.

1. Genişletin **rolleri** düğümü.

1. Kaldırın ve bağlam menüsünden seçmek için istediğiniz düğüme sağ **Kaldır**.

    ![Bir rol bir Azure bulut hizmetine eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Bir rol için bir Azure bulut hizmeti projesi yeniden ekleniyor
Bulut hizmeti projenizi bir rolünü kaldırmak, ancak daha sonra rolü yeniden projeye eklemek karar yalnızca Rol bildirimi ve uç noktaları ve tanılama bilgileri gibi temel öznitelikler eklenir. Ek kaynaklar veya başvurular eklenen `ServiceDefinition.csdef` dosya veya `ServiceConfiguration.cscfg` dosya. Bu bilgiyi eklemek istiyorsanız, bu dosyalar onu el ile eklemeniz gerekir.

Örneğin, bir web hizmeti rolü kaldırabilir ve bu rolün geri çözümünüze eklemek daha sonra karar verin. Bunu yaparsanız, bir hata oluşur. Bu hatayı önlemek için eklemek zorunda `<LocalResources>` yeniden içine aşağıdaki XML'de gösterilen öğesinin `ServiceDefinition.csdef` dosya. Ad özniteliği için bir parçası olarak geri projeye eklenen web hizmeti rolü adını kullanın **<LocalStorage>** öğesi. Bu örnekte, web hizmeti rolü adıdır **WCFServiceWebRole1**.

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio ile bir Azure bulut hizmeti rollerini yapılandırma](vs-azure-tools-configure-roles-for-cloud-service.md)
