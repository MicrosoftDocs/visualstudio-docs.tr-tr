---
title: "Nasıl yapılır: XML şema Gezgini'nden çalışma alanına düğümleri eklemek"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752059"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Nasıl yapılır: XML şema Gezgini'nden çalışma alanına düğümleri eklemek

Bu konuda düğüm ekleme açıklanmaktadır [XML şema Tasarımcısı çalışma](../xml-tools/xml-schema-designer-workspace.md) gelen **XML Şeması Explorer**. Bu düğümlerden bırakarak sağlanabilir **XML Şeması Explorer** kullanarak veya bir XSD Tasarımcısı görünümü üzerine **XML Şeması Explorer'ın** bağlam menüsü. Tarafından gerçekleştirilen bir arama sonucunda vurgulanmış düğümleri de ekleyebilirsiniz **XML Şeması Explorer**. Daha fazla bilgi için bkz: [nasıl yapılır: çalışma alanı'na şema kümesi arama sonucu düğümleri eklemek](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Yalnızca genel düğümler eklenebilir [XML şema Tasarımcısı çalışma](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML Explorer bağlam menüsü aracılığıyla düğümleri eklemek için

1.  Adımları [nasıl yapılır: oluşturma ve bir XSD şema dosyası düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Sağ tıklayın `PurchaseOrderType` XSD Gezgininde düğümü. Seçin **Göster Grafik görünümünde**.

     `purchaseOrderType` Düğümü grafik görünümü tasarım yüzeyine görüntülenir.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Bir düğüm bir görünümü açın, sürüklenip

1.  Sağ `PurchaseOrderType` grafik görünümü düğümünde. Seçin **Göster XML Şeması Explorer'da**.

     Düğüm vurgulanan **XML Şeması Explorer**.

2.  Sağ tıklayın `PurchaseOrderType` düğümünde **XML Şeması Explorer** seçip **Göster tüm başvuruları**.

     `purchaseOrder` Düğüm vurgulanacak.

3.  Sürükleme `purchaseOrder` düğümü grafik görünümü açın.

     `purchaseOrder` Düğümü ve `PurchaseOrderType` düğümü birbirinin yanına grafik görünümü tasarım yüzeyine görünür. İki düğüm birbiriyle ilişkili olmadığından ( `purchaseOrder` öğesidir `PurchaseOrderType` türü), bir ok aralarında çizilir.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Şema Explorer arama özelliği kullanarak düğümleri eklemek için

1.  "PurchaseOrder" yazın arama metin kutusuna [XML Explorer](../xml-tools/xml-schema-explorer.md) araç çubuğu ve arama düğmesini tıklatın.

     ![XML şema Explorer anahtar sözcük araması](../xml-tools/media/schemaexplorersearch.gif)

     İçinde arama sonuçlarında vurgulanır **XML Şeması Explorer** ve çizgilerine dikey kaydırma çubuğunda olarak işaretlenmiş.

2.  Arama sonuçlarını çalışma alanı'na tıklayarak ekleyin **çalışma alanına vurgulanan düğümleri eklemek** Özet Sonuçlar bölmesindeki düğmesi.

     ![XML şema Explorer arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Düğümü ve `PurchaseOrderType` düğümünün görünen diğer yanındaki tasarım yüzeyine [grafik görünümü](../xml-tools/graph-view.md). İki düğüm birbiriyle ilişkili olmadığından ( `purchaseOrder` öğesidir `PurchaseOrderType` türü), bir ok aralarında çizilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)