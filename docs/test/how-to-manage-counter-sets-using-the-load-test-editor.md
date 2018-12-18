---
title: Yük Testi Sayaç kümeleri
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 995cf0653886745d44ede4553e03f81ed45d37d7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049087"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisini kullanılarak sayaç kümelerini yönetme

İle bir yük testi oluşturduğunuzda, **Yeni Yük Testi Sihirbazı**, bir başlangıç sayaç kümesini ekleyin. Bu, Yük testiniz için ön tanımlı sayaç kümeleri kümesini sunar.

> [!NOTE]
> Yük testlerinizi Uzak makinelerde dağıtılmışsa, denetleyici ve aracı sayaçları denetleyicisi ve aracısı için eşlenen sayaç kümeleri. Uzak makinede yük testinizde kullanma hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracılarını](configure-test-agents-and-controllers-for-load-tests.md).

Sayaç kümelerini yönetme performans verilerini toplamak istediğiniz bilgisayar kümesini seçme ve atama her bir bilgisayardan toplamak için sayaç kümeleri kümesini içerir. Sayaçlarınızı yönettiğiniz **Yük Testi Düzenleyicisi**.

![Sayaç kümelerini yönetme](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Sayaç kümelerini yönetme

1.  Bir yük testi açın.

2.  Seçin **sayaç kümelerini Yönet** düğmesi.

     – veya –

     Sağ **sayaç kümeleri** klasörü yük testi ağacında ve seçin **sayaç kümelerini Yönet**.

     **Sayaç kümelerini Yönet** iletişim kutusu görüntülenir.

3.  (İsteğe bağlı) İçinde **seçili bilgisayarlar ve sayaç kümeleri aşağıdaki çalışma ayarları altına eklenecek** liste kutusu, farklı bir çalışma ayarı seçin.

    > [!NOTE]
    > Bu, yalnızca yük testinize birden fazla çalışma ayarı varsa geçerlidir.

4.  (İsteğe bağlı) Seçin **bilgisayar Ekle** izlemek için yeni bir bilgisayar eklemek için. İçin bir ad istenir. Bir bilgisayarın adını yazın ve yeni girdi altındaki düğümleri görürsünüz. Örneğin **ASP.NET**, **IIS**, **SQL**ve diğerleri. Seçmek istediğiniz düğümleri önünde onay kutularını seçin. Yeni sayaç görünür **Önizleme seçimleri** bölmesi.

5.  (İsteğe bağlı) İçinde **bilgisayar etiketleri** metin kutusuna bilgisayarla ilişkilendirmek için bir etiket yazın. Örneğin, "TestMachine12 olarak lab3".

     Bilgisayar etiketleri bir kolayca tanımak ada sahip bir bilgisayar tanımlamanıza olanak sağlar.

     Etiketler görüntülenir **sayaç kümesi eşlemeleri** Yük Testi Düzenleyicisi'nde ağaç düğümü. Daha da önemlisi, etiketler yardımcı olan bilgisayar ve yük testinde sahip rolü proje katılımcılarını belirleme, Excel raporlarında görüntülenir. Örneğin, "Web Sunucu1 lab2 içinde" veya "SQL Server2 Phoenix Office". Daha fazla bilgi için [rapor yük testleri için test karşılaştırmaları veya eğilim analizi sonuçları](../test/compare-load-test-results.md).

6.  Seçin **Tamam**.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testi içinde belirtin.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)