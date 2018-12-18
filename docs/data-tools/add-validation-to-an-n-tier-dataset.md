---
title: N Katmanlı bir veri kümesine doğrulama ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 81d929aaffb6f08e5e1cda1cf3329de81fe13bc8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38778067"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>N Katmanlı bir veri kümesine doğrulama ekleme
Bir n katmanlı çözüme bölünen bir veri kümesine doğrulama ekleme temelde tek dosyalı veri kümesine (tek bir projede bir dataset) doğrulama ekleme ile aynı olur. Veri üzerine doğrulama yapmak için önerilen konum sırasındadır <xref:System.Data.DataTable.ColumnChanging> ve/veya <xref:System.Data.DataTable.RowChanging> veri tablosundaki olayları.

 Veri kümesi, kullanıcı kodu kümesindeki veri tablolarının sütun ve satır değiştiren olaylarına ekleyebileceğiniz kısmı sınıflar oluşturma işlevselliği sağlar. Bir n-katmanı çözümündeki bir veri kümesine kod ekleme hakkında daha fazla bilgi için bkz. [n katmanlı uygulamalarda veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md), ve [n katmanlı uygulamalarda Tableadapter'lara kod ekleyin](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Kısmi sınıflar hakkında daha fazla bilgi için bkz: [nasıl yapılır: sınıfı kısmi sınıflara (Sınıf Tasarımcısı) bölme](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) veya [kısmi sınıflar ve yöntemler](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
>  Veri kümelerini Tableadapters'dan ayırdığınızda ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları olmaz taşınması otomatik olarak. Varolan kısmi veri kümesi sınıfları, veri kümesi projesine el ile taşınmalıdır.

> [!NOTE]
>  Veri kümesi Tasarımcısı otomatik olarak oluşturmaz olay işleyicileri, C# ' ta <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olayları. El ile bir olay işleyicisi oluşturun ve temeldeki olaya olay işleyiciye bağlama gerekir. Aşağıdaki yordamlar Visual Basic ve C# içinde gerekli olay işleyicilerini oluşturma işlemini açıklar.

## <a name="validate-changes-to-individual-columns"></a>Tek tek sütunlara yapılan değişiklikleri doğrulama
 İşleyerek, tek tek sütunlardaki değerleri doğrulayın <xref:System.Data.DataTable.ColumnChanging> olay. <xref:System.Data.DataTable.ColumnChanging> Olayı, bir sütundaki bir değer değiştirildiğinde oluşturulur. İçin bir olay işleyicisi oluşturun <xref:System.Data.DataTable.ColumnChanging> istediğiniz sütunu çift tıklatarak olay **veri kümesi Tasarımcısı**.

 Bir sütunu çift tıkladığınızda ilk kez Tasarımcısı için bir olay işleyicisi oluşturur. <xref:System.Data.DataTable.ColumnChanging> olay. Bir `If...Then` deyimi de oluşturulur, belli sütun için test eder. Örneğin, aşağıdaki kod, çift tıkladığınızda oluşturulur **RequiredDate** Northwind siparişleri tablosundaki sütun:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
>  C# projelerinde, Dataset Designer yalnızca veri kümesi ve tek tek tablolar için kısmi sınıflar oluşturur. Veri kümesi Tasarımcısı otomatik olarak olay işleyiciler oluşturmaz <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olayları C# ' de Visual Basic'te yaptığı gibi. C# projelerinde, olayı işlemek ve temeldeki olaya yöntemi bağlama için bir yöntem el ile oluşturmak gerekir. Aşağıdaki yordam Visual Basic ve C# içinde gerekli olay işleyicilerini oluşturma adımlarını sağlar.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Ayrı ayrı sütun değerlerine değişiklikler sırasında doğrulama eklemek için

1.  Veri kümesine çift tıklayarak açın *.xsd* dosyası **Çözüm Gezgini**. Daha fazla bilgi için [izlenecek yol: veri kümesi Tasarımcısı'nda bir veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Doğrulamak istediğiniz sütunu çift tıklatın. Bu eylem oluşturur <xref:System.Data.DataTable.ColumnChanging> olay işleyicisi.

    > [!NOTE]
    >  Dataset Designer C# olayı için olay işleyicisi otomatik olarak oluşturmaz. C# ' taki olayı işlemek gerekli olan kod, sonraki bölümde eklenmiştir. `SampleColumnChangingEvent` oluşturulur ve en fazla kancalandı <xref:System.Data.DataTable.ColumnChanging> olayında <xref:System.Data.DataTable.EndInit%2A> yöntemi.

3.  Doğrulamak için kod ekleme `e.ProposedValue` uygulamanızın gereksinimlerini karşılayan verileri içerir. Önerilen değer kabul edilemezse, hata içerdiğini belirtmek için sütunu ayarlayın.

     Aşağıdaki kod örneği, doğrulama **miktar** sütun 0'dan büyük bir değer içeriyor. Varsa **miktar** küçük veya ona eşit 0, sütun hata olarak ayarlanır. `Else` Yan tümcesi hatayı siler, **miktar** 0 değerinden fazla. Sütun değiştirme olay işleyicisinin kodu aşağıdakine benzemelidir:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```
    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Bütün olarak satırlardaki değişiklikleri doğrulama
 İşleyerek, bütün değerleri doğrulamak <xref:System.Data.DataTable.RowChanging> olay. <xref:System.Data.DataTable.RowChanging> Olayı, tüm sütunlardaki değerlerin taahhüt olduğunda oluşturulur. İçinde doğrulamak gerekli olan <xref:System.Data.DataTable.RowChanging> olay bir sütundaki değer başka bir sütun değeri kullanır. Örneğin, Northwind siparişleri tablosundaki alan OrderDate ve Requireddate'i düşünün.

 Siparişler Girilmekte olduğunda, doğrulama, siparişin OrderDate veya bir RequiredDate ile girilmedi emin olur. Tek tek sütun değişikliğinin anlamsız için bu örnekte, RequiredDate ve OrderDate sütunlarının değerleri karşılaştırılmalıdır olması gerekir.

 İçin bir olay işleyicisi oluşturun <xref:System.Data.DataTable.RowChanging> tablonun başlık çubuğundaki tablo adını çift tıklatarak olay **veri kümesi Tasarımcısı**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Tüm satırlara değişiklikler sırasında doğrulama eklemek için

1.  Veri kümesine çift tıklayarak açın *.xsd* dosyası **Çözüm Gezgini**. Daha fazla bilgi için [izlenecek yol: veri kümesi Tasarımcısı'nda bir veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Tasarımcı üzerinde veri tablosunun başlık çubuğunu çift tıklatın.

     Kısmi sınıf oluşturulur bir `RowChanging` olay işleyicisi ve Kod Düzenleyicisi'nde açılır.

    > [!NOTE]
    >  Veri kümesi Tasarımcısı için bir olay işleyicisi otomatik olarak oluşturmaz <xref:System.Data.DataTable.RowChanging> C# projelerinde olay. İşlemek için bir yöntem oluşturmak sahip olduğunuz <xref:System.Data.DataTable.RowChanging> olay ve olayı tablonun başlatma yöntemine denetime kodu çalıştırın.

3.  Kısmi sınıf bildirimi içerisine kullanıcı kodu ekleyin.

4.  Aşağıdaki kod sırasında doğrulamak üzere kullanıcı kodunun nereye ekleneceğini göstermektedir <xref:System.Data.DataTable.RowChanging> olay. C# örnek ayrıca en fazla olay işleyicisi yöntemi bağlamak için kodu içerir `OrdersRowChanging` olay.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```
    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [İzlenecek yol: bir N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)