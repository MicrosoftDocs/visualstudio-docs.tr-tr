---
title: Veri kümelerindeki verileri düzenleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1ad74243c70b4ca7aaa8460759abbc898d30bb9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757155"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
Herhangi bir veritabanı bir tablodaki verileri düzenleme çok gibi veri tablolarındaki verileri düzenleyin. İşlem ekleme, güncelleştirme ve tablodaki kayıt silme içerebilir. Veri bağlama formunda, hangi alanlar kullanıcı düzenlenebilir belirtebilirsiniz. Bu durumlarda, böylece değişiklikleri veritabanına geri daha sonra gönderilebilir tüm değişiklik izleme veri bağlama altyapısı işler. Verileri programlı olarak düzenlemeleri yapın ve bu değişiklikleri veritabanına geri göndermek istiyorsanız, nesneleri ve değişiklik izleme bunu yöntemleri kullanmanız gerekir.

Gerçek veri değiştirmenin yanı sıra, ayrıca Sorgulayabileceğiniz bir <xref:System.Data.DataTable> belirli sayıda veri dönün. Örneğin, tek tek satır, satırları (özgün ve önerilen) belirli sürümleri, değiştirilen satırları veya hatalar içeren satırların için sorgu.

## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesinde satır düzenlemek için
Var olan bir satır düzenlemek için bir <xref:System.Data.DataTable>, bulmaya ihtiyaç <xref:System.Data.DataRow> düzenleme ve güncelleştirilmiş değerleri istenen sütunlar atayın istiyor.

Satırın dizini bilmiyorsanız, istediğiniz Düzenle kullanmak `FindBy` yöntemi tarafından birincil anahtarı aramak için:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Satır dizini biliyorsanız, erişebilir ve satır şu şekilde düzenler:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine yeni satır eklemek için
Verilere bağlı denetimler genellikle kullanan uygulamalar aracılığıyla yeni kayıtlar ekleme **yeni Ekle** düğmesini bir [BindingNavigator denetimi](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

El ile yeni kayıtlar ekleme için yeni bir veri satırı DataTable nesnesinde yöntemini çağırarak oluşturun. Ardından, satır <xref:System.Data.DataRow> koleksiyonu (<xref:System.Data.DataTable.Rows%2A>), <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Veri kümesi veri kaynağına güncelleştirmeleri göndermek için gereken bilgileri korumak için kullanmak <xref:System.Data.DataRow.Delete%2A> yöntemi bir veri tablosunda satırları kaldırır. Örneğin, uygulamanız bir TableAdapter kullanıyorsa (veya <xref:System.Data.Common.DataAdapter>), TableAdapter's `Update` yöntemi siler olması ve veritabanında satır bir <xref:System.Data.DataRow.RowState%2A> , <xref:System.Data.DataRowState.Deleted>.

Uygulamanızı bir veri kaynağına güncellemelerin gerekmez varsa, veri satır koleksiyonu doğrudan erişerek kayıtlarını kaldırmak mümkündür (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Bir veri tablosundan kayıtları silmek için

-   Çağrı <xref:System.Data.DataRow.Delete%2A> yöntemi bir <xref:System.Data.DataRow>.

     Bu yöntem, fiziksel olarak kaydı kaldırmaz. Bunun yerine, kayıt silme işlemi için işaretler.

    > [!NOTE]
    >  Count özelliği alırsanız bir <xref:System.Data.DataRowCollection>, sonuçta elde edilen sayısı silinmek üzere işaretlenmiş kayıtları içerir. Silinmek üzere işaretlenmiş olmayan kayıtları doğru bir sayıyı almak için bakarak koleksiyonu aracılığıyla bir döngüye girer <xref:System.Data.DataRow.RowState%2A> her bir kayıt özelliği. (Kayıtları silinmek üzere işaretlenmiş bir <xref:System.Data.DataRow.RowState%2A> , <xref:System.Data.DataRowState.Deleted>.) Alternatif olarak, bir veri görünümü filtreleri satır durumuna bağlı bir veri kümesi oluşturmak ve buradan count özelliğini alın.

Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Data.DataRow.Delete%2A> ilk satırda işaretlemek için yöntemi `Customers` tablo silindi olarak:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırları olup olmadığını belirleme
Kayıt bir veri kümesinde yapılan bir değişiklik olduğunda bunları kaydedene kadar bu değişiklikler hakkında bilgi depolanır. Çağırdığınızda, değişiklikleri `AcceptChanges` yöntemi dataset ya da veri tablonun veya çağırdığınızda `Update` bir TableAdapter veya veri bağdaştırıcısı yöntemi.

Değişiklikleri izlenen iki yolla her veri satırı şunlardır:

-   Her veri satırı ilgili bilgiler içeren kendi <xref:System.Data.DataRow.RowState%2A> (örneğin, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, veya <xref:System.Data.DataRowState.Unchanged>).

-   Her değiştirilen verileri satır satır birden fazla sürümünü içerir (<xref:System.Data.DataRowVersion>), özgün sürüm (önce değişiklikleri) ile geçerli sürümü (sonra değişir). Bir değişiklik olduğunda bekleyen süre boyunca (zaman, yanıt verebilmesini için zaman <xref:System.Data.DataTable.RowChanging> olay), üçüncü bir sürüm — önerilen sürüm — de kullanılabilir.

<xref:System.Data.DataSet.HasChanges%2A> Yöntemi bir veri kümesinin döndürür `true` kümesinde yapılan değişiklikler varsa. Değiştirilen satırları mevcut olduğunu belirledikten sonra çağırabilirsiniz `GetChanges` yöntemi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> değiştirilen satır kümesini dönün.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Herhangi bir satır değişiklik yapılıp yapılmadığını belirlemek için

-   Çağrı <xref:System.Data.DataSet.HasChanges%2A> yöntemi olup olmadığını denetlemek için bir veri kümesinin satırları değiştirildi.

Aşağıdaki örnek, dönüş değerini denetlemek gösterilmiştir <xref:System.Data.DataSet.HasChanges%2A> adlı bir veri kümesinde değiştirilen satır olup olmadığını algılamak için yöntemi `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Değişiklikleri türünü belirleme
Ne tür bir değişiklikleri görmek için yapıldı bir veri kümesinde arasında bir değer geçirerek de denetleyebilirsiniz <xref:System.Data.DataRowState> numaralandırma <xref:System.Data.DataSet.HasChanges%2A> yöntemi.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Belirlemek için ne tür değişikliklerin yapılan bir satır

-   Geçirmek bir <xref:System.Data.DataRowState> değeri <xref:System.Data.DataSet.HasChanges%2A> yöntemi.

Aşağıdaki örnek adlı bir veri denetlemek nasıl gösterir `NorthwindDataset1` herhangi bir yeni satır için eklenene varsa belirlemek için:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Hatalar içeren satırların bulmak için
Tek tek sütun ve veri satırı ile çalışırken hatalarla karşılaşabilirsiniz. Kontrol edebilirsiniz `HasErrors` hataları içinde olup olmadığını belirlemek için özelliğini bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow>.

1.  Denetleme `HasErrors` kümesindeki herhangi bir hata olup olmadığını görmek için özellik.

2.  Varsa `HasErrors` özelliği `true`, tablolar, koleksiyonlar üzerinden yineleme ve ardından hata satırı bulur. satırlar, aracılığıyla.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)