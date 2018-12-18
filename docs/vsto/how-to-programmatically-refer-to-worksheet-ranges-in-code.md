---
title: 'Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla bakma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 608ce006ccc34330631da8d4c947405b027f1a1f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677206"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla bakma
  Benzer bir süreç içeriğine başvurmak için kullandığınız bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi veya yerel Excel range nesnesi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma  
 Aşağıdaki örnek ekler bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma ve hücre aralığı içinde metin ekler.  
  
### <a name="to-refer-to-a-namedrange-control"></a>NamedRange denetimine başvurmak için  
  
1.  Bir dizeye atama <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliği <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi. Bu kod, bir sayfa sınıfında değil yerleştirilmelidir `ThisWorkbook` sınıfı.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>Yerel Excel aralıkları kullanın  
 Aşağıdaki örnek, bir çalışma sayfasına yerel Excel aralığı ekler ve hücre aralığı içinde metin ekler.  
  
### <a name="to-refer-to-a-native-range-object"></a>Bir yerel aralığı nesnesine başvurmak için  
  
1.  Bir dizeye atama <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> aralık özelliği.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Aralıklarla çalışma](../vsto/working-with-ranges.md)   
 [Nasıl yapılır: program aracılığıyla çalışma sayfaları Yazımı denetleme](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara biçimler uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Nasıl yapılır: program aracılığıyla otomatik biçimde aralıkları artımlı şekilde değişen verilerle ile doldurun.](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Nasıl yapılır: program aracılığıyla çalışma sayfası aralıklarında metin arama](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  