---
title: Etki Alanına Özgü Dil Araçlarına Genel Bakış
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 538ebb2121c488fa56f693a424f91b8af19a0c3e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966849"
---
# <a name="overview-of-domain-specific-language-tools"></a>Etki Alanına Özgü Dil Araçlarına Genel Bakış
Visual Studio'da barındırılan, etki alanına özgü dil Araçları (DSL araçları), bir etki alanına özgü dil tasarlayın ve kullanıcıların diline dayalı modeller oluşturmak için gereken her şeyi oluşturmak olanak tanır.

 Aşağıdaki araçlar, DSL araçları dahil edilmiştir:

-   Alana özgü dilinizi geliştirmeye başlamanıza yardımcı olmak için farklı çözüm şablonları kullanan bir Proje Sihirbazı.

-   Oluşturma ve düzenleme, etki alanına özgü dil tanımı için bir grafik Tasarımcı.

-   Etki alanına özgü dil tanımı iyi biçimlendirilmemiş ve ilgili sorun varsa, hataları ve uyarıları görüntüler xenapp'i doğrulama motoru.

-   Etki alanına özgü dil tanımıma girdi olarak alır ve çıktı olarak kaynak kodu üretir bir kod Oluşturucu.

## <a name="the-dsl-tools-solution"></a>DSL araçları çözümü
 Etki alanına özgü Tasarımcısı Sihirbazı'nı aşağıdaki çözüm şablonlarını sunar:

- Görev akışı

- Sınıf diyagramları

- Minimal dil

- Bileşen modelleri

- En az bir WPF

- En az Windows.Forms

- DSL kitaplığı

  Daha fazla bilgi için [bir etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Sihirbaz aşağıdaki projeleri içeren bir Visual Studio çözümü oluşturur:

- DSL

   Dsl projesi, etki alanına özgü dil ve işlemek ve düzenleme araçları tanımlar.

- **DslPackage**

   Dil araçları Visual Studio ile tümleştirmek DslPackage proje belirler.

## <a name="the-dsl-tools-graphical-interface"></a>DSL araçları grafik arabirimi
 DSL araçları grafik arabirim öğeleri ve ilişkileri için etki alanına özgü dil eklemek için kullanabilirsiniz. Öğeleri ekledikten sonra bunları şekillere eşleme renkleri özelleştirme ve dekoratörler ekleme görünümleri tanımlayabilirsiniz. Araç kutusu öğeleri de ekleyebilirsiniz.

## <a name="validation-in-dsl-tools"></a>DSL araçları doğrulama
 DSL bir etki alanı modeli, kod oluşturma için temel gereksinimleri karşıladığından emin olmak için doğrulama düzeyini sağlar. Genellikle, kendi etki alanına özgü dil oluşturduğunuzda, iş mantığı kurallarınızı ifade etmek için kendi doğrulama ekleyin. Özel doğrulama hakkında daha fazla bilgi için bkz: [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 Bunu tasarlarken, etki alanına özgü dil genellikle doğrulamak önerilir. Alana özgü dilinizi doğrulama hatası varsa, kaynak kod üretilemiyor. Şablonlar'dan kaynak kodu oluşturma işleminin tıklayarak gerçekleştirilir **tüm Şablonları Dönüştür** Çözüm Gezgini araç çubuğundaki. Dil tanımı değişiklik olduğunda da emin olun **tüm Şablonları Dönüştür**. Daha fazla bilgi için [nasıl yapılır: bir etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>DSL araçları özelleştirme
 Ek kod modeli davranışlarını iyileştirmek ve dilinizi kısıtlamaları tanımlamak için sağlayabilir. Zorunlu kılınırsa, metin şablonlarını değiştirerek önemli değişiklik yapabilirsiniz.

## <a name="distributing-your-dsl-solution"></a>DSL çözümünüzü dağıtma
 DSL araçları, Visual Studio'da barındırılan bir paket oluşturur. Paket bir araç kutusu, bir DSL Gezgini ve modelleri, alana özgü dil kullanarak kullanıcıların diğer kullanıcı Arabirimi öğeleri görüntüler.

 Yapı ve Visual Studio DSL araçları çözümü çalıştırın, Visual Studio'nun ikinci bir örneğini, etki alanına özgü dil dilinin kullanıcıya nasıl görüneceğini gösterir. Her şeyin düzgün çalıştığını doğruladıktan sonra dağıtabilirsiniz `.vsix` dosyası DslPackage projesinin yapı klasöründe bulabilirsiniz. Bu dosya, diğer bilgisayarlarda Visual Studio uzantısı DSL yüklemek için kullanılabilir.  Daha fazla bilgi için [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Deneysel Örnek](../extensibility/the-experimental-instance.md)
- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)