---
title: Dışarı aktarma ve kod haritalarını kaydedin
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267741"
---
# <a name="share-code-maps"></a>Kod haritaları paylaşma

Kod Haritaları, Visual Studio projesinin bir parçası olarak, görüntü veya XPS dosyası olarak kaydedebilirsiniz.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Kod Haritası diğer Visual Studio kullanıcılarla paylaşma

Kullanım **dosya** harita kaydetmek için menüsünden.

-veya-

Harita belirli projesinin bir parçası harita kaydetmek için araç çubuğunda, seçin **paylaşımı** > **taşıma \<CodeMapName > .dgml içine**ve ardından, kaydetmek istediğiniz proje seçin eşleyin.

![Başka bir projeye bir harita taşıma](../modeling/media/codemapsmovemapmenu.png)

Visual Studio kaydeder eşlemesi olarak bir *.dgml* Visual Studio Enterprise ve Visual Studio Professional diğer kullanıcılarla paylaşmak dosya.

> [!NOTE]
> Visual Studio Professional kullananlar ile bir eşleme paylaşmadan önce tüm gruplar'ı genişletin, gizli düğümleri gösterin ve gruplar arası bağlantılar ve başkalarının harita üzerinde görmesini istediğiniz silinen tüm düğümleri almak emin olun. Aksi takdirde, diğer kullanıcıların bu öğeleri görmesi mümkün olmayacaktır.
>
> Modelleme projesinde veya bir modelleme projesinden başka bir konuma kopyalanan bir harita kaydettiğinizde, aşağıdaki hata oluşabilir:
>
> "Kaydedilemiyor *fileName* proje dizininin dışında. Bağlantılı öğeler desteklenmez."
>
> Visual Studio hatayı gösterir, ancak kaydedilen sürümü de oluşturur. Hatayı önlemek için modelleme projesi dışında eşlemesi oluşturun. Ardından istediğiniz konuma kaydedebilirsiniz. Yalnızca çözümdeki başka bir konuma dosya kopyalama ve onu kaydetmeye çalışmak başarısızlıkla sonuçlanacaktır.

## <a name="export-a-code-map-as-an-image"></a>Kod Haritası bir görüntü olarak dışarı aktarma

Kod Haritası bir görüntü olarak dışa aktardığınızda, Microsoft Word veya PowerPoint gibi diğer uygulamalara kopyalayabilirsiniz.

1. Kod Haritası araç çubuğunda seçin **paylaşımı** > **e-posta görüntüsü olarak** veya **görüntüsünü kopyalama**.

2. Görüntüyü başka bir uygulamaya yapıştırın.

## <a name="export-the-map-as-an-xps-file"></a>Harita XPS dosyası olarak dışarı aktarma

Kod Haritası XPS dosyası olarak dışa aktardığınızda, Internet Explorer gibi XML ya da XAML görüntüleyiciler görebilirsiniz.

1. Kod Haritası araç çubuğunda seçin **paylaşımı** > **e-posta olarak taşınabilir XPS** veya **taşınabilir XPS olarak Kaydet**.

2. Dosyayı kaydetmek istediğiniz yere göz atın.

3. Kod Haritası olarak adlandırın. Olduğundan emin olun **farklı türde Kaydet** kutusunu ayarlanmış **XPS dosyaları (\*.xps)**. Seçin **kaydetmek**.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod haritaları ile bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)