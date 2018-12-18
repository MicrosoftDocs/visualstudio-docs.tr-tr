---
title: 'Nasıl yapılır: kaynak dosyası ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0091054c0c0d2cfb7f19f2ca46839cfdcf47832b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861195"
---
# <a name="how-to-add-a-resource-file"></a>Nasıl yapılır: kaynak dosyası ekleme
  Komutlar kaynak dosyaları eklemek için çözüm düğüm ve Çözüm Gezgini'nde özellik düğümlerin kısayol menüsünü açıktır. Daha fazla bilgi için [yerelleştirme SharePoint çözümleri](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint çözüm genel kaynak dosyası eklemek için  
  
1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], bir SharePoint çözümünü açın.  
  
2. İçinde **Çözüm Gezgini**, bir SharePoint proje düğümünü seçin ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
3. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Genel kaynaklar dosyası** şablonu seçip **Ekle** düğmesi.  
  
   > [!NOTE]  
   >  Genel kaynaklar dosyası proje öğesi şablonu, yalnızca bir SharePoint proje öğesi seçildiğinde görünür.  
  
4. İçinde **kaynak Ekle** iletişim kutusunda, bir kültür için İngilizce (Amerika Birleşik Devletleri) gibi bir kaynak dosyası seçin.  
  
    Bu adım, çözümünüze Resource_x_ biçimde genel kaynak dosyası ekler.**.** <em>kültür</em><strong>.</strong> resx, gibi *Resource1.en-US.resx*.  
  
5. Zaman **Kaynak Düzenleyicisi** açılır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kaynakları kaynak dosyasına ekleyin.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Bir SharePoint özelliği için özellik kaynak dosyası eklemek için  
  
1.  SharePoint çözümü zaten açık değilse, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], çözümü açın.  
  
2.  İçinde **Çözüm Gezgini**, altında bir özelliği adı için kısayol menüsünü açın **özellikleri** düğümünü seçip **özellik kaynağı Ekle**.  
  
     Bu adım, özellikle biçiminde bir kaynak dosyası ekler. _ResourceFileName_**.** _kültür_**.resx**, gibi *Feature1.en-US.resx*.  
  
3.  Zaman **Kaynak Düzenleyicisi** açılır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kaynakları kaynak dosyasına ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
 
