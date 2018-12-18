---
title: TableAdapters'ı kullanarak veri kümelerini doldurma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 673c364c1750afbaa4b319c40550be7cfac3b53b
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131979"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapters'ı kullanarak veri kümelerini doldurma

Bir TableAdapter bileşeni, bir veri kümesi bir veya daha fazla sorguları veya belirttiğiniz saklı yordamlar göre veritabanındaki verilerle doldurur. TableAdapter'ları da gerçekleştirebilirsiniz ekler, güncelleştirir ve veri kümesine yaptığınız değişiklikleri kalıcı hale getirmek için veritabanında siler. Ayrıca, belirli bir tabloya ilişkisiz genel komutları da verebilir.

> [!NOTE]
> TableAdapter bağdaştırıcılarını Visual Studio tasarımcılar tarafından oluşturulur. Veri kümeleri programlı olarak oluşturuyorsanız, bir .NET Framework sınıf olan DataAdapter'ni kullanın.

TableAdapter işlemleri hakkında ayrıntılı bilgi için doğrudan aşağıdaki konulardan birine atlayabilirsiniz:

|Konu|Açıklama|
|-----------|-----------------|
|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|Tableadapter'lar oluşturma ve yapılandırma için tasarımcılar kullanma|
|[Parametreleştirilmiş TableAdapter sorguları oluşturma](../data-tools/create-parameterized-tableadapter-queries.md)|Kullanıcılara, TableAdapter yordamları ya da sorguları bağımsız değişkenleri tanıma|
|[Bir TableAdapter ile veritabanına doğrudan erişme](../data-tools/directly-access-the-database-with-a-tableadapter.md)|TableAdapter Dbdirect yöntemleri kullanma|
|[Bir veri kümesini doldururken kısıtlamaları kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Verileri güncelleştirirken yabancı anahtar kısıtlamaları ile çalışma|
|[Bir TableAdapter işlevini genişletme](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapter bağdaştırıcıları için özel kod ekleme|
|[Bir veri kümesinin içine XML verileri okuma](../data-tools/read-xml-data-into-a-dataset.md)|XML ile çalışma|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter genel bakış

TableAdapter'ları, bir veritabanına, çalışma sorguları veya saklı yordamları bağlanın ve döndürülen verilerle kendi DataTable Doldur tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapter ayrıca uygulamanızdan veritabanına güncelleştirilmiş veriler göndermek. TableAdapter bağdaştırıcısının ilişkili olduğu tablosunun şemasına uyan veriler döndürmeleri sürece, TableAdapter bağdaştırıcısında istediğiniz sayıda sorgunuz çalıştırabilirsiniz. Aşağıdaki diyagramda, TableAdapter'ları ile veritabanları ve diğer nesneleri bellekte nasıl etkileşim kurduğu gösterilmektedir:

![Bir istemci uygulamasında veri akışı](../data-tools/media/clientdatadiagram.gif)

TableAdapter'ları ile tasarlandığında **veri kümesi Tasarımcısı**, TableAdapter sınıfları, iç içe sınıfları olarak oluşturulmaz <xref:System.Data.DataSet>. Bunlar, her veri kümesine özgü ayrı ad alanlarında bulunur. Örneğin adlı bir veri kümeniz, `NorthwindDataSet`, ilişkili TableAdapter'ları <xref:System.Data.DataTable>s'te `NorthwindDataSet` uzayında olacaktır `NorthwindDataSetTableAdapters` ad alanı. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örneğin:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>İlişkili DataTable şeması

Bir TableAdapter oluşturduğunuzda, ilk sorgu kullanın veya saklı yordamı TableAdapter şemasını tanımlamak için ilişkili zaman <xref:System.Data.DataTable>. Bu başlangıç sorgusunu çalıştırın veya saklı yordamı TableAdapter bağdaştırıcısının çağırarak `Fill` yöntemi (tablosu doldurulur ilişkili <xref:System.Data.DataTable>). TableAdapter bağdaştırıcısının ana sorgusunda yapılan değişiklikler ilişkili veri tablosunun şemada yansıtılır. Örneğin, ana sorgudan bir sütun kaldırılması da sütunu ilişkili veri tablosundan kaldırır. TableAdapter üzerindeki ek sorgular ana sorguda bulunmayan sütunları döndüren SQL deyimleri kullanıyorsanız, Tasarımcı ana sorgu ve ek sorgular arasındaki sütun değişikliklerini eşitlemeye çalışır.

## <a name="tableadapter-update-commands"></a>TableAdapter güncelleştirme komutları

Güncelleştirme işlevleri TableAdapter bağdaştırıcısının ana sorgusunda kullanılabilir ne kadar bilgi olduğuna bağlıdır **TableAdapter Sihirbazı**. Örneğin, birden çok tablodan değerlerini alacak şekilde yapılandırılan TableAdapter bağdaştırıcıları (kullanarak bir `JOIN`), skaler değerler, görünümleri ya da toplu işlevlerin sonuçlarından başlangıçta oluşturulmaz güncelleştirmeleri temel alınan veritabanına geri gönderme olanağı. Ancak, yapılandırabileceğiniz `INSERT`, `UPDATE`, ve `DELETE` el ile komutları **özellikleri** penceresi.

## <a name="tableadapter-queries"></a>TableAdapter sorguları

![TableAdapter ile birden çok sorgu](../data-tools/media/tableadapter.gif)

TableAdapter'ları, ilişkili olduğu veri tablolarını doldurmak için birden çok sorgu bulunabilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu özellik, farklı ölçütlere göre farklı sonuçlar yüklemek bir TableAdapter sağlar.

Örneğin, uygulamanızda müşteri adları içeren bir tablo varsa tabloyu aynı bölgede bulunan müşterilerle dolduran belli bir harfle başlayan her müşteri adı ve başka bir tabloyu dolduran bir sorgu oluşturabilirsiniz. Doldurmak için bir `Customers` tablosu belirli bir durumda olan müşteriler, oluşturduğunuz bir `FillByState` gibi durum değeri için bir parametre alan sorgu: `SELECT * FROM Customers WHERE State = @State`. Çağırarak sorguyu çalıştırmak `FillByState` yöntemi ve ve parametre değerini geçirme gibi bu: `CustomerTableAdapter.FillByState("WA")`.

TableAdapter bağdaştırıcısının veri tablosuyla aynı şemaya veri döndüren sorgular eklemenin yanı sıra skalar (tek) değerler döndüren sorgular da ekleyebilirsiniz. Örneğin, müşterilerin sayısını döndüren bir sorgu (`SELECT Count(*) From Customers`) için geçerli bir `CustomersTableAdapter,` rağmen döndürülen veriler tablonun şemasına uygun değil.

## <a name="clearbeforefill-property"></a>ClearBeforeFill özelliği

Varsayılan olarak, TableAdapter bağdaştırıcısının veri tablosunu doldurmak için bir sorguyu her çalıştırdığınızda, var olan veriler temizlenir ve yalnızca sorgunun sonuçları tabloya yüklenir. TableAdapter bağdaştırıcısının ayarlamak `ClearBeforeFill` özelliğini `false` ekleyebilir veya var olan verileri bir veri tablosunda bir sorgudan döndürülen verileri birleştirmek istiyorsanız. Bunları sürdürülmesi istiyorsanız verileri olup olmadığını temizleyip temizlemediğinizden bağımsız olarak, güncelleştirmeleri açıkça veritabanına geri göndermek gerekir. Bu nedenle, tabloyu dolduran başka bir sorgu çalıştırmadan önce herhangi bir değişiklik tablosundaki verileri kaydetmek unutmayın. Daha fazla bilgi için [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter devralması

TableAdapters işlevselliğini standart veri bağdaştırıcılarından yapılandırılmış bir kapsülleyerek <xref:System.Data.Common.DataAdapter> sınıfı. Varsayılan olarak, TableAdapter'in devralındığı <xref:System.ComponentModel.Component> sınıfı ve yayınlanamıyor <xref:System.Data.Common.DataAdapter> sınıfı. Bir TableAdapter bağdaştırıcısına atama <xref:System.Data.Common.DataAdapter> sınıfı sonuçları bir <xref:System.InvalidCastException> hata. TableAdapter bağdaştırıcısının temel sınıfını değiştirmek için türetilen bir sınıf belirtebilirsiniz <xref:System.ComponentModel.Component> içinde **temel sınıf** Özellik Düzenleyici içindeki TableAdapter'ın **veri kümesi Tasarımcısı**.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter yöntemleri ve özellikleri

TableAdapter sınıfı değil parçası [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Bu, olamaz arayın belgelerinde anlamına gelir veya **Nesne Tarayıcısı**. Yukarıda belirtilen sihirbazlardan birini kullandığınızda, tasarım zamanında oluşturulur. Oluşturduğunuz bir TableAdapter bağdaştırıcısına atanan ad çalıştığınız tablonun adı temel alır. Örneğin, adında bir veritabanındaki bir tabloda temel bir TableAdapter oluşturduğunuzda `Orders`, TableAdapter adlı `OrdersTableAdapter`. TableAdapter bağdaştırıcısının sınıf adı kullanılarak değiştirilebilir. **adı** özelliğinde **veri kümesi Tasarımcısı**.

Yaygın olarak kullanılan yöntemleri ve TableAdapters özellikleri aşağıda verilmiştir:

|Üye|Açıklama|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter bağdaştırıcısının ilişkili veri tablosunu TableAdapter bağdaştırıcısının sonuçlarıyla doldurur `SELECT` komutu.|
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını temsil eden bir tamsayı döndürür. Daha fazla bilgi için [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Yeni bir <xref:System.Data.DataTable> verilerle doldurulur.|
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için [veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|

## <a name="tableadapter-update-method"></a>TableAdapter güncelleştirme yöntemi

TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. TableAdapter bağdaştırıcısının başlangıç kullanmak `Fill` ilişkili veri tablosunun şema oluşturmak için temel olarak (ana) sorgusu yanı sıra `InsertCommand`, `UpdateCommand`, ve `DeleteCommand` ilişkili komutları `TableAdapter.Update` yöntemi. TableAdapter bağdaştırıcısının `Update` yöntemi, TableAdapter bağdaştırıcısının özgün yapılandırmasında oluşturulan deyimleri çalışır, ek bir sorgular, eklenen **TableAdapter sorgu Yapılandırma Sihirbazı'nı**.

Bir TableAdapter kullandığınızda, aynı işlemleri genelde uyguladığınız komutlarla etkin bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının çağırdığınızda `Fill` yöntemi, bağdaştırıcı veri komutu çalıştırır kendi `SelectCommand` özelliği ve bir veri okuyucu kullanır (örneğin, <xref:System.Data.SqlClient.SqlDataReader>) sonuç kümesini veri tablosuna yüklemek için. Benzer şekilde, bağdaştırıcının çağırdığınızda `Update` yöntemi, uygun komutu çalıştırır (içinde `UpdateCommand`, `InsertCommand`, ve `DeleteCommand` özellikleri) her biri için veri tablosundaki kayıt değiştirildi.

> [!NOTE]
> Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter bağdaştırıcısının ana sorgu tek bir tabloyu birden fazla ise `SELECT` deyiminde olduğu Tasarımcı oluşturmak mümkün olmayacak olası `InsertCommand`, `UpdateCommand`, ve `DeleteCommand`. Bu komutlar oluşturursa, bu olmayan çalışırken bir hata alabilirsiniz `TableAdapter.Update` yöntemi.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği

Ek olarak `InsertCommand`, `UpdateCommand`, ve `DeleteCommand`, TableAdapter veritabanına karşı doğrudan çalıştırılabilen yöntemleri ile oluşturulur. Bu yöntemleri çağırabilir (`TableAdapter.Insert`, `TableAdapter.Update`, ve `TableAdapter.Delete`) doğrudan veritabanındaki verileri işlemek için. Yani, koddan çağırmak yerine bu tek tek yöntemleri çağırabilir `TableAdapter.Update` ekleme, güncelleştirme ve bekleyen silme işlemek için ilişkili veri tablosu için.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız TableAdapter bağdaştırıcısının ayarlamak **GenerateDbDirectMethods** özelliğini `false` (içinde **özellikleri** pencere). TableAdapter bağdaştırıcısına eklenen ek sorgular olan tek başına sorgulardır; bu yöntemler oluşturmak yok.

## <a name="tableadapter-support-for-nullable-types"></a>Boş değer atanabilir türler için TableAdapter desteği

TableAdapter boş değer atanabilir türler Destek `Nullable(Of T)` ve `T?`. Visual Basic'te boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [boş değer atanabilir değer türleri](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). C# dilinde boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [boş değer atanabilir türleri kullanma](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu

İlişkili tabloları içeren bir veri kümesi oluşturduğunuzda varsayılan olarak, bir TableAdapterManager sınıfı oluşturur. Sınıf oluşturulmasını önlemek için değerini değiştirmek `Hierarchical Update` özelliği false kümesi. WPF sayfası ya da Windows Form Tasarım yüzeyine bir ilişkisi olan bir tabloda sürüklediğinizde, Visual Studio sınıfının bir üye değişkeni bildirir. Veri bağlama kullanmazsanız, el ile değişkenini tanımlamak zorunda.

TableAdapterManager sınıf değil parçası [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Bu nedenle, bu belgelerde bakarak olamaz. Tasarım zamanında veri kümesi oluşturma işleminin bir parçası olarak oluşturulur.

Sık kullanılan yöntemleri ve özellikleri verilmiştir `TableAdapterManager` sınıfı:

|Üye|Açıklama|
|------------|-----------------|
|`UpdateAll` Yöntemi|Tüm veriler, tüm veri tablolarından kaydeder.|
|`BackUpDataSetBeforeUpdate` Özelliği|Yürütmeden önce yedek bir kopyası, veri kümesinin oluşturulup oluşturulmayacağını belirler `TableAdapterManager.UpdateAll` yöntemi. Boole değeri.|
|*tableName* `TableAdapter` özelliği|Bir TableAdapter temsil eder. Oluşturulan TableAdapterManager her biri için bir özellik içeriyor `TableAdapter` yönettiği. Örneğin, müşteriler ve siparişler bir tablo olan bir veri kümesini içeren bir TableAdapterManager ile oluşturur `CustomersTableAdapter` ve `OrdersTableAdapter` özellikleri.|
|`UpdateOrder` Özelliği|Ayrı ayrı INSERT, update ve delete komutlarını sırasını denetler. Bu değerler birine `TableAdapterManager.UpdateOrderOption` sabit listesi.<br /><br /> Varsayılan olarak, `UpdateOrder` ayarlanır **InsertUpdateDelete**. Ekler, sonra güncelleştirir ve siler Bunun anlamı, veri kümesindeki tüm tabloların gerçekleştirilir.|

## <a name="security"></a>Güvenlik

Ayarlanan CommandType özelliği ile veri komutlarını kullanırken <xref:System.Data.CommandType.Text>, dikkatli bir şekilde veritabanına geçirmeden önce bir istemciden gönderilen bilgilere bakın. Kötü amaçlı kullanıcılara gönderilecek deneyin (Ekle) yetkisiz erişim veya veritabanı zarar vermek için çaba değiştirilmiş veya ek SQL deyimlerinde. Bir veritabanına kullanıcı girişi aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Parametreli sorgular veya saklı yordamları mümkün olduğunda her zaman kullanmak iyi bir uygulamadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
