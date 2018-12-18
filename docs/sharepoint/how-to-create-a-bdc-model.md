---
title: 'Nasıl yapılır: bir BDC modeli oluşturma | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a0e2bc47c902707ee896c46fa0d9988551fa6fd
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757928"
---
# <a name="how-to-create-a-bdc-model"></a>Nasıl yapılır: bir BDC modeli oluşturma
  Bu tür bir öğe için şablon kullanılarak ve sonra herhangi bir SharePoint projesine model ekleyerek bir iş verileri bağlantı (BDC) modeli oluşturabilirsiniz. Daha fazla bilgi için bkz: [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md). Model tasarlama hakkında daha fazla bilgi için bkz: [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>BDC projesi oluşturmak için  
  
1.  Menü çubuğunda seçin **dosya** > **yeni** > **proje**.  
  
    > [!NOTE]  
    >  Visual Basic geliştirme ayarlarını kullanmak için IDE'yi ayarlarsanız seçin **dosya** > **yeni proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
2.  Ya da altında **Visual Basic** veya **Visual C#**, seçin **Office/SharePoint**, **SharePoint çözümlerini**.  
  
3.  İçinde **şablonları** bölmesinde seçin **SharePoint 2013 - boş proje** öğesini ve ardından **Tamam** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı'nı** açar.  
  
4.  Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtmek** sayfasında, yerel bilgisayarda bir SharePoint sitesinin URL'sini belirtin, **Grup çözümü olarak dağıtma** seçeneği düğmesine ve ardından **Son** düğmesi.  
  
     Belirtilen SharePoint sitesindeki modeli test edeceğiz.  
  
    > [!IMPORTANT]  
    >  BDC modeli yalnızca küme çözümleri desteklemediğinden proje Grup çözümü dağıtmanız gerekir.  
  
     Boş bir SharePoint projesi oluşturulur.  
  
5.  Menü çubuğunda seçin **proje** > **Yeni Öğe Ekle**.  
  
6.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, seçin **Office/SharePoint** düğümü.  
  
7.  SharePoint şablonları listesinden seçip **iş verileri bağlantı modeli (yalnızca Grup çözüm)**.  
  
8.  İçinde **adı** kutusunda BDC modeli için bir ad belirtin ve ardından **Ekle** düğmesi.  
  
     A **iş verileri bağlantı modeli** öğe projeye eklenmiş. Varsayılan olarak, model BDC Tasarımcısı'nda görünür. Daha fazla bilgi için bkz: [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Nasıl yapılır: yerelleştirilmiş adlar, özellikler ve izinleri belirtmek için kaynak dosyası kullanın](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Nasıl yapılır: bir BDC özelliğine özel bir derlemeyi dahil etme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
