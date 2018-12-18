---
title: Bu kullanım Web önbellek verilerini Yük testleri için sanal kullanıcı yüzdesi belirtin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 2195b99658d05e9e73a86cf723fcb8e9d4f36bd4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060245"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Nasıl yapılır: web önbellek verilerini kullanan sanal kullanıcıların yüzdesini belirtme

İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, senaryoları özelliklerini kullanarak test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirebilirsiniz **Yük Testi Düzenleyicisi**. Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Yeni kullanıcıların yüzdesini** özelliği ayarlandığında **özellikleri** penceresi. Yük testi senaryosu özelliklerini Düzenle **Yük Testi Düzenleyicisi**.

**Yeni kullanıcıların yüzdesini** özelliği bir web tarayıcısı tarafından gerçekleştirilen yük testi taklit eden önbelleğe almayı biçimini etkiler. Varsayılan olarak, **yeni kullanıcıların yüzdesini** özelliği % 0'a ayarlayın. Varsa değerini **yeni kullanıcıların yüzdesini** özelliği, % 100'e ayarlandığında, her web performans testi yük testi çalıştırma gibi ilk kullanıcı Web sitesine kabul edilir kullanan herhangi bir içerik Web sitesinden kendi tarayıcı önbelleğinden yok Önceki ziyaretler. Bu nedenle, tüm istekler görüntüleri gibi tüm bağımlı istekleri dahil olmak üzere web testinde indirilir.

> [!NOTE]
> İsteklerin önbelleğe aynı kaynağa birden çok kez web testinde istendiğinde yüklenmez.

Yük testi çok sayıda görüntü sahip olma olasılıkları dönüş kullanıcılar sahip bir Web sitesi ise ve diğer önbelleğe içerik yerel olarak, ardından bir ayar için % 100 önbelleğe **yeni kullanıcıların yüzdesini** özelliği daha fazla oluşturacağını karşıdan yükleme isteği gerçek hayat oluşacak. Bu durumda, kullanıcılar ilk kez Web sitesinin ve ayarlama ziyaretler sitenize yüzdesini tahmin etmelidir **yeni kullanıcıların yüzdesini** özelliği uygun şekilde.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Bir senaryo için yeni kullanıcıların yüzdesini belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2. Yük testi **senaryoları** klasörü için yeni kullanıcı yüzde değeri değiştirmek istediğiniz senaryoyu düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Senaryonun kategoriler ve özellikler görüntülenir **özellikleri** penceresi.

4. Değerini **yeni kullanıcıların yüzdesini** birkaç yeni kullanıcıların yüzdesi için girerek özelliği.

5. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni kullanarak yük testlerini çalıştırabilirsiniz **yeni kullanıcıların yüzdesini** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)