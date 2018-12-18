---
title: Geliştirici test araçları
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 396bbfdb915d0e3ecc31f516d60eab80cca6a421
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295156"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Geliştirici test araçları, senaryoları ve yetenekleri

İle birim testi kodu sistem durumu korur. Visual Studio, çok çeşitli güçlü araçlar ve teknikler uygulamaları test ederken kullanmak, geliştiriciler için sağlar.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Intellitest ile kod kapsamı elde etmek ve gerilemeleri önleyin

Geleneksel birim test paketleri, her test çalışması işbu kullanım senaryosu temsil eder ve onaylar giriş ve çıkış arasındaki ilişkiyi toplamıştır.  Birkaç tür senaryoların yanı sıra doğrulama yeterli olabilir, ancak deneyimli geliştiriciler hataları daha iyi test edilmiş kod içinde doğru olduğunda ne zaman ortaya ancak test edilmemiş girişleri yanlış yanıtlar yol açabilirsiniz bildirin.

Kapsamı geliştirin ve Intellitest ile gerilemeleri önleyin. Intellitest yeni veya mevcut koda yönelik birim testleri oluşturmak ve sürdürmek için gereken çabayı önemli ölçüde azaltır.

![Intellitest sürüyor](media/devtest-intellitest.png)

* [Intellitest Visual Studio ile giriş](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [Intellitest – hepsini yönetmek için bir test](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)
* [Intellitest videoları](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Intellitest ile çalışmaya başlama](generate-unit-tests-for-your-code-with-intellitest.md)
* [Intellitest başvuru kılavuzu](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Kullanıcı arabirimi kodlanmış UI ve Selenium ile test

Türünün en iyisi, kullanıcı arabirimi (UI) test veya UI testi topluluk onaylandı. Kodlanmış UI testleri, uygulamanızın kullanıcı arabiriminin davranışı ve işlevsellik doğrulamak için tam olarak otomatikleştirilmiş testler oluşturmak için bir yol sağlar. Bunlar, teknoloji, XAML tabanlı UWP uygulamaları, tarayıcı uygulamaları ve SharePoint uygulamaları gibi birçok platformda UI testi otomatik hale getirebilirsiniz.

Seçtiğiniz kodlanmış UI testleri en iyi şekilde breed veya Selenium, Visual Studio test genel tarayıcı tabanlı kullanıcı Arabirimi, ihtiyacınız olan araçları sağlar.

![Kullanıcı Arabirimi ile kodlanmış UI testi](media/devtest-codeduitest.png)

* [UI otomasyonunu kullanarak kodunuzu test etme](use-ui-automation-to-test-your-code.md)
* [Oluşturma, düzenleme ve kodlanmış UI testi Bakımı kullanmaya başlayın](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Kodlanmış UI testleriyle UWP uygulamalarını test etme](test-uwp-app-with-coded-ui-test.md)
* [Kodlanmış UI testleriyle SharePoint uygulamaları test etme](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Kodlanmış UI testlerini Visual Studio Enterprise (Laboratuvar) ile giriş](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Geçerli birim testi ile Visual Studio kod kapsamı

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından edildiğini belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz çalışma veya 'kodunuzun büyük bir kısmı kapsamalıdır'.

Kod kapsamı analizi, yönetilen ve yönetilmeyen (yerel) kod için uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

* [Ne kadar kodun test edildiğini belirlemek için kod kapsamını kullanma](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Birim testi, kod kapsamını ve kod kopya Analizi ile Visual Studio (Laboratuvar)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Kod kapsamı analizini özelleştirme](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** oluşturma, yönetme ve birim testleri geliştiricilerin yardımcı olur.

![Visual Studio Test Gezgini](media/devtest-testexplorer.png)

* [Birim testi ile çalışmaya başlama](unit-test-your-code.md)
* [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Test Gezgini Hakkında SSS](test-explorer-faq.md)
* [Üçüncü taraf birim testi çerçevelerini yükleme](install-third-party-unit-test-frameworks.md)

Visual Studio ayrıca genişletilebilir ve üçüncü taraf birim test bağdaştırıcısı NUnit ve xUnit.net gibi kapısı açılır. Ayrıca, kod kopyalama yeteneğini yakından el gider yaygın hata düzeltmeleri için aday olabilecek anlamsal olarak benzer bir kod bloklarını belirlemenize yardımcı olur veya yeniden düzenleme yüksek kaliteli yazılım sunmaya ile.

![Üçüncü taraf test tümleştirmesi](media/devtest-thirdparty.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Birim testi ile çalışmaya başlama](getting-started-with-unit-testing.md)
* [Birim testi yürütme Team Foundation Server'da hızlandırın](https://blogs.msdn.microsoft.com/devops/2015/07/30/speeding-up-unit-test-execution-in-tfs/)
* [Paralel ve bağlam hassas birim testi yürütme](https://blogs.msdn.microsoft.com/devops/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Birim testi, kod kapsamını ve kod kopya Analizi ile Visual Studio (Laboratuvar)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
