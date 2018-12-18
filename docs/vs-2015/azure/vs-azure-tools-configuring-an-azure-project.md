---
title: Azure bulut hizmeti projesi yapılandırma
description: Bu proje için gereksinimlerinize bağlı olarak Visual Studio'da bir Azure bulut hizmeti projesi yapılandırmayı öğrenin.
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: e117eb436ff1cf37740e97ee1889bc1bf063db94
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051380"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesini yapılandırma
Bu proje için gereksinimlerinize bağlı olarak, bir Azure bulut hizmeti projesi yapılandırabilirsiniz. Aşağıdaki kategorilerde projesi için özellikleri ayarlayabilirsiniz:

- **Azure'a bir bulut hizmeti yayım** -Azure'a dağıtılan var olan bir bulut hizmeti yanlışlıkla olarak silinmediğinden emin olmak için bir özelliği ayarlayabilirsiniz.
- **Çalıştırabilir veya yerel bilgisayarda bir bulut hizmetinde hata ayıklama** -Azure depolama öykünücüsü'nü başlatmak isteyip istemediğinizi belirtin ve kullanmak için bir hizmet yapılandırması seçebilirsiniz.
- **Bir bulut hizmeti paketi oluşturulduğunda doğrulama** -bulut hizmeti paketi herhangi bir sorun olmadan dağıtır sağlayabilirsiniz. böylece, tüm uyarıları hata olarak değerlendir karar verebilirsiniz.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Bir Azure bulut hizmeti projesi yapılandırma adımları
1. Visual Studio'da bir bulut hizmeti projesini oluşturun veya açın

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden seçin **özellikleri**.

1. Proje özellikleri sayfasında seçin **geliştirme** sekmesi.

    ![Proje Özellikleri menüsü](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Ayarlama **mevcut bir dağıtımı silmeden önce sor** için **True**. Bu ayar mevcut bir Azure dağıtımında yanlışlıkla silme sağlamaya yardımcı olur

1. İstenen seçin **hizmet yapılandırması** çalıştırdığınızda veya Bulut hizmetinizi yerel olarak hata ayıklama kullanmak istediğiniz hangi hizmet yapılandırmasını belirtmek için. Bir rol için bir hizmet yapılandırmasının nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [Visual Studio ile bir Azure bulut hizmeti için rolleri yapılandırmak nasıl](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Ayarlama **Başlat Azure storage öykünücüsü** için **True** çalıştırdığınızda veya Bulut hizmetinizi yerel olarak hata ayıklama ve Azure storage öykünücüsü başlatmak için.

1. Ayarlama **uyarıları hata olarak değerlendir** için **True** paket doğrulama hataları varsa yayımlayamıyor emin olmak için.

1. Ayarlama **web projesi bağlantı noktalarını kullanacak** için **True** web rolünüz aynı bağlantı noktasını kullandığından emin olmak için her zaman, IIS Express'in yerel olarak başlatır.

1. Visual Studio araç çubuğundan seçin **Kaydet**.

## <a name="next-steps"></a>Sonraki adımlar
- [Birden çok hizmet yapılandırması'nı kullanarak bir Azure projesi yapılandırın](vs-azure-tools-multiple-services-project-configurations.md)
