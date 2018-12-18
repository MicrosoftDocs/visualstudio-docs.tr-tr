---
title: 'Nasıl yapılır: çalışma sayfalarında verileri programlamayla sıralama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 179cf5fab5a1b2690cb4b46160f7a5c3342fe7bc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914222"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Nasıl yapılır: çalışma sayfalarında verileri programlamayla sıralama
  Çalışma zamanında çalışma sayfası aralıklarına ve listelerinde bulunan verileri sıralayabilirsiniz. Aşağıdaki kodu adlı bir çok sütunlu aralık sıralar `Fruits` ilk sütunundaki verileri ve ardından ikinci sütundaki verileri.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sort-data-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesinde verileri sıralama  
  
### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange denetimi verileri sıralama  
  
1. Çağrı <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> yöntemi <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi. Aşağıdaki örnek gerektiren bir <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `Fruits` çalışma sayfasında. Bu kod, bir sayfa sınıfında değil yerleştirilmelidir `ThisWorkbook` sınıfı.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
   Aşağıdaki kodda yerleştirin *Sheet1.vb* veya *Sheet1.cs* verileri sıralamak için bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi. Kod, olduğunu varsayar bir <xref:Microsoft.Office.Tools.Excel.ListObject> adlı Denetim `fruitList` adlı çalışma sayfasındaki `Sheet1`.  
  
### <a name="to-sort-data-in-a-listobject-control"></a>ListObject denetiminde verileri sıralama  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> yöntemi <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> özelliği <xref:Microsoft.Office.Tools.Excel.ListObject> konak kontrolü.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sort-data-in-a-vsto-add-in"></a>Bir VSTO eklentisi verileri sıralama  
  
### <a name="to-sort-data-in-a-native-range"></a>Yerel bir aralıkta verileri sıralamak için  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> yöntemi yerel Excel <xref:Microsoft.Office.Interop.Excel.Range> denetimi. Aşağıdaki örnekte adlı yerel bir Excel Denetim gerektiren `Fruits` çalışma sayfasında.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
### <a name="to-sort-data-in-a-listobject-control"></a>ListObject denetiminde verileri sıralama  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> yöntemi <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> özelliği yerel Excel <xref:Microsoft.Office.Interop.Excel.ListObject> denetimi. Aşağıdaki örnek, yerel bir Excel sahibi olduğunuzu varsayar <xref:Microsoft.Office.Interop.Excel.ListObject> adlı Denetim `fruitList` etkin çalışma sayfasındaki.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çalışma sayfaları ile çalışma](../vsto/working-with-worksheets.md)   
 [Nasıl yapılır: program aracılığıyla otomatik biçimde aralıkları artımlı şekilde değişen verilerle ile doldurun.](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla bakma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara biçimler uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [ListObject denetimi](../vsto/listobject-control.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  