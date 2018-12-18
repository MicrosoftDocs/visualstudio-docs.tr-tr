---
title: 'Nasıl yapılır: çalışma sayfasında satırları program aracılığıyla gruplama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa9624f90a337fb85ba2868b3b5c4f3cb1553ffb
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258742"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Nasıl yapılır: çalışma sayfasında satırları program aracılığıyla gruplama
  Bir veya daha fazla satırı gruplayabilirsiniz. Bir çalışma sayfasına bir grup oluşturmak için kullanın bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi veya yerel bir Excel aralık nesnesi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanın  
 Eklerseniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi için belge düzeyi proje tasarım zamanında denetimi program aracılığıyla bir grup oluşturmak için kullanabilirsiniz. Aşağıdaki örnekte, üç olduğunu varsayar <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimleri aynı çalışma sayfası üzerinde: `data2001`, `data2002`, ve `dataAll`. Her adlandırılmış bir aralık çalışma tam bir satıra ifade eder.  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>NamedRange denetimlerinin çalışma sayfası üzerinde bir grup oluşturmak için  
  
1.  Üç adlandırılmış aralıkları çağırarak grup <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> her aralığın yöntemi. Bu kod sayfa sınıfında değil yerleştirilmelidir `ThisWorkbook` sınıfı.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Satır çözmek için arama <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> yöntemi.  
  
## <a name="use-native-excel-ranges"></a>Yerel Excel aralıkları kullanın  
 Kod adında üç Excel aralıklarında olduğunu varsayar `data2001`, `data2002`, ve `dataAll` çalışma sayfası üzerinde.  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Bir çalışma sayfasında Excel aralıklarında bir grup oluşturmak için  
  
1.  Üç adlandırılmış aralıkları çağırarak grup <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> her aralığın yöntemi. Aşağıdaki örnekte, üç olduğunu varsayar <xref:Microsoft.Office.Interop.Excel.Range> adlı denetimleri `data2001`, `data2002`, ve `dataAll` aynı çalışma sayfası üzerinde. Her adlandırılmış bir aralık çalışma tam bir satıra ifade eder.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Satır çözmek için arama <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çalışma sayfaları ile çalışma](../vsto/working-with-worksheets.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  