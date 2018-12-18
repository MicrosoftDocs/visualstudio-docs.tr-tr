---
title: 'Nasıl yapılır: bir güncelleyici metodu ekleme | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4d50180173673b4999c18b8980c682d79637bd3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951424"
---
# <a name="how-to-add-an-updater-method"></a>Nasıl yapılır: bir güncelleyici metodu ekleme
  Kullanıcılar oluşturarak dış bir SharePoint listesindeki iş verileri güncelleştirmek etkinleştirebilirsiniz bir *güncelleştirici* yöntemi. Daha fazla bilgi için [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Bir güncelleyici yöntemi oluşturmak için  
  
1. İVB Tasarımcısı üzerinde bir varlık seçin.  
  
2. Menü çubuğunda, **görünümü** > **diğer Windows** > **BDC yöntem ayrıntıları**.  
  
    BDC yöntem Ayrıntıları penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC modeli Tasarım araçları genel bakış](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. İçinde **bir yöntem ekleyin** listesinde **güncelleştirici metodu Oluştur**.  
  
    Visual Studio modele aşağıdaki öğeleri ekler. Bu öğeler, İVB metot Ayrıntıları penceresinde görünür.  
  
   - Adlı bir yöntem **güncelleştirme**.  
  
   - Yöntemi giriş parametresi.  
  
   - Parametresi için bir tür tanımlayıcı. Varsayılan olarak, Visual Studio tanımladığınız varlık türü tanımlayıcısı için Bulucu metodunu kullanır (örneğin: kişi).  
  
   - Yöntemi için yöntem örneği.  
  
     Daha fazla bilgi için [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
   > [!NOTE]  
   >  Varlık türü tanımlayıcısı bir alan otomatik olarak oluşturulan bir veritabanı tablosundaki temsil ediyorsa, ayarlama **güncelleştirici öncesi alanı** özelliğini **True**.  
  
4. İçinde **Çözüm Gezgini**, oluşturulan hizmet kodu dosyası varlık için kısayol menüsünü açın ve ardından **kodu görüntüle**.  
  
    Varlık hizmet kodu dosyası açılır **Kod Düzenleyicisi**. Bu dosya hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Verileri güncelleştirmek için güncelleştirme yöntemine kod ekleyin. Aşağıdaki örnek, SQL Server için bir kişinin AdventureWorks örnek veritabanındaki bilgileri güncelleştirir.  
  
   > [!NOTE]  
   >  Değiştirin `ServerName` alanını sunucunuzun adıyla.  
  
    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Nasıl yapılır: bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)   
 [Nasıl yapılır: belirli bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Nasıl yapılır: bir yaratıcı metodu ekleme](../sharepoint/how-to-add-a-creator-method.md)   
 [Nasıl yapılır: bir güncelleyici metodu ekleme](../sharepoint/how-to-add-an-updater-method.md)   
 [Nasıl yapılır: bir Silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)   
 [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)   
 [Nasıl yapılır: bir yönteme bir parametre ekleyin](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Nasıl yapılır: bir yöntemi örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)  
  
 
