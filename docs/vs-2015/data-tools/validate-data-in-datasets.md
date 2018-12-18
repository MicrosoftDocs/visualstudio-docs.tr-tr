---
title: Veri kümelerindeki verileri doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa90ddb397d1c18e88ab8f25e2a0c3aee3e4d9a5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891134"
---
# <a name="validate-data-in-datasets"></a>Veri kümelerindeki verileri doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Verileri doğrulama içinde bir veri kümesi şema kısıtlamalara uyması veri nesnelerine girilen değerlerin onaylanması işlemidir. Doğrulama işlemi ayrıca, bu değerler uygulamanız için kurulmuş kuralları takip ettiğiniz onaylar. Alttaki veritabanına güncelleştirmeleri göndermeden önce verileri doğrulamak için iyi bir uygulamadır. Bu, hataları ve bunun yanı sıra bir uygulama ve veritabanı arasındaki gidiş gelişlerin potansiyel sayısını azaltır.  
  
 Veri kümesine doğrulama denetimlerini oluşturarak, bir veri kümesine yazılan veri geçerli olduğunu doğrulayabilirsiniz. Veri kümesini güncelleştirme nasıl gerçekleştirildiği ne olursa olsun veri denetleyebilirsiniz — kullanılıp bir bileşeni, formda veya başka bir şekilde denetimleri tarafından doğrudan. Veri kümesi (aksine, veritabanı arka ucu), uygulamanızın bir parçası olduğundan, uygulamaya özgü doğrulama oluşturmak için mantıksal bir yerdir.  
  
 Veri kümesinin parçalı sınıf dosyasında doğrulama uygulamanıza eklemek için en iyi yerdir. İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../includes/csprcs-md.md)]açın **veri kümesi Tasarımcısı** ve doğrulama oluşturmak istediğiniz sütunun veya tablonun çift tıklayın. Bu eylem otomatik olarak oluşturur bir <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay işleyicisi. Daha fazla bilgi için [nasıl yapılır: değişiklikleri sütun sırasında veri doğrulama](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) veya [nasıl yapılır: değişiklikleri Satır sırasında veri doğrulama](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Tam bir örnek için bkz. [izlenecek yol: bir veri kümesine doğrulama ekleme](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Verileri doğrulama  
 Bir veri kümesi içinde doğrulama aşağıdaki yollarla gerçekleştirilebilir:  
  
- Uygulamaya özgü doğrulama oluşturarak değişiklikleri sırasında bir tek veri sütundaki değerleri kontrol edebilirsiniz.  Daha fazla bilgi için [nasıl yapılır: değişiklik sütun sırasında veri doğrulama](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Değerleri bir tüm veriler için veri denetleyebilirsiniz kendi uygulamaya özgü doğrulama oluşturarak satır değişiyor. Daha fazla bilgi için [nasıl yapılır: Değişiklik Satır sırasında veri doğrulama](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
- Benzersiz kısıtlamalar, anahtarlar vb. gerçek bir şema tanımı veri kümesinin bir parçası olarak oluşturarak. Şema tanımı doğrulama ekleme hakkında daha fazla bilgi için bkz. [sınırlamak için benzersiz değerler içeren bir DataColumn](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
- Özelliklerini ayarlayarak <xref:System.Data.DataColumn> nesnenin, gibi <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, ve <xref:System.Data.DataColumn.Unique%2A>.  
  
  Tarafından tetiklenen çeşitli olayları <xref:System.Data.DataTable> nesnesi bir değişiklik kaydı oluştuğu zaman:  
  
- <xref:System.Data.DataTable.ColumnChanging> Ve <xref:System.Data.DataTable.ColumnChanged> olayları oluştuğunda sırasında ve sonrasında her değişiklik için tek bir sütun. <xref:System.Data.DataTable.ColumnChanging> Olay, belirli sütunlardaki değişiklikleri doğrulamak istediğinizde yararlıdır. Önerilen değişikliğin hakkında bilgi içeren olay bağımsız değişkeni olarak geçirilir. Daha fazla bilgi için [nasıl yapılır: değişiklik sütun sırasında veri doğrulama](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- <xref:System.Data.DataTable.RowChanging> Ve <xref:System.Data.DataTable.RowChanged> olayları oluştuğunda sırasında ve sonrasında herhangi bir satır değişikliği. <xref:System.Data.DataTable.RowChanging> Daha genel bir olay işleme çözümüdür. Bu, bir değişiklik yere satırda oluştuğunu, ancak hangi sütunun değişti bilmiyorum gösterir. Daha fazla bilgi için [nasıl yapılır: Değişiklik Satır sırasında veri doğrulama](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
  Varsayılan olarak, her değişiklik bir sütunu için bu nedenle dört olayları başlatır. İlk <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> değiştirilirken belli sütun için olayları. Sonraki olan <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları. Satırda birden çok değişiklik yaptığınız, her değişiklik için olayları gerçekleştirilecektir.  
  
> [!NOTE]
>  Veri sıranın <xref:System.Data.DataRow.BeginEdit%2A> yöntemi kapanmadan <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> her bireysel sütun değişimi sonra olayları. Bu durumda, olayı kadar oluşmaz <xref:System.Data.DataRow.EndEdit%2A> yönteminin çağrılıp çağrılmadığını, ne zaman <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları yalnızca bir kez başlatılır. Daha fazla bilgi için [bir veri kümesini doldururken kısıtlamaları kapatma kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 Seçtiğiniz olayın ne kadar ayrıntılı, doğrulama olması için istediğinize bağlıdır. Bir sütun değiştiğinde hemen bir hata catch önemli ise, doğrulama kullanarak yapı <xref:System.Data.DataTable.ColumnChanging> olay. Aksi takdirde kullanın <xref:System.Data.DataTable.RowChanging> olayı aynı anda yakalama çeşitli hatalar oluşabilir. Ayrıca, bir sütunun değerini başka bir sütunun içeriğine göre doğrulanır. böylece verilerinizi yapılandırılırsa, sonra doğrulama sırasında gerçekleştirmek <xref:System.Data.DataTable.RowChanging> olay.  
  
 Kayıt güncelleştirildiğinde, <xref:System.Data.DataTable> nesne değişiklikleri ortaya çıkan ve değişiklikler yapıldıktan sonra yanıt verebilirsiniz olayları başlatır.  
  
 Uygulamanızın kullandığı bir türü belirtilmiş veri kümesi, türü kesin belirlenmiş olay işleyicileri oluşturabilirsiniz. Bu, işleyicileri için oluşturabileceğiniz dört ek yazılan olaylar ekler: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, ve `dataTableNameRowDeleted`. Bu yazılı olay işleyicileri tablonuzun kod yazma ve okuma daha kolay hale getirmek sütun adları içeren bağımsız değişken olarak geçirin.  
  
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
  
- Birşey yapmayarak önerilen değeri kabul edin.  
  
- Sütun hatasını ayarlayarak önerilen değeri Reddet (<xref:System.Data.DataRow.SetColumnError%2A>) gelen sütun değiştirme olay işleyicisinin içerisinde.  
  
- İsteğe bağlı olarak bir <xref:System.Windows.Forms.ErrorProvider> denetimi kullanıcıya bir hata iletisi görüntüler. Daha fazla bilgi için [ErrorProvider bileşeni](http://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
  Doğrulama de yapılabilir sırasında <xref:System.Data.DataTable.RowChanging> olay. Daha fazla bilgi için [nasıl yapılır: Değişiklik Satır sırasında veri doğrulama](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Satır değişiklikleri sırasında veri doğrulama  
 Doğrulamak istediğiniz her bir sütunun, uygulamanızın gereksinimlerini karşılayan verileri içerdiğini doğrulamak için kod yazabilirsiniz. Önerilen değer kabul edilebilir değilse, hata içerdiğini belirtmek için sütunu ayarlayarak bunu yapabilirsiniz. Aşağıdaki örnekler bir sütun hatasını belirtmektedir olduğunda `Quantity` 0 veya daha az sütun. Satır değiştiren olay işleyicileri aşağıdaki örneklere benzemelidir.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>(Visual Basic) değiştiğinde verileri bir satır doğrulamak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doğrulamak istediğiniz tablonun başlık çubuğunu çift tıklatın. Bu eylem otomatik olarak oluşturur <xref:System.Data.DataTable.RowChanging> olay işleyicisine <xref:System.Data.DataTable> veri kümesinin parçalı sınıf dosyasında.  
  
    > [!TIP]
    >  Satır değiştiren olay işleyicisi oluşturmak için tablo adının solunda çift tıklayın. Tablo adını çift tıklatırsanız, düzenleyebilirsiniz.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Bir satır (C#) değiştiğinde verileri doğrulamak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doğrulamak istediğiniz tablonun başlık çubuğunu çift tıklatın. Bu eylem için bir parçalı sınıf dosyası oluşturur <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  **Veri kümesi Tasarımcısı** otomatik olarak bir olay işleyicisi oluşturmaz <xref:System.Data.DataTable.RowChanging> olay. İşlemek için bir yöntem oluşturmak sahip olduğunuz <xref:System.Data.DataTable.RowChanging> olayı tablonun başlatma yöntemine bağlamak için olay ve kodu çalıştırın.  
  
3.  Aşağıdaki kodu kısmi sınıfın içine kopyalayın:  
  
    ```  
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
 Her satırda bir veri tablosuna sahip bir <xref:System.Data.DataRow.RowState%2A> geçerli durumunu satır değerleri kullanarak izler özelliği <xref:System.Data.DataRowState> sabit listesi. Çağırarak bir dataset ya da veri tablosundan değiştirilen satırları döndürebilirsiniz `GetChanges` yöntemi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>. Değişiklikler çağırmadan önce mevcut doğrulayabilirsiniz `GetChanges` çağırarak <xref:System.Data.DataSet.HasChanges%2A> bir veri kümesinin yöntemi. Hakkında daha fazla bilgi için <xref:System.Data.DataSet.HasChanges%2A>, bkz: [nasıl yapılır: değiştirilen satırları denetleme](http://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
>  Bir veri kümesi veya veri tablosuna değişiklikleri sonra (çağırarak <xref:System.Data.DataSet.AcceptChanges%2A> yöntemi), `GetChanges` yöntemi hiçbir veri döndürür. Değiştirilen satırların işlenecek uygulamanız gerekiyorsa çağırmadan önce değişiklikleri işleme `AcceptChanges` yöntemi.  
  
 Çağırma <xref:System.Data.DataSet.GetChanges%2A> yöntemi bir dataset ya da veri tablonun değiştirilmiş tek kayıtları içeren yeni bir veri kümesi veya veri tablosu döndürür. Belirli kayıtları almak istiyorsanız — örneğin, yalnızca yeni kayıtları veya yalnızca değiştirilmiş kayıtlar — arasında bir değer geçirebilirsiniz <xref:System.Data.DataRowState> bir parametre olarak numaralandırması `GetChanges` yöntemi.  
  
 Kullanım <xref:System.Data.DataRowVersion> bir satır (işlemekte önce bir satırda olan gibi orijinal değerleri) farklı sürümlerine erişmek için sabit listesi.  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Bir veri kümesinden değişen tüm kayıtları almak için  
  
-   Çağrı <xref:System.Data.DataSet.GetChanges%2A> bir veri kümesinin yöntemi.  
  
     Aşağıdaki örnekte adlı yeni bir veri kümesi oluşturur `changedRecords` ve adlı başka bir veri kümesindeki tüm kayıtlar ile doldurur `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Bir veri tablosundan değişen tüm kayıtları almak için  
  
-   Çağrı <xref:System.Data.DataTable.GetChanges%2A> DataTable yöntemi.  
  
     Aşağıdaki örnekte adlı yeni bir veri tablosu oluşturur `changedRecordsTable` ve adlı başka bir veri tablosundaki tüm kayıtlar ile doldurur `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Belirli bir satır durumunda olan tüm kayıtları almak için  
  
-   Çağrı `GetChanges` yöntemi, bir veri kümesi veya veri tablosu ve geçişi bir <xref:System.Data.DataRowState> bağımsız değişken olarak sabit listesi değeri.  
  
     Aşağıdaki örnekte adlı yeni bir veri kümesi oluşturma işlemi gösterilmektedir `addedRecords` ve yalnızca eklenmiş kayıtlarla doldurmak `dataSet1` veri kümesi.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
-   Aşağıdaki örnek, en son eklenen tüm kayıtları döndürmek gösterilmektedir `Customers` tablosu:  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Bir DataRow özgün sürümüne erişme  
 Veri satırlarına değişiklik yapıldığında, hem özgün veri kümesini tutar (<xref:System.Data.DataRowVersion>) ve yeni (<xref:System.Data.DataRowVersion>) satır sürümleri. Örneğin, çağırmadan önce `AcceptChanges` yöntemi, uygulamanız bir kaydın farklı sürümlerine erişebilir (sınıfında tanımlandığı gibi <xref:System.Data.DataRowVersion> numaralandırma) ve değişiklikleri buna göre işleyebilir.  
  
> [!NOTE]
>  Bir satırın farklı sürümleri yalnızca düzenlenmiş sonra ve kendisinden önce mevcut `AcceptChanges` yöntemi çağrılır. Sonra `AcceptChanges` yönteminin çağrılıp çağrılmadığını, geçerli ve orijinal sürümler aynıdır.  
  
 Geçirme <xref:System.Data.DataRowVersion> değeri sütun diziniyle (veya sütun adı bir dize olarak) yanı sıra söz konusu sütunun belirli bir satır sürümündeki değeri döndürür. Değiştirilen sütun sırasında tanımlanan <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olayları. Bu, doğrulama amacıyla farklı satır sürümlerini incelemek için iyi bir zamandır. Ancak, kısıtlamaları geçici olarak askıya, bu olay harekete geçirilen olmaz ve program aracılığıyla yapmanız gerekir hangi sütunların değiştiğini belirleyin. İle Yinelem yaparak bunu yapabilirsiniz <xref:System.Data.DataTable.Columns%2A> toplama ve farklı karşılaştırma <xref:System.Data.DataRowVersion> değerleri.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için  
  
-   Geçirerek bir sütun değerine erişin <xref:System.Data.DataRowVersion> döndürmek istediğiniz satırın.  
  
     Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Data.DataRowVersion> orijinal değerini almak için değer bir `CompanyName` alanındaki bir <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Geçerli bir DataRow sürümüne erişme  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için  
  
-   Bir sütun değerine erişin ve hangi satır sürümünü döndürmek istediğinizi belirten dizine bir parametre ekleyin.  
  
     Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Data.DataRowVersion> değeri geçerli değerini almak için bir `CompanyName` alanındaki bir <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türü belirtilmiş veri kümeleri oluşturma ve düzenleme](../data-tools/creating-and-editing-typed-datasets.md)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Nasıl yapılır: Windows Forms DataGridView denetiminde verileri doğrulama](http://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
 [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme](http://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)

