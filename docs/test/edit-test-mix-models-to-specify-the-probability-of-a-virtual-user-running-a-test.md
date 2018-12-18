---
title: Karışımı modellerini düzenleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6016aaa3273347509d82af5ef4fba70fa3ecc253
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057119"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Bir testi çalıştıran sanal kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleme

*Test karışımı modeli* bir yük testi senaryosunda belirli bir testi çalıştıran sanal kullanıcıya yönelik olasılığı belirtir. Bu, yükü daha gerçekçi bir benzetimini sağlar. Uygulamalarınız boyunca yalnızca bir iş akışı sahip olmak yerine, son kullanıcıların uygulamalarınızla nasıl etkileşmeleri hakkında daha yakın bir benzetim olan birkaç iş olabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Test karışım modeli seçenekleri

Yük testi senaryonuzun aşağıdaki test karışımı modeli seçeneklerinden birini belirtebilirsiniz:

-   **Toplam test sayısı tabanlı:** sanal kullanıcı bir test yinelemesi başlattığında hangi web performans veya birim testi çalıştırma belirler. Yük testi sonunda, belirli bir testin çalışma sayısı, atanan test dağıtımını eşleşir. Bu test karışımı modeli, test karışımını bir IIS günlüğü ya da üretim verilerindeki işlem yüzdeleri dayandırırken kullanın.

-   **Sanal kullanıcı sayısına göre:** belirli bir web performans veya birim testi çalıştıracak sanal kullanıcıların yüzdesini belirler. Yük testi içindeki herhangi bir noktada, belirli bir testi çalıştıran kullanıcıların sayısı, atanan dağıtım eşleşir. Belirli bir testi çalıştıran kullanıcıların yüzdesi üzerinde test karışımını dayandırırken bu test karışımı modelini kullanın.

-   **Kullanıcı adımı tabanlı:** yük testi boyunca, her bir web performans testi veya birim testi belirtilen sayıda kullanıcı, saat başına bir kez çalıştırılır. Bu test karışımı modeli, yük testi boyunca belirli bir hızda testi çalıştırmak için sanal kullanıcıların istediğinizde kullanın.

-   **Ardışık düzenine dayanan:** her sanal kullanıcı, testlerin senaryoda tanımlandığı sırada web performans veya birim testleri çalıştırır. Sanal kullanıcı yük testi tamamlanana kadar testler içinde bu sırada dolaşma devam eder.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testi için test karışımını belirtme:** bir yük testi oluşturduğunuzda, yük testi için ayarları belirtin **Yeni Yük Testi Sihirbazı**. İçinde **Yeni Yük Testi Sihirbazı**, ilk senaryoya eklemek için var olan web ve birim testi seçin. Testleri senaryoya ekledikten sonra test karışımını senaryosu için belirtin.<br /><br /> Bir yük testi Web sitesinin veya uygulamanın beklenen gerçek hayatta kullanımı daha doğru bir şekilde tahmin etmek için yük modelleme seçenekleri kullanın. Bir doğru yük modeli dayalı olmayan bir yük testi yanıltıcı sonuçlara neden olabilir çünkü bunu yapmak önemlidir.|-   [Web sitenize veya uygulamanıza beklenen gerçek dünya kullanımının öykünmesini](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Test karışımı modeli Düzenle:** kullanarak test karışımı modellerini birini kullanmak için bir yük testi senaryosuna değiştirebilirsiniz **Yük Testi Düzenleyicisi**.||
|**Bir kullanıcı belirlediğiniz hızda ilerleyebileceğiniz test karışımı modeli için ilerleme gecikmesini yapılandırmak:** yük testi senaryonuzun kullanmak üzere yapılandırılmışsa **kullanıcı adım testi karışım modeli tabanlı**, ilerleme gecikme yapılandırılan dağıtım nasıl istediğinizi belirtebilirsiniz.|-   [Nasıl yapılır: kullanıcı adım testi karışım modeli kullanılırken Adım Gecikmesine dağıtımı Uygula](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Bir senaryoda test karışımı modelini değiştirme

Kullanarak yük testi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için.

> [!NOTE]
> Yükleme ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

Kullanarak **Yük Testi Düzenleyicisi**, bir yük testi senaryosunda test karışımı modeli düzenleyerek değiştirebilirsiniz **Test karışımı türü** özelliğinde **özellikleri** penceresi.

### <a name="to-change-the-test-mix-model"></a>Test karışımı modeli değiştirmek için

1.  Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2.  İçinde *senaryoları* klasörü yük testi ağacında, en fazla test yinelemesi sayısını belirtmek istediğiniz senaryoyu düğümünü seçin.

3.  Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Kategoriler ve özellikler bu senaryonun görüntülenir.

4.  İçinde **Test karışımı türü** özelliği, üç nokta düğmesini ( **...** ).

     **Test Karışımını Düzenle** iletişim kutusu görüntülenir.

5.  Aşağı açılan listesinde seçin **Test karışımı modeli** senaryo için kullanmak istediğiniz test karışımı modeli seçin.

6.  (İsteğe bağlı) Test karışımını kullanarak değiştirme **Ekle**, **Kaldır** ve **Dağıt** düğmeler ve dağıtım kaydırıcıları. Daha fazla bilgi için [bir yük testi senaryosunda dahil etmek için hangi testlerin belirlemek için test karışımını Düzenle](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7.  (İsteğe bağlı) Başlatma veya onay kutularını kullanarak ve istenen testleri seçerek sonlandırmak için bir web başarım ve birim testi belirtin. Daha fazla bilgi için [Emulate beklenen gerçek dünya kullanımının Web sitenize veya uygulamanıza](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8.  Seçin **Tamam**.

     **Özellikleri** penceresi için yeni test karışımı modeli görüntüler **Test karışımı türü** özelliği.

9. Özellik değiştirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Ardından, yeni kullanarak yük testi çalıştırabilirsiniz **Test karışımı türü** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)