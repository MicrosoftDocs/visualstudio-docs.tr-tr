---
title: 'Nasıl yapılır: veritabanındaki kayıtları silme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 87ab5ccde2c1100fbd0efc5f4272efe27803b717
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938623"
---
# <a name="how-to-delete-records-in-a-database"></a>Nasıl yapılır: Veritabanındaki Kayıtları Silme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kayıtlarını veritabanından silmek için kullanın `TableAdapter.Update` yöntemi veya `TableAdapter.Delete` yöntemi. Veya uygulamanız TableAdapters kullanmıyorsa, komut nesneleri kayıtlarını veritabanından silmek için kullanabilirsiniz (örneğin, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 `TableAdapter.Update` Yöntemi genellikle kullanılan uygulamanız veri kümeleri verileri depolamak için ise kullandığında `TableAdapter.Delete` yöntemi genellikle, uygulama verilerini depolamak için nesneleri kullandığında kullanılır.  
  
 TableAdapter yoksa bir `Delete` yöntemi geldiğini TableAdapter ya da saklı yordamlar kullanacak şekilde yapılandırıldığını veya kendi `GenerateDBDirectMethods` özelliği `false`. TableAdapter bağdaştırıcısının yapmayı deneyin `GenerateDBDirectMethods` özelliğini `true` içinden [veri kümesi Tasarımcısı](../data-tools/creating-and-editing-typed-datasets.md) ve veri kümesini TableAdapter yeniden kaydedin. TableAdapter hala yoksa bir `Delete` yöntemi daha sonra tablonun büyük olasılıkla sağlamaz arasında bireysel satırları ayırt etmek için yeterli şema bilgileri (örneğin, birincil anahtarı olmayan tablo üzerinde ayarlanır).  
  
## <a name="delete-records-using-tableadapters"></a>TableAdapter kullanarak kayıtlarını sil  
 TableAdapters kayıtlarını uygulamanızın gereksinimlerine bağlı olarak bir veritabanından silmek için farklı yollar sunar.  
  
 Uygulama verilerini depolamak için veri kümelerini kullanıyorsa kayıtları istenen silmeniz yeterlidir <xref:System.Data.DataTable> içinde <xref:System.Data.DataSet>ve sonra çağrı `TableAdapter.Update` yöntemi. `TableAdapter.Update` Yöntemi veri tablosunda değişiklikleri alır ve bu değişiklikleri (eklenen, güncelleştirilen ve silinen kayıtlar da dahil) veritabanına gönderir.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>TableAdapter.Update yöntemi kullanarak bir veritabanındaki kayıtları silme  
  
- İstenen kayıtları silme <xref:System.Data.DataTable> silerek <xref:System.Data.DataRow> tablosundan nesneleri. Daha fazla bilgi için [nasıl yapılır: bir DataTable tablosundaki satırları silme](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Satırları gelen silindikten sonra <xref:System.Data.DataTable>, çağrı `TableAdapter.Update` yöntemi. Tüm geçirerek güncelleştirmek için veri miktarını denetleyebilirsiniz <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, bir dizi <xref:System.Data.DataRow>s ya da tek bir <xref:System.Data.DataRow>. Aşağıdaki kod, bir kaydı silmek gösterilmiştir bir <xref:System.Data.DataTable> ve sonra çağrı `TableAdapter.Update` Değiştir iletişim kurmak ve satır veritabanından silmek için yöntemi. (Bu örnekte Northwind veritabanının `Region` tablo.)  
  
   [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
   [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
  Uygulamanız, uygulamanızda verileri depolamak için nesneleri kullanıyorsa, verileri doğrudan veritabanından silmek için TableAdapter bağdaştırıcısının DBDirect yöntemleri kullanabilirsiniz. Çağırma `Delete` yöntemi veritabanından geçirilen parametre değerlerini temel alarak kayıtları kaldırır.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>TableAdapter.Delete yöntemi kullanarak bir veritabanındaki kayıtları silme  
  
-   TableAdapter bağdaştırıcısının çağrı `Delete` değerleri her sütun için parametre olarak geçirerek yöntemini `Delete` yöntemi. (Bu örnekte Northwind veritabanının `Region` tablo.)  
  
    > [!NOTE]
    >  Kullanmak istediğiniz TableAdapter kullanılabilir bir örnek yoksa örneği.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Komut nesneleri kullanarak kayıtlarını sil  
 Aşağıdaki örnek, doğrudan komut nesneleri kullanarak bir veritabanındaki kayıtları siler. Komutlar ve saklı yordamları çalıştırmak için komut nesneleri kullanma hakkında daha fazla bilgi için bkz. [uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Komut nesneleri kullanarak bir veritabanındaki kayıtları silme  
  
-   Yeni bir komut nesnesi oluşturur, ayarla, `Connection`, `CommandType`, ve `CommandText` özellikleri. (Bu örnekte Northwind veritabanının `Region` tablo.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 İstenen tablosundan kayıtları silme izni yanı sıra, bağlanmaya çalıştığınız veritabanı erişimi olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)   
 [Nasıl yapılır: veritabanındaki kayıtları güncelleştirme](../data-tools/how-to-update-records-in-a-database.md)   
 [Verileri bir nesneden veritabanına kaydetme](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Veri uygulamaları Visual Studio'da genel bakış](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)