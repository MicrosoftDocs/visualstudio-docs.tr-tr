---
title: XML şema kümesi arama sonucu düğümlerini çalışma alanına ekleme
description: Çalışma alanında bir anahtar sözcük aramasının sonucu olarak XML şema Gezgini 'nde vurgulanan düğümleri nasıl ekleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e306ec76b6089d822dfdcd154ff1947aef1c9cac
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049184"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Nasıl yapılır: şema kümesi arama sonucu düğümlerini çalışma alanına ekleme

Bu konu, çalışma alanında bir anahtar sözcük aramasının sonucu olarak **XML şema Gezgini** 'nde vurgulanan düğümlerin nasıl ekleneceğini açıklar.

> [!NOTE]
> [Çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)yalnızca genel düğümler eklenebilir.

Bu örnek, örnek [satın alma siparişi şemasını](../xml-tools/sample-xsd-file-purchase-order-schema.md)kullanır.

## <a name="to-add-schema-set-result-nodes"></a>Şema kümesi sonuç düğümleri eklemek için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. [XML Explorer](../xml-tools/xml-schema-explorer.md) araç çubuğunun arama metin kutusuna "PurchaseOrder" yazın ve arama düğmesine tıklayın.

     ![XML şema Gezgini anahtar sözcük arama](../xml-tools/media/schemaexplorersearch.gif)

     Arama sonuçları, **XML şema Gezgini** 'nde vurgulanır ve dikey kaydırma çubuğundaki Tick 'ler tarafından işaretlenir.

3. Özet sonuçlar bölmesinde, **çalışma alanına vurgulanan düğümleri Ekle** düğmesine tıklayarak arama sonuçlarını çalışma alanına ekleyin.

     ![XML şema Gezgini arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`Düğüm ve düğüm, `PurchaseOrderType` [Grafik görünümünün](../xml-tools/graph-view.md)tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan ( `purchaseOrder` öğe `PurchaseOrderType` türünde olduğundan) aralarında bir ok çizilir.
