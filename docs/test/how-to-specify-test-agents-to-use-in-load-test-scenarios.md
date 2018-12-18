---
title: Yük testi senaryolarında kullanılacak Test aracıları belirtme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: db7c901dd081155fe7341433f700f60de415a153
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061023"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Nasıl yapılır: test belirtin yükleme kullanılacak aracı test senaryoları

Kullanarak yük testi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

Aracıları kullanarak belirtilen **Yük Testi Düzenleyicisi** değiştirmek için **kullanılacak aracılar** özelliğinde **özellikleri** penceresi.

Senaryonuz denetleyicileri kullanıyorsanız ve uzaktan test yükü çalıştırmak için aracıları kullanmak istediğiniz aracıları belirtebilirsiniz. Örneğin, performans eğilimlerini analiz ederken tutarlılık sağlamak için belirli bir aracı kümesi belirtmek isteyebilirsiniz. Benzeşim var. böylece arasında hangi betiklerin çalıştıkları ve aracıyı bulunduğu Ayrıca, aracıların coğrafi olarak, dağıtılabilir.

> [!TIP]
> Bir aracı uzak sitede fiziksel olarak koyarak yerine, başka bir yavaş bir ağa benzetmek için ağ öykünmesini kullanabilmek için seçenektir. Daha fazla bilgi için [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Daha fazla bilgi için [Test denetleyicileri ve test aracılarını](configure-test-agents-and-controllers-for-load-tests.md).

Diğer bir neden olan bazı, tümü değil, aracıları belirli bir senaryo için gerekli olan yüklü yazılımlar olabilir.

Aracı seçimi test ayarlarında rollerini kullanarak çalışan belirli bir testi için kontrol edebilirsiniz. Daha fazla bilgi için [test ayarlarını kullanarak tanılama bilgi toplayan](../test/collect-diagnostic-information-using-test-settings.md).

Bir test aracısı makineye CPU kullanımı yüzde 75'inden daha vardır veya yüzde 10'den az kullanılabilir fiziksel bellek varsa, aracı makinenin yük testinizde bir darboğaz haline gelmediğinden emin olmak için Yük testiniz için daha fazla aracı ekleyin.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Bir senaryo için kullanılacak aracı belirtmek için

1.  Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2.  Yük testi **senaryoları** klasöründe kullanılacak aracı belirtmek istediğiniz senaryoyu düğümünü seçin.

3.  Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Kategoriler ve özellikler bu senaryonun görüntülenen **özellikleri** penceresi.

4.  Metin kutusunda **kullanılacak aracılar** özellik, senaryo çalışabilir aracıların listesini yazın.

     Aracıları ayrılmalıdır virgüllerle, örneğin "**agent1'e, birim testi Agent2, Aracı3**". Özellik boş bırakılırsa, senaryo kullanılabilir tüm aracılar kullanması gerektiğini belirtir.

    > [!NOTE]
    > **Kullanılacak aracılar** özelliği yerel çalışmalar için yoksayılır. Belirtilen aracıların hiçbiri uzaktan çalıştırmalar için **kullanılacak aracılar** var, testlerin senaryoda çalışmaz.

5.  Özellik değiştirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Ardından, yeni kullanarak yük testi çalıştırabilirsiniz **kullanılacak aracılar** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)