---
title: BDC modeli Tasarım araçları genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c5a799a245d2149161809977446d0c005dbe293
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914508"
---
# <a name="bdc-model-design-tools-overview"></a>BDC modeli tasarım araçlarına genel bakış
  İVB Tasarımcısı kullanarak bir iş verileri bağlantısı (BDC) modeli tasarlayabilirsiniz **BDC yöntem ayrıntıları** penceresinde ve **BDC Gezgini**.  
  
 **BDC Gezgini** modeli Gözat'ı, model arama ve tür tanımlayıcısı tanımlamanızı sağlar.  
  
## <a name="bdc-designer"></a>İVB Tasarımcısı
 İVB Tasarımcısı, modelinizdeki varlıklar tanımlayan ve görsel olarak birbirleriyle ilişkilerini düzenlemek için sağlar. İVB Tasarımcısı, aşağıdaki görevleri gerçekleştirmek için kullanın:  
  
- Modele varlık ekleme.  
  
- Varlıkları modelden kaldırın.  
  
- Varlıklar arasındaki ilişkileri tanımlayın.  
  
  İVB Tasarımcısı'nı açmak için projenizde, model dosyasına çift tıklayın veya model dosyası için kısayol menüsünü açın ve ardından **açın**. Sürükleyerek veya kopyalayarak modele bir varlık eklemek bir **varlık** gelen **araç kutusu** tasarımcıya. İki varlık arasında bir ilişki oluşturmak için seçin **ilişkilendirme** denetim **araç kutusu**, birinci varlığın seçin ve ardından ikinci varlığı seçin.  
  
## <a name="bdc-method-details-window"></a>BDC yöntem Ayrıntıları penceresi
 Kullanım **BDC yöntem ayrıntıları** parametreleri, örnekleri tanımlayın ve filtre tanımlayıcıları bir yöntemin penceresi.  
  
 Bulucu, belirli Bulucu, oluşturucu, güncelleştirici ve Silici yöntemleri hızlı bir şekilde oluşturabileceğiniz **BDC yöntem ayrıntıları** penceresi. Bu yöntemleri oluşturduğunuzda, Visual Studio yönteme parametre, örnekleri ve tür tanımlayıcısı gibi meta veri ekler. Bu meta veriler kendi senaryonuza karşılamak için değiştirebilirsiniz.  
  
 Açmak için **BDC yöntem ayrıntıları** menü çubuğunda, pencere **görünümü** > **diğer Windows** > **BDC yöntem ayrıntıları** .  
  
 Yöntemleri görüntülemek için **BDC yöntem ayrıntıları** penceresinde İVB Tasarımcısı'nda varlık seçin. Seçilen varlığın yöntemleri görünür **BDC yöntem ayrıntıları** penceresi. Bir varlığı İVB Tasarımcısı'nda seçmezseniz **BDC yöntem ayrıntıları** penceresi hiçbir bilgi görüntüler.  
  
 Genişlet veya daralt düğümler **BDC yöntem ayrıntıları** parametreleri, örnekler, tanımlamak ve filtre tanımlayıcıları penceresi. Kullanım **BDC Gezgini** tür tanımlayıcısı tanımlamak için.  
  
## <a name="bdc-explorer"></a>BDC Gezgini
 **BDC Gezgini** modeli öğeleri görüntüler. Açmak için **BDC Gezgini**, menü çubuğunda, **görünümü** > **diğer Windows** > **BDC Gezgini**. Model göz atmak için düğümleri genişletin **BDC Gezgini**. Her düğüm, model dosyası XML içindeki bir öğeyi temsil eder.  
  
 Düğümler seçerken **BDC Gezgini**, seçtiğiniz her bir düğümün özellikleri görünür **özellikleri** penceresi. Bu özelliklerin çoğu model dosyası özniteliğine karşılık gelir. En üstündeki arama kutusunu kullanarak model arayabilirsiniz **BDC Gezgini**.  
  
> [!NOTE]  
>  **BDC Gezgini** tanımlayıcıları, özel özellikler, yerelleştirilmiş dizeleri, ilişkilendirme grupları, Eylemler, filtre tanımlayıcıları, eylem denetim listeleri ve varsayılan parametre değerlerini görüntülemez.  
  
### <a name="define-type-descriptors"></a>Tür tanımlayıcıları tanımlayın
 Kullanım **BDC Gezgini** tür tanımlayıcısı tanımlamak için. BDC Gezgini, bir tür tanımlayıcı bir kez tanımlamanızı ve daha sonra bu tür tanımlayıcıyı modelinizdeki başka bir yerde yeniden sağlar. Bunu gerçekleştirmek için bir tür tanımlayıcı kopyalayıp başka bir parametre yapıştırın veya tür tanımlayıcısı.  
  
> [!NOTE]  
>  Özgün bir tür tanımlayıcı değişiklikler, bu tür tanımlayıcıyı kopyalarını etkilemez.  
  
 Daha fazla bilgi için [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)   
 [Nasıl yapılır: modele bir varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Nasıl yapılır: bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)   
 [Nasıl yapılır: belirli bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Nasıl yapılır: bir yaratıcı metodu ekleme](../sharepoint/how-to-add-a-creator-method.md)   
 [Nasıl yapılır: bir Silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)   
 [Nasıl yapılır: bir güncelleyici metodu ekleme](../sharepoint/how-to-add-an-updater-method.md)   
 [Varlıklar arasında ilişkilendirme oluşturma](../sharepoint/creating-an-association-between-entities.md)   
 [İzlenecek yol:, iş verileri kullanarak SharePoint'te dış liste oluşturma](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
 
