---
title: 'Nasıl yapılır: çalışma sayfalarını program aracılığıyla kopyalama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eddecb7bdb087797bc3f9f4abf4841ab4cdf97b5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256545"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Nasıl yapılır: çalışma sayfalarını program aracılığıyla kopyalama
  Bir çalışma sayfasına bir kopyasını oluşturun ve çalışma önce veya sonra varolan bir çalışma kitabındaki ekleyin. Excel çalışma sayfası eklemek istediğiniz yeri belirtmezseniz, yeni çalışma içeren yeni bir çalışma kitabı oluşturur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Program aracılığıyla çalışma sayfası kopyalama ister el ile son kullanıcı çalışma kopyalar, yeni çalışma arkasındaki kodu yok ve yeni çalışma sayfasına denetimler çalışmaz. Yeni kopyalanan çalışma sayfası Bunun nedeni bir <xref:Microsoft.Office.Interop.Excel.Worksheet> nesne ve bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi. Windows Forms denetimleri ve ana bilgisayar denetimleri yalnızca konak öğelerine eklenebilir. Daha fazla bilgi için bkz: [konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmelerinde çalışma kitabına kopyalanan bir çalışma sayfası eklemek için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> geçerli çalışma kitabına ilk çalışma kopyalamak ve kopyayı üçüncü sayfadan sonra yerleştirmek için yöntem.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Çalışma kitabında VSTO eklenti kopyalanan bir çalışma sayfası eklemek için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> geçerli çalışma kitabına ilk çalışma kopyalamak ve kopyayı üçüncü sayfadan sonra yerleştirmek için yöntem.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çalışma sayfaları ile çalışma](../vsto/working-with-worksheets.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Nasıl yapılır: program aracılığıyla yeni çalışma sayfaları çalışma kitaplarına ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarından çalışma sayfaları silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Nasıl yapılır: program aracılığıyla çalışma sayfalarını seçin](../vsto/how-to-programmatically-select-worksheets.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  