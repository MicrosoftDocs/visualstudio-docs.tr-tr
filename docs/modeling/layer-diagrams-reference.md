---
title: Bağımlılık diyagramları başvurusu
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1ef2d68cb0f8e3d6904bdf3f3ebbab321649c3e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920939"
---
# <a name="dependency-diagrams-reference"></a>Bağımlılık diyagramları: başvuru

Visual Studio'da kullanabileceğiniz bir *bağımlılık diyagramı* sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için. Bir bağımlılık diyagramı fiziksel yapıları sisteminizde adı verilen mantıklı, soyut gruplar halinde düzenler *katmanları*. Bu katmanlar, yapıların gerçekleştirdiği temel görevleri veya sistemin ana bileşenlerini açıklar. Her katman aynı zamanda daha ayrıntılı görevleri açıklayan iç içe katmanlar içerebilir.

Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bağımlılık diyagramları Visual Studio 2017'de .NET Core projeleri için desteklenmiyor.

Katmanlar arasındaki hedeflenen veya varolan bağımlılıkları belirtebilirsiniz. Oklar olarak temsil edilen Bu bağımlılıklar, hangi katmanların kullanın veya diğer Katmanlar tarafından temsil edilen işlevi kullanmakta gösterir. Sisteminiz farklı rolleri ve işlevleri açıklayan katmanlara düzenleyerek, bir bağımlılık diyagramı anlamak, yeniden kullanmak ve kodunuzu bakımını kolaylaştırmak yardımcı olabilir.

Aşağıdaki görevleri gerçekleştirmenize yardımcı olması için bir bağımlılık diyagramı kullanın:

-   Sisteminizde varolan veya hedeflenen mantıksal mimarisi iletişim kurar.

-   Mevcut kodunuzu ve hedeflenen mimariyi arasında çakışmalar keşfedin.

-   Yeniden düzenleyin, güncelleştirin veya sisteminizin evrim Geçiren hedeflenen mimari üzerindeki değişikliklerin etkisini görselleştirin.

-   İadeniz doğrulama dahil ederek geliştirme ve kodunuzun bakım sırasında hedeflenen mimariyi güçlendirmek ve yapı işlemleri.

Bu konuda, bir bağımlılık diyagram üzerinde kullanabileceğiniz öğeleri açıklar. Oluşturma ve bağımlılık diyagramları çizmek için bkz hakkında daha ayrıntılı bilgi için [bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md). Katman desenleri hakkında daha fazla bilgi için ziyaret [desenler ve uygulamalar site](http://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-dependency-diagrams"></a>Bağımlılık diyagramları okuma

![Bağımlılık diyagramları üzerinde öğeler](../modeling/media/uml_layerrefreading.png)

Aşağıdaki tabloda, bir bağımlılık diyagram üzerinde kullanabileceğiniz öğeleri açıklar.

|**Şekil**|**Öğe**|**Açıklama**|
|-|-|-|
|1.|**Katman**|Sisteminizdeki fiziksel yapıları mantıksal grubudur. Bu yapılar ad alanları, projeler, sınıflar, yöntemler vb. olabilir.<br /><br /> Bir katmana bağlı yapıların listesini görmek için katmanın kısayol menüsünü açın ve ardından **bağlantıları görüntüle** açmak için **Katman Gezgini**.<br /><br /> Daha fazla bilgi için [Katman Gezgini](#Explorer).<br /><br /> -   **Namespace bağımlılıkları Yasak** -Bu katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtir.<br />-   **Ad Yasak** -Bu katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtir.<br />-   **Gerekli ad alanları** -Bu katman ile ilişkili yapıların belirli ad alanlarına birine ait olduğunu belirtir.|
|2|**Bağımlılık**|Bir katmanın işlevselliği kullanabileceğini belirtir başka bir katmanda ancak tersi doğru değildir.<br /><br /> -   **Yön** -Bağımlılık yönünü belirtir.|
|3|**Çift yönlü bağımlılık**|Bir katmanın işlevselliği kullanabileceğini belirtir başka bir katmanda ve bunun tersi de geçerlidir.<br /><br /> -   **Yön** -Bağımlılık yönünü belirtir.|
|4|**Yorum**|Genel Notlar ve diyagramı diyagram üzerindeki öğeleri eklemek için bu seçeneği kullanın.|
|5|**Açıklama bağlantısı**|Açıklamalar diyagram üzerindeki öğeleri bağlamak için bu seçeneği kullanın.|

## <a name="Explorer"></a> Katman Gezgini

Her katman, çözümünüzdeki projeler, sınıflar, ad alanları, proje dosyaları ve diğer bölümlerini yazılım gibi yapıtları bağlayabilirsiniz. Bir katmandaki sayı katmana bağlı olan yapıların sayısını gösterir. Ancak, bir katmandaki yapı sayısını okurken aşağıdakileri unutmayın:

-   Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

-   Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

Katmanlar ve yapılar bağlama hakkında daha fazla bilgi için bkz:

-   [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)

-   [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Bağlı yapıtlar inceleyin

Bağımlılık diyagramında bir veya daha fazla katmanı için kısayol menüsünü açın ve ardından **bağlantıları görüntüle**.

**Katman Gezgini** açılır ve Seçili katmanlara bağlanmış yapılar gösterir. **Katman Gezgini** her yapı bağlantılarını özelliklerini gösteren bir sütun vardır.

> [!NOTE]
> Bu özelliklerin tümünü göremiyorsanız genişletin **Katman Gezgini** penceresi.

|**Katman Gezgini'nde sütun**|**Açıklama**|
|-|-|
|**Kategorileri**|Sınıfı, ad alanı, kaynak dosyasını ve benzeri gibi bir yapı türü|
|**Katman**|Yapıya katmanı|
|**Doğrulamayı destekler**|Varsa **True**, sonra da katman doğrulama işlemine proje ya da bu öğeden bağımlılıklara uygun olduğunu doğrulayabilirsiniz.<br /><br /> Varsa **False**, sonra bağlantının katman doğrulama işleminde yer almaz.<br /><br /> Daha fazla bilgi için [bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md).|
|**tanımlayıcı**|Bağlantılı yapıt başvurusu|

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
