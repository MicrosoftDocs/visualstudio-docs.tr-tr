---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09e477d802b9d92ca4f9e1cd3a532145ad0e68a0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677917"
---
# <a name="how-to-programmatically-select-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Yöntemi yeni nesneye kullanıcının seçimi taşır belirtilen nesneyi seçer. Kullanım <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> yöntemi, kullanıcının seçimini değiştirmeden nesnesine odaklanmak istiyorsanız.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO eklentisi içinde varolan bir çalışma sayfası seçin veya çalışma zamanında belge düzeyi özelleştirmesinde oluşturulduysa, Excel kullanarak erişebilmesi gerekir istiyorsanız <xref:Microsoft.Office.Interop.Excel.Sheets> Excel çalışma kitabı; koleksiyonunu Aksitakdirde,erişebileceğiniz<xref:Microsoft.Office.Tools.Excel.Worksheet>doğrudan konak öğesi.  
  
## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesi kullanın  
 Belge düzeyi özelleştirmesinde, aşağıdaki kodu ekleyin *Sheet1.vb* veya *Sheet1.cs*.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>İlk çalışma sayfası konak öğesi kullanarak bir çalışma kitabında seçmek için  
  
1.  Çağrı <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> yöntemi `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabını sayfaları koleksiyonunu kullanın  
 Excel kullanarak çalışma sayfasına erişin <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyonu.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabı ve sayfalar koleksiyonunu kullanarak bir çalışma kitabında ilk çalışma sayfası seçin  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> yöntemi <xref:Microsoft.Office.Interop.Excel.Sheets> ilk çalışma etkin çalışma kitabının seçmek için koleksiyon.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çalışma sayfaları ile çalışma](../vsto/working-with-worksheets.md)   
 [Nasıl yapılır: çalışma sayfalarını program aracılığıyla yazdırma](../vsto/how-to-programmatically-print-worksheets.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarından çalışma sayfaları silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Nasıl yapılır: çalışma sayfalarını program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Nasıl yapılır: çalışma sayfalarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)   
 [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)  
  
  