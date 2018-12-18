---
title: 'Nasıl yapılır: yerelleştirilmiş adlar, özellikler ve izinleri belirtmek için kaynak dosyası kullanın | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c54aa87f09d4821f9fde5cceb95e6ec3a8e089fa
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120433"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Nasıl yapılır: yerelleştirilmiş adlar, özellikler ve izinleri belirtmek için kaynak dosyası kullanın
  Kaynak dosyası kullanarak, yerelleştirilmiş adlar sağlamak, özelliklerini tanımlamak ve iş verileri bağlantı (BDC) modelde tanımlanan izinleri tor nesneler geçerli. Bu bilgileri belirtmek için eklediğiniz bir **iş verileri bağlantı kaynak** içeren bir proje öğesi bir **iş verileri bağlantı modeli** öğesi. Ardından, adlar, özellikler ve izinleri kaynak dosyası için XML düzenleyerek belirtin.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Bir SharePoint projesine bir BDC kaynak dosyası eklemek için  
  
1.  İçinde **Çözüm Gezgini**, SharePoint proje klasörünü genişletin ve ardından BDC modeli içeren klasörü seçin.  
  
2.  Menü çubuğunda seçin **proje** > **Yeni Öğe Ekle**.  
  
3.  Genişletme **SharePoint** düğümünü ve ardından **2010** düğümü.  
  
4.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, seçin **iş verileri bağlantı kaynak öğesi**.  
  
5.  İçinde **adı** kutusunda kaynak dosyasının adını belirtin ve ardından **Ekle** düğmesi.  
  
     .Bdcr uzantısına sahip bir kaynak dosyası projeye eklendi ve düzenleme için açıldı.  
  
6.  Yerelleştirilmiş adlar, özellikler ve BDC modeli uygulamak istediğiniz izinlerini tanımlamak için XML ekleyin.  
  
     Bu öğeleri tanımlama hakkında daha fazla bilgi için bkz: [modeli ve kaynak dosyaları](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Nasıl yapılır: bir BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)   
 [Nasıl yapılır: bir BDC özelliğine özel bir derlemeyi dahil etme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
