---
title: 'Nasıl yapılır: ListObject sütunlarını verilerle eşleme'
description: SetDataBinding metodunu çağırdığınızda ListObject 'te görünmesini istediğiniz sütunları nasıl eşleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68cb12503d0f8ad59de92f965c0ed51fbc0d7f40
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827467"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Nasıl yapılır: ListObject sütunlarını verilerle eşleme
  Bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi öğesine bağladığınızda <xref:System.Data.DataTable> , bir listedeki tüm sütunları göstermek istemeyebilirsiniz veya verilere bağlı olmayan belirli sütunlara sahip olabilirsiniz. Yöntemini çağırdığınızda içinde görünmesini istediğiniz sütunları eşleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Harita sütunları

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Bir veri tablosunu bir listedeki sütunlarla eşlemek için

1. <xref:System.Data.DataTable>Sınıf düzeyinde oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. `Startup` `Sheet1` Sınıfın (belge düzeyi projesinde) veya `ThisAddIn` sınıfında (VSTO eklenti projesindeki) olay işleyicisine örnek sütun ve veri ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Yöntemi çağırın <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> ve sütun adlarını görünmesi gereken sırada geçirin. Liste nesnesi yeni oluşturulan ' e bağlanacak <xref:System.Data.DataTable> , ancak liste nesnesindeki sütunların sırası içinde göründükleri sırada farklılık gösterir <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Eşlenmemiş sütunları belirt
 Sütunları bir ile eşleştirdiğinizde <xref:System.Data.DataTable> , belirli sütunların boş bir dizeye geçerek veriye bağlanmamalıdır. Veriye bağlanmamış yeni bir sütun daha sonra <xref:Microsoft.Office.Tools.Excel.ListObject> denetime eklenir.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>ListObject sütunlarını eşlerken eşlenmemiş bir sütun belirtmek için

1. Yöntemi çağırın <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> ve sütun adlarını görünmesi gereken sırada geçirin. Eşlenmemiş bir sütunun eklendiğini göstermek için boş bir dize kullanın; Bu durumda, başlık sütunu ve soyadı sütunu arasında.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği, <xref:Microsoft.Office.Tools.Excel.ListObject> `list1` Bu kodun göründüğü çalışma sayfasında var olan bir ada sahip olduğunuzu varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: ListObject denetimlerini verilerle Doldur](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject denetimi](../vsto/listobject-control.md)
