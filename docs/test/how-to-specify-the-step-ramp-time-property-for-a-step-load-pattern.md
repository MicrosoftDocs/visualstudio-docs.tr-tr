---
title: Yük testi için Adım yük düzeni için Adım Rampa Süresi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 81373e30498ad02f4007e096cfbc6a7cff953402
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895725"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Nasıl yapılır: Adım yük düzeni için Adım Rampa Süresi özelliğini belirtme

İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için. Daha fazla bilgi için [izlenecek yol: bir yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

**Adım eğrisi süresi** özelliği ayarlandığında **özellikleri** penceresi. Yük testi senaryosu özelliklerini Düzenle **Yük Testi Düzenleyicisi**.

**Adım eğrisi süresi** özelliği yalnızca bir adım yük düzeni ile kullanılır. Daha fazla bilgi için [düzenleme yük desen modeli sanal kullanıcı etkinliği](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Adım yük düzeni, kullanıcı yükü arttıkça performansın nasıl değişeceğini görebileceğiniz şekilde yük testi yapılırken sunucu veya sunucular üzerindeki yükü artırmak için kullanılır. Örneğin kullanıcı yükü 2.000 kullanıcıya olarak sunucu veya sunucularınızın nasıl gerçekleştirmek görmek için aşağıdaki özelliklere sahip bir adım yükü düzenini kullanarak 10 saatlik yük testi çalıştırabilirsiniz:

-   İlk kullanıcı sayısı: 100

-   En yüksek kullanıcı sayısı: 2000

-   Adım Süresi (saniye): 1800

-   Adım Rampa Süresi (saniye): 20

-   Adım kullanıcısı sayısı: 100

Bu ayarlar, kullanıcı yükü 100, 200, 300, 2.000 kullanıcıya kadar 30 dakika (1800 saniye) süresince yükleme testi vardır.

> [!NOTE]
> **Adım eğrisi süresi** özelliği seçin kullanılamıyor bu özelliklerden yalnızca biri **Yeni Yük Testi Sihirbazı**.

**Adım eğrisi süresi** özelliği bir adımdan bir sonrakine (örneğin 100 kullanıcıdan 200 kullanıcıya) artırma aşamalı yerine hemen olmasını sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süreçte 100 kullanıcıdan 200'e yükseltilmiştir (saniyede 5 kullanıcılık bir Yükseliş).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Adım yük düzeni için Adım Rampa Süresi özelliği düzenlemek için

1.  Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2.  Yük testi **senaryoları** senaryo düğümünü Adım Rampa belirtmek istediğiniz zaman için klasörü açın.

3.  Seçin **adım yükü düzenini** düğümü.

    > [!NOTE]
    > Yük düzeni senaryo için Adım yük düzeni olması gerekir. Yük düzeni, yüklü değilse, şu anda senaryosu ile ilişkili olan yük deseni türü görüntülenir. Daha fazla bilgi için [düzenleme yük desen modeli sanal kullanıcı etkinliği](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4.  Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Senaryonun kategoriler ve özellikler görüntülenir **özellikleri** penceresi.

5.  Değerini **adım eğrisi süresi** özelliği tarafından belirtilen kullanıcıların kademeli olarak her adımda geçen saniye eklemek için birkaç girerek **adım kullanıcı sayısı** özelliği.

6.  Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni kullanarak yük testlerini çalıştırabilirsiniz **adım eğrisi süresi** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)