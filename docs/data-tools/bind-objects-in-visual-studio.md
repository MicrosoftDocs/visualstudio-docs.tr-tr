---
title: Özel nesneler veri bağlama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7790f5205aa24a68505a1b34e97283aff05e13c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950150"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Visual Studio'da veri kaynağı olarak nesneleri bağlama

Visual Studio, uygulamanızdaki veri kaynağı olarak özel nesneler ile çalışma için tasarım zamanı aracı sağlar. Kullanıcı Arabirimi denetimlerine bağlamanıza bir nesne veritabanından veri depolamak istediğinizde, önerilen yaklaşım Entity Framework sınıf veya sınıflar oluşturmak için kullanmaktır. Entity Framework otomatik-AcceptChanges olan DB nesnesinde çağırdığınızda değişiklikleri yerel nesneleri otomatik olarak veritabanına kaybolacağından yani tüm standart değişiklik izleme kodunu üretir. Daha fazla bilgi için [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Uygulamanızın veri kümelerinde zaten alıyorsa bu makalede nesneye bağlamada yaklaşımları yalnızca kabul edilmelidir. Bu yaklaşım, zaten veri kümeleriyle ilgili bilgi sahibi olduğunuz ve verileri, işleme tablolu ve çok karmaşık veya çok büyük ise de kullanabilirsiniz. DataReader kullanarak ve kullanıcı Arabirimi olmadan veri bağlama, el ile güncelleştirme doğrudan nesnelerine veri yükleme ile ilgili örneği artık çok daha kolay görmek [ADO.NET kullanarak basit veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri

Visual Studio Tasarım araçları verilerle çalışmak özel nesneler için tek gereksinim nesne en az bir ortak özelliği gerekiyor.

Genellikle, özel nesneleri herhangi bir belirli arabirimleri, Oluşturucular veya bir uygulama için veri kaynağı olarak görev yapacak öznitelikleri gerektirmez. Ancak, nesneyi sürükleyin istiyorsanız **veri kaynakları** verilere bağlı bir denetim oluşturmak için bir tasarım yüzeyine penceresi ve nesne uyguluyorsa <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimi, varsayılan bir nesne olmalıdır Oluşturucu. Aksi takdirde, Visual Studio, veri kaynağı nesnesi başlatılamıyor ve öğe tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneler veri kaynakları olarak kullanma örnekleri

Veri kaynağı olarak nesneleriyle çalışırken, uygulama mantığını uygulamak için sayısız yollar olsa da, SQL var. Visual Studio tarafından oluşturulan TableAdapter nesneleri kullanılarak basitleştirilebilir birkaç standart işlem veritabanlarıdır. Bu sayfa, TableAdapter'ı kullanarak bu standart işlemleri uygulamak üzere açıklanmaktadır. Bir kılavuz olarak, özel nesneleri oluşturmak için tasarlanmamıştır. Örneğin, genellikle nesnelerinizi ya da uygulamanın mantıksal özgü uygulama bağımsız olarak standart aşağıdaki işlemleri gerçekleştirir:

-   Veri nesneleri (genellikle bir veritabanından) yükleme.

-   Nesne türü belirtilmiş koleksiyonu oluşturuluyor.

-   Nesneler ekleme ve nesneleri bir koleksiyonundan kaldırılıyor.

-   Nesne verilerini bir formu kullanıcılara görüntüleniyor.

-   Değiştirme veya bir nesne verileri düzenleme.

-   Veri nesneleri veritabanına geri kaydediliyor.

### <a name="load-data-into-objects"></a>Nesnelerine veri yükleme

Bu örnek için TableAdapter'ı kullanarak, nesneleri verileri yükleyin. Varsayılan olarak, TableAdapter bağdaştırıcıları veritabanından veri getirir ve veri tablolarını doldurmak yöntemleri iki tür oluşturulur.

-   `TableAdapter.Fill` Yöntemi, mevcut bir veri tablosu döndürülen verilerle doldurur.

-   `TableAdapter.GetData` Yöntemi verilerle doldurulmuş yeni bir veri tablosu döndürür.

Özel nesnelerinizi veri yüklemek için en kolay yolu çağırmaktır `TableAdapter.GetData` yöntemi döndürülen veri tablosundaki satır koleksiyonu aracılığıyla döngü ve her satırdaki değerlerin her nesnesiyle doldurur. Oluşturabileceğiniz bir `GetData` doldurulmuş veri tablosunu TableAdapter bağdaştırıcısına eklenen herhangi bir sorgu için döndüren yöntem.

> [!NOTE]
> Visual Studio adları TableAdapter sorguları `Fill` ve `GetData` varsayılan olarak, ancak herhangi bir geçerli yöntemi ad bu adları değiştirebilirsiniz.

Aşağıdaki örnek, bir veri tablosundaki satırları döngü ve nesneyi verilerle doldurmak gösterilmektedir:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Nesne türü belirtilmiş bir koleksiyon oluşturun

Koleksiyon sınıfları için nesnelerinizi oluşturma veya tarafından otomatik olarak sağlanan yazılan koleksiyonları kullanın [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component).

Nesneler için bir özel koleksiyon sınıfı oluştururken, kaynağından devraldığından öneririz <xref:System.ComponentModel.BindingList%601>. Bu genel bir sınıf özelliği Windows Forms veri bağlama altyapısında bildirimleri göndermek olay yanı sıra, koleksiyonunuzu yönetmek için işlevsellik sağlar.

Otomatik olarak oluşturulan koleksiyonda <xref:System.Windows.Forms.BindingSource> kullanan bir <xref:System.ComponentModel.BindingList%601> kendi türü belirtilmiş bir koleksiyon için. Uygulamanızı ek işlevler gerekmiyorsa, koleksiyon içinde koruyabilirsiniz <xref:System.Windows.Forms.BindingSource>. Daha fazla bilgi için <xref:System.Windows.Forms.BindingSource.List%2A> özelliği <xref:System.Windows.Forms.BindingSource> sınıfı.

> [!NOTE]
> Koleksiyonunuz temel uygulaması tarafından sağlanmayan işlevselliği gerektirip gerektirmediğini <xref:System.ComponentModel.BindingList%601>, gerektiğinde sınıfa eklemek için özel bir koleksiyona oluşturmanız gerekir.

Aşağıdaki kod, sınıf için kesin türü belirtilmiş bir koleksiyonunu oluşturma işlemi gösterilmektedir `Order` nesneler:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Nesneleri bir koleksiyona Ekle

Çağırarak bir koleksiyona eklediğiniz nesneleri `Add` yöntemi özel bir koleksiyona sınıfınızın veya, <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Add` Öğesinden devraldığı durumlarda yöntemi özel koleksiyonunuz için otomatik olarak sağlanan <xref:System.ComponentModel.BindingList%601>.

Aşağıdaki kod, belirlenmiş koleksiyonda nesneleri eklemek gösterilmiştir bir <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 Aşağıdaki kod, devralınan belirlenmiş bir koleksiyon nesneleri eklemek gösterilmektedir <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> Bu örnekte, `Orders` koleksiyondur özelliği `Customer` nesne.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Nesneleri bir koleksiyondan Kaldır

Çağırarak nesneleri bir koleksiyondan Kaldır `Remove` veya `RemoveAt` yöntemi özel bir koleksiyona sınıfınızın veya, <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Remove` Ve `RemoveAt` yöntemleri otomatik olarak sağlanan özel koleksiyonunuz için öğesinden devraldığı durumlarda <xref:System.ComponentModel.BindingList%601>.

Aşağıdaki kodu bulun ve belirlenmiş koleksiyonda nesneleri kaldırmak gösterilmiştir bir <xref:System.Windows.Forms.BindingSource> ile <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> yöntemi:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Kullanıcılara nesne verilerini görüntüleme

Verileri kullanıcılara nesneleri görüntülemek için bir nesne veri kaynağı kullanılarak oluşturma **veri kaynağı yapılandırması** Sihirbazı'nı ve ardından formunuzun içinden üzerine nesnenin tamamını veya tek tek özellikler sürükleyin **veri kaynakları**penceresi.

### <a name="modify-the-data-in-objects"></a>Veri nesneleri değiştirme

Verilere Windows Forms denetimlerine bağlı özel nesneleri verileri düzenlemek için yalnızca veri ilişkili denetim (veya doğrudan bir nesnenin özelliklerinde) düzenleyin. Veri bağlama mimarisi, nesne verileri güncelleştirir.

Uygulamanızı, değişiklikleri izleme ve arkasına önerilen değişiklikler orijinal değerlerine alınıyor gerektiriyorsa, bu işlev, nesne modelinde uygulamalıdır. Nasıl veri tabloları önerdiğiniz değişiklikleri takip örnekleri için bkz: <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, ve <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Veri nesneleri veritabanına geri kaydedin

Verileri, TableAdapter bağdaştırıcısının DBDirect yöntemleri için bir nesneden değerler geçirerek veritabanına geri kaydedin.

Visual Studio doğrudan veritabanında yürütülebilecek DBDirect yöntemleri oluşturur. Bu yöntemler, veri kümesi ya da DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
| - |-----------------|
|`TableAdapter.Insert`|Yöntem parametreleri olarak ayrı ayrı sütun değerlerine geçirin olanak tanıyan bir veritabanına yeni kayıtlar ekler.|
|`TableAdapter.Update`|Mevcut veritabanındaki kayıtları güncelleştirir. Güncelleştirme yöntemi, yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Orijinal değerleri özgün kaydı bulmak için kullanılır ve bu kaydı güncelleştirmek için yeni değerler kullanılır.<br /><br /> `TableAdapter.Update` Yöntemi dataset içindeki değişiklikleri veritabanına geri alarak karşılaştırmak için kullanılan ayrıca bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, veya dizi <xref:System.Data.DataRow>yöntem parametreleri olarak s.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen var olan kayıtların özgün sütun değerlerine göre veritabanından siler.|

Nesnelerin bir koleksiyondaki verileri kaydetmek için (örneğin, bir sonraki için döngü kullanarak) nesne koleksiyonunu döngü. Değerlerin her nesne için TableAdapter bağdaştırıcısının DBDirect yöntemleri kullanarak veritabanına göndermek.

Aşağıdaki örnek nasıl kullanılacağını gösterir `TableAdapter.Insert` DBDirect yöntemi doğrudan veritabanına yeni bir müşteri eklemek için:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)