---
title: XML şema Tasarımcısı'nda içerik modeli görünümünü kullanarak düğümlerinin içerik modeli inceleyin
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 650478a92ea2dabc9aeef239a68bdff428429cd7
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548602"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Nasıl yapılır: içerik modeli içerik modeli görünümü kullanarak düğümler, İnceleme

Bu konu, kullanarak düğümleriniz keşfetmek açıklar [içerik modeli görünümü](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturun ve içerik modeli görünümünde kök öğe görüntülemek için

1.  Yeni bir XML Şeması dosyası oluşturun.

2.  Tıklatın **görüntülemek ve temel alınan XML şema dosyasını düzenlemek için XML Düzenleyicisi'ni kullanma** Başlat görünüm.

3.  XML Şeması örnek kodunu kopyalama [örnek XML şeması: Satınalma siparişi şeması](../xml-tools/sample-xsd-file-purchase-order-schema.md) ve yeni XSD dosyası varsayılan olarak eklenen kodu değiştirmek için yapıştırın.

4.  Seçin `purchaseOrder` sağ tıklanarak şema Gezgini'nde öğe `purchaseOrder` öğesi XML Düzenleyicisi'ni seçerek **Göster XML Explorer'da**.

5.  Sağ `purchaseOrder` XML Explorer seçip **Göster içerik modeli görünümünde**.

     İçerik modeli görünümü görüntüler `purchaseOrder` tasarım yüzeyinde öğesi.

6.  Genişletme `shipTo`, `billTo`, ve `items` düğümleri her düğümün çift veya her düğüm sağındaki oku çift tıklatarak.

     Düğümleri `purchaseOrder` öğesi artık genişletilmiş ve öğenin içerik modeli görebilirsiniz.

7.  ' Yi tıklatın altında herhangi bir düğümde `purchaseOrder` öğesi ve Seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğunu bakın.

8.  Tıklatın **Göster belgelerine** belgelerine geçiş yapmak için XSD araç çubuğu düğmesi. Ayrıca, belge geçiş yapmak için tasarım yüzeyi sağ.

9. Rick tıklatma `purchaseOrder` düğümü ve select **örnek XML oluşturmak** XML örneği belgeyi görmek için.