---
title: Yük testi için dağıtım gecikmesine için geçerlidir
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 19634186e13574c322c2e9bcc636dda3a823b158
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896204"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Nasıl yapılır: kullanıcı adım testi karışım modeli gecikmesine dağıtımı Uygula

Kullanarak yük testi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, senaryonun özelliklerini test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Gecikmesine Dağıtım uygulama** özelliği ayarlanmış kullanarak **özellikleri** penceresi. Yük Testi Düzenleyicisini kullanarak yük testi senaryosu özellikleri değiştirilmiştir.

> [!NOTE]
> **Gecikmesine Dağıtım uygulama** özelliği, yalnızca geçerli *yük test karışımını* kullanıcı adımı tabanlı yapılandırılır. Daha fazla bilgi için [bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Değeri **Gecikmesine Dağıtım uygulama** true veya false olarak ayarlanabilir:

- **True**: değer tarafından belirtilen normal istatistiksel dağılımı gecikmeler senaryo geçerlidir **saatte kullanıcı başına testler** sütununda **Test Karışımını Düzenle** iletişim kutusu. Daha fazla bilgi için [bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Örneğin, sahip olduğunuz varsayılmıştır **saatte kullanıcı başına testler** değerini **Test Karışımını Düzenle** Ayarla iletişim kutusu test için saat başına iki kullanıcı. Varsa **Gecikmesine Dağıtım uygulama** özelliği **True**, normal bir istatistiksel dağılımı testler arasındaki bekleme süresi uygulanır. Testleri saatte iki test çalışmaya devam edecektir, ancak bunlar arasında 30 dakikalık bir gecikmeyle mutlaka olmayacaktır. Dört dakika sonra 45 dakika sonra ikinci test ilk testin çalıştırabilirsiniz.

- **False**: değeri için belirtilen bir hızda testler **saatte kullanıcı başına testler** sütununda **Test Karışımını Düzenle** iletişim kutusu. Daha fazla bilgi için [bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Örneğin, sahip olduğunuz varsayılmıştır **saatte kullanıcı başına testler** değerini **Test Karışımını Düzenle** Ayarla iletişim kutusu test için saat başına iki kullanıcı. Varsa **Gecikmesine Dağıtım uygulama** özelliği **False**, testlerinizi çalıştırdığınızda, hiçbir yaratmamış olursunuz. Test, 30 dakikada bir çalışır. Bu, saat başına iki testleri çalıştırmanızı sağlar.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Dağıtım senaryosu gecikmesine özellik ayarı Uygula belirtmek için

1. Bir yük testi açın.

   **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2. İçinde **senaryoları** yük testi ağacında, klasörünü gönderilmemiş dağıtım için uygulamak istediğiniz senaryo düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

   Kategoriler ve özellikler bu senaryonun görüntülenen **özellikleri** penceresi.

4. Özellik değeri için **Gecikmesine Dağıtım uygulama**, şunlardan birini seçin **True** veya **False**.

5. Seçin **dosya** > **Kaydet**. Artık yük testi yeni çalıştırabilirsiniz **Gecikmesine Dağıtım uygulama** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)