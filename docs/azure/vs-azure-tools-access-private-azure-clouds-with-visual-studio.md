---
title: Azure özel bulutlara erişme
description: Visual Studio kullanarak özel bulut kaynakları erişmeyi öğrenin.
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 04f2576fcc96f11bda8d46e2c187f6f0030710b6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061895"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Visual Studio ile Azure özel bulutlara erişme

Varsayılan olarak, Visual Studio, Azure bulut REST uç noktalarını destekler. Bu makalede, özel bulutunuzun sertifika erişmek ve Visual Studio'dan bir özel bulutla etkileşim kurmak için nasıl kullanılacağını öğrenin.

1. Özel bulut için Azure portalında, yayımlama ayarları dosyasını indirin veya bir yayımlama ayarları dosyası için yöneticinize başvurun. (Dosya uzantısına sahip `.publishsettings`.)

1. Visual Studio'da **Sunucu Gezgini**, sağ **Azure** düğümünü seçip alt **yönetin ve filtre abonelikleri**.

    ![Komut Abonelikleri Yönetme](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. İçinde **Microsoft Azure abonelikleri yönetme** iletişim kutusunda **sertifikaları** sekmesine ve ardından seçin **alma**.

    ![Azure sertifikaları içeri aktarma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. İçinde **alma Microsoft Azure abonelikleri** iletişim kutusunda **Gözat**.

    ![Gözat düğmesi alma Microsoft Azure abonelikleri iletişim](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. İçinde **açık** Seç dosyasını ve ardından seçin iletişim kutusu, yayımlama ayarları dosyasını kaydettiğiniz dizine gidin **açık**.

    ![Yayımlama ayarları dosyası seçin](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. İçin döndürülen **alma Microsoft Azure abonelikleri** iletişim kutusunda **alma**.

    ![Yayımlama ayarları dosyasını içeri aktar](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Sertifikaları yayımlama ayarlarını dosyasından Visual Studio'ya içeri aktarılır ve artık, özel bulut kaynakları ile etkileşim kurabilir.

