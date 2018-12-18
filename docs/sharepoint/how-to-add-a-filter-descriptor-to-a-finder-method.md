---
title: 'Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63374f4d96c86ea3eafbd4c6fa3fbe3d1f5a5899
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755605"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme
  Filtre tanımlayıcıları bunlar yürütmeden önce değerleri yöntemlere geçirmek model tüketicileri etkinleştirin. Daha fazla bilgi için bkz: [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Yaygın bir senaryo, SharePoint kullanıcılar bazı ölçütlere uyan bir dış içerik türü örnekleri almak istediğiniz ' dir. Bu senaryoyu desteklemek için bir Bulucu yöntemine filtre tanımlayıcısı ekleyerek.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Bir Bulucu yöntemine filtre tanımlayıcısı ekleme  
  
1.  İçinde **BDC yöntem ayrıntıları** penceresinde bir Bulucu yöntemi düğümünü genişletin, **parametreleri** düğümünü ve ardından bir giriş parametresi ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  İçinde **yöntemi ayrıntılarını** penceresinde, parametrenin tür tanımlayıcısını seçin.  
  
3.  Menü çubuğunda seçin **Görünüm** > **Özellikler penceresini**.  
  
4.  İçinde **özellikleri** penceresindeki ayarlayın **türü adı** filtre için uygun olan bir veri türü için özellik.  
  
     Örneğin, bir filtre, sipariş tarihi siparişler yöntemi tarafından döndürülen sayısını sınırlamak için kullanabilirsiniz. Bu filtre desteklemek için **türü adı** tür tanımlayıcı özelliği ayarlanmalıdır **System.DateTime**.  
  
5.  İçinde **yöntemi ayrıntılarını** penceresinde genişletin **filtre tanımlayıcıları** düğümü.  
  
6.  İçinde **filtre tanımlayıcısı ekleme** listesinde, seçin **oluşturma filtre tanımlayıcısı**.  
  
     Altında yeni bir filtre tanımlayıcısı görülür **filtre tanımlayıcıları** düğümü.  
  
7.  Menü çubuğunda seçin **Görünüm** > **Özellikler penceresini**.  
  
8.  İçinde **özellikleri** penceresinde, seçin **türü** özelliği.  
  
9. İçin görünen listesindeki **türü** özelliği, istediğiniz filtreleme deseni seçin.  
  
     Örneğin, bir Bulucu yöntemi döndürülen satış siparişleri sayısını sınırlamak için bir sipariş tarihi kullanan bir filtresi oluşturmak için seçtiğiniz **karşılaştırma**. Bir karşılaştırma filtresi bir Bulucu yöntemi yalnızca belirli bir koşula örnekleri döndürür sağlar. Her filtre desen hakkında daha fazla bilgi için bkz: [, filtreleri tarafından desteklenen türleri BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. İçinde **özellikleri** penceresinde, seçin **ilişkili tür tanımlayıcısı** özelliği.  
  
11. İçin görünen listesindeki **ilişkili tür tanımlayıcısı** özelliği, bu yordamda daha önce oluşturduğunuz tür tanımlayıcısı'ı seçin. Bu filtre Bulucu yöntemine giriş parametresi olarak ilişkilendirir.  
  
12. Kod veri döndüren bir Bulucu yöntemine ekleyin. Seçme sorgusu bir koşul olarak giriş parametresini kullanabilirsiniz.  
  
     Aşağıdaki örnek, belirtilen sipariş tarihi olan siparişler döndürür.  
  
    > [!NOTE]  
    >  Değerini `ServerName` alanını sunucunuzun adıyla.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)   
 [Nasıl yapılır: belirli bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
