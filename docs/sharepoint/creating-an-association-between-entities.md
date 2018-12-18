---
title: Varlıklar arasında ilişkilendirme oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22ac00ac48f4fe907e4fb4215992b49227f39961
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325469"
---
# <a name="create-an-association-between-entities"></a>Varlıklar arasında ilişkilendirme oluşturma
  İş verileri bağlantı (BDC) modelinizdeki ilişkilendirmeleri oluşturarak varlıklar arasındaki ilişkiler tanımlayabilirsiniz. Visual Studio tüketicileri modelin her bir ilişkilendirme hakkında bilgi sağlayan yöntemler oluşturur. Bu yöntemler, SharePoint web bölümleri, liste veya veri ilişkileri kullanıcı arabiriminde (UI) görüntülemek için özel uygulamaları tarafından kullanılabilecek.  
  
## <a name="create-an-association"></a>İlişkilendirme oluşturma
 Seçerek ilişkilendirme oluşturma **ilişkilendirme** denetim Visual Studio'da **araç**, (kaynak varlık olarak adlandırılır) ilk varlık seçme ve ikinci varlık seçme (çağrılır Hedef varlık). Association'ında ayrıntılarını tanımlayabilirsiniz **ilişkilendirme Düzenleyicisi**. Daha fazla bilgi için bkz: [nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>İlişkilendirme yöntemleri
 SharePoint iş verileri web bölümlerini gibi uygulamalar, bir varlığın hizmet sınıfı yöntemleri çağırarak ilişkilendirmeleri tüketir. Bunları seçerek bir varlığın hizmet sınıfı yöntemleri ekleyebilirsiniz **ilişkilendirme Düzenleyicisi**.  
  
 Varsayılan olarak, **ilişkilendirme Düzenleyicisi** kaynak ve hedef varlıklara bir ilişkilendirme Gezinti yöntemi ekler. Kaynak varlık ilişkisi Gezinti yönteminde hedef Varlık listesini almak tüketicilere sağlar. Hedef varlık ilişkisi Gezinti yönteminde bir hedef varlık ilişkili kaynak varlık almak üzere tüketiciler sağlar.  
  
 Kod uygun bilgileri döndürmek için bu yöntemlerin her biri için eklemeniz gerekir. Diğer tür daha gelişmiş senaryoları desteklemek için yöntemi de ekleyebilirsiniz. Bu yöntemlerin her biri hakkında daha fazla bilgi için bkz: [desteklenen işlemler](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Tür ilişkileri
 BDC Tasarımcısı'nda ilişkilendirmeleri iki tür oluşturabilirsiniz: yabancı anahtar tabanlı ilişkileri ve yabancı anahtar kullanmadan ilişkilendirmeleri.  
  
### <a name="foreign-key-based-association"></a>Yabancı anahtar tabanlı ilişkilendirme
 Bir yabancı anahtar tabanlı ilişkisi hedef varlık tanımlanan tanımlayıcıları yazmak için kaynak varlık tanımlayıcıda ilişkilendirilerek oluşturabilirsiniz. Bu ilişki, kullanıcılar için Gelişmiş bir kullanıcı Arabirimi sağlar tüketici modelinin sağlar. Örneğin, aşağı açılan listesinde müşteriler görüntüleyen bir sipariş oluşturmak bir kullanıcının sağlayan Outlook içinde bir formun; veya siparişler bir müşteri için bir profili sayfasını açmak kullanıcıların sağlayan SharePoint listesi.  
  
 Bir yabancı anahtar tabanlı ilişkisi oluşturmak için tanımlayıcıları ilgili ve aynı ad ve türe paylaşmak tanımlayıcıları yazın. Örneğin, arasında bir yabancı anahtar tabanlı ilişkilendirmesi oluşturabilirsiniz bir `Contact` varlık ve `SalesOrder` varlık. `SalesOrder` Varlık döndürür bir `ContactID` tanımlayıcısı Bulucu veya belirli bir Bulucu yöntemi dönüş parametresi bir parçası olarak yazın. Her iki tür tanımlayıcısı görünür **ilişkilendirme Düzenleyicisi**. Bir yabancı anahtar tabanlı ilişkisi oluşturmak için `Contact` varlık ve `SalesOrder` varlığı seçin `ContactID` bu alanların her biri yanındaki tanımlayıcısı.  
  
 Kod bir hedef varlık koleksiyonunu döndürür kaynak varlık ilişkisi Gezgini yöntemine ekleyin. Aşağıdaki örnek, bir kişi için satış siparişleri döndürür.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Kod bir kaynak varlık döndüren hedef varlık ilişkisi Gezgini yöntemine ekleyin. Aşağıdaki örnek satış siparişine ilgili kişi döndürür.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Yabancı anahtar kullanmadan ilişkilendirme
 Alan türü tanımlayıcıları tanımlayıcılarını eşleme olmadan ilişkilendirme oluşturabilirsiniz. Kaynak varlık hedef varlık ile doğrudan bir ilişkisi yok, bu tür bir ilişki oluşturun. Örneğin, bir `SalesOrderDetail` tabloda bir birincil anahtar eşleyen bir yabancı anahtar yok bir `Contact` tablo.  
  
 Bilgileri görüntülenecek istiyorsanız `SalesOrderDetail` ilişkili tablo bir `Contact`, arasında bir yabancı anahtar kullanmadan ilişkilendirmesi oluşturabilirsiniz `Contact` varlık ve `SalesOrderDetail` varlık.  
  
 İlişkilendirme Gezinti yöntemi de `Contact` varlık, dönüş `SalesOrderDetail` varlıklar tabloları birleştirme ya da bir saklı yordam çağırma.  
  
 Aşağıdaki örnek, tablolar birleştirerek tüm satış siparişleri ayrıntılarını döndürür.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 İlişkilendirme Gezinti yöntemi de `SalesOrderDetail` varlık, ilgili iade `Contact`. Aşağıdaki örnekte bu gösterir.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)  
  
 
