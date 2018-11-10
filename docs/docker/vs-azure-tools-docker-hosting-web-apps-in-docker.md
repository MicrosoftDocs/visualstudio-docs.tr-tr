---
title: Azure Container Registry (ACR) için bir ASP.NET Docker kapsayıcısı dağıtma | Microsoft Docs
description: ASP.NET Core web uygulaması bir kapsayıcı kayıt defterine dağıtmak için Docker için Visual Studio Araçları'nı kullanmayı öğrenin
services: azure-container-service
documentationcenter: .net
author: mlearned
manager: douge
editor: ''
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.service: azure-container-service
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 05/21/2018
ms.author: mlearned
ms.openlocfilehash: 584faff1c09e6d345d7e166616a9036da2223b51
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673913"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>ASP.NET kapsayıcısını bir kapsayıcı kayıt defterine Visual Studio kullanarak dağıtma
## <a name="overview"></a>Genel Bakış
Docker, bazı açılardan konak uygulamalar ve hizmetler için kullanabileceğiniz bir sanal makineye, benzer bir basit bir kapsayıcı alt yapısıdır.
Bu öğreticide, kapsayıcıya alınmış uygulamanızı yayımlamak için Visual Studio kullanarak açıklanmaktadır bir [Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Azure aboneliğiniz yoksa, oluşturun bir [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) başlamadan önce.

## <a name="prerequisites"></a>Önkoşullar
Bu öğreticiyi tamamlamak için:

* En son sürümünü yükleyin [Visual Studio 2017](https://azure.microsoft.com/downloads/) "ASP.NET ve web geliştirme" iş yüküyle birlikte sağlanır
* Yükleme [Windows için Docker](https://docs.docker.com/docker-for-windows/install/)

## <a name="1-create-an-aspnet-core-web-app"></a>1. Bir ASP.NET Core web uygulaması oluşturma
Aşağıdaki adımlar Bu öğreticide kullanılan temel bir ASP.NET Core uygulaması oluşturmada size yol.

[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]

## <a name="2-publish-your-container-to-azure-container-registry"></a>2. Kapsayıcınızı Azure Container Registry'ye yayımlama
1. Projenize sağ tıklayın **Çözüm Gezgini** ve **Yayımla**.
2. Yayımlama hedefi iletişim kutusunda seçin **kapsayıcı kayıt defteri** sekmesi.
3. Seçin **yeni Azure Container Registry** tıklatıp **Yayımla**.
4. İstenen değerleri doldurun **yeni bir Azure Container Registry oluşturma**.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS ön eki** | Genel olarak benzersiz adı | Kapsayıcı kayıt defterinizde benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizde oluşturulacağı kaynak grubunun adı. Seçin **yeni** yeni bir kaynak grubu oluşturmak için.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standart | Hizmet katmanı kapsayıcı kayıt defterinin  |
    | **Kayıt defteri konumu** | Size yakın bir konum | Bir konumdan seçin bir [bölge](https://azure.microsoft.com/regions/) yakınınızdaki veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlere yakın. |
    ![Visual Studio'nun iletişim Azure Container Registry oluşturma][0]
5. Tıklayın **oluşturma**

Artık kapsayıcı kayıt defterinden herhangi bir konağa Docker görüntüleri, örneğin çalıştırma yeteneğine çekebilirsiniz [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:media/vs-azure-tools-docker-hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png