---
title: 'Nasıl yapılır: eşleme ListObject sütunlarıyla verileri'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b77d33b8d30ed7f581e27e1cbe07d0c90715ff04
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677734"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Nasıl yapılır: eşleme ListObject sütunlarıyla verileri
  Bağladığınızda bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi bir <xref:System.Data.DataTable>, listedeki tüm sütunları görüntülemek istemeyebilirsiniz veya verilerine bağlı olmayan bazı sütunları olabilir. Görünmesini istediğiniz sütunları eşlemeniz <xref:Microsoft.Office.Tools.Excel.ListObject> çağırdığınızda <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> yöntemi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![video bağlantı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [nasıl bir SharePoint listesine bağlı Excel'de bir listesi: oluşturma musunuz?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="map-columns"></a>Sütun eşleme  
  
### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Bir veri tablosuna sütun listesinde eşlemek için  
  
1.  Oluşturma <xref:System.Data.DataTable> sınıf düzeyinde.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Örnek sütunları ve verileri ekleme `Startup` olay işleyicisine `Sheet1` sınıfı (belge düzeyi projede) veya `ThisAddIn` (bir VSTO eklenti projesinde sınıftaki).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Çağrı <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> yöntemi ve sütun adları göründükleri sırayla geçirin. Liste nesnesi bağlı için yeni oluşturulan <xref:System.Data.DataTable>, ancak liste nesnesinde sütunların sırasını sırada görüntülendiğini içinde farklılık gösterir <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specify-unmapped-columns"></a>Eşlenmemiş sütunları belirtme  
 Sütunları eşlemeniz ne zaman bir <xref:System.Data.DataTable>, belirli sütunları veri için boş bir dize olarak geçirerek bağlanmalıdır değil olduğunu da belirtebilirsiniz. Verilere bağlı olmayan yeni bir sütun daha sonra eklenen <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi.  
  
### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>ListObject sütunlarıyla eşlerken eşlenmemiş bir sütun belirtmek için  
  
1.  Çağrı <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> yöntemi ve sütun adları göründükleri sırayla geçirin. Burada eşlenmemiş bir sütun eklenir belirtmek için boş bir dize kullanın. Bu durumda, başlık sütunu arasında son ad sütunu.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu kod örneği, mevcut bir varsayar <xref:Microsoft.Office.Tools.Excel.ListObject> adlı `list1` bu kodu göründüğü çalışma.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Nasıl yapılır: dolgu ListObject denetimlerini veri ile](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject denetimi](../vsto/listobject-control.md)  
  
  