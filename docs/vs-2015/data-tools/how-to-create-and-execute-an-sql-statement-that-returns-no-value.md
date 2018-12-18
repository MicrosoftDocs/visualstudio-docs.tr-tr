---
title: 'Nasıl yapılır: değer döndürmeyen bir SQL ifadesi oluşturma ve yürütme | Microsoft Docs'
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1768db097d2555726b17862c9c4a4b82a3e2a6a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188610"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>Nasıl yapılır: Hiçbir Değer Döndürmeyen bir SQL İfadesi Oluşturma ve Yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Değer döndürmeyen bir SQL deyimi yürütmek için bir SQL deyimini çalıştırmak için yapılandırılmış bir TableAdapter sorgu çalıştırabilirsiniz (örneğin, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Uygulamanızı TableAdapter'ları kullanmazsa, çağrı `ExecuteNonQuery` ayarı, bir komut nesnesi üzerinde yöntemi, `CommandType` özelliğini <xref:System.Data.CommandType>. ("Komut nesnesi", belirli bir komut için başvurduğu [.NET Framework veri sağlayıcısı](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) uygulamanızı kullanarak. For example, uygulamanızı SQL Server için .NET Framework veri sağlayıcısı kullanarak, komut nesnesi olması <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Aşağıdaki örnekler, iki TableAdapter'ı kullanarak bir veritabanından herhangi bir değer döndüren SQL deyimleri yürütmek ya da nesneleri komut gösterilmektedir. TableAdapter'ları ve komutları ile sorgulama hakkında daha fazla bilgi için bkz: [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>Bir TableAdapter kullanarak değer döndürmeyen bir SQL deyimleri çalıştırma  
 Bu örnekte, TableAdapter kullanarak sorgu oluşturma işlemi gösterilmektedir [TableAdapters düzenleme](../data-tools/editing-tableadapters.md), ve ardından TableAdapter'ın bir örneği bildirin ve sorguyu hakkında bilgi sağlar.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>Bir TableAdapter kullanarak değer döndürmeyen bir SQL deyimi oluşturmak için  
  
1.  Bir veri kümesini açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Zaten bir yoksa, bir TableAdapter'ı oluşturun. TableAdapters oluşturma hakkında daha fazla bilgi için bkz. [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Değer döndürmeyen bir SQL deyimi kullanır, TableAdapter bağdaştırıcısında bir sorgu zaten varsa, sonra "TableAdapter'ın bir örneği bildirmek ve sorguyu yürütmek için." adlı sonraki yordama için atlayın Aksi takdirde, hiçbir değer döndüren yeni bir sorgu oluşturmak için 4. adım ile devam edin.  
  
4.  İstediğiniz TableAdapter'ı sağ tıklayın ve bir sorgu eklemek için kısayol menüsünü kullanın.  
  
     **TableAdapter sorgu Yapılandırma Sihirbazı'nı** açılır.  
  
5.  Varsayılan değerini bırakın **SQL deyimi kullan**ve ardından **sonraki**.  
  
6.  Seçin **güncelleştirme**, **Ekle** veya **Sil** seçeneğini ve ardından **sonraki**.  
  
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
        >  TableAdapters içinde kendi ilişkili bir veri kümesi sınıfları bulunmayan. Her bir veri kümesi, TableAdapter kendi ad alanındaki karşılık gelen koleksiyonu vardır. Örneğin, adlı bir veri kümeniz `SalesDataSet`, olacaktır bir `SalesDataSetTableAdapters` , TableAdapter'ları içeren ad alanı.  
  
2.  Kodda herhangi bir yöntemini çağıracak şekilde sorgunuzu çağırın. Sorgunuz, TableAdapter üzerindeki bir yöntemdir. Aşağıdaki kod, TableAdapter ve sorgu adlarıyla değiştirin. Ayrıca, sorgu için gerekli tüm parametreleri geçirmek gerekir. Sorgunuzu parametre gerektiriyorsa, emin değilseniz veya gerektiriyorsa, parametreleri sorgu için gerekli imza sonra IntelliSense denetleyin. Olup, sorgu parametreleri veya alan bağlı olarak, kod aşağıdaki örneklerden birini benzer görünür:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Herhangi bir değer döndüren olarak düşünüyoruz sorguları aslında bir değer döndürür; sorgu tarafından etkilenen satır sayısını içeren bir tamsayı. Bir TableAdapter örneğini bildirme ve bir sorgu yürütme için tam kodu aşağıdakine benzer görünmelidir:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>Komut nesnesi kullanarak herhangi bir değer döndüren SQL deyimleri çalıştırma  
 Aşağıdaki örnek, bir komut oluşturun ve değer döndürmeyen bir SQL deyimi yürütme gösterilmektedir. Bir komut için parametre değerlerini alma ve ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: ayarlama ve alma parametreleri komut nesneleri için](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Bu örnekte <xref:System.Data.SqlClient.SqlCommand> nesne ve gerektirir:  
  
-   Başvurular <xref:System>, <xref:System.Data>, ve <xref:System.Xml> ad alanları.  
  
-   Adlı bir veri bağlantısı `SqlConnection1`.  
  
-   Adlı bir tablo `Customers` verileri kaynağı `SqlConnection1` bağlanır. (Aksi takdirde, geçerli bir SQL deyimi veri kaynağınız için gerekir).  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>Bir DataCommand kullanarak değer döndürmeyen bir SQL deyimi yürütmek için  
  
-   SQL deyiminden yürütmek istediğiniz bir yönteme aşağıdaki kodu ekleyin. Çağrı `ExecuteNonQuery` hiçbir değer döndürmek için bir komutu yöntemi (örneğin, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulama, veritabanına erişir ve SQL deyimi yürütme izni gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md)   
 [Nasıl yapılır: TableAdapter sorgularını düzenleme](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Nasıl yapılır: bir veri kümesi ile veri doldurun](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [TableAdapters'ı kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Nasıl yapılır: parametre ayarlama ve alma için komut nesneleri](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)