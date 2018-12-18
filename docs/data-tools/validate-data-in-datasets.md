---
title: Veri kümelerindeki verileri doğrulama
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a0a8846719c6ad57e65e1e308e9884e81e1997d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174728"
---
# <a name="validate-data-in-datasets"></a>Veri kümelerindeki verileri doğrulama
Verileri doğrulama içinde bir veri kümesi şema kısıtlamalara uyması veri nesnelerine girilen değerlerin onaylanması işlemidir. Doğrulama işlemi ayrıca, bu değerler uygulamanız için kurulmuş kuralları takip ettiğiniz onaylar. Alttaki veritabanına güncelleştirmeleri göndermeden önce verileri doğrulamak için iyi bir uygulamadır. Bu, hataları ve bunun yanı sıra bir uygulama ve veritabanı arasındaki gidiş gelişlerin potansiyel sayısını azaltır.

Veri kümesine doğrulama denetimlerini oluşturarak, bir veri kümesine yazılan veri geçerli olduğunu doğrulayabilirsiniz. Veri kümesini güncelleştirme nasıl gerçekleştirildiği ne olursa olsun veri denetleyebilirsiniz — kullanılıp bir bileşeni, formda veya başka bir şekilde denetimleri tarafından doğrudan. Veri kümesi (aksine, veritabanı arka ucu), uygulamanızın bir parçası olduğundan, uygulamaya özgü doğrulama oluşturmak için mantıksal bir yerdir.

Veri kümesinin parçalı sınıf dosyasında doğrulama uygulamanıza eklemek için en iyi yerdir. İçinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]açın **veri kümesi Tasarımcısı** ve doğrulama oluşturmak istediğiniz sütunun veya tablonun çift tıklayın. Bu eylem otomatik olarak oluşturur bir <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay işleyicisi.

## <a name="validate-data"></a>Verileri doğrulama
 Bir veri kümesi içinde doğrulama aşağıdaki yollarla sağlanır:

-   Uygulamaya özgü doğrulama oluşturarak değişiklikleri sırasında bir tek veri sütundaki değerleri kontrol edebilirsiniz. Daha fazla bilgi için [nasıl yapılır: sütun değişiklikleri sırasında veri doğrulama](validate-data-in-datasets.md).

-   Değerleri bir tüm veriler için veri denetleyebilirsiniz kendi uygulamaya özgü doğrulama oluşturarak satır değişiyor. Daha fazla bilgi için [nasıl yapılır: satır değişiklikleri sırasında veri doğrulama](validate-data-in-datasets.md).

-   Benzersiz kısıtlamalar, anahtarlar vb. gerçek bir şema tanımı veri kümesinin bir parçası olarak oluşturarak.

-   Özelliklerini ayarlayarak <xref:System.Data.DataColumn> nesnenin, gibi <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, ve <xref:System.Data.DataColumn.Unique%2A>.

Tarafından tetiklenen çeşitli olayları <xref:System.Data.DataTable> nesnesi bir değişiklik kaydı oluştuğu zaman:

-   <xref:System.Data.DataTable.ColumnChanging> Ve <xref:System.Data.DataTable.ColumnChanged> olayları oluştuğunda sırasında ve sonrasında her değişiklik için tek bir sütun. <xref:System.Data.DataTable.ColumnChanging> Olay, belirli sütunlardaki değişiklikleri doğrulamak istediğinizde yararlıdır. Önerilen değişikliğin hakkında bilgi içeren olay bağımsız değişkeni olarak geçirilir.
-   <xref:System.Data.DataTable.RowChanging> Ve <xref:System.Data.DataTable.RowChanged> olayları oluştuğunda sırasında ve sonrasında herhangi bir satır değişikliği. <xref:System.Data.DataTable.RowChanging> Daha genel bir olay işleme çözümüdür. Bu, bir değişiklik yere satırda oluştuğunu, ancak hangi sütunun değişti bilmiyorum gösterir.

Varsayılan olarak, her değişiklik bir sütunu için bu nedenle dört olayları başlatır. İlk <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> değiştirilirken belli sütun için olayları. Sonraki olan <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları. Satırda birden çok değişiklik yaptığınız, her değişiklik için olayları gerçekleştirilecektir.

> [!NOTE]
>  Veri sıranın <xref:System.Data.DataRow.BeginEdit%2A> yöntemi kapanmadan <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> her bireysel sütun değişimi sonra olayları. Bu durumda, olayı kadar oluşmaz <xref:System.Data.DataRow.EndEdit%2A> yönteminin çağrılıp çağrılmadığını, ne zaman <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları yalnızca bir kez başlatılır. Daha fazla bilgi için [bir veri kümesini doldururken kısıtlamaları kapatma kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Seçtiğiniz olayın ne kadar ayrıntılı, doğrulama olması için istediğinize bağlıdır. Bir sütun değiştiğinde hemen bir hata catch önemli ise, doğrulama kullanarak yapı <xref:System.Data.DataTable.ColumnChanging> olay. Aksi takdirde kullanın <xref:System.Data.DataTable.RowChanging> olayı aynı anda yakalama çeşitli hatalar oluşabilir. Ayrıca, bir sütunun değerini başka bir sütunun içeriğine göre doğrulanır. böylece verilerinizi yapılandırılırsa sırasında doğrulama işlemini yapabilir <xref:System.Data.DataTable.RowChanging> olay.

Kayıt güncelleştirildiğinde, <xref:System.Data.DataTable> nesne değişiklikleri ortaya çıkan ve değişiklikler yapıldıktan sonra yanıt verebilirsiniz olayları başlatır.

Uygulamanızın kullandığı bir türü belirtilmiş veri kümesi, türü kesin belirlenmiş olay işleyicileri oluşturabilirsiniz. Bu işleyiciler için oluşturabileceğiniz dört ek yazılan olaylar ekler: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, ve `dataTableNameRowDeleted`. Bu yazılı olay işleyicileri tablonuzun kod yazma ve okuma daha kolay hale getirmek sütun adları içeren bağımsız değişken olarak geçirin.

## <a name="data-update-events"></a>Olay verileri güncelleştirme

|Olay|Açıklama|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Bir sütundaki değer olarak değiştiriliyor. Olay satır ve sütunları için önerilen yeni değerin yanı sıra geçirir.|
|<xref:System.Data.DataTable.ColumnChanged>|Bir sütundaki değeri değiştirildi. Olay satır ve sütunları için önerilen değeri yanı sıra geçirir.|
|<xref:System.Data.DataTable.RowChanging>|Yapılan değişiklikler bir <xref:System.Data.DataRow> nesne olan veri kümesine hakkında yürütülmesi. Değil çağrılırsa <xref:System.Data.DataRow.BeginEdit%2A> yöntemi <xref:System.Data.DataTable.RowChanging> olayı yükseltildiğinde her değişiklik bir sütunu için hemen sonra <xref:System.Data.DataTable.ColumnChanging> olay tetiklenir. Aradığınız varsa <xref:System.Data.DataRow.BeginEdit%2A> değişiklikleri yapmadan önce <xref:System.Data.DataTable.RowChanging> yalnızca çağırdığınızda olayı oluşturulur <xref:System.Data.DataRow.EndEdit%2A> yöntemi.<br /><br /> Olay satır için ne tür bir eylem (değiştirme, ekleme ve benzeri) gerçekleşen belirten bir değer ile birlikte geçirir.|
|<xref:System.Data.DataTable.RowChanged>|Satır değiştirildi. Olay satır için ne tür bir eylem (değiştirme, ekleme ve benzeri) gerçekleşen belirten bir değer ile birlikte geçirir.|
|<xref:System.Data.DataTable.RowDeleting>|Bir satır siliniyor. Olay satır için ne tür (Sil) eyleminin gerçekleştirildiği belirten bir değer ile birlikte geçirir.|
|<xref:System.Data.DataTable.RowDeleted>|Bir satır silindi. Olay satır için ne tür (Sil) eyleminin gerçekleştirildiği belirten bir değer ile birlikte geçirir.|

<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, Ve <xref:System.Data.DataTable.RowDeleting> olayları güncelleştirme işlemi sırasında oluşur. Bu olaylar, verileri doğrulamak veya diğer işleme türlerini gerçekleştirmek için kullanabilirsiniz. Güncelleştirme sırasında bu olayları işlemde olduğundan, bir özel Update'ten önleyen durum tarafından iptal edebilirsiniz sonlandırılıyor.

<xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> Ve <xref:System.Data.DataTable.RowDeleted> güncelleştirme başarıyla tamamlandığında, oluşturulan uyarı olayları olaylardır. Bu olaylar, başka bir işlem başarılı bir güncelleştirmeye göre yapmanıza istediğinizde yararlıdır.

## <a name="validate-data-during-column-changes"></a>Sütun değişiklikleri sırasında veri doğrulama

> [!NOTE]
>  **Veri kümesi Tasarımcısı** hangi Doğrulama mantığı bir veri kümesine eklenebilecek kısmi bir sınıf oluşturur. Tasarımcı tarafından oluşturulan veri kümesini silin veya kısmi sınıftaki herhangi bir kod değişikliği değil.

Bir veri sütununun değeri değiştiğinde yanıtlayarak verileri doğrulayabilirsiniz <xref:System.Data.DataTable.ColumnChanging> olay. Oluştuğunda, bu olay bir olay bağımsız değişkeni geçirir (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) geçerli bir sütun için önerilmekte değeri içerir. İçeriklerine dayanan `e.ProposedValue`, şunları yapabilirsiniz:

-   Birşey yapmayarak önerilen değeri kabul edin.

-   Sütun hatasını ayarlayarak önerilen değeri Reddet (<xref:System.Data.DataRow.SetColumnError%2A>) gelen sütun değiştirme olay işleyicisinin içerisinde.

-   İsteğe bağlı olarak bir <xref:System.Windows.Forms.ErrorProvider> denetimi kullanıcıya bir hata iletisi görüntüler. Daha fazla bilgi için [ErrorProvider bileşeni](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Doğrulama de yapılabilir sırasında <xref:System.Data.DataTable.RowChanging> olay.

## <a name="validate-data-during-row-changes"></a>Satır değişiklikleri sırasında veri doğrulama
Doğrulamak istediğiniz her bir sütunun, uygulamanızın gereksinimlerini karşılayan verileri içerdiğini doğrulamak için kod yazabilirsiniz. Önerilen değer kabul edilebilir değilse, hata içerdiğini belirtmek için sütunu ayarlayarak bunu yapabilirsiniz. Aşağıdaki örnekler bir sütun hatasını belirtmektedir olduğunda `Quantity` 0 veya daha az sütun. Satır değiştiren olay işleyicileri aşağıdaki örneklere benzemelidir.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>(Visual Basic) değiştiğinde verileri bir satır doğrulamak için

1.  Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [izlenecek yol: veri kümesi Tasarımcısı'nda bir veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Doğrulamak istediğiniz tablonun başlık çubuğunu çift tıklatın. Bu eylem otomatik olarak oluşturur <xref:System.Data.DataTable.RowChanging> olay işleyicisine <xref:System.Data.DataTable> veri kümesinin parçalı sınıf dosyasında.

    > [!TIP]
    >  Satır değiştiren olay işleyicisi oluşturmak için tablo adının solunda çift tıklayın. Tablo adını çift tıklatırsanız, düzenleyebilirsiniz.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Bir satır (C#) değiştiğinde verileri doğrulamak için

1.  Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [izlenecek yol: veri kümesi Tasarımcısı'nda bir veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Doğrulamak istediğiniz tablonun başlık çubuğunu çift tıklatın. Bu eylem için bir parçalı sınıf dosyası oluşturur <xref:System.Data.DataTable>.

    > [!NOTE]
    >  **Veri kümesi Tasarımcısı** otomatik olarak bir olay işleyicisi oluşturmaz <xref:System.Data.DataTable.RowChanging> olay. İşlemek için bir yöntem oluşturmak sahip olduğunuz <xref:System.Data.DataTable.RowChanging> olayı tablonun başlatma yöntemine bağlamak için olay ve kodu çalıştırın.

3.  Aşağıdaki kodu kısmi sınıfın içine kopyalayın:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Değiştirilen satırların almak için
Her satırda bir veri tablosuna sahip bir <xref:System.Data.DataRow.RowState%2A> geçerli durumunu satır değerleri kullanarak izler özelliği <xref:System.Data.DataRowState> sabit listesi. Çağırarak bir dataset ya da veri tablosundan değiştirilen satırları döndürebilirsiniz `GetChanges` yöntemi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>. Değişiklikler çağırmadan önce mevcut doğrulayabilirsiniz `GetChanges` çağırarak <xref:System.Data.DataSet.HasChanges%2A> bir veri kümesinin yöntemi.

> [!NOTE]
>  Bir veri kümesi veya veri tablosuna değişiklikleri sonra (çağırarak <xref:System.Data.DataSet.AcceptChanges%2A> yöntemi), `GetChanges` yöntemi hiçbir veri döndürür. Değiştirilen satırların işlenecek uygulamanız gerekiyorsa çağırmadan önce değişiklikleri işleme `AcceptChanges` yöntemi.

Çağırma <xref:System.Data.DataSet.GetChanges%2A> yöntemi bir dataset ya da veri tablonun değiştirilmiş tek kayıtları içeren yeni bir veri kümesi veya veri tablosu döndürür. Belirli kayıtları almak istiyorsanız — örneğin, yalnızca yeni kayıtları veya yalnızca değiştirilmiş kayıtlar — arasında bir değer geçirebilirsiniz <xref:System.Data.DataRowState> bir parametre olarak numaralandırması `GetChanges` yöntemi.

Kullanım <xref:System.Data.DataRowVersion> bir satır (işlemekte önce bir satırda olan gibi orijinal değerleri) farklı sürümlerine erişmek için sabit listesi.

### <a name="to-get-all-changed-records-from-a-dataset"></a>Bir veri kümesinden değişen tüm kayıtları almak için

-   Çağrı <xref:System.Data.DataSet.GetChanges%2A> bir veri kümesinin yöntemi.

     Aşağıdaki örnekte adlı yeni bir veri kümesi oluşturur `changedRecords` ve adlı başka bir veri kümesindeki tüm kayıtlar ile doldurur `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Bir veri tablosundan değişen tüm kayıtları almak için

-   Çağrı <xref:System.Data.DataTable.GetChanges%2A> DataTable yöntemi.

     Aşağıdaki örnekte adlı yeni bir veri tablosu oluşturur `changedRecordsTable` ve adlı başka bir veri tablosundaki tüm kayıtlar ile doldurur `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Belirli bir satır durumunda olan tüm kayıtları almak için

-   Çağrı `GetChanges` yöntemi, bir veri kümesi veya veri tablosu ve geçişi bir <xref:System.Data.DataRowState> bağımsız değişken olarak sabit listesi değeri.

     Aşağıdaki örnekte adlı yeni bir veri kümesi oluşturma işlemi gösterilmektedir `addedRecords` ve yalnızca eklenmiş kayıtlarla doldurmak `dataSet1` veri kümesi.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Aşağıdaki örnek, en son eklenen tüm kayıtları döndürmek gösterilmektedir `Customers` tablosu:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Bir DataRow özgün sürümüne erişme
Veri satırlarına değişiklik yapıldığında, hem özgün veri kümesini tutar (<xref:System.Data.DataRowVersion.Original>) ve yeni (<xref:System.Data.DataRowVersion.Current>) satır sürümleri. Örneğin, çağırmadan önce `AcceptChanges` yöntemi, uygulamanız bir kaydın farklı sürümlerine erişebilir (sınıfında tanımlandığı gibi <xref:System.Data.DataRowVersion> numaralandırma) ve değişiklikleri buna göre işleyebilir.

> [!NOTE]
>  Bir satırın farklı sürümleri yalnızca düzenlenmiş sonra ve kendisinden önce mevcut `AcceptChanges` yöntemi çağrılır. Sonra `AcceptChanges` yönteminin çağrılıp çağrılmadığını, geçerli ve orijinal sürümler aynıdır.

Geçirme <xref:System.Data.DataRowVersion> değeri sütun diziniyle (veya sütun adı bir dize olarak) yanı sıra söz konusu sütunun belirli bir satır sürümündeki değeri döndürür. Değiştirilen sütun sırasında tanımlanan <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olayları. Bu, doğrulama amacıyla farklı satır sürümlerini incelemek için iyi bir zamandır. Ancak, kısıtlamaları geçici olarak askıya, bu olay harekete geçirilen olmaz ve program aracılığıyla yapmanız gerekir hangi sütunların değiştiğini belirleyin. İle Yinelem yaparak bunu yapabilirsiniz <xref:System.Data.DataTable.Columns%2A> toplama ve farklı karşılaştırma <xref:System.Data.DataRowVersion> değerleri.

### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için

-   Geçirerek bir sütun değerine erişin <xref:System.Data.DataRowVersion> döndürmek istediğiniz satırın.

     Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Data.DataRowVersion> orijinal değerini almak için değer bir `CompanyName` alanındaki bir <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Geçerli bir DataRow sürümüne erişme

### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için

-   Bir sütun değerine erişin ve hangi satır sürümünü döndürmek istediğinizi belirten dizine bir parametre ekleyin.

     Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Data.DataRowVersion> değeri geçerli değerini almak için bir `CompanyName` alanındaki bir <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde verileri doğrulama](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile form doğrulama için hata simgeleri görüntüleme](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)