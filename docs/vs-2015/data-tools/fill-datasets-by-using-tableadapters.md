---
title: TableAdapters'ı kullanarak veri kümelerini doldurma | Microsoft Docs
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
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 118b8165b4c5ad972aacf9a3d91cff78c1b776e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251857"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapters'ı kullanarak veri kümelerini doldurma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir TableAdapter bileşeni, bir veri kümesi bir veya daha fazla sorguları veya belirttiğiniz saklı yordamlar göre veritabanındaki verilerle doldurur. TableAdapter'ları da gerçekleştirebilirsiniz ekler, güncelleştirir ve veri kümesine yaptığınız değişiklikleri kalıcı hale getirmek için veritabanında siler. Ayrıca, belirli bir tabloya ilişkisiz genel komutları da verebilir.  
  
> [!NOTE]
>  TableAdapter bağdaştırıcılarını Visual Studio tasarımcılar tarafından oluşturulur. Veri kümeleri programlı olarak oluşturuyorsanız, bir .NET Framework sınıf olan DataAdapter'ni kullanın.  
  
 TableAdapter işlemleri hakkında ayrıntılı bilgi için doğrudan aşağıdaki konulardan birine atlayabilirsiniz:  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|Tableadapter'lar oluşturma ve yapılandırma için tasarımcılar kullanma|  
|[Parametreleştirilmiş TableAdapter sorguları oluşturma](../data-tools/create-parameterized-tableadapter-queries.md)|Kullanıcılara, TableAdapter yordamları ya da sorguları bağımsız değişkenleri tanıma|  
|[Bir TableAdapter ile veritabanına doğrudan erişme](../data-tools/directly-access-the-database-with-a-tableadapter.md)|TableAdapter Dbdirect yöntemleri kullanma|  
|[Bir veri kümesini doldururken kısıtlamaları kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Verileri güncelleştirirken yabancı anahtar kısıtlamaları ile çalışma|  
|[Bir TableAdapter işlevini genişletme](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapter bağdaştırıcıları için özel kod ekleme|  
|[Bir veri kümesinin içine XML verileri okuma](../data-tools/read-xml-data-into-a-dataset.md)|XML ile çalışma|  
  
## <a name="tableadapters-overview"></a>TableAdapter’lara genel bakış  
 TableAdapter'ları, bir veritabanına, çalışma sorguları veya saklı yordamları bağlanın ve döndürülen verilerle kendi DataTable Doldur tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapter ayrıca uygulamanızdan veritabanına güncelleştirilmiş veriler göndermek. TableAdapter bağdaştırıcısının ilişkili olduğu tablosunun şemasına uyan veriler döndürmeleri sürece, TableAdapter bağdaştırıcısında istediğiniz sayıda sorgunuz çalıştırabilirsiniz. Aşağıdaki diyagramda, TableAdapter'ları ile veritabanları ve diğer nesneleri bellekte nasıl etkileşim kurduğu gösterilmektedir:  
  
 ![Bir istemci uygulama, veri akışında](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 TableAdapter'ları ile tasarlandığında **veri kümesi Tasarımcısı**, TableAdapter sınıfları, iç içe sınıfları olarak oluşturulmaz <xref:System.Data.DataSet>. Bunlar, her veri kümesine özgü ayrı ad alanlarında bulunur. Örneğin adlı bir veri kümeniz, `NorthwindDataSet`, ilişkili TableAdapter'ları <xref:System.Data.DataTable>s'te `NorthwindDataSet` uzayında olacaktır `NorthwindDataSetTableAdapters` ad alanı. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örneğin:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>İlişkili DataTable şeması  
 Bir TableAdapter oluşturduğunuzda, ilk sorgu kullanın veya saklı yordamı TableAdapter şemasını tanımlamak için ilişkili zaman <xref:System.Data.DataTable>. Bu başlangıç sorgusunu çalıştırın veya saklı yordamı TableAdapter bağdaştırıcısının çağırarak `Fill` yöntemi (tablosu doldurulur ilişkili <xref:System.Data.DataTable>). TableAdapter bağdaştırıcısının ana sorgusunda yapılan değişiklikler ilişkili veri tablosunun şemada yansıtılır. Örneğin, ana sorgudan bir sütun kaldırılması da sütunu ilişkili veri tablosundan kaldırır. TableAdapter üzerindeki ek sorgular ana sorguda bulunmayan sütunları döndüren SQL deyimleri kullanıyorsanız, Tasarımcı ana sorgu ve ek sorgular arasındaki sütun değişikliklerini eşitlemeye çalışır. Daha fazla bilgi için [nasıl yapılır: Edit TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>TableAdapter güncelleştirme komutları  
 TableAdapter bağdaştırıcısının güncelleştirme işlevleri TableAdapter Sihirbazı'nı ana sorgusunda kullanılabilir ne kadar bilgi olduğuna bağlıdır. Örneğin, değerleri birden çok tablodan (JOIN), skalar değerden veya görünümden ya da toplu işlevlerin sonuçlarından alacak şekilde yapılandırılan TableAdapter bağdaştırıcıları, başlangıçta güncelleştirmeleri temel alınan veritabanına geri gönderebilme özelliğiyle oluşturulmaz. Ancak INSERT, UPDATE ve DELETE komutlarını el ile yapılandırabilirsiniz **özellikleri** penceresi.  
  
## <a name="tableadapter-queries"></a>TableAdapter sorguları  
 ![TableAdapter ile birden çok sorgu](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapter'ları, ilişkili olduğu veri tablolarını doldurmak için birden çok sorgu bulunabilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu özellik, farklı ölçütlere göre farklı sonuçlar yüklemek bir TableAdapter etkinleştirin.  
  
 Örneğin, uygulamanızda müşteri adları içeren bir tablo varsa tabloyu aynı bölgede bulunan müşterilerle dolduran belli bir harfle başlayan her müşteri adı ve başka bir tabloyu dolduran bir sorgu oluşturabilirsiniz. Doldurmak için bir `Customers` tablosu belirli bir durumda olan müşteriler, oluşturduğunuz bir `FillByState` gibi durum değeri için bir parametre alan sorgu: `SELECT * FROM Customers WHERE State = @State`. Çağırarak sorguyu çalıştırmak `FillByState` yöntemi ve ve parametre değerini geçirme gibi bu: `CustomerTableAdapter.FillByState("WA")`.  
  
 TableAdapter bağdaştırıcısının veri tablosuyla aynı şemaya veri döndüren sorgular eklemenin yanı sıra skalar (tek) değerler döndüren sorgular da ekleyebilirsiniz. Örneğin, müşterilerin sayısını döndüren bir sorgu (`SELECT Count(*) From Customers`) için geçerli bir `CustomersTableAdapter,` rağmen döndürülen veriler tablonun şemasına uygun değil.  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill özelliği  
 Varsayılan olarak, TableAdapter bağdaştırıcısının veri tablosunu doldurmak için bir sorguyu her çalıştırdığınızda, var olan veriler temizlenir ve yalnızca sorgunun sonuçları tabloya yüklenir. TableAdapter bağdaştırıcısının ayarlamak `ClearBeforeFill` özelliğini `false` ekleyebilir veya var olan verileri bir veri tablosunda bir sorgudan döndürülen verileri birleştirmek istiyorsanız. Bunları sürdürülmesi istiyorsanız verileri olup olmadığını temizleyip temizlemediğinizden bağımsız olarak, güncelleştirmeleri açıkça veritabanına geri göndermek gerekir. Bu nedenle, tabloyu dolduran başka bir sorgu çalıştırmadan önce herhangi bir değişiklik tablosundaki verileri kaydetmek unutmayın. Daha fazla bilgi için [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>TableAdapter devralması  
 TableAdapters işlevselliğini standart veri bağdaştırıcılarından yapılandırılmış bir kapsülleyerek <xref:System.Data.Common.DataAdapter> sınıfı? qualifyHint = False & autoUpgrade = True. Varsayılan olarak, TableAdapter'in devralındığı <xref:System.ComponentModel.Component> sınıfı ve yayınlanamıyor <xref:System.Data.Common.DataAdapter> sınıfı. Bir TableAdapter bağdaştırıcısına atama <xref:System.Data.Common.DataAdapter> sınıfı sonuçları bir <xref:System.InvalidCastException> hata? qualifyHint = False & autoUpgrade = True. TableAdapter bağdaştırıcısının temel sınıfını değiştirmek için türetilen bir sınıf yazabilirsiniz <xref:System.ComponentModel.Component> içinde **temel sınıf** Özellik Düzenleyici içindeki TableAdapter'ın **veri kümesi Tasarımcısı**.  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter yöntemleri ve özellikleri  
 TableAdapter sınıfı değil parçası [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Bu, olamaz arayın belgelerinde anlamına gelir veya **Nesne Tarayıcısı**. Yukarıda belirtilen sihirbazlardan birini kullandığınızda, tasarım zamanında oluşturulur. Oluşturduğunuz bir TableAdapter bağdaştırıcısına atanan ad çalıştığınız tablonun adı temel alır. Örneğin, adında bir veritabanındaki bir tabloda temel bir TableAdapter oluşturduğunuzda `Orders`, TableAdapter adlı `OrdersTableAdapter`. TableAdapter bağdaştırıcısının sınıf adı kullanılarak değiştirilebilir. **adı** özelliğinde **veri kümesi Tasarımcısı**.  
  
 Yaygın olarak kullanılan yöntemleri ve TableAdapters özellikleri aşağıda verilmiştir:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`TableAdapter.Fill`|TableAdapter bağdaştırıcısının ilişkili veri tablosunu TableAdapter'ın SELECT komutunun sonuçlarıyla doldurur.|  
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını temsil eden bir tamsayı döndürür. Daha fazla bilgi için [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Yeni bir <xref:System.Data.DataTable> verilerle doldurulur.|  
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için [veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|  
  
## <a name="tableadapter-update-method"></a>TableAdapter güncelleştirme yöntemi  
 TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. TableAdapter bağdaştırıcısının başlangıç `Fill` (ana) sorgusu, ilişkili veri tablosunun şema oluşturmak için temel olarak kullanılır ve `InsertCommand`, `UpdateCommand`, ve `DeleteCommand` ilişkili komutları `TableAdapter.Update` yöntemi. TableAdapter bağdaştırıcısının `Update` yöntemi çalışır TableAdapter başlangıçta olduğunda, oluşturulan deyimlerin yapılandırılmış, ile eklenen ilave sorgulardan birinin değil **TableAdapter sorgu Yapılandırma Sihirbazı'nı**.  
  
 Bir TableAdapter kullandığınızda, aynı işlemleri genelde uyguladığınız komutlarla etkin bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının çağırdığınızda `Fill` yöntemi, bağdaştırıcı veri komutu çalıştırır kendi `SelectCommand` özelliği ve bir veri okuyucu kullanır (örneğin, <xref:System.Data.SqlClient.SqlDataReader>) sonuç kümesini veri tablosuna yüklemek için. Benzer şekilde, bağdaştırıcının çağırdığınızda `Update` yöntemi, uygun komutu çalıştırır (içinde `UpdateCommand`, `InsertCommand`, ve `DeleteCommand` özellikleri) her biri için veri tablosundaki kayıt değiştirildi.  
  
> [!NOTE]
>  Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter bağdaştırıcısının ana sorgusunda tek tablolu bir SELECT deyimi birden fazla ise, Tasarımcı oluşturmak mümkün olmayacak olası `InsertCommand`, `UpdateCommand`, ve `DeleteCommand`. Bu komutlar oluşturulmazsa, çalışırken bir hata alabilirsiniz `TableAdapter.Update` yöntemi.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği  
 Ek olarak `InsertCommand`, `UpdateCommand`, ve `DeleteCommand`, TableAdapter'ları doğrudan veritabanında çalıştırılabilen yöntemleri ile oluşturulur. Bu yöntemler (`TableAdapter.Insert`, `TableAdapter.Update` ve `TableAdapter.Delete`) veritabanındaki verileri işlemek için doğrudan çağrılabilir. Yani, koddan çağırmak yerine bu tek tek yöntemleri çağırabilir `TableAdapter.Update` ekleme, güncelleştirme ve bekleyen silme işlemek için ilişkili veri tablosu için.  
  
 Bu doğrudan yöntemleri oluşturmak istemiyorsanız TableAdapter bağdaştırıcısının ayarlamak **GenerateDbDirectMethods** özelliğini `false` (içinde **özellikleri** pencere). TableAdapter bağdaştırıcısına eklenen ek sorgular olan tek başına sorgulardır; bu yöntemler oluşturmak yok.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Boş değer atanabilir türler için TableAdapter desteği  
 TableAdapter boş değer atanabilir türler Destek `Nullable(Of T)` ve `T?`. Visual Basic'te boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [boş değer atanabilir değer türleri](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). C# dilinde boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [kullanarak boş değer atanabilir türler](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="security"></a>Güvenlik  
 Veri komutları ile kullandığınızda bir `CommandType` özelliğini <xref:System.Data.CommandType>, dikkatli bir şekilde veritabanına geçirmeden önce bir istemciden gönderilen bilgilere bakın. Kötü amaçlı kullanıcılara gönderilecek deneyin (Ekle) yetkisiz erişim veya veritabanı zarar vermek için çaba değiştirilmiş veya ek SQL deyimlerinde. Bir veritabanına kullanıcı girişi aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Parametreli sorgular veya saklı yordamları mümkün olduğunda her zaman kullanmak iyi bir uygulamadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)

