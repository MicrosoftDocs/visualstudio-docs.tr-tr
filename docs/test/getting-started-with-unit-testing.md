---
title: Birim testi ile çalışmaya başlama
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e8835edb2b340778c4431d3de5b554d6aeb6c6d
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158820"
---
# <a name="get-started-with-unit-testing"></a>Birim testi ile çalışmaya başlama

Tanımlamak ve kod durumunu korumak için kod kapsamından emin olmak ve müşterilerinizin yapmadan önce hataları ve hataları bulmak için birim testlerini çalıştırmak için Visual Studio'yu kullanın.

## <a name="create-unit-tests"></a>Birim testleri oluşturma

Birim testleri oluşturun ve bunları sık kodunuzun düzgün çalıştığından emin olmak için çalıştırın.

1. Birim testi projesi oluşturun.

   ![Birim test projesi çözümünüze ekleyin.](media/createunittest1.png)

1. Projenizi adlandırın.

   ![Birim test projesi şablonu](media/createunittest2.png)

   Projeyi çözümünüze eklenir.

   ![Çözüm Gezgini'nde birim testi projesi](media/createunittest5.png)

1. Birim test projesinde test etmek istediğiniz projeye bir başvuru ekleyin.

   ![Birim test projenize bir başvuru ekleyin](media/createunittest6.png)

1. Test edeceğiniz kodu içeren projeyi seçin.

   ![Başvuru eklemek için seçin](media/createunittest7.png)

1. Birim testinizi kodlayın.

   ![Kod için birim test Ekle](media/createunittest8.png)

Birim testi ile yöntemi saptamalar oluşturabilirsiniz **birim testleri Oluştur** [komut](create-unit-tests-menu.md).

![Birim Testleri Oluştur komutunu kullanarak](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Birim testleri çalıştırma

1. Açık **Test Gezgini**.

   ![Test menüsünde Test gezginini açın](media/rununittest1.png)

1. Birim testlerini çalıştırın.

   ![Test Gezgini'nde birim testleri çalıştırma](media/rununittest2.png)

   Birim testleri, Geçti veya başarısız gördüğünüz **Test Gezgini**.

   ![Test Gezgini'nde birim testi sonuçlarını gözden geçirin](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>Canlı birim testi sonuçlarını görüntüleme

MSTest, xUnit ve NUnit test çerçevesi Visual Studio 2017 veya sonraki bir sürümde kullanıyorsanız, Canlı Birim testlerinizin sonuçları görebilirsiniz.

> [!NOTE]
> Live unit Testing, yalnızca Visual Studio 2017 Enterprise sürümünde kullanılabilir.

1. Live unit testing alanından açma **Test** menüsü.

   ![Live unit Testing üzerinde Aç](media/live-test-results-start.png)

1. Yazma ve kod düzenleme gibi kod düzenleyicisi penceresi içinde test sonuçlarını görüntüleyin.

   ![Test sonuçlarını görüntüleme](media/live-test-results-ui.png)

1. Test sonucu göstergeleri daha fazla bilgi görmek için seçin.

   ![Test sonucu göstergelerini seçin](media/live-test-results-details.png)

Daha fazla ayrıntı için [Live unit testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Intellitest ile birim testleri oluşturma

Intellitest çalıştırdığınızda, hangi testlerin başarısız oluyor ve onları düzeltmek için tüm gerekli kodu eklemek kolayca görebilirsiniz. Hangi testlerin bir regresyon paketi sağlamak için bir test projesine kaydetmek için seçebilirsiniz. Kodunuzu değiştikçe, üretilen testler, kod değişikliğine eşitlenmiş şekilde tutmanızı sağlayacak Intellitest yeniden çalıştırın. Bilgi edinmek için bkz. nasıl [Intellitest ile kodunuz için birim testleri oluşturmak](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Intellitest oluşturma birim testleriyle](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Kullanım **Test Gezgini** birim testlerini Visual Studio ya da üçüncü taraf birim testi projelerini çalıştırmak için testleri kategoriler halinde gruplandırmak, test listesini filtrelemek ve oluşturmak, kaydedin ve test çalma listeleri çalıştırın. Ayrıca, Testlerde Hata Ayıkla ve test, performans ve kod kapsamını analiz edin. Bilgi edinmek için bkz. nasıl [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md).

![Test Gezgini ile birim testleri çalıştırılırken](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz kodunuzun büyük bir kısmı entegrasyonlar için çalışılmalı. Bilgi edinmek için bkz. nasıl [ne kadar kodun test edildiğini belirlemek için kod kapsamı kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-different-unit-test-framework"></a>Farklı birim testi çerçevesini kullanın

Visual Studio'da, Boost, Google ve NUnit gibi üçüncü taraf test çerçevelerini kullanarak birim testleri çalıştırabilirsiniz. Visual Studio test Çalıştırıcısı bu çerçeveyle çalışabilmesi için eklenti çerçevesini kullanın.

Üçüncü taraf test çerçevelerini etkinleştirme adımları şunlardır:

1. Seçin **Araçları** > **Uzantılar ve güncelleştirmeler** menü çubuğundan.

1. İçinde **Uzantılar ve güncelleştirmeler** iletişim kutusunda **çevrimiçi** kategorisi ve ardından **Visual Studio Market**. Ardından, **Araçları** > **test**.

   ![Visual Studio Market](media/extensions-and-updates-testing.png)

1. Framework veya yükleyin ve ardından istediğiniz bağdaştırıcıyı seçin **indirme**.

1. Bir sınıf kitaplığı projesi oluşturun ve çözümünüze ekleyin.

   ![Sınıf Kitaplığı projesini adlandırın ve ekleyin](media/create3rdpartyunittest3.png)

1. Eklentiyi yükleyin. İçinde **Çözüm Gezgini**, sınıf kitaplığı Projesi'ni seçin ve ardından **NuGet paketlerini Yönet** , sağ tıklayın veya bağlam menüsünde.

   ![Eklentiyi yüklemek için NuGet paketlerini Yönet](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) ekleme ve güncelleştirme kitaplıkları ve araçları projeleriniz için kullanabileceğiniz Visual Studio uzantısıdır.

1. İçinde **NuGet Paket Yöneticisi** penceresinde arayın ve eklentiyi seçin ve ardından **yükleme**.

   ![3. taraf Framework'ü yükleme](media/create3rdpartyunittest4.png)

   Projenizde çerçevenin başvuruldu.

   ![3. taraf birim testi çerçevesi için başvuru çözümünüze eklenir](media/create3rdpartyunittest6.png)

1. Sınıf kitaplığı Proje öğesinden **başvuruları** düğümünü **Başvuru Ekle**.

   ![Projeye bir başvuru ekleyin](media/createunittest6.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda, test kodu içeren projeyi seçin.

   ![Kod projesi, test etmek için seçin](media/createunittest7.png)

1. Birim testinizi kodlayın.

   ![Kod birim testi kod dosyanıza ekleyin](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Birim Testleri Oluştur komutu](create-unit-tests-menu.md)
* [Intellitest ile testleri oluşturma](generate-unit-tests-for-your-code-with-intellitest.md)
* [Test Gezgini ile testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Kod kapsamı belirleme](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Kod kalitesini geliştirme](improve-code-quality.md)