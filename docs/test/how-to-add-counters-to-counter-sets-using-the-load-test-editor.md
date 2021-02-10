---
title: Yük testi için sayaç kümelerine sayaç ekleme
description: Yük Testi Sihirbazı bir yük testi oluşturduğunuzda, bir ilk sayaç kümesi eklersiniz. Yük Testi Düzenleyicisi kullanarak sayaçların nasıl ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ddfdf00a366c18524d2a666a74c7b7a164400402
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966974"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisi kullanarak sayaç kümelerine sayaç ekleme

**Yük Testi Sihirbazı** bir yük testi oluşturduğunuzda, bir ilk sayaç kümesi eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri kümesi sunar. Daha fazla bilgi için bkz. [bir yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testleriniz uzak makineler arasında dağıtılmışsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayaç kümelerine eşlenir. Yük testinizde uzak makinelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Sayaçlarınızı **Yük Testi Düzenleyicisi** yönetirsiniz. Teste zaten eklenmiş olan sayaç kümeleri, yük testinin **sayaç kümeleri** düğümünde görünür. Yük testi oluşturduktan sonra, mevcut sayaç kümelerine yeni sayaçlar ekleyebilirsiniz.

## <a name="to-add-counters-to-a-counter-set"></a>Sayaç kümesine sayaç eklemek için

1. Bir yük testi açın.

2. **Sayaç kümeleri** düğümünü genişletin. Yük testine eklenmiş olan tüm sayaç kümeleri görünür.

    > [!NOTE]
    > Yük testi hiyerarşisi ağacı, **çalışma ayarları** düğümünü de içerir. Bu düğüm, bu bilgisayarlarla eşlenen tüm bilgisayarları ve sayaç kümelerini gösteren **sayaç kümesi eşlemeleri** düğümünü içerir.

3. Var olan bir sayaç kümesine sağ tıklayın ve ardından **Sayaç Ekle**' yi seçin.

     **Performans sayaçlarını Seç** iletişim kutusu görüntülenir.

4. **Bilgisayar** açılan kutusu açılan kutusuna, eşlemek istediğiniz bilgisayarın adını yazın. Alternatif olarak, açılan listeden bilgisayarlardan birini seçin.

    > [!NOTE]
    > Performans verileri toplanmadan önce sayaç kümelerinin bir bilgisayara eşlenmesi gerektiğinden, performans verilerinin toplanacağı bir bilgisayar belirtmeniz gerekir.

5. Performans veri sayacı kategorilerini filtrelemek için bir **Performans kategorisi** seçin. Performans sayaçlarını seçmek için iki veri sütunu görürsünüz.

    > [!NOTE]
    > Bazı sayaç kategorileri aynı zamanda bir örnek seçmenizi gerektirir. Örneğin, bir SQL sayacı seçerseniz, hedef bilgisayarda birden fazla SQL örneği yüklü olabileceğinden bir SQL örneği seçmelisiniz.

6. Özel sayaç kümesine eklemek için bir sayaç ve örnek seçin.

     \- veya

     Tüm kullanılabilir sayaçları seçmek için **Tüm sayaçlar** radyo düğmesini seçin.

7. **Tamam ' ı** seçin.

    > [!NOTE]
    > Ayrıca, var olan bir sayacı veya sayaç kategorisini seçip Kopyala ' yı seçip farklı bir sayaç kümesi düğümüne yapıştırarak sayaç kümesine sayaçlar eklemek mümkündür. Kopyalanmış, ancak gerekli olmayan ek sayaçlar silinebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
