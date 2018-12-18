---
title: "Nasıl yapılır: ekleme ve kaldırma özellikler ve öğeler bir pakete paketleme Gezgini'ni kullanarak | Microsoft Docs"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7875401dee07961d63de6c7b71a97e647c21a0b7
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755618"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Nasıl yapılır: ekleme ve özellikler ve öğeler bir pakete paketleme Gezgini'ni kullanarak kaldırma
  SharePoint öğeleri ve özellikleri dağıtacağınız bir paket yapılandırmak için paketleme Gezgini'ni kullanabilirsiniz. .Wsp dosyanızı içinde SharePoint Proje öğeleri ve özellikleri ayarlayabilirsiniz.  
  
 Alternatif olarak, görüntülemek ve etkinleştirme sırasını değiştirmek için özellikleri yeniden sıralamak için paketleme Tasarımcısı'nı kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: ekleyip özellikler ve öğeler bir paket için paket Tasarımcısını kullanarak](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="open-the-packaging-explorer"></a>Paketleme Gezgini'ni açın  
 Visual Studio çözümünüzü en az bir SharePoint Proje varsa paketleme Gezgini'ni açmak için aşağıdaki yordamı kullanabilirsiniz. Alternatif olarak, paketleme Gezgini'ni otomatik olarak bir özellik veya paket tasarımcısını görüntülediğinizde açılır. Tüm özellik ve paket tasarımcıları kapattıktan sonra da paketleme Gezgini'ni kapatır.  
  
#### <a name="to-open-the-packaging-explorer"></a>Paketleme Gezgini'ni açmak için  
  
1.  Menü çubuğunda seçin **Görünüm** > **diğer pencereler** > **paketleme Gezgini'ni**.  
  
     **Paketleme Gezgini'ni** görünür **araç**.  
  
## <a name="adding-a-feature-to-a-package"></a>Bir paket için bir özellik ekleme  
 Paketleme Gezgini'ni kullanarak bir pakete yeni ve mevcut özellikleri ekleyebilirsiniz.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Bir SharePoint özelliğini eklemek için
  
1.  Açık **paketleme Gezgini'ni**projesi için kısayol menüsünü açın ve ardından **ekleme özelliği**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Var olan bir SharePoint özelliğini taşımak için  
  
1.  Açık **paketleme Gezgini'ni**ve ardından aşağıdaki adımlardan birini gerçekleştirin:  
  
    -   Sürükleme bir **özelliği** başka bir projeye bir projeye ait.  
  
    -   Bir özellik için kısayol menüsünü açın, seçin **Kes**, özellik taşıyabilir ve ardından istediğiniz proje için kısayol menüsünü açın **Yapıştır**.  
  
    > [!NOTE]  
    >  Birden çok SharePoint Proje, çözümünüz varsa, bu yordamı kullanın.  
  
## <a name="validate-a-feature-or-package"></a>Bir özellik veya paket doğrula  
 SharePoint özellikleri ve paketleri olası sorunları dosyaları doğrulayarak tanımlayabilirsiniz. Uyarıları ve hataları çıktı penceresi ve Hata Listesi penceresi görüntülenir.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Bir SharePoint özelliğini veya paket doğrulamak için
  
1.  Açık **paketleme Gezgini'ni**.  
  
2.  Bir özellik veya paket için bir kısayol menüsünü açın ve ardından **doğrulama**.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
