---
title: XML Şeması Gezgini | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32116de7bb88fe937980b02e1789830a27ca36b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845881"
---
# <a name="xml-schema-explorer"></a>XML Şema Gezgini
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Şeması Gezgini XML Şeması Tanım Dili (XSD) şemalarla çalışma sağlamak için Microsoft Visual Studio ile XML Düzenleyicisi ile tümleşiktir. Bir XML şeması dosyasını açtığınızda **şeması Ayarla** düğümü içinde XML Şeması Gezgini görüntülenir. Aracılığıyla başvurulan dosyaları yanı sıra, hedef dosya için tüm dahil, içeri aktarılan veya yeniden tanımlanan şema bir `include` veya `import` deyimi, ayrıca XML şema Gezgini'nde görünür.  
  
 XML Şeması Gezgini aşağıdakileri yapmanızı sağlar:  
  
- Şema kümesi hızlı bir bakış edinin.  
  
- Gözat ve ağaç gidin.  
  
- Anahtar sözcüğü ve şema özgü aramaları gerçekleştirin. Daha fazla bilgi için [şema kümesi arama](../xml-tools/searching-the-schema-set.md).  
  
- Arama sonuçlarını grafik görünümü veya içerik Modle görünümü ekleme  
  
- Belge sırada, tür veya ad ağaç sıralayın. Daha fazla bilgi için [sıralama, filtreleme ve gruplandırma](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
- XML Düzenleyicisi'ni açın ve XSD dosyası kod konumlarda atlayın. Daha fazla bilgi için [Tümleştirmesi ile XML Düzenleyicisi](../xml-tools/integration-with-xml-editor.md).  
  
- Genel öğeler için XML örneği oluşturur.  
  
  XML Şeması Gezgini ağaç görünümü ayarlamak şema Cerberus bir görünümünü sağlar. XML Şeması Gezgini ayrıca arama, filtreleme, gezinti ve sıralama sağlar. XML Şeması Gezgini erişmek için aşağıdakilerden birini yapın:  
  
- Kullanıyorsanız [başlangıç görünümündeki](../xml-tools/start-view.md), tıklayın **XML Şeması Gezgini** bağlantı.  
  
- Kullanıyorsanız [graf görünümünü](../xml-tools/graph-view.md) veya [içerik modeli görünümünü](../xml-tools/content-model-view.md) ve çalışma alanınızda düğümünüz, XML şema Gezgini seçmek için bağlam menüsünü kullanın.  
  
- XML şema Explorerfrom belirleyebilirsiniz **görünümü** menüsü.  
  
- Bir Visual Basic .xsd dosyası ile ilişkili XML değişmez değeri olan bir .vb dosyası XML şema Explorerfrom erişebilirsiniz. XML şema Gezgini içinde ayarlamak için bir XML düğümünde bir XML değişmez değer veya bir XML ad alanı alma sağ tıklayın ve seçin şemasını görmek için **şema Gezgini'nde Göster** komutu. Daha fazla bilgi için [tümleştirme, XML değişmez değerleri ile XML Şeması Gezgini](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>Ağaç görünümü  
 XML Şeması Gezgini ağaç yapısında önceden derlenmiş şema kümesi bilgilerini görüntüler. Ağaç yapısı şu şekilde düzenlenmiştir:  
  
- En üst düzeyinde şema düğüm ayarlanır.  
  
- İkinci düzey ad alanlarını içerir.  
  
- Üçüncü düzeyini dosyaları içerir.  
  
- Dördüncü düzey genel düğümleri içerir. Bu içerebilir öğeler, grupları, karmaşık türler, basit türler, öznitelikleri, öznitelik grupları ve `include`, `import`, ve `redefine` deyimleri.  
  
  Bir ağaç yapısı örneği verilmiştir:  
  
  ![XML Şeması Gezgini](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Seçim ve etkinleştirme  
 Vurgulayın ve bir düğümü seçmek için şema Gezgini içinde bir kez tıklayın.  
  
 Bir düğüm etkinleştirmek için çift tıklayın veya basın **Enter** düğümü seçildiğinde.  
  
-   Bir düğüm etkinleştirme bu düğümde tanımlanan (dosya zaten açık değilse) dosya açılır ve dosyayı düğümü seçer.  
  
-   Bir dosya düğümü etkinleştirme (zaten açık değilse), seçili dosyayı açar ve vurgular `<schema>` düğümü.  
  
-   Bir SchemaSet veya bir ad alanı düğümü etkinleştirme hiçbir şey yapmaz.  
  
## <a name="draging-and-dropping-nodes"></a>Draging ve düğümleri bırakılıyor  
 Sürükleyin ve genel düğümler, dosya düğümleri ve ad alanı düğümleri bir XSD Tasarımcısı görünümü üzerine bırakın. Geçerli Görünüm ise [başlangıç görünümündeki](../xml-tools/start-view.md), bir düğüm görünümü açın sürükleyerek açılır [graf görünümünü](../xml-tools/graph-view.md). Geçerli Görünüm ise [içerik modeli görünümünü](../xml-tools/content-model-view.md) veya grafik görünümü, görünümün üzerine bir düğüm düşürdüğünüzde değiştirmez.  
  
 Dosyalar görünümünde bırakarak eklenir genel tüm düğümleri dosyasındaki [XSD Tasarımcısı çalışma](../xml-tools/xml-schema-designer-workspace.md). Ad alanları görünümünden bırakmayı genel tüm düğümleri çalışma alanına ad alanında ekleyeceksiniz. Çalışma alanı, tüm görünümleri arasında paylaşılır.  
  
 Sürükleyin ve yerel düğümleri veya içeri aktarmalar bırakın olamaz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Şema Kümesini Arama](../xml-tools/searching-the-schema-set.md)  
  
-   [Sıralama, Filtreleme ve Gruplandırma](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Bağlam Menüleri](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [XML Değişmez Değerlerinin XML Şeması Gezgini ile Tümleştirilmesi](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: XML Şema Gezgininden Çalışma Alanına Düğüm Ekleme](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)







