---
title: TableAdapter genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fb5ebcdaa1bebe67c2fb8e378c7345467dd10b78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269054"
---
# <a name="tableadapter-overview"></a>TableAdapter Genel Bakışı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter veritabanına bağlanmak, sorguları veya saklı yordamları çalıştırmak ve döndürülen verilerle kendi DataTable Doldur, tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapter ayrıca uygulamanızdan veritabanına güncelleştirilmiş veriler göndermek için de kullanılır. TableAdapter bağdaştırıcısının ilişkili olduğu tablosunun şemasına uyan veriler döndürmeleri sürece, TableAdapter bağdaştırıcısında istediğiniz sayıda sorgunuz olabilir. Aşağıdaki diyagramda, TableAdapter'ları ile veritabanları ve diğer nesneleri bellekte nasıl etkileşim kurduğu gösterilmektedir:  
  
 ![Bir istemci uygulama, veri akışında](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 TableAdapter'ları ile tasarlandığında **veri kümesi Tasarımcısı**, oluşturulan TableAdapter sınıfları, iç içe sınıfları olarak oluşturulmaz <xref:System.Data.DataSet>. Bunlar her veri kümesine özgü ayrı bir isim uzayında bulunur. Örneğin, `NorthwindDataSet` adında bir veri kümeniz varsa <xref:System.Data.DataTable> veri kümesinin içindeki `NorthwindDataSet` tablolarıyla ilişkilendirilen TableAdapter bağdaştırıcıları `NorthwindDataSetTableAdapters` isim uzayında olacaktır. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örneğin:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>İlişkili DataTable Şeması  
 Bir TableAdapter oluştururken TableAdapter bağdaştırıcısının ilişkili <xref:System.Data.DataTable> şemasını tanımlamak için başlangıç sorgusu veya saklı yordamı kullanılır. TableAdapter bağdaştırıcısının çağırarak bu başlangıç sorgusunu veya saklı yordam yürütme `Fill` yöntemi (tablosu doldurulur ilişkili <xref:System.Data.DataTable>). TableAdapter bağdaştırıcısının ana sorgusunda yapılan değişiklikler ilişkili veri tablosunun şemasına yansıtılır. Örneğin, ana sorgudan bir sütun kaldırılması ilişkili veri tablosundan da sütunu kaldırır. TableAdapter üzerindeki ek sorgular ana sorguda bulunmayan sütunları döndüren SQL deyimleri kullanırsa, tasarımcı ana sorgu ve ek sorgular arasındaki sütun değişikliklerini eşitlemeye çalışır. Daha fazla bilgi için [nasıl yapılır: Edit TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>TableAdapter Güncelleştirme Komutları  
 TableAdapter bağdaştırıcısının güncelleştirme işlevleri TableAdapter Sihirbazı'nda sağlanan ana sorguda ne kadar bilgi olduğuna bağlıdır. Örneğin, değerleri birden çok tablodan (JOIN), skalar değerden veya görünümden ya da toplu işlevlerin sonuçlarından alacak şekilde yapılandırılan TableAdapter bağdaştırıcıları, başlangıçta güncelleştirmeleri temel alınan veritabanına geri gönderebilme özelliğiyle oluşturulmaz. Ancak INSERT, UPDATE ve DELETE komutlarını el ile yapılandırabilirsiniz **özellikleri** penceresi.  
  
## <a name="tableadapter-queries"></a>TableAdapter Sorguları  
 ![TableAdapter ile birden çok sorgu](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapter'ları, ilişkili olduğu veri tablolarını doldurmak için birden çok sorgu bulunabilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu, farklı ölçütleri karşılayan verilerin yüklenmesini sağlar. Örneğin, uygulamanızda müşteri tablosu varsa tabloyu adı belli bir harfle başlayan müşterilerle dolduran bir sorgu ve tabloyu aynı bölgede bulunan müşterilerle dolduran başka bir sorgu oluşturabilirsiniz. `Customers` tablosunu belirli bir bölgede bulunan müşterilerle doldurmak için bölge değerinin parametresini alan bir `FillByState` sorgusu oluşturabilirsiniz: `SELECT * FROM Customers WHERE State = @State`. `FillByState` yöntemini çağırarak sorguyu çalıştırır ve parametre değerini şu şekilde geçirirsiniz: `CustomerTableAdapter.FillByState("WA")`. Daha fazla bilgi için [nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md).  
  
 TableAdapter bağdaştırıcısının veri tablosuyla aynı şemaya ait verileri döndüren sorguların yanı sıra skalar (tek) değerler döndüren sorgular da ekleyebilirsiniz. Örneğin, müşterilerin sayısını döndüren bir sorgu oluşturulduğunda (`SELECT Count(*) From Customers`) döndürülen veriler tablonun şemasına uygun olmasa da `CustomersTableAdapter` için geçerlidir.  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill Özelliği  
 Varsayılan olarak, TableAdapter bağdaştırıcısının veri tablosunu doldurmak için her sorgu çalıştırmanızda veriler temizlenir ve yalnızca söz konusu sorgunun sonuçları tabloya yüklenir. Bir sorgudan döndürülen verileri veri tablosundaki verilere eklemek veya bu verilerle birleştirmek istiyorsanız, TableAdapter bağdaştırıcısının `ClearBeforeFill` özelliğini `false` olarak ayarlayın. Verileri temizleyip temizlemediğinizden bağımsız olarak, isteniyorsa güncelleştirmeleri açıkça veritabanına geri göndermeniz gerekir. Bu nedenle, tabloyu dolduran başka bir sorgu çalıştırmadan önce tabloda yapılan değişiklikleri kaydetmeyi unutmayın. Daha fazla bilgi için [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>TableAdapter Devralması  
 TableAdapter bağdaştırıcısının içinde yapılandırılmış bir <xref:System.Data.Common.DataAdapter> bulunduğundan standart veri bağdaştırıcılardan daha geniş bir işlevselliğe sahiptir. Varsayılan olarak, TableAdapter <xref:System.ComponentModel.Component> özelliklerini devralır ve <xref:System.Data.Common.DataAdapter> sınıfına atanamaz. TableAdapter bağdaştırıcısının bir <xref:System.Data.Common.DataAdapter> bağdaştırıcısına atanması <xref:System.InvalidCastException> durumuyla sonuçlanır. TableAdapter bağdaştırıcısının temel sınıfını değiştirmek için türetilen bir sınıf yazabilirsiniz <xref:System.ComponentModel.Component> içinde **temel sınıf** Özellik Düzenleyici içindeki TableAdapter'ın **veri kümesi Tasarımcısı**.  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter Yöntemleri ve Özellikleri  
 TableAdapter sınıfı değil parçası [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], ve bu nedenle, bu belgelerinde arama olamaz veya **Nesne Tarayıcısı**. Yukarıda belirtilen sihirbazlardan birini kullandığınızda, tasarım sırasında oluşturulur. Bir TableAdapter oluşturduğunuzda kendisine ad atanırken çalıştığınız tablonun adı temel alınır. Örneğin, `Orders` adındaki veritabanında bulunan bir tabloyu temel alan bir TableAdapter oluşturduğunuzda TableAdapter `OrdersTableAdapter` olarak adlandırılır. TableAdapter bağdaştırıcısının sınıf adı kullanılarak değiştirilebilir. **adı** özelliğinde **veri kümesi Tasarımcısı**.  
  
 Aşağıdaki yaygın olarak kullanılan TableAdapter yöntemleri ve özellikleri verilmiştir:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`TableAdapter.Fill`|TableAdapter bağdaştırıcısının ilişkili veri tablosunu TableAdapter'ın SELECT komutunun sonuçlarıyla doldurur. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini verilerle doldurmak](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını gösteren bir tamsayı döndürür. Daha fazla bilgi için [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Veri ile doldurulan yeni bir <xref:System.Data.DataTable> döndürür.|  
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için [nasıl yapılır: bir DataTable Add Rows](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|  
  
## <a name="tableadapter-update-method"></a>TableAdapter Güncelleştirme Yöntemi  
 TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. İlişkili veri tablosunun şemasının yanı sıra `Fill` yöntemiyle ilişkili `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutlarını oluşturmak için TableAdapter bağdaştırıcısının başlangıç `TableAdapter.Update` (ana) sorgusu kullanır. Bu, TableAdapter bağdaştırıcısının çağırma anlamına gelir `Update` yöntemi, TableAdapter bağdaştırıcısının özgün yapılandırmasında ve ile eklenen ilave sorgulardan birinin değil, oluşturulan deyimleri yürütür **TableAdapter sorgu Yapılandırma Sihirbazı'nı**.  
  
 Bir TableAdapter kullandığınızda, aynı işlemleri genelde uyguladığınız komutlarla etkin bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının `Fill` yöntemini çağırdığınızda, bağdaştırıcı veri komutunu `SelectCommand` özelliğinde çalıştırır ve sonuç kümesini veri tablosuna yüklemek için bir veri okuyucu (örneğin, <xref:System.Data.SqlClient.SqlDataReader>) kullanır. Benzer şekilde, bağdaştırıcının `Update` yöntemini çağırdığınızda, veri tablosundaki değiştirilen her kayıt için ilgili komutu (`UpdateCommand`, `InsertCommand` ve `DeleteCommand` özelliklerinde) çalıştırır.  
  
> [!NOTE]
>  Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter bağdaştırıcısının ana sorgusunda tek bir tablo SELECT deyiminden daha fazlası varsa, tasarımcının `InsertCommand`, `UpdateCommand` ve `DeleteCommand` oluşturması mümkün olmayabilir. Bu komutlar oluşturulmazsa `TableAdapter.Update` yöntemini çalıştırırken hata alabilirsiniz.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği  
 TableAdapter `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutlarına ek olarak doğrudan veritabanında yürütülebilecek yöntemlerle oluşturulur. Bu yöntemler (`TableAdapter.Insert`, `TableAdapter.Update` ve `TableAdapter.Delete`) veritabanındaki verileri işlemek için doğrudan çağrılabilir. Bu, ilişkili veri tablosu için bekletilen ekleme, güncelleştirme ve silme işlemlerini yapmak üzere TableAdapter.Update yöntemini çağırmak yerine bu yöntemleri kodunuzda tek tek çağırabilmeniz anlamına gelir.  
  
 Bu doğrudan yöntemleri oluşturmak istemiyorsanız TableAdapter bağdaştırıcısının ayarlamak **GenerateDbDirectMethods** özelliğini `false` (içinde **özellikleri** pencere). TableAdapter bağdaştırıcısına eklenen ilave sorgular tek başına sorgulardır; bu yöntemleri oluşturmazlar.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Boş Değer Atanabilir Türler İçin TableAdapter Desteği  
 TableAdapter boş değer atanabilir türleri (`Nullable(Of T)` ve `T?`) destekler. Visual Basic'te boş değer atanabilir türler hakkında daha fazla bilgi için bkz. [boş değer atanabilir değer türleri](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). C# dilinde boş değer atanabilir türler hakkında daha fazla bilgi için bkz. [kullanarak boş değer atanabilir türler](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [İzlenecek yol: (Windows Forms) bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)