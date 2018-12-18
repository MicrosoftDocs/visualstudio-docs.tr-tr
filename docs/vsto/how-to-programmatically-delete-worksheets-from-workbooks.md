---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarından çalışma sayfaları silme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 73c501d545f76012b63bde291001b38c214c3eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950231"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarından çalışma sayfaları silme
  Çalışma kitabındaki silebilirsiniz. Bir çalışma sayfası silmek için çalışma sayfası konak öğesi kullanın veya çalışma kitabını sayfaları koleksiyonunu kullanarak çalışma sayfasına erişin.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesi kullanın  
 Belge düzeyi özelleştirmesinde tasarım zamanında çalışma eklendiyse kullanın <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> belirtilen çalışma silmek için yöntemi. Aşağıdaki kod, çalışma sayfası konak öğesi doğrudan başvuruda bulunarak, bir çalışma kitabından çalışma siler.  
  
> [!IMPORTANT]
>  Şu proje şablonlarını kullanarak oluşturduğunuz projelerde bu kodu çalıştırır:  
> 
> - Excel 2013'ün çalışma kitabı  
> - Excel 2013 şablonu  
> - Excel 2010 Çalışma Kitabı  
> - Excel 2010 Şablonu  
> 
>   Bu görev başka bir türü proje içinde gerçekleştirmek istiyorsanız, bir başvuru eklemelisiniz **Microsoft.Office.Interop.Excel** derleme ve daha sonra derlemeye sınıflardan bir çalışma kitabını açıp bir çalışma sayfasını silmek için kullanmalısınız. Daha fazla bilgi için [nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Excel 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Bir çalışma sayfası bir çalışma sayfası konak öğesi kullanarak silmek için  
  
1.  Çağrı <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> yöntemi `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabını sayfaları koleksiyonunu kullanın  
 Microsoft Office Excel çalışma sayfalarına erişim <xref:Microsoft.Office.Interop.Excel.Sheets> aşağıdaki durumlarda koleksiyonu:  
  
- Bir VSTO eklentisi çalışma silmek istediğiniz.  
  
- Silmek istediğiniz çalışma sayfası, belge düzeyinde özelleştirme çalışma zamanında oluşturuldu.  
  
  Aşağıdaki kod bir çalışma kitabından dizin numarasını sayfasını başvurarak siler **sayfaları** koleksiyonu. Bu kod, yeni bir çalışma sayfasına programlı bir şekilde oluşturulduğunu varsayar.  
  
> [!IMPORTANT]  
>  Bu görev başka bir türü proje içinde gerçekleştirmek istiyorsanız, bir başvuru eklemelisiniz **Microsoft.Office.Interop.Excel** derleme ve daha sonra derlemeye sınıflardan bir çalışma kitabını açıp bir çalışma sayfasını silmek için kullanmalısınız. Daha fazla bilgi için [nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Excel 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Çalışma sayfalarını Excel çalışma kitabını koleksiyonunu kullanarak silmek için  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> yöntemi <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyonu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çalışma sayfaları ile çalışma](../vsto/working-with-worksheets.md)   
 [Nasıl yapılır: çalışma sayfalarını program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Nasıl yapılır: program aracılığıyla kitaplarındaki taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme](../vsto/how-to-programmatically-select-worksheets.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitapları için yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)   
 [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  