---
title: Veri kümelerini sorgulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6e1ff0cd6f77d2155ff4982ca02657a741c02d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890575"
---
# <a name="query-datasets"></a>Veri kümelerini sorgulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir veri kümesindeki belirli kayıtları aramak için üzerinde DataTable FindBy yöntemi kullanmak, tablonun satır koleksiyonu kendi foreach döngünüzü veya kullanın [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>Veri kümesi büyük/küçük harfe duyarlılık  
 Tablo ve sütun adları bir veri kümesi içinde varsayılan olarak büyük küçük harf duyarsız — diğer bir deyişle, "Müşteri" adlı bir veri kümesi tablosunda da için "Müşteri" olarak adlandırılabilir Bu SQL Server.In SQL Server dahil olmak üzere çok sayıda veritabanı adlandırma kuralları ile eşleşir, veri öğelerinin adlarını yalnızca büyük küçük harfle ayırt varsayılan davranıştır.  
  
> [!NOTE]
>  Şemalarda tanımlanan veri öğelerinin adlarını büyük küçük harfe duyarlı olacak şekilde veri kümeleri farklı olarak XML belgeleri, duyarlıdır. Örneğin, "Müşteri" ve "Müşteri" olarak adlandırılan farklı bir tablo adında bir tablo tanımlamak şema şema protokol sağlar Küçük harfe göre farklılık öğeleri içeren bir şema, bir veri kümesi sınıfı oluşturmak için kullanıldığında, bu ad çakışmalarını yol açabilir.  
  
 Büyük/küçük harfe duyarlılık ancak veri kümesi içinde verileri nasıl yorumlanacağını bir etken olabilir. Örneğin, bir veri kümesi tablodaki verileri filtreleme, arama ölçütlerini karşılaştırma büyük/küçük harfe olmasına bağlı olarak farklı sonuçlar döndürebilir. Filtreleme, aramayı ve veri kümesinin ayarlayarak sıralama büyük/küçük harf duyarlılığı denetleyebilirsiniz <xref:System.Data.DataSet.CaseSensitive%2A> özelliği. Veri kümesindeki tüm tabloları, varsayılan olarak bu özelliğin değerini devralır. (Bu özellik tek tek her tablo için tablo ayarlayarak kılabilirsiniz <xref:System.Data.DataTable.CaseSensitive%2A> özellik.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Belirli bir satır veri tablosunda bulun  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Türü belirtilmiş DataSet birincil bir anahtar değere sahip bir satır bulmak için  
  
-   Bir satır bulmak için türü kesin belirlenmiş çağrı `FindBy` tablonun birincil anahtarı kullanan bir yöntem.  
  
     Aşağıdaki örnekte, `CustomerID` sütundur birincil anahtarı `Customers` tablo. Oluşturulan buna `FindBy` yöntemi `FindByCustomerID`. Örnek, belirli bir atama gösterir <xref:System.Data.DataRow> kullanarak oluşturulan bir değişkene `FindBy` yöntemi.  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Birincil bir anahtar değere sahip yazılmamış bir veri kümesi bir satır bulunamadı  
  
-   Çağrı <xref:System.Data.DataRowCollection.Find%2A> yöntemi bir <xref:System.Data.DataRowCollection> birincil anahtarı bir parametre olarak geçirerek koleksiyonu.  
  
     Aşağıdaki örnekte adlı yeni bir satır bildirmek gösterilmektedir `foundRow` ve dönüş değerini atayın <xref:System.Data.DataRowCollection.Find%2A> yöntemi. Birincil anahtar bulunursa, sütun dizini 1 içeriğini bir ileti kutusunda görüntülenir.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>Sütun değerleri tarafından Findrows  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Herhangi bir sütun değerlere göre satır bulmak için  
  
-   Veri tabloları ile oluşturulur<xref:System.Data.DataTable.Select%2A> bir dizi döndüren yöntemi <xref:System.Data.DataRow>s ifadeye göre geçirilen <xref:System.Data.DataTable.Select%2A> yöntemi. Geçerli ifadeler oluşturma hakkında daha fazla bilgi için sayfanın "İfadesi söz dizimi" bölümüne bakın <xref:System.Data.DataColumn.Expression%2A> özelliği.  
  
     Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Data.DataTable.Select%2A> yöntemi <xref:System.Data.DataTable> belirli satırlar bulunacak.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="accessrelated-records"></a>Accessrelated kayıtları  
 Bir veri kümesindeki tabloların işlerken bir <xref:System.Data.DataRelation> nesne yapabilir ilgili kayıtlar başka bir tablodaki kullanılabilir. Örneğin, bir veri kümesi içeren `Customers` ve `Orders` tablolar kullanılabilir hale.  
  
 Kullanabileceğiniz bir <xref:System.Data.DataRelation> çağırarak ilgili kayıtları bulun nesnesine <xref:System.Data.DataRow.GetChildRows%2A> yöntemi bir <xref:System.Data.DataRow> içinde üst tablo. Bu yöntem, bir dizi ilgili alt kayıtları döndürür. Veya çağırabilirsiniz <xref:System.Data.DataRow.GetParentRow%2A> yöntemi bir <xref:System.Data.DataRow> alt tabloda. Bu yöntem tek bir döndüren <xref:System.Data.DataRow> üst tablodan.  
  
 Bu sayfa, türü belirlenmiş veri kümelerini kullanan örnekler sağlar. Yazılmayan veri kümeleri ilişkilerinde gezinme hakkında daha fazla bilgi için bkz: [gezinme DataRelations](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
>  Bir Windows Forms uygulamasında çalışan ve verileri görüntülemek için veri bağlama özellikleri kullanarak, tasarımcı tarafından oluşturulan form uygulamanız için yeterli işlevler sağlayabilir. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Özellikle, görmek[nasıl yapılır: Windows Forms uygulamasında görüntü ilgili verileri](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md) ve [izlenecek yol: bir Windows formunda ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md).  
  
 Aşağıdaki kod örnekleri, yazılan veri kümelerindeki ilişkiler yukarı ve aşağı gitmek nasıl ekleyebileceğiniz gösterilmektedir. Yazılan kod örneklerini kullanımı <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) ve oluşturulan `FindBy` *PrimaryKey* (`FindByCustomerID`) istenen satırı bulun ve ilgili kayıtları döndürmek için yöntemleri. Örnekleri derleme ve yalnızca varsa doğru bir şekilde çalıştırın:  
  
- Adlı bir veri kümesi örneği `NorthwindDataSet` ile bir `Customers` tablo.  
  
- Bir `Orders` tablo.  
  
- Adlı bir ilişki `FK_Orders_Customers`iki tablo, kod kapsamını ilgili  
  
  Ayrıca, her iki tablonun döndürülecek herhangi bir kayıt için verilerle doldurulması gerekir.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Alt seçili üst kaydının kayıtları döndürmek için  
  
-   Çağrı <xref:System.Data.DataRow.GetChildRows%2A> belirli bir yöntemi `Customers` veri satır ve bir dizi satır döndürür `Orders` tablosu:  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Seçilen alt kaydının üst kaydı döndürmek için  
  
-   Çağrı <xref:System.Data.DataRow.GetParentRow%2A> belirli bir yöntemi `Orders` veri satırı ve tek bir satır gelen dönüş `Customers` tablosu:  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]

