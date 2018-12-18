---
title: Birim Testi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b38d68d9883325d0654d476a869887bf8dc48a0c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057093"
---
# <a name="unit-test-your-code"></a>Birim testi kod

Birim testleri, geliştiricilere ve test edicilere C#, Visual Basic ve C++ projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir şekilde verin.

Birim testi araçları şunları içerir:

* **Test Gezgini**&mdash;birim testleri çalıştırmak ve bunların sonuçları görmeniz **Test Gezgini**. Bir bağdaştırıcı için olan bir üçüncü taraf çerçeve dahil olmak üzere tüm birim testi çerçevesini kullanabilirsiniz **Test Gezgini**.

* **Yönetilen kod için Microsoft birim test çerçevesi**&mdash;yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sunar.

* **C++ için Microsoft birim test çerçevesi**&mdash;C++ için Microsoft birim test çerçevesi bir parçası olarak yüklü **C++ ile masaüstü geliştirme** iş yükü. Bu, yerel kodu test etmek için bir çerçeve sunar. CTest Google Test ve Boost.Test çerçeveleri de dahildir ve ek test çerçeveleri için üçüncü taraf bağdaştırıcılar bulunmaktadır. Daha fazla bilgi için [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

* **Kod kapsamı Araçları**&mdash;Birim Test Gezgini'nde tek komuttan alıştırma testleri ürün kodu miktarını belirleyebilirsiniz.

* **Microsoft Fakes yalıtım çerçevesi**&mdash;sınıfları ve test edilen kodda bağımlılıklar oluşturan üretim ve sistem kodunun yöntemleri yerine Microsoft Fakes yalıtım çerçevesi oluşturabilirsiniz. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

Ayrıca [Intellitest](../test/generate-unit-tests-for-your-code-with-intellitest.md) test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu keşfedin. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Koddaki her koşullu şube için bir vaka analizi yapılır.

## <a name="key-tasks"></a>Ana görevler

Birim testlerini anlamaya ve oluşturmaya yardımcı olmaları için aşağıdaki konuları kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Hızlı başlangıçlar ve izlenecek yollar:** birim kod örneklerini kullanarak Visual Studio'da testi gerçekleştirmeyi öğrenmek için aşağıdaki konuları kullanın.|-   [İzlenecek yol: Oluşturma ve yönetilen kod için birim testleri çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Hızlı Başlangıç: Test Gezgini ile Test güdümlü geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**Test Gezgini ile birim testi:** Test Gezgini'nin daha üretken ve verimli birim testleri oluşturma nasıl yardımcı olabileceğini öğrenin.|-   [Birim testi temel bilgileri](../test/unit-test-basics.md)<br />-   [Bir birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />-   [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)<br />-   [Üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)|
|**Birim testleri C++ kodu**|-   [C++ için Microsoft birim testi çerçevesi ile C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Birim testlerini yalıtma**|-   [Microsoft Fakes ile test edilen kodu Ayır](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Proje kodunuzun ne oranda test edilen belirlemek için kod kapsamı kullanın:** Visual Studio Test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|-   [Ne kadar kodun test edildiğini belirlemek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Yük testlerini kullanarak stres ve performans analizleri gerçekleştirin:** yük testi oluşturma ve birim testlerinizi buna ekleyerek uygulamanızdaki performans ve stres sorularınızın yardımcı ekleyin.|-   [Test (Azure Test planları ve TFS) yükleyin](/azure/devops/test/load-test/index?view=vsts)|
|**Kalite kapıları ayarlayın:** testleri kod iade veya birleştirilmiş önce çalışmaya zorlamak için kodun kalitesini sağlamaya yardımcı olmak için kalite kapıları oluşturabilirsiniz.|-   [İade ilkeleri (Azure depoları TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Test seçeneklerini belirleyin:** örneğin test sonuçlarının nerede depolanacağını belirtebilirsiniz.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API başvuru belgeleri

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> öznitelikler, özel durumlar, bildirimler ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting ad alanını açıklar.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> ASP.NET ve web hizmeti birim testleri için destek sağlayan UnitTesting ad alanını genişleten alanını UnitTesting.Web ad alanını ad alanını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesini geliştirme](../test/improve-code-quality.md)
