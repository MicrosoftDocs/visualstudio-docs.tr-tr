---
title: Kodu görselleştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 49f3c0e9cdd1feee0161c95d30bed03244d14e15
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857633"
---
# <a name="visualize-code"></a>Kodu görselleştirme

Görselleştirme ve modelleme araçlarını Visual Studio'da, mevcut kodu anlamanıza ve uygulamanızı tanımlamanıza yardımcı olması için kullanabilirsiniz. Bu görsel olarak yaptığınız değişiklikler kod ve iş ve bu değişikliklerden kaynaklanan riskleri değerlendirme Yardım nasıl etkileyebilecek öğrenmenize olanak tanır. Örneğin:

- Kodunuzdaki ilişkileri anlamak için bu ilişkileri görsel olarak eşleyin.

- Sisteminizin mimarisini ve kod, tasarım ile tutarlı tutmak için bağımlılık diyagramları oluşturmak ve kodu bu diyagramları karşı doğrulayın.

- Sınıf yapılarını açıklamak için sınıf diyagramları oluşturun.

Bu araçlar, ayrıca daha kolay proje ile ilgili kişilerle iletişim kurmasına yardımcı olur.

Visual Studio'nun hangi sürümlerinin her özelliğini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|||
|-|-|
|**Kod ve ilişkilerini anlayın:**<br /><br /> Belirli kod parçaları arasındaki ilişkileri eşleyin.<br /><br /> Çözümün tamamını kodunuzdaki ilişkileri genel bir bakış görürsünüz.|- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Kod Haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Hata ayıklarken çağrı yığınında yöntemler eşleştirme](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Sınıf yapıları anlayın:**<br /><br /> Koddan sınıf diyagramları oluşturarak bir projedeki sınıf yapısını görselleştirin.|[Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Üst düzey sistem tasarımı tanımlamak ve bu tasarım karşı kodu doğrulayın:**<br /><br /> Bağımlılık diyagramları oluşturarak, üst düzey sistem tasarımı ve hedeflenen bağımlılıklarını açıklar. Kodu bir koddaki bağımlılıkları tasarım ile tutarlı kalmasını sağlamak için bu tasarım karşı doğrulayın.|- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analiz ve Model mimarisi](../modeling/analyze-and-model-your-architecture.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
