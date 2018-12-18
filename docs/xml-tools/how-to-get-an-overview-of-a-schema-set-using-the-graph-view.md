---
title: 'Nasıl yapılır: XML şema graf görünümünü kullanarak şema kümesine genel bakış Tasarımcısı Al'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 004d40992e24f0df651d93b43761add1d2efa673
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381426"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Nasıl yapılır: graf görünümünü kullanarak şema genel bakış

Bu konu nasıl kullanılacağını açıklar [graf görünümünü](../xml-tools/graph-view.md) düğümlerin ve düğümler arasındaki ilişkileri şema kümesi üst düzey bir görünümünü görmek için.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturun ve kök öğe içerik modeli Görünümü'nde görüntülemek için

1.  Yeni bir XML şema dosyası oluşturma ve dosyayı farklı Kaydet *Relationships.xsd*.

2.  Tıklayın **görüntülemek ve temel alınan XML şema dosyasını düzenlemek için XML Düzenleyicisi'ni kullanma** başlangıç görünümünde bağlantı.

3.  XML şema örnek koddan kopyalama [örnek XML şeması: ilişkileri](../xml-tools/sample-xsd-file-relationships.md) ve varsayılan olarak yeni bir XSD dosyasına eklenen kodu değiştirmek için yapıştırın.

4.  XML Düzenleyicisi'nde herhangi bir yere sağ tıklayıp **Görünüm Tasarımcısı**.

5.  Graf görünümünden seçim **XSD araç**.

6.  Seçin **şeması Ayarla** düğümünde **XML Şeması Gezgini** ve düğümü graf görünümünü tasarım yüzeyine sürükleyin. Tüm genel düğümleri ve ilişkileri düğümlerini bağlayan oklar görmeniz gerekir.

     ![Graf Görünümü](../xml-tools/media/relationshipingraphview.gif)

7.  Tasarım yüzeyinde herhangi bir düğümde tıklayın ve şema kümesindeki Seçili düğümün nerede bulunduğunu görmek için içerik haritası çubuğu bakın.

8.  Tasarım yüzeyi ve select herhangi bir öğe düğümü Rick tıklayın **örnek XML oluşturmak** XML örneği görmek için.