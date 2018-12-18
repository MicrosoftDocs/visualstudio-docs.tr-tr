---
title: 'Nasıl yapılır: veritabanındaki kayıtları güncelleştirme | Microsoft Docs'
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b62dc86425dcbebb225c66eecd51505f674e20ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949038"
---
# <a name="how-to-update-records-in-a-database"></a>Nasıl yapılır: Veritabanındaki Kayıtları Güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz `TableAdapter.Update` veritabanındaki güncelleştirin (düzenleyin) kayıtları için yöntemi. `TableAdapter.Update` Yöntemi geçirilen parametreleri bağlı olarak farklı işlemler yapan çeşitli aşırı yükler sağlar. Bu farklı yöntem imzaları arama sonuçlarını anlamak önemlidir.  
  
> [!NOTE]
>  Uygulamanızı TableAdapters kullanmaz sonra komut nesneleri veritabanınızda kayıtları güncelleştirmek için kullanabilirsiniz (örneğin, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Komut nesneleri ile veri güncelleştirme hakkında daha fazla bilgi için "komut nesneleri kullanarak güncelleştirme kayıtları" aşağıya bakın.  
  
 Aşağıdaki tabloda çeşitli davranışını açıklar `TableAdapter.Update` yöntemleri:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Tüm değişiklikleri kaydetmek isterse <xref:System.Data.DataTable> veritabanı. (Bu, satır tabloya eklenen ekleme ve tablosundaki değiştirilmiş satırları güncelleştirme tablodan silinen satırları kaldırmayı içerir.)|  
|`TableAdapter.Update(DataSet)`|Bir veri kümesi parametre sürmekle birlikte, TableAdapter bağdaştırıcısının içinde tüm değişiklikleri kaydetmek için TableAdapter denemeleri ilişkili <xref:System.Data.DataTable> veritabanı. (Bu tablodaki satırları eklenen ekleme ve tablosundaki değiştirilmiş satırları güncelleştirme tablodan silinen satırları kaldırmayı içerir.) **Not:** TableAdapter bağdaştırıcısının ilişkili <xref:System.Data.DataTable> olduğu <xref:System.Data.DataTable> TableAdapter bağdaştırıcısının özgün yapılandırmasında oluşturulan.|  
|`TableAdapter.Update(DataRow)`|Belirtilen değişiklikleri kaydetmek isterse <xref:System.Data.DataRow> veritabanı.|  
|`TableAdapter.Update(DataRows())`|Dizisindeki herhangi bir satırdaki değişikliklerini kaydetmek isterse <xref:System.Data.DataRow>veritabanına s.|  
|`TableAdapter.Update("new column values", "original column values")`|Özgün sütun değerleri tarafından tanımlanmış tek bir satıra değişiklikleri kaydetmek çalışır.|  
  
 Tipik olarak kullandığınız `TableAdapter.Update` gereken yöntemini bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow>(s), uygulamanızın özel verileri depolamak için veri kümeleri kullandığında.  
  
 Tipik olarak kullandığınız `TableAdapter.Update` yönteminin, uygulama verilerini depolamak için nesneleri kullandığında sütun değerleri alan.  
  
 TableAdapter yoksa bir `Update` yönteminin, TableAdapter ya da saklı yordamları kullanmak için yapılandırıldığını anlamına gelir sütun değerleri, alan veya kendi `GenerateDBDirectMethods` özelliği `false`. TableAdapter bağdaştırıcısının yapmayı deneyin `GenerateDBDirectMethods` özelliğini `true` içinden [veri kümesi Tasarımcısı](../data-tools/creating-and-editing-typed-datasets.md) ve veri kümesini TableAdapter yeniden kaydedin. TableAdapter hala yoksa bir `Update` yönteminin muhtemelen sütun değerleri, sonra tabloya alan arasında bireysel satırları ayırt etmek için yeterli şema bilgileri sağlamaz (örneğin, birincil anahtarı olmayan tablo üzerinde ayarlanır).  
  
## <a name="update-existing-records-using-tableadapters"></a>TableAdapter kullanarak mevcut kayıtları güncelleştirme  
 TableAdapters uygulamanızın gereksinimlerine bağlı olarak veritabanındaki kayıtları güncelleştirmek için farklı yollar sunar.  
  
 Uygulama verilerini depolamak için veri kümelerini kullanan sonra istediğiniz kayıtları yalnızca güncelleştirebilir <xref:System.Data.DataTable> ve sonra çağrı `TableAdapter.Update` yöntemi ve öğesinden birini geçirin <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, veya dizi <xref:System.Data.DataRow>s. Yukarıdaki tabloda farklı açıklar `Update` yöntemleri.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Veri kümesi, DataTable, DataRow veya DataRows() alan TableAdapter.Update yöntemi veritabanındaki kayıtları güncelleştirmek için  
  
1. Düzenlemek istediğiniz kayıtları <xref:System.Data.DataTable> doğrudan düzenleyerek <xref:System.Data.DataRow> içinde <xref:System.Data.DataTable>. Daha fazla bilgi için [nasıl yapılır: bir DataTable tablosundaki satırları düzenleme](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2. Satırları dalda düzenlendi sonra <xref:System.Data.DataTable>, çağrı `TableAdapter.Update` yöntemi. Tüm geçirerek ya da güncelleştirmek için veri miktarını denetleyebilirsiniz <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, bir dizi <xref:System.Data.DataRow>s ya da tek bir <xref:System.Data.DataRow>.  
  
    Aşağıdaki kod, bir kaydı düzenlemek gösterilmiştir bir <xref:System.Data.DataTable> ve sonra çağrı `TableAdapter.Update` değişiklikleri veritabanına kaydetmek için yöntemi. (Bu örnekte, Northwind veritabanı bölge tablosu kullanılır.)  
  
    [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
    [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
   Uygulamanız, uygulamanızda verileri depolamak için nesneleri kullanıyorsa, TableAdapter bağdaştırıcısının kullanabileceğiniz `DBDirect` veri, nesneleri doğrudan veritabanına göndermek için yöntemleri. Bu yöntemlerin her bir sütunun değerlerini ayrı ayrı yöntem parametre olarak geçirmenize izin verin. Bu yöntemin çağrılması metodun Metoda geçilen sütun değerleri veritabanında varolan bir kaydı güncelleştirir.  
  
   Aşağıdaki yordam, Northwind kullanır `Region` örnek olarak bir tablo.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Sütun değerleri alır TableAdapter.Update yöntemini kullanarak bir veritabanındaki kayıtları güncelleştirmek için  
  
-   TableAdapter bağdaştırıcısının çağrı `Update` yöntemi, yeni ve orijinal değerleri her sütun için parametre olarak geçirerek.  
  
    > [!NOTE]
    >  Kullanmak istediğiniz TableAdapter kullanılabilir bir örnek yoksa örneği.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Komut nesneleri kullanarak kayıtları güncelleştirme  
 Aşağıdaki örnek komut nesneleri kullanarak bir veritabanına doğrudan mevcut kayıtları güncelleştirir. Komutlar ve saklı yordamları çalıştırmak için komut nesneleri kullanma hakkında daha fazla bilgi için bkz. [uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md).  
  
 Aşağıdaki yordam, Northwind kullanır `Region` örnek olarak bir tablo.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Komut nesneleri kullanarak bir veritabanında var olan kayıtların güncelleştirmek için  
  
-   Yeni bir komut nesnesi oluşturma ayarlama, `Connection`, `CommandType`, ve `CommandText` özellikler; ve bir bağlantı açıp komutu yürütün.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 İstenen tablodaki kayıtları güncelleştirmek için izinleri yanı sıra, bağlanmaya çalıştığınız veritabanı erişimi olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Nasıl yapılır: veritabanındaki kayıtları silme](../data-tools/how-to-delete-records-in-a-database.md)   
 [Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)   
 [Verileri bir nesneden veritabanına kaydetme](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Veri uygulamaları Visual Studio'da genel bakış](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)