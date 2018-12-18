---
title: Bir Azure bulut hizmeti projesi oluşturma
description: Artık Visual Studio ile bir Azure bulut hizmeti projesi oluşturmayı öğrenin
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 43944856f05afe8b7236d9ea7d6468164dd1f2cb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062602"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile bir Azure bulut hizmeti projesi oluşturma
Visual Studio için Azure Araçları oluşturmanıza imkan tanıyan bir proje şablonu sağlar bir [Azure bulut hizmeti](/azure/cloud-services/cloud-services-choose-me), basit bir genel amaçlı Azure hizmet. Visual Studio projesi oluşturulduktan sonra yapılandırma, hata ayıklama ve bulut hizmetini Azure'a dağıtmak sağlar.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Visual Studio'da bir Azure bulut hizmeti projesi oluşturma adımları
Bu bölüm bir veya daha fazla web rolleri ile Visual Studio'da bir Azure bulut hizmeti projesi oluşturma işleminde size yol gösterir.

1. Visual Studio'yu yönetici olarak başlatın.

1. Ana menüden **dosya** > **yeni** > **proje**.

1. Seçin **bulut** Visual C# veya Visual Basic şablonu düğümleri proje ve seçin **Azure bulut hizmeti** şablonları listesinden.

    ![Yeni Azure bulut hizmeti](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Hangi proje geliştirmek için kullanmak istediğiniz .NET Framework sürümünü belirtin.

1. Bir ad ve projenizin konumunu ve çözüm için bir ad girin.

1. Seçin **Tamam**.

1. İçinde **yeni Microsoft Azure bulut hizmeti** iletişim kutusunda, eklemek istediğiniz rolü seçin ve bunları çözümünüze eklemek için sağ ok düğmesini seçin.

    ![Yeni Azure bulut hizmeti rolleri seçin](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Eklediğiniz bir rolü yeniden adlandırmak için vurgulama rolünde üzerinde **yeni Microsoft Azure bulut hizmeti** iletişim kutusunda, bağlam menüsünden seçin **Yeniden Adlandır**. Çözümünüz içinde bir rol de adlandırabilirsiniz (içinde **Çözüm Gezgini**) eklendikten sonra.

    ![Azure bulut hizmeti rolü yeniden adlandır](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure project ilişkilendirmeleri rolü projeleri için çözüm vardır. Proje yöntemlerine *Hizmet tanım dosyası* ve *hizmet yapılandırma dosyasını*:

- **Hizmet tanım dosyası** -uygulama, hangi roller gereklidir dahil olmak üzere, uç noktaları ve sanal makine boyutu için çalışma zamanı ayarlarını tanımlar.
- **Hizmet yapılandırma dosyasını** -kaç rol örneklerini çalıştırma ve bir rol için tanımlanan ayarlara değerleri olan yapılandırır.

Bu dosyalar hakkında daha fazla bilgi için bkz. [Visual Studio ile bir Azure bulut hizmeti için rolleri yapılandırmak](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio ile Azure bulut hizmeti projelerinde rollerini yönetme](./vs-azure-tools-cloud-service-project-managing-roles.md)
