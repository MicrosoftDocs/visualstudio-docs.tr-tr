---
title: Kod eşlemelerini dışarı ve Kaydet
description: Kod eşlemelerini bir Visual Studio projesinin parçası olarak, görüntü olarak veya XPS dosyası olarak nasıl kaydedebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9898b720e51c2750b67054d1f095200372f426da
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363776"
---
# <a name="share-code-maps"></a>Kod haritalarını paylaşma

Kod haritalarını bir Visual Studio projesinin parçası olarak, görüntü olarak veya XPS dosyası olarak kaydedebilirsiniz.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Bir kod haritasını diğer Visual Studio kullanıcılarıyla paylaşma

Haritayı kaydetmek için **Dosya** menüsünü kullanın.

-veya-

Haritayı belirli projenin bir parçası olarak kaydetmek için harita araç çubuğunda,   >  **Move \<CodeMapName> . dgml**' i içine Share ' ı seçin ve ardından Haritayı kaydetmek istediğiniz projeyi seçin.

![Haritayı başka bir projeye taşıma](../modeling/media/codemapsmovemapmenu.png)

Visual Studio, Haritayı Visual Studio Enterprise ve Visual Studio Professional diğer kullanıcılarıyla paylaşabileceğiniz bir *. dgml* dosyası olarak kaydeder.

> [!NOTE]
> Visual Studio Professional kullananlarla bir Haritayı paylaşmadan önce, herhangi bir grubu genişlettikten, gizli düğümleri ve çapraz grup bağlantılarını gösterdiğinizden ve başkalarının haritada görmesini istediğiniz silinmiş düğümleri aldığınızdan emin olun. Aksi takdirde, diğer kullanıcıların bu öğeleri görmesi mümkün olmayacaktır.
>
> Modelleme projesinde olan veya bir modelleme projesinden başka bir konuma kopyalanmış olan bir Haritayı kaydettiğinizde aşağıdaki hata ortaya çıkabilir:
>
> " *Dosya adı* proje dizininin dışına kaydedilemez. Bağlantılı öğeler desteklenmez."
>
> Visual Studio hatayı gösterir, ancak kaydedilen sürümü de oluşturur. Hatayı önlemek için Haritayı modelleme projesinin dışında oluşturun. Ardından istediğiniz konuma kaydedebilirsiniz. Yalnızca çözümdeki başka bir konuma dosya kopyalama ve onu kaydetmeye çalışmak başarısızlıkla sonuçlanacaktır.

## <a name="export-a-code-map-as-an-image"></a>Kod haritasını görüntü olarak dışarı aktarma

Bir kod haritasını görüntü olarak dışarı aktardığınızda, Microsoft Word veya PowerPoint gibi diğer uygulamalara kopyalayabilirsiniz.

1. Kod Haritası araç çubuğunda,   >  **e-postayı görüntü olarak** paylaşma veya **görüntü kopyalama**' yı seçin.

2. Görüntüyü başka bir uygulamaya yapıştırın.

## <a name="export-the-map-as-an-xps-file"></a>Haritayı XPS dosyası olarak dışarı aktarma

Bir kod haritasını XPS dosyası olarak dışa aktardığınızda, bu dosyayı Internet Explorer gibi XML veya XAML görüntüleyicilerinde görebilirsiniz.

1. Kod Haritası araç çubuğunda,   >  **e-postayı taşınabilir XPS olarak** paylaşma veya **Taşınabilir XPS olarak kaydet**' i seçin.

2. Dosyayı kaydetmek istediğiniz yere gidin.

3. Kod eşlemesini adlandırın. **Farklı kaydet türü** kutusunun **XPS dosyaları ( \* . XPS)** olarak ayarlandığından emin olun. **Kaydet**'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılıkları kod eşlemeleriyle eşleyin](../modeling/map-dependencies-across-your-solutions.md)
