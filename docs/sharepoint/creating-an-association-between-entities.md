---
title: Varlıklar arasında Ilişkilendirme oluşturma | Microsoft Docs
description: Iş verileri bağlantısı (BDC) modelinizdeki varlıklar arasında bir ilişki oluşturun. İlişkilendirme yöntemleri ve ilişkilerin türleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d40c4e5c5d61b9da3cdbdd3fe96f45c4a0cff929
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213972"
---
# <a name="create-an-association-between-entities"></a>Varlıklar arasında ilişkilendirme oluşturma
  İlişkiler oluşturarak Iş verileri bağlantısı (BDC) modelinizdeki varlıklar arasında ilişkiler tanımlayabilirsiniz. Visual Studio, her ilişki hakkında bilgi içeren modelin tüketicilerini sağlayan yöntemler oluşturur. Bu yöntemler, veri ilişkilerini bir kullanıcı arabiriminde (UI) göstermek için SharePoint Web bölümleri, listeleri veya özel uygulamalar tarafından kullanılabilir.

## <a name="create-an-association"></a>İlişki oluşturma
 Visual Studio **araç kutusunda** **ilişki** denetimini seçip ilk varlığı (kaynak varlık olarak adlandırılır) seçip ikinci varlığı (hedef varlık olarak adlandırılır) seçerek bir ilişki oluşturun. İlişki **Düzenleyicisi**' nde ilişkilendirmenin ayrıntılarını tanımlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: varlıklar arasında Ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>İlişkilendirme yöntemleri
 SharePoint iş verileri Web bölümleri gibi uygulamalar, bir varlığın hizmet sınıfındaki yöntemleri çağırarak ilişkilendirmeleri kullanır. **Ilişki düzenleyicisinde** seçerek bir varlığın hizmet sınıfına Yöntemler ekleyebilirsiniz.

 Varsayılan olarak, **Ilişkilendirme Düzenleyicisi** kaynak ve hedef varlıklara bir ilişkilendirme gezinti yöntemi ekler. Kaynak varlıktaki bir Ilişkilendirme gezinti yöntemi, tüketicilerin hedef varlıkların bir listesini almasını sağlar. Hedef varlıktaki bir Ilişkilendirme gezinti yöntemi, tüketicilerin bir hedef varlıkla ilgili kaynak varlığı almasını sağlar.

 Uygun bilgileri döndürmek için bu yöntemlerin her birine kodu eklemeniz gerekir. Daha gelişmiş senaryolar desteklemek için diğer yöntem türleri de ekleyebilirsiniz. Bu yöntemlerin her biri hakkında daha fazla bilgi için bkz. [desteklenen işlemler](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>İlişki türleri
 İVB tasarımcısında iki tür ilişki oluşturabilirsiniz: yabancı anahtar tabanlı ilişkilendirmeler ve yabancı anahtarsız ilişkilendirmeleri.

### <a name="foreign-key-based-association"></a>Yabancı anahtar tabanlı ilişkilendirme
 Kaynak varlıktaki bir tanımlayıcıyı hedef varlıkta tanımlanan tür tanımlayıcılarıyla ilişkilendirerek, yabancı anahtar tabanlı bir ilişki oluşturabilirsiniz. Bu ilişki, modelin tüketicilerinin kullanıcıları için gelişmiş bir kullanıcı arabirimi sağlamasına olanak sağlar. Örneğin, Outlook 'ta, bir kullanıcının bir açılan listede müşterileri görüntüleyebilen bir satış siparişi oluşturmasını sağlayan bir form; veya SharePoint 'te, kullanıcıların bir müşteri için bir profil sayfası açmasını sağlayan satış siparişlerinin bir listesi.

 Yabancı anahtar tabanlı bir ilişki oluşturmak için, aynı adı ve türü paylaşan tanımlayıcıları ve tür tanımlayıcılarını ilişkilendirin. Örneğin, bir varlık ve varlık arasında yabancı anahtar tabanlı bir ilişki oluşturabilirsiniz `Contact` `SalesOrder` . `SalesOrder`Varlık, `ContactID` Bulucu veya belirli Bulucu yöntemlerinin dönüş parametresinin bir parçası olarak bir tür tanımlayıcısı döndürür. Her iki tür tanımlayıcısı da **Ilişkilendirme düzenleyicisinde** görünür. Varlık ve varlık arasında yabancı anahtar tabanlı bir ilişki oluşturmak için `Contact` `SalesOrder` , `ContactID` Bu alanların her birinin yanındaki tanımlayıcıyı seçin.

 Hedef varlıkların koleksiyonunu döndüren kaynak varlığın Ilişkilendirme gezgin yöntemine kod ekleyin. Aşağıdaki örnek, bir kişinin satış siparişlerini döndürür.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 Kaynak varlık döndüren hedef varlığın Ilişkilendirme gezgin yöntemine kod ekleyin. Aşağıdaki örnek, satış siparişiyle ilgili olan kişiyi döndürür.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>Yabancı anahtarsız ilişkilendirmesi
 Tanımlayıcıları alan türü tanımlayıcılarıyla eşleştirmeden bir ilişkilendirme oluşturabilirsiniz. Kaynak varlığın hedef varlıkla doğrudan bir ilişkisi olmadığında, bu tür bir ilişki oluşturun. Örneğin, bir `SalesOrderDetail` tablo, bir tablodaki birincil anahtarla eşleşen yabancı anahtara sahip değildir `Contact` .

 İle `SalesOrderDetail` ilişkili olan tablodaki bilgileri göstermek istiyorsanız `Contact` , `Contact` varlık ve varlık arasında yabancı bir anahtar daha az ilişki oluşturabilirsiniz `SalesOrderDetail` .

 Varlığın Ilişkilendirme gezinti yönteminde `Contact` , `SalesOrderDetail` tabloları birleştirerek veya saklı bir yordam çağırarak varlıkları döndürün.

 Aşağıdaki örnek, tabloları birleştirerek tüm satış siparişlerinin ayrıntılarını döndürür.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 Varlığın Ilişkilendirme gezinti yönteminde `SalesOrderDetail` ilgili öğesini döndürün `Contact` . Aşağıdaki örnek bunu gösterir.
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)
