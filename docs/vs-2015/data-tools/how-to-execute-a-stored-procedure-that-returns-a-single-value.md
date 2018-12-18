---
title: 'Nasıl yapılır: tek bir değer döndüren bir saklı yordamı yürütme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandType.StoredProcedure
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- ExecuteReader method example [Visual Basic]
- stored procedures, examples
- stored procedures, executing
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2c27c8e0fca1393e097f1244a01988052911f73a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281014"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-a-single-value"></a>Nasıl yapılır: Tek Bir Değer Döndüren Bir Saklı Yordamı Yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tek bir değer döndüren bir saklı yordamı yürütmek için bir saklı yordam çalıştırmak için yapılandırılan TableAdapter sorgu çalıştırabilirsiniz (örneğin, `CustomersTableAdapter.CustomerCount()`).  
  
 Uygulamanızı TableAdapter'ları kullanmazsa, çağrı `ExecuteScalar` ayarı, bir komut nesnesi üzerinde yöntemi, `CommandType` özelliğini <xref:System.Data.CommandType>. ("Komut nesnesi", belirli bir komut için başvurduğu [.NET Framework veri sağlayıcısı](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) uygulamanızı kullanarak. For example, uygulamanızı SQL Server için .NET Framework veri sağlayıcısı kullanarak, komut nesnesi olması <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Aşağıdaki örnekler, iki TableAdapter'ı kullanarak bir veritabanından tek değer döndüren saklı yordamları yürütme veya nesneleri komut gösterilmektedir. TableAdapter'ları ve komutları ile sorgulama hakkında daha fazla bilgi için bkz: [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-tableadapter"></a>Depolanmış bir TableAdapter kullanarak tek bir değer yordamları çalıştırma  
 Bu örnekte, TableAdapter kullanarak sorgu oluşturma işlemi gösterilmektedir [TableAdapters düzenleme](../data-tools/editing-tableadapters.md), ve ardından TableAdapter'ın bir örneği bildirin ve sorguyu hakkında bilgi sağlar.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-tableadapter"></a>Bir TableAdapter kullanarak tek bir değer döndüren bir saklı yordamı yürütmek için  
  
1.  Bir veri kümesini açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Zaten bir yoksa, bir TableAdapter'ı oluşturun. TableAdapters oluşturma hakkında daha fazla bilgi için bkz. [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Tek bir değer döndürmek için bir saklı yordam kullanır, TableAdapter bağdaştırıcısında bir sorguya zaten sahip, "TableAdapter'ın bir örneği bildirmek ve sorguyu yürütmek için." adlı sonraki yordama için atlayın. Aksi takdirde, tek bir değer döndüren yeni bir sorgu oluşturmak için 4. adım ile devam edin.  
  
4.  İstediğiniz TableAdapter'ı sağ tıklayın ve bir sorgu eklemek için kısayol menüsünü kullanın.  
  
     **TableAdapter sorgu Yapılandırma Sihirbazı'nı** açılır.  
  
5.  Seçin **varolan bir saklı yordam kullanmak**ve ardından **sonraki**.  
  
6.  Aşağı açılan listeden bir saklı yordam seçin ve ardından **sonraki**.  
  
7.  Döndürülecek seçeneğini **tek bir değer**ve ardından **sonraki**.  
  
8.  Sorgu için bir ad sağlayın.  
  
9. Tıklayın **sonraki** veya **son** ; Sihirbazı tamamlamak için sorgu Tableadapter'a eklenir.  
  
10. Projenizi yapılandırın.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>TableAdapter'ın bir örneği bildirmek ve sorguyu yürütmek için  
  
1.  Yürütmek istediğiniz sorguyu içeren TableAdapter'ın bir örneği bildirin.  
  
    -   Tasarım zamanı araçlarını kullanarak örneği oluşturmak için istediğiniz TableAdapter sürükleyin **araç kutusu**. (Projenizdeki bileşenleri artık görünür **araç kutusu** projenizin adına eşleşen bir başlık altında.) TableAdapter içinde görünmüyorsa, **araç kutusu**, projenizi oluşturmanız gerekebilir.  
  
         veya  
  
    -   Kodda bir örnek oluşturmak için aşağıdaki kodu adlarıyla değiştirin, <xref:System.Data.DataSet> ve TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters içinde kendi ilişkili bir veri kümesi sınıfları bulunmayan. Her bir veri kümesi, TableAdapter kendi ad alanındaki karşılık gelen koleksiyonu vardır. Örneğin, adlı bir veri kümeniz `SalesDataSet`, olacaktır bir `SalesDataSetTableAdapters` , TableAdapter'ları içeren ad alanı.  
  
2.  Kodda herhangi bir yöntemini çağıracak şekilde sorgunuzu çağırın. Sorgunuz, TableAdapter üzerindeki bir yöntemdir. Aşağıdaki kod, TableAdapter ve sorgu adlarıyla değiştirin. Sorgunuz tarafından gerekli tüm parametreleri geçirmek gerekir. Sorgunuzu parametre gerektiriyorsa, emin değilseniz veya gerektiriyorsa, parametreleri sorgu için gerekli imza sonra IntelliSense denetleyin. Olup, sorgu parametreleri veya alan bağlı olarak, kod aşağıdaki örneklerden birini benzer görünür:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     TableAdapter'ın bir örneği bildirmek ve sorguyu yürütmek için tam kod aşağıdaki gibi görünmelidir:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-command-object"></a>Saklı olan komut nesnesini kullanarak tek bir değer yordamları çalıştırma  
 Aşağıdaki örnek, bir komut oluşturun ve tek bir değer döndüren bir saklı yordamı yürütmek gösterilmektedir. Bir komut için parametre değerlerini alma ve ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: ayarlama ve alma parametreleri komut nesneleri için](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Bu örnekte <xref:System.Data.SqlClient.SqlCommand> nesne ve gerektirir:  
  
-   Başvurular <xref:System>, <xref:System.Data>, ve <xref:System.Xml> ad alanları.  
  
-   Adlı bir veri bağlantısı `SqlConnection1`.  
  
-   Adlı bir tablo `Customers` verileri kaynağı `SqlConnection1` bağlanır. (Aksi takdirde, geçerli bir SQL deyimi veri kaynağınız için gerekir).  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-datacommand"></a>Bir DataCommand kullanarak tek bir değer döndüren bir saklı yordamı yürütmek için  
  
-   Kod yürütmek istediğiniz bir yönteme aşağıdaki kodu ekleyin. Çağrı yaparak tek bir değer döndürmek `ExecuteScalar` komut yöntemi (örneğin, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Veriler içerisinde geri dönmemiş ise bir `object`.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#14)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#14)]  
  
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