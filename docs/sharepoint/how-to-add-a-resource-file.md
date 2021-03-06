---
title: 'Nasıl yapılır: kaynak dosyası ekleme | Microsoft Docs'
description: Çözüm düğümünün kısayol menüsündeki komutları ve Çözüm Gezgini içindeki Özellik düğümlerini kullanarak Visual Studio 'da bir kaynak dosyası ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22b5638f7251b34c74da348e55e755cd27132aff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934851"
---
# <a name="how-to-add-a-resource-file"></a>Nasıl yapılır: kaynak dosyası ekleme
  Kaynak dosyalarını ekleme komutları, Çözüm Gezgini çözüm düğümünün kısayol menüsünde ve özellik düğümlerinin ' de yer alır. Daha fazla bilgi için bkz. [SharePoint çözümlerini yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Bir SharePoint çözümüne genel kaynak dosyası eklemek için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir SharePoint çözümünü açın.

2. **Çözüm Gezgini**, bir SharePoint proje düğümü seçin ve ardından menü çubuğunda **Proje**  >  **Ekle yeni öğe**' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusunda **Genel kaynaklar dosya** şablonunu seçin ve sonra **Ekle** düğmesini seçin.

   > [!NOTE]
   > Genel kaynak dosyası proje öğesi şablonu yalnızca bir SharePoint proje öğesi seçildiğinde görüntülenir.

4. **Kaynak Ekle** iletişim kutusunda, kaynak dosyası için ingilizce (Birleşik Devletler) gibi bir kültür seçin.

    Bu adım, çözümünüze Resource_x_ bir genel kaynak dosyası ekler **.** <em>kültür</em><strong>.</strong> resx, örneğin, *Resource1. en-US. resx*.

5. **Kaynak Düzenleyicisi** içinde açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynakları kaynak dosyasına ekleyin.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Bir SharePoint özelliğine Özellik kaynak dosyası eklemek için

1. SharePoint çözümü içinde zaten açık değilse [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , çözümü açın.

2. **Çözüm Gezgini**' de, **Özellikler** düğümü altında bir özelliğin adı için kısayol menüsünü açın ve ardından **Özellik kaynağı Ekle**' yi seçin.

     Bu adım, _resourceFileName_ biçimindeki özelliğe bir kaynak dosyası ekler **.** _kültür_**. resx**, örneğin, *özellik1. en-US. resx*.

3. **Kaynak Düzenleyicisi** içinde açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynakları kaynak dosyasına ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
