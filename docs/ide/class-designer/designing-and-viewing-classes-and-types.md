---
title: Sınıf Tasarımcısı'nı kullanın
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4e4cf8e21f3f053783b1f7b70dcc51f2fd4ef2a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447966"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Tasarım ve görünüm sınıfları ve Sınıf Tasarımcısı ile türleri

Tasarım, görselleştirin ve sınıfları ve diğer türleri ile kodunuzda yeniden düzenlemeniz **Sınıf Tasarımcısı** Visual Studio. Sınıf diyagramları oluşturmak ve C#, Visual Basic veya C++ projesi sınıflarda düzenlemek için kullanın. Sınıf diyagramları, proje yapınızı daha iyi anlamak veya kodunuzu yeniden düzenlemek için de kullanabilirsiniz.

## <a name="what-you-can-do-with-class-diagrams"></a>Sınıf diyagramları ile yapabilecekleriniz

- **Tasarım**: sınıf diyagramı düzenleyerek projenizin kodu. Yeni öğeler eklemek ve istenmeyen öğeleri silebilir. Değişikliklerinizi kodda yansıtılır.

- **Görselleştirme**: projenizdeki diyagramında sınıfları görüntüleyerek projenizin yapısı anlamak. En önemli proje ayrıntıları odaklanabiliriz, diyagram özelleştirin. Tanıtım veya belge için daha sonra kullanmak üzere, diyagram kaydedin.

- **Yeniden Düzenle**: geçersiz kılma yöntemleri, tanımlayıcıları yeniden adlandırın, parametreleri yeniden düzenlemeniz ve arabirimleri ve soyut sınıflar uygular.

## <a name="view-types-and-relationships"></a>Türleri ve ilişkileri görüntüleme

Sınıf diyagramları türleri, örneğin, bağlı üyeleri ve aralarındaki ilişkilerin ayrıntılarını gösterin. Bu varlıklar görselleştirme dinamik koda görülmektedir. Bu tasarımcıda türlerini düzenlemek ve varlığın kaynak kodunda yansıtılan düzenlemeleriniz bkz anlamına gelir. Benzer şekilde, sınıf diyagramı kod dosyalarında yapılan değişiklikler ile senkronize tutulur.

> [!NOTE]
> Proje türü için yapı kadar sınıf diyagramı sınıf diyagramında projeniz varsa ve başka bir projesinde bulunan bir tür projeniz başvuruyor. Başvurulan tür göstermez. Benzer şekilde, bu varlık için projeyi yeniden kadar diyagram değişiklikleri Dış varlık kodu görüntülemez.

## <a name="class-diagram-workflow"></a>Sınıf diyagramı iş akışı

Sınıf diyagramları projelerin sınıf yapısı anlamanıza yardımcı olabilir. Bu projeler diğer geliştiriciler tarafından oluşturulmuş olabilir veya kendi başınıza oluşturduğunuz bir proje üzerinde Yenileyici yeterlidir. Sınıf diyagramları, özelleştirme, paylaşma ve başkalarıyla proje bilgileri sunmak için kullanabilirsiniz.

Proje bilgileri sunan ilk adımı göstermek istediğiniz görüntüleyen bir sınıf diyagramı oluşturmaktır. Daha fazla bilgi için bkz: [sınıf diyagramı eklemek](how-to-add-class-diagrams-to-projects.md). Birden çok sınıf diyagramları projesi, seçilen alt projenin türlerinin ya da seçilen üyelerin bir alt kümesini türlerinin farklı bir görünümünü görüntülemek için kullanılan bir proje oluşturabilirsiniz.

Ne her sınıf diyagramı gösterir tanımlamanın yanı sıra, bilgiler sunulur şeklini de değiştirebilirsiniz; Daha fazla bilgi için bkz: [nasıl yapılır: sınıf diyagramlarını özelleştirme](how-to-customize-class-diagrams.md).

Bir veya daha fazla sınıf diyagramları ince ayar sonra Microsoft Office belgelerine kopyalamak ve yazdırmak veya görüntü dosyaları olarak verme. Daha fazla bilgi için bkz: [nasıl yapılır: bir Microsoft Office belgesine sınıf diyagramı öğeleri kopyalama](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [nasıl yapılır: sınıf diyagramlarını yazdırma](how-to-print-class-diagrams.md) ve [nasıl yapılır: sınıf diyagramlarını görüntüdışarıaktarma](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Sınıf Tasarımcısı, kaynak dosyalarının konumunu böylece proje yapınızı değiştirme izlemez veya projedeki kaynak dosyalarını taşıma sınıfı Designer'ın türü, özellikle kaynak türü bir typedef, temel sınıfların veya ilişki türleri kaybetmesine neden olabilir. Gibi bir hata alabilirsiniz **Sınıf Tasarımcısı bu tür görüntüleyemiyor**. Bunu yaparsanız, yeniden yeniden görüntülemek için sınıf diyagramı konumlandırılan veya değiştirilen kaynak kodunu sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../writing-code-in-the-code-and-text-editor.md)
- [Çözümlerinizdeki bağımlılıkları eşleme](../../modeling/map-dependencies-across-your-solutions.md)