---
title: 'Nasıl yapılır: tek bir değer döndüren bir SQL ifadesi oluşturma ve yürütme | Microsoft Docs'
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
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7d5d57637a25db62832ad535bbad60214a0aa4ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192159"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Nasıl yapılır: Tek Bir Değer Döndüren bir SQL İfadesi Oluşturma ve Yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tek bir değer döndüren bir SQL deyimi yürütmek için bir SQL deyimini çalıştırmak için yapılandırılmış bir TableAdapter sorgu çalıştırabilirsiniz (örneğin, `CustomersTableAdapter.CustomerCount()`).  
  
 Uygulamanızı TableAdapter'ları kullanmazsa, çağrı `ExecuteScalar` ayarı, bir komut nesnesi üzerinde yöntemi, `CommandType` özelliğini <xref:System.Data.CommandType>. ("Komut nesnesi", belirli bir komut için başvurduğu [.NET Framework veri sağlayıcısı](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) uygulamanızı kullanarak. For example, uygulamanızı SQL Server için .NET Framework veri sağlayıcısı kullanarak, komut nesnesi olması <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Aşağıdaki örnekler, iki TableAdapter'ı kullanarak bir veritabanından tek değer döndüren SQL deyimleri yürütmek ya da nesneleri komut gösterilmektedir. TableAdapter'ları ve komutları ile sorgulama hakkında daha fazla bilgi için bkz: [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>Bir TableAdapter kullanarak tek değer döndüren SQL deyimleri çalıştırma  
 Bu örnekte, TableAdapter kullanarak sorgu oluşturma işlemi gösterilmektedir [TableAdapters düzenleme](../data-tools/editing-tableadapters.md), ve ardından TableAdapter'ın bir örneği bildirin ve sorguyu hakkında bilgi sağlar.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Bir TableAdapter kullanarak tek bir değer döndüren bir SQL deyimi oluşturmak için  
  
1.  Bir veri kümesini açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Zaten bir yoksa, bir TableAdapter'ı oluşturun. TableAdapters oluşturma hakkında daha fazla bilgi için bkz. [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Tek bir değer döndürmek için bir SQL deyimi kullanır, TableAdapter bağdaştırıcısında bir sorgu zaten varsa, sonra "TableAdapter'ın bir örneği bildirmek ve sorguyu yürütmek için." adlı sonraki yordama için atlayın Aksi takdirde, tek bir değer döndüren yeni bir sorgu oluşturmak için 4. adım ile devam edin.  
  
4.  İstediğiniz TableAdapter'ı sağ tıklayın ve bir sorgu eklemek için kısayol menüsünü kullanın.  
  
     **TableAdapter sorgu Yapılandırma Sihirbazı'nı** açılır.  
  
5.  Varsayılan değerini bırakın **SQL deyimi kullan**ve ardından **sonraki**.  
  
6.  Seçin **, tek bir değer döndüren SELECT** seçeneğini ve ardından **sonraki**.  
  
7.  SQL deyiminizi yazın veya **Sorgu Oluşturucu** oluşturma ile yardımcı ve ardından **sonraki**.  
  
8.  Sorgu için bir ad sağlayın.  
  
9. Sihirbazı tamamlayın; TableAdapter sorgu eklenir.  
  
10. Projenizi yapılandırın.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>TableAdapter'ın bir örneği bildirmek ve sorguyu yürütmek için  
  
1.  Yürütmek istediğiniz sorguyu içeren TableAdapter'ın bir örneği bildirin.  
  
    -   Tasarım zamanı araçlarını kullanarak örneği oluşturmak için istediğiniz TableAdapter sürükleyin **araç kutusu**. (Projenizdeki bileşenleri artık görünür **araç kutusu** projenizin adına eşleşen bir başlık altında.) TableAdapter içinde görünmüyorsa, **araç kutusu**, projenizi oluşturmanız gerekebilir.  
  
         veya  
  
    -   Kodda bir örnek oluşturmak için aşağıdaki kodu adlarıyla değiştirin, <xref:System.Data.DataSet> ve TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters içinde kendi ilişkili bir veri kümesi sınıfları bulunmayan. Her bir veri kümesi, TableAdapter kendi ad alanındaki karşılık gelen koleksiyonu vardır. Örneğin, adlı bir veri kümeniz `SalesDataSet`, olacaktır sonra bir `SalesDataSetTableAdapters` , TableAdapter'ları içeren ad alanı.  
  
2.  Kodda herhangi bir yöntemini çağıracak şekilde sorgunuzu çağırın. Sorgunuz, TableAdapter üzerindeki bir yöntemdir. Aşağıdaki kod, TableAdapter ve sorgu adlarıyla değiştirin. Ayrıca, sorgu için gerekli tüm parametreleri geçirmek ve dönüş değeri ile bir şey gerekir (örneğin, bir değişkene atayın). Sorgunuzu parametre gerektiriyorsa, emin değilseniz veya gerektiriyorsa, parametreleri sorgu için gerekli imza sonra IntelliSense denetleyin. Olup, sorgu parametreleri veya alan bağlı olarak, kod aşağıdaki örneklerden birini benzer görünür:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Büyük olasılıkla bir değişkene sorgu tarafından döndürülen değer atamak gerekir. Tek bir değer döndürmesi TableAdapter sorguları dönüş sorguya dayalı bir veri türü (başlangıcı yerine sonundan `ExecuteScalar` yöntemi bir nesne döndürür). Örneğin, TableAdapter sorgunuzu tamsayı veri türü olan tek bir sütun seçerse, sorgunun dönüş değeri bir tamsayı olduğu. Sütun null değerlere izin verir, dönüş değeri, boş değer atanabilir türler biridir (örneğin, `Nullable(Of Integer)`). Boş değer atanabilir türler hakkında daha fazla bilgi için bkz. <xref:System.Nullable>. Bir TableAdapter örneğini bildirme ve bir sorgu yürütme için tam kodu aşağıdakine benzer olmalıdır (Bu örnekte, dönüş varsayılmaktadır. bir tamsayı değerdir; kodunuzu sorgunuz tarafından döndürülen veri türüne göre ayarlayın):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>Komut nesnesi kullanarak tek değer döndüren SQL deyimleri çalıştırma  
 Aşağıdaki örnek, bir komut oluşturun ve tek bir değer döndüren bir SQL deyimi yürütme gösterilmektedir. Bir komut için parametre değerlerini alma ve ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: ayarlama ve alma parametreleri komut nesneleri için](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Bu örnekte <xref:System.Data.SqlClient.SqlCommand> nesne ve gerektirir:  
  
-   Başvurular <xref:System>, <xref:System.Data>, ve <xref:System.Xml> ad alanları.  
  
-   Adlı bir veri bağlantısı `SqlConnection1`.  
  
-   Adlı bir tablo `Customers` verileri kaynağı `SqlConnection1` bağlanır. (Aksi takdirde, geçerli bir SQL deyimi veri kaynağınız için gerekir).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>Bir DataCommand kullanarak tek bir değer döndüren bir SQL deyimi yürütmek için  
  
-   Kod yürütmek istediğiniz bir yönteme aşağıdaki kodu ekleyin. Çağrı yaparak tek bir değer döndürmesi `ExecuteScalar` komut yöntemi (örneğin, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Veriler içerisinde geri dönmemiş ise bir <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulama, veritabanına erişir ve SQL deyimi yürütme izni gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md)   
 [Nasıl yapılır: TableAdapter sorgularını düzenleme](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Nasıl yapılır: bir veri kümesi ile veri doldurun](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [TableAdapters'ı kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Nasıl yapılır: parametre ayarlama ve alma için komut nesneleri](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)