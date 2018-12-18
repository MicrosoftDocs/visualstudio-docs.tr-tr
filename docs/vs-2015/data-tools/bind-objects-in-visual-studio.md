---
title: Nesneleri bağlama
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 875ea4491fa91063339008362d132b4416afe2af
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065006"
---
# <a name="bind-objects-in-visual-studio"></a>Visual Studio'da nesne bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio, uygulamanızdaki veri kaynağı olarak özel nesneler ile çalışma için tasarım zamanı aracı sağlar. Kullanıcı Arabirimi denetimlerine bağlamanıza bir nesne veritabanından veri depolamak istediğinizde, önerilen yaklaşım Entity Framework sınıf veya sınıflar oluşturmak için kullanmaktır. Varlık Frameworkautogenerates AcceptChanges olan DB nesnesinde çağırdığınızda değişiklikleri yerel nesneleri otomatik olarak veritabanına kaybolacağından yani tüm ortak değişiklik izleme kod.    Daha fazla bilgi için [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Uygulamanızın veri kümelerinde zaten alıyorsa bu makalede nesneye bağlamada yaklaşımları yalnızca kabul edilmelidir. Bu yaklaşım, zaten veri kümeleriyle ilgili bilgi sahibi olduğunuz ve verileri, işleme tablolu ve çok karmaşık veya çok büyük ise kullanılabilir. DataReader kullanarak ve kullanıcı Arabirimi olmadan veri bağlama, el ile güncelleştirme doğrudan nesnelerine veri yükleme ile ilgili örneği artık çok daha kolay görmek [ADO.NET kullanarak basit veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri
 Visual Studio Tasarım araçları verilerle çalışmak özel nesneler için tek gereksinim nesne en az bir ortak özelliği gerekiyor.

 Genellikle, özel nesneleri herhangi bir belirli arabirimleri, Oluşturucular veya bir uygulama için veri kaynağı olarak görev yapacak öznitelikleri gerektirmez. Ancak, nesneyi sürükleyin istiyorsanız **veri kaynakları** verilere bağlı bir denetim oluşturmak için bir tasarım yüzeyine penceresi ve nesne uyguluyorsa <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimi, varsayılan bir nesne olmalıdır Oluşturucu. Aksi takdirde, Visual Studio, veri kaynağı nesnesi başlatılamıyor ve öğe tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneler veri kaynakları olarak kullanma örnekleri
 Veri kaynağı olarak nesneleriyle çalışırken, uygulama mantığını uygulamak için sayısız yollar olsa da, SQL var. Visual Studio – oluşturulan TableAdapter nesneleri kullanılarak basitleştirilebilir birkaç standart işlem veritabanlarıdır. Bu sayfa, bu standart işlemleri uygulamak üzere açıklanmaktadır TableAdapters.It kullanarak tasarlanmamıştır kılavuz olarak, özel nesneleri oluşturmak için. Örneğin, genellikle nesnelerinizi ya da uygulamanın mantıksal özgü uygulama bağımsız olarak standart aşağıdaki işlemleri gerçekleştirir:

-   Veri nesneleri (genellikle bir veritabanından) yükleme.

-   Nesne türü belirtilmiş koleksiyonu oluşturuluyor.

-   Nesneler ekleme ve nesneleri bir koleksiyonundan kaldırılıyor.

-   Nesne verilerini bir formu kullanıcılara görüntüleniyor.

-   Değiştirme veya bir nesne verileri düzenleme.

-   Veri nesneleri veritabanına geri kaydediliyor.

> [!NOTE]
>  Daha iyi anlamanıza ve bu sayfadaki örnekleri için bağlam sağlamak için aşağıdaki tamamlamanızı öneririz: [izlenecek yol: nesneler (Windows Forms) verilere bağlanma](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Bu izlenecek yol, burada tartışılan nesneleri oluşturur.

### <a name="loaddata-into-objects"></a>LoadData nesnelere
 Bu örnek için TableAdapter'ı kullanarak, nesneleri verileri yükleyin. Varsayılan olarak, TableAdapter bağdaştırıcıları veritabanından veri getirir ve veri tablolarını doldurmak yöntemleri iki tür oluşturulur.

- `TableAdapter.Fill` Yöntemi, mevcut bir veri tablosu döndürülen verilerle doldurur.

- `TableAdapter.GetData` Yöntemi verilerle doldurulmuş yeni bir veri tablosu döndürür.

  Özel nesnelerinizi veri yüklemek için en kolay yolu çağırmaktır `TableAdapter.GetData` yöntemi döndürülen veri tablosundaki satır koleksiyonu aracılığıyla döngü ve her satırdaki değerlerin her nesnesiyle doldurur. Oluşturabileceğiniz bir `GetData` doldurulmuş veri tablosunu TableAdapter bağdaştırıcısına eklenen herhangi bir sorgu için döndüren yöntem.

> [!NOTE]
>  Visual Studio adları TableAdapter sorguları `Fill` ve `GetData` varsayılan olarak, ancak bu adları için herhangi bir geçerli yöntem adı değiştirilebilir.

 Aşağıdaki örnek, bir veri tablosundaki satırları döngü ve nesneyi verilerle doldurmak gösterilmektedir:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Nesne türü belirtilmiş bir koleksiyon oluşturun
 Koleksiyon sınıfları için nesnelerinizi oluşturma veya tarafından otomatik olarak sağlanan yazılan koleksiyonları kullanın [BindingSource bileşeni](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Nesneler için bir özel koleksiyon sınıfı oluştururken kaynağından devraldığından öneririz <xref:System.ComponentModel.BindingList%601>. Bu genel bir sınıf özelliği Windows Forms veri bağlama altyapısında bildirimleri göndermek olay yanı sıra, koleksiyonunuzu yönetmek için işlevsellik sağlar.

 Otomatik olarak oluşturulan koleksiyonda <xref:System.Windows.Forms.BindingSource> kullanan bir <xref:System.ComponentModel.BindingList%601> kendi türü belirtilmiş bir koleksiyon için. Ek İşlevler, uygulamanızın gerektirmez sonra koleksiyonunuz içinde koruyabilirsiniz <xref:System.Windows.Forms.BindingSource>. Daha fazla bilgi için <xref:System.Windows.Forms.BindingSource.List%2A> özelliği <xref:System.Windows.Forms.BindingSource> sınıfı.

> [!NOTE]
>  Koleksiyonunuz temel uygulaması tarafından sağlanmayan işlevselliği gerektirip gerektirmediğini <xref:System.ComponentModel.BindingList%601>, gerektiğinde sınıfa eklemek için özel bir koleksiyona oluşturmanız gerekir.

 Aşağıdaki kod, sınıf için kesin türü belirtilmiş bir koleksiyonunu oluşturma işlemi gösterilmektedir `Order` nesneler:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Bir koleksiyona Addobjects
 Çağırarak bir koleksiyona eklediğiniz nesneleri `Add` yöntemi özel bir koleksiyona sınıfınızın veya, <xref:System.Windows.Forms.BindingSource>.

 Bir koleksiyon kullanarak ekleme örneği için bir <xref:System.Windows.Forms.BindingSource>, bakın `LoadCustomers` yönteminde [izlenecek yol: nesneler (Windows Forms) verilere bağlanma](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Nesne özel bir koleksiyona ekleme örneği için bkz. `LoadOrders` yönteminde [izlenecek yol: nesneler (Windows Forms) verilere bağlanma](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
>  `Add` Öğesinden devraldığı durumlarda yöntemi özel koleksiyonunuz için otomatik olarak sağlanan <xref:System.ComponentModel.BindingList%601>.

 Aşağıdaki kod, belirlenmiş koleksiyonda nesneleri eklemek gösterilmiştir bir <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Aşağıdaki kod, devralınan belirlenmiş bir koleksiyon nesneleri eklemek gösterilmektedir <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  Bu örnekte `Orders` koleksiyondur özelliği `Customer` nesne.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Bir koleksiyondaki Removeobjects
 Çağırarak nesneleri bir koleksiyondan Kaldır `Remove` veya `RemoveAt` yöntemi özel bir koleksiyona sınıfınızın veya, <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  `Remove` Ve `RemoveAt` yöntemleri otomatik olarak sağlanan özel koleksiyonunuz için öğesinden devraldığı durumlarda <xref:System.ComponentModel.BindingList%601>.

 Aşağıdaki kodu bulun ve belirlenmiş koleksiyonda nesneleri kaldırmak gösterilmiştir bir <xref:System.Windows.Forms.BindingSource> ile <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> yöntemi:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Kullanıcılara DisplayObject veri
 Verileri kullanıcılara nesneleri görüntülemek için bir nesne veri kaynağı kullanılarak oluşturma **veri kaynağı yapılandırması** Sihirbazı'nı ve ardından formunuzun içinden üzerine nesnenin tamamını veya tek tek özellikler sürükleyin **veri kaynakları**penceresi.

### <a name="modify-the-data-in-objects"></a>Veri nesneleri değiştirme
 Verilere Windows Forms denetimlerine bağlı özel nesneleri verileri düzenlemek için yalnızca veri ilişkili denetim (veya doğrudan bir nesnenin özelliklerinde) düzenleyin. Veri bağlama mimarisi, nesne verileri güncelleştirir.

 Uygulamanızı, değişiklikleri izleme ve arkasına önerilen değişiklikler orijinal değerlerine alınıyor gerektiriyorsa, bu işlev, nesne modelinde uygulamalıdır. Nasıl veri tabloları önerdiğiniz değişiklikleri takip örnekleri için bkz: <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, ve <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData veritabanına nesneleri
 Verileri, TableAdapter bağdaştırıcısının DBDirect yöntemleri için bir nesneden değerler geçirerek veritabanına geri kaydedin.

 Visual Studio doğrudan veritabanında yürütülebilecek DBDirect yöntemleri oluşturur. Bu yöntemler, veri kümesi ya da DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Yöntem parametreleri olarak ayrı ayrı sütun değerlerine geçirin olanak tanıyan bir veritabanına yeni kayıtlar ekler.|
|`TableAdapter.Update`|Mevcut veritabanındaki kayıtları güncelleştirir. Güncelleştirme yöntemi, yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Orijinal değerleri özgün kaydı bulmak için kullanılır ve bu kaydı güncelleştirmek için yeni değerler kullanılır.<br /><br /> `TableAdapter.Update` Yöntemi dataset içindeki değişiklikleri veritabanına geri alarak karşılaştırmak için kullanılan ayrıca bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, veya dizi <xref:System.Data.DataRow>yöntem parametreleri olarak s.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen var olan kayıtların özgün sütun değerlerine göre veritabanından siler.|

 Nesnelerin bir koleksiyondaki verileri kaydetmek için (örneğin, bir sonraki için döngü kullanarak) nesne koleksiyonunu döngü. Değerlerin her nesne için TableAdapter bağdaştırıcısının DBDirect yöntemleri kullanarak veritabanına göndermek.

 Aşağıdaki örnek nasıl kullanılacağını gösterir `TableAdapter.Insert` DBDirect yöntemi doğrudan veritabanına yeni bir müşteri eklemek için:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
