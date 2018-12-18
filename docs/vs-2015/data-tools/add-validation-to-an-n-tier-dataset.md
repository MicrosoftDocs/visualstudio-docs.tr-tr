---
title: Bir n katmanlı bir veri kümesine doğrulama ekleme | Microsoft Docs
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
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a0f7c21dcffb7c17f859d79d3aed5522beb14acf
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220540"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>N Katmanlı bir veri kümesine doğrulama ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir n katmanlı çözüme bölünen bir veri kümesine doğrulama ekleme temelde tek dosyalı veri kümesine (tek bir projede bir dataset) doğrulama ekleme ile aynı olur. Veri üzerine doğrulama yapmak için önerilen konum sırasındadır <xref:System.Data.DataTable.ColumnChanging> ve/veya <xref:System.Data.DataTable.RowChanging> veri tablosundaki olayları.  
  
 [Oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) sütun-kullanıcı kodu olduğu ekleyebileceğiniz kısmı sınıflar oluşturma işlevselliği sağlar ve satır-veri kümesindeki veri tablolarının olayları değiştirme. Bir n-katmanı çözümündeki bir veri kümesine kod ekleme hakkında daha fazla bilgi için bkz. [n katmanlı uygulamalarda veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md), ve [n katmanlı uygulamalarda Tableadapter'lara kod ekleyin](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Kısmi sınıflar hakkında daha fazla bilgi için bkz: [nasıl yapılır: sınıfı kısmi sınıflara (Sınıf Tasarımcısı) bölme](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) veya [kısmi sınıflar ve yöntemler](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
>  Veri kümelerini Tableadapters'dan ayırdığınızda ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları olmaz taşınması otomatik olarak. Var olan veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.  
  
> [!NOTE]
>  Veri kümesi Tasarımcısı otomatik olarak olay işleyicileri, C# ' ta oluşturmaz <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olayları. El ile bir olay işleyicisi oluşturun ve temeldeki olaya olay işleyiciye bağlama gerekir. Aşağıdaki yordamlar Visual Basic ve C# içinde gerekli olay işleyicilerini oluşturma işlemini açıklar.  
  
## <a name="validatechanges-to-individual-columns"></a>Tek tek sütunlara yapılan Validatechanges  
 İşleyerek, tek tek sütunlardaki değerleri doğrulayın <xref:System.Data.DataTable.ColumnChanging> olay. <xref:System.Data.DataTable.ColumnChanging> Olayı, bir sütundaki bir değer değiştirildiğinde oluşturulur. İçin bir olay işleyicisi oluşturun <xref:System.Data.DataTable.ColumnChanging> istediğiniz sütunu çift tıklatarak olay [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Bir sütunu çift tıkladığınızda ilk kez Tasarımcısı için bir olay işleyicisi oluşturur. <xref:System.Data.DataTable.ColumnChanging> olay. Bir `If…Then` deyimi de oluşturulur, belli sütun için test eder. Örneğin, Northwind siparişleri tablosundaki RequiredDate sütunu çift tıkladığınızda aşağıdaki kod oluşturulur:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  C# projelerinde, Dataset Designer yalnızca veri kümesi ve tek tek tablolar için kısmi sınıflar oluşturur. Veri kümesi Tasarımcısı otomatik olarak olay işleyiciler oluşturmaz <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olayları C# ' de Visual Basic'te yaptığı gibi. C# projelerinde, olayı işlemek ve temeldeki olaya yöntemi bağlama için bir yöntem el ile oluşturmak gerekir. Aşağıdaki yordam Visual Basic ve C# içinde gerekli olay işleyicilerini oluşturma adımlarını sağlar.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Ayrı ayrı sütun değerlerine değişiklikler sırasında doğrulama eklemek için  
  
1.  Veri kümesini açın [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) çift tıklayarak **.xsd** dosyası **Çözüm Gezgini**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doğrulamak istediğiniz sütunu çift tıklatın. Bu eylem oluşturur <xref:System.Data.DataTable.ColumnChanging> olay işleyicisi.  
  
    > [!NOTE]
    >  Dataset Designer C# olayı için olay işleyicisi otomatik olarak oluşturmaz. C# ' taki olayı işlemek gerekli olan kod, sonraki bölümde eklenmiştir. `SampleColumnChangingEvent` oluşturulur ve en fazla kancalandı <xref:System.Data.DataTable.ColumnChanging> olayında <xref:System.Data.DataTable.EndInit%2A> yöntemi.  
  
3.  Doğrulamak için kod ekleme `e.ProposedValue` uygulamanızın gereksinimlerini karşılayan verileri içerir. Önerilen değer kabul edilemezse, hata içerdiğini belirtmek için sütunu ayarlayın.  
  
     Aşağıdaki kod örneği, doğrulama **miktar** 0'dan fazla sütun içeriyor. Varsa **miktar** küçük veya ona eşit 0, sütun hata olarak ayarlanır. `Else` Yan tümcesi hatayı siler, **miktar** 0 değerinden fazla. Sütun değiştirme olay işleyicisinin kodu aşağıdakine benzemelidir:  
  
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
    // C#  
    // Add this code to the DataTable   
    // partial class.  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Bütün olarak satırlardaki Validatechanges  
 İşleyerek, bütün değerleri doğrulamak <xref:System.Data.DataTable.RowChanging> olay. <xref:System.Data.DataTable.RowChanging> Olayı, tüm sütunlardaki değerlerin taahhüt olduğunda oluşturulur. İçinde doğrulamak gerekli olan <xref:System.Data.DataTable.RowChanging> olay bir sütundaki değer başka bir sütun değeri kullanır. Örneğin, Northwind siparişleri tablosundaki alan OrderDate ve Requireddate'i düşünün.  
  
 Siparişler Girilmekte olduğunda, doğrulama, siparişin OrderDate veya bir RequiredDate ile girilmedi emin olur. Tek tek sütun değişikliğinin anlamsız için bu örnekte, RequiredDate ve OrderDate sütunlarının değerleri karşılaştırılmalıdır olması gerekir.  
  
 İçin bir olay işleyicisi oluşturun <xref:System.Data.DataTable.RowChanging> tablonun başlık çubuğundaki tablo adını çift tıklatarak olay [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md).  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Tüm satırlara değişiklikler sırasında doğrulama eklemek için  
  
1.  Veri kümesini açın [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) çift tıklayarak **.xsd** dosyası **Çözüm Gezgini**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Tasarımcı üzerinde veri tablosunun başlık çubuğunu çift tıklatın.  
  
     Kısmi sınıf oluşturulur bir `RowChanging` olay işleyicisi ve Kod Düzenleyicisi'nde açılır.  
  
    > [!NOTE]
    >  Veri kümesi Tasarımcısı için bir olay işleyicisi otomatik olarak oluşturmaz <xref:System.Data.DataTable.RowChanging> C# projelerinde olay. İşlemek için bir yöntem oluşturmak sahip olduğunuz <xref:System.Data.DataTable.RowChanging> olayı tablonun başlatma yöntemine bağlamak için olay ve kodu çalıştırın.  
  
3.  Kısmi sınıf bildirimi içerisine kullanıcı kodu ekleyin.  
  
4.  Aşağıdaki kod sırasında doğrulamak üzere kullanıcı kodunun nereye ekleneceğini göstermektedir <xref:System.Data.DataTable.RowChanging> Visual Basic için olay:  
  
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
  
5.  Aşağıdaki kod nasıl oluşturulacağını gösterir `RowChanging` olay işleyicisi ve sırasında doğrulamak üzere kullanıcı kodunun nereye ekleneceğini <xref:System.Data.DataTable.RowChanging> olay C# için:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)   
 [İzlenecek yol: bir N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)

