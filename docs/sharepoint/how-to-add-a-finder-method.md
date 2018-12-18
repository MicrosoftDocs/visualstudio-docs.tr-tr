---
title: 'Nasıl yapılır: bir Bulucu yöntemi ekleme | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 597d1e706ad75ba6ec16b958c94b5ba9d8e97760
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836235"
---
# <a name="how-to-add-a-finder-method"></a>Nasıl yapılır: bir Bulucu yöntemi ekleme
  Bir web bölümü veya listedeki varlıkların listesini görüntülemek İş Verileri Bağlantısı (BDC) hizmeti etkinleştirmek için oluşturmalısınız bir *Bulucu* yöntemi. Varlığın örneklerinin bir koleksiyonunu döndüren özel bir yöntem bir Bulucu metodudur. Daha fazla bilgi için [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Bir Bulucu yöntemi oluşturmak için  
  
1. Üzerinde **İVB Tasarımcısı**, varlık seçin.  
  
    Daha fazla bilgi için [nasıl yapılır: modele bir varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2. Menü çubuğunda, **görünümü** > **diğer Windows** > **BDC yöntem ayrıntıları**.  
  
    **BDC yöntem ayrıntıları** penceresi açılır. Hakkında daha fazla bilgi için **BDC yöntem ayrıntıları** penceresinde görmek [BDC modeli Tasarım araçları genel bakış](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. İçinde **bir yöntem ekleyin** listesinde **Bulucu metodu Oluştur**.  
  
    Visual Studio, bir tür tanımlayıcı bir yöntem ve bir dönüş parametresi ekler.  
  
4. Tür tanımlayıcısını bir varlık koleksiyon türü tanımlayıcısı yapılandırın. Bir varlık koleksiyon türü tanımlayıcısı oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
   > [!NOTE]  
   >  Varlığa bir belirli Bulucu metodunu eklediyseniz, bu adımı gerçekleştirmeniz gerekmez. Visual Studio, belirli Bulucu metodunu içinde tanımlanan tür tanımlayıcısını kullanır.  
  
5. İçinde **Çözüm Gezgini**, oluşturulan hizmet kodu dosyası varlık için kısayol menüsünü açın ve ardından **kodu görüntüle**. Hizmet kodu dosyası hakkında daha fazla bilgi için bkz: [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6. Bulucu yöntemine kod ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:  
  
   - Verileri bir veri kaynağından alır.  
  
   - BDC hizmeti için varlıklar listesi döndürür.  
  
     Aşağıdaki örnek bir koleksiyonunu döndürür `Contact` AdventureWorks örnek veritabanındaki verileri kullanarak SQL Server için varlıklar.  
  
   > [!NOTE]  
   >  Değiştirin `ServerName` alanını sunucunuzun adıyla.  
  
    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)   
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Nasıl yapılır: belirli bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Nasıl yapılır: bir yaratıcı metodu ekleme](../sharepoint/how-to-add-a-creator-method.md)   
 [Nasıl yapılır: bir Silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)   
 [Nasıl yapılır: bir güncelleyici metodu ekleme](../sharepoint/how-to-add-an-updater-method.md)   
 [Nasıl yapılır: bir yönteme bir parametre ekleyin](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Nasıl yapılır: bir yöntemi örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)  
  
  
