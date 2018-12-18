---
title: XML Şema Gezgini
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 110cad9883cbb129368dac4d481443a9f5d9813c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751595"
---
# <a name="xml-schema-explorer"></a>XML Şema Gezgini

**XML Şeması Explorer** XML Şeması Tanım Dili (XSD) şemalarda çalışmanıza olanak sağlamak için Microsoft Visual Studio ve XML Düzenleyicisi ile tümleşiktir. Bir XML Şeması dosyayı açtığınızda **şema ayarlamak** düğümü görünür **XML Şeması Explorer**. Tüm dahil, içe aktarılan ya da yeniden tanımlanan şemaları aracılığıyla başvurulan herhangi bir dosya yanı sıra, hedef dosya için bir `include` veya `import` deyimi, da görünür **XML Şeması Explorer**.

 **XML Şeması Explorer** aşağıdakileri sağlar:

-   Şema kümesini hızlı bir genel bakış alın.

-   Gözat ve ağaç gidin.

-   Anahtar sözcüğü ve şema özgü aramaları gerçekleştirin. Daha fazla bilgi için bkz: [şema kümesini arama](../xml-tools/searching-the-schema-set.md).

-   Arama sonuçlarını grafik görünümü veya içerik modeli görünümü ekleme

-   Belge sipariş, türü veya ad ağacında sıralayın. Daha fazla bilgi için bkz: [sıralama, filtreleme ve gruplandırma](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

-   XML Düzenleyicisi'ni açın ve XSD dosyası kodu konumlarda atlanacak. Daha fazla bilgi için bkz: [tümleştirme XML Düzenleyicisi ile](../xml-tools/integration-with-xml-editor.md).

-   Genel öğeler için XML örneği oluşturur.

**XML Şeması Explorer** ağaç görünümü ayarlamak şema hiyerarşik bir görünümünü sağlar. **XML Şeması Explorer** arama, filtreleme, gezinti ve sıralama de sağlar. Erişim için **XML Şeması Explorer**, aşağıdakilerden birini yapın:

-   Kullanıyorsanız [Başlangıç'ı](../xml-tools/start-view.md), tıklatın **XML Şeması Explorer** bağlantı.

-   Kullanıyorsanız [grafik görünümü](../xml-tools/graph-view.md) veya [içerik modeli görünümü](../xml-tools/content-model-view.md) ve çalışma alanınızda düğümünüz, seçmek için bağlam menüsü kullanma **XML Şeması Explorer**.

-   Öğesini de seçebilirsiniz **XML Şeması Explorer** gelen **Görünüm** menüsü.

-   Erişebileceğiniz **XML Şeması Explorer** gelen bir *.vb* ile ilişkili bir Visual Basic XML değişmez değeri olan dosyayı bir *.xsd* dosya. Şema görmek için kümesinde **XML Şeması Explorer**, bir XML değişmez değeri veya bir XML ad alanı içe aktardığınız XML düğümünü sağ tıklatın ve seçin **Göster şema Explorer'da** komutu. Daha fazla bilgi için bkz: [XML Şeması Gezgini ile tümleştirme, XML değişmez değerleri](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Ağaç görünümü
 **XML Şeması Explorer** görüntüler önceden derlenmiş şema bilgileri ağaç yapısında ayarlayın. Ağaç yapısı şu şekilde düzenlenmiştir:

-   En üst düzeyinde şema düğümü ayarlanır.

-   İkinci düzey ad alanları içerir.

-   Üçüncü düzey dosyaları içerir.

-   Dördüncü düzey genel düğümleri içerir. Bu içerebilir öğeleri, gruplar, karmaşık türler, basit türler, öznitelikler, öznitelik grupları ve `include`, `import`, ve `redefine` deyimleri.

Bir ağaç yapısı örneği verilmiştir:

![XML Şema Gezgini](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Seçim ve etkinleştirme
 Vurgulayın ve bir düğümü seçmek için bir kez şema Explorer'ın tıklatın.

 Bir düğüm etkinleştirmek için çift tıklayın veya basın **Enter** düğümü seçildiğinde.

-   Bir düğüm etkinleştirme dosyayı açar, bu düğüm tanımlanır (dosya zaten açık değilse) ve düğüm dosyasında seçer.

-   Bir dosya düğümü etkinleştirme (zaten açık değilse) seçili dosyayı açar ve vurgular `<schema>` düğümü.

-   Bir SchemaSet veya bir ad alanı düğümü etkinleştirme hiçbir şey yapmaz.

## <a name="drag-and-drop-nodes"></a>Düğüm sürükleme ve bırakma
 Sürükleme ve genel düğümleri, dosya düğümleri ve ad alanı düğümleri bir XSD Tasarımcısı görünümü üzerine bırakın. Geçerli Görünüm ise [Başlangıç'ı](../xml-tools/start-view.md), görünümü açın bir düğüm sürükleme açılır [grafik görünümü](../xml-tools/graph-view.md). Geçerli Görünüm ise [içerik modeli görünümü](../xml-tools/content-model-view.md) veya grafik görünümü, görünümün bir düğüm üzerine bıraktığınızda değiştirmez.

 Görünüm dosyalarda bırakarak ekleyecek genel tüm düğümleri dosyasında [XSD Designer çalışma](../xml-tools/xml-schema-designer-workspace.md). Ad alanları görünümünden bırakmayı tüm genel düğümlerini ad alanında çalışma alanına ekleyecek. Çalışma alanı görünüm arasında paylaşılır.

 Sürükleme ve yerel düğümler veya içeri aktarmalar bırakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: XML şema Gezgini'nden çalışma alanına düğümleri eklemek](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)