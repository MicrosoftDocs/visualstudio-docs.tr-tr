---
title: 64 bitlik bir işlem olarak birim testi çalıştırma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4ee070adba33328253d7abeb122ec2ca2da145ef
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062722"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

Bir 64 bit makineniz varsa, birim testleri çalıştırma ve 64-bit işlem olarak kod kapsamı bilgileri yakalayın.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Bir 64 bit işlem olarak birim testi çalıştırmak için

1. Kod veya testleri 32-bit/x86 derlendi ancak artık bunları 64 bit işlem olarak çalıştırmak istediğiniz, olarak yeniden derleyin **herhangi bir CPU**, ya da isteğe bağlı olarak **64-bit**.

    > [!TIP]
    > Maksimum esneklik için test projelerinizi derleyin **herhangi bir CPU** yapılandırma. Daha sonra hem 32-bit hem de 64 bit aracıların çalıştırabilirsiniz. İle test projelerini derlemek için herhangi bir avantaj sağlamaz **64-bit** yapılandırma.

2. Visual Studio menüsünden **Test**, ardından **ayarları**ve ardından **İşlemci mimarisi**. Seçin **x64** testleri 64 bit işlem olarak çalıştırılacak.

   - veya -

   Belirtin `<TargetPlatform>x64</TargetPlatform>` içinde bir *.runsettings* dosya. Bu yöntemin avantajı, farklı dosyalarında ayar gruplarını belirtin ve farklı ayarlar arasında hızlıca geçiş olmasıdır. Ayrıca, ayarları çözümleri arasında kopyalayabilirsiniz. Daha fazla bilgi için [bir .runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Birim testi kod](../test/unit-test-your-code.md)
