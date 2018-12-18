---
title: İş verilerini SharePoint ile tümleştirme | Microsoft Docs
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e75367844a3a62e044a98f9d52c567fcfca3590e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120613"
---
# <a name="integrate-business-data-into-sharepoint"></a>İş verilerini SharePoint ile tümleştirme
  İş verilerini SharePoint ile tümleştirebilirsiniz. İş verileri gelebilir arka uç sunucu uygulamalardan gibi [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel ve SAP, veya bir Web hizmeti. Kullanıcılar görüntüleme, ekleme, güncelleştirme veya dış listeler veya iş veri SharePoint Web Bölümleri kullanarak iş verileri silme.  Kullanıcılar ayrıca bu verileri çevrimdışı Microsoft Outlook gibi Microsoft Office uygulamasında erişebilir. Daha fazla bilgi için bkz: [burada olabilir, göster dış veri](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Verilerini SharePoint ile tümleştirmek için iş verileri bağlantı (BDC) hizmeti için bir model oluşturun. BDC hizmeti iş uygulamalarında verilerle ilgili bilgileri depolar SharePoint'te bir uygulamadır. Daha fazla bilgi için bkz: [iş verileri bağlantı (BDC) hizmeti](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Visual Studio'da modelleri  
 Visual Studio'da modelleri almak ve arka uç veri kaynaklarından verileri güncelleştirmek için özel kod yazmanıza olanak sağlar. Ayrıca, birden çok veri kaynaklarından veri toplama erişebilirsiniz. Örneğin, verileri içeren müşterilerin listesini görüntüleyebilirsiniz bir [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] veritabanı ve Web hizmeti.  
  
 Ayrıca, SharePoint'e zaten dağıtılmış olan modelleri içe aktarabilirsiniz. Model içeri aktardıktan sonra özel kod ekleme ya da yalnızca paketini ve model için birden çok SharePoint sunucu grubu dağıtmak için Visual Studio kullanın. Daha fazla bilgi için bkz: [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="design-a-model-in-visual-studio"></a>Visual Studio'da bir model tasarlama
 Bir tasarımcı ve birkaç araç pencereleri kullanarak bir model tasarlayabilirsiniz. Model tasarlarken, Visual Studio XML modeli oluşturur. Daha fazla bilgi için bkz: [BDC modeli Tasarım araçları genel bakış](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Bir modeli varlıkları ve yöntemleri içerir.  
  
### <a name="entities"></a>varlıklar  
 Bir varlık alanların koleksiyonunu açıklar. Örneğin, bir varlığın bir veritabanındaki bir tablo temsil edebilir. Bir varlık SharePoint'te dış içerik türü olarak görünür. Dış içerik türleri hakkında daha fazla bilgi için bkz: [dış içerik türleri nelerdir?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Yöntemler  
 Bir yöntemi, bir varlık alanları üzerinde bir işlemi gerçekleştirmesi için bir dış içerik türü tüketicileri etkinleştirir. Örneğin, bir güncelleyici yöntemi adresi değiştirmelerini sağlayan ve doğum tarihi bir müşterinin nerede `Address` ve `BirthDate` alanlar, `Customer` varlık.  
  
 Visual Studio modelinizde her varlık için bir hizmet kod dosyası oluşturur. Bir yöntem modelinize eklediğinizde, Visual Studio karşılık gelen bir yöntemi hizmeti kod dosyasını oluşturur. Kodu uygun görevi gerçekleştirmek için her yöntemine ekleyin. Modele bir yaratıcı yöntemi ekleme, örneğin, Visual Studio bir yaratıcı yöntemi, hizmet kod dosyasında oluşturur. Bir kullanıcı tıkladığında bu yöntem BDC hizmeti tarafından çağrılır **yeni öğe** düğmesini modelini temel alan bir listesi. Bu nedenle, bir veri kaynağı için yeni veri ekleyen yaratıcı yöntemi kodu ekleyin. Daha fazla bilgi için bkz: [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>İlgili konular
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)|Nasıl yeni bir model oluşturmak veya dışarı aktarmak istediğiniz SharePoint'ten model içeri aktarma gösterir.|  
|[İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio tasarım araçlarını kullanarak bir model öğelerini tasarım açıklanmaktadır.|  
|[Ne zaman SharePoint Designer'ı kullanın vs. Visual Studio oluştururken çözümleri BCS kullanma](http://go.microsoft.com/fwlink/?LinkID=183448)|Visual Studio veya BDC için bir model oluşturmak için SharePoint Designer kullanın karar vermenize yardımcı olur.|  
  
