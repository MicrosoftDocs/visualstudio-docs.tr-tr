---
title: 'Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38aa92ae1c320ae9eb5ad4bdb1e43b761048661f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547140"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme
  Çalışma kitabındaki tüm çalışma sayfalarını silebilirsiniz. Çalışma sayfasını silmek için çalışma sayfası konak öğesini kullanın veya çalışma kitabının sayfalar koleksiyonunu kullanarak çalışma sayfasına erişin.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesini kullan
 Belge düzeyi özelleştirmesindeki çalışma sayfası tasarım zamanında eklendiyse, <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> belirtilen çalışma sayfasını silmek için yöntemini kullanın. Aşağıdaki kod, çalışma sayfası konak öğesine doğrudan başvurarak çalışma kitabını çalışma kitabından siler.

> [!IMPORTANT]
> Bu kod yalnızca aşağıdaki proje şablonlarından birini kullanarak oluşturduğunuz projelerde çalışır:
>
> - Excel 2013 çalışma kitabı
> - Excel 2013 şablonu
> - Excel 2010 Çalışma Kitabı
> - Excel 2010 Şablonu
>
>   Bu görevi başka bir proje türünde gerçekleştirmek istiyorsanız, **Microsoft. Office. Interop. Excel** derlemesine bir başvuru eklemeniz ve ardından çalışma kitabını açmak ve bir çalışma sayfasını silmek için bu derlemedeki sınıfları kullanmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma derlemeleri](how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Excel 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md)aracılığıyla Office uygulamalarını hedefleme.

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Çalışma sayfası konak öğesi kullanarak çalışma sayfasını silmek için

1. Yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabının sayfalar koleksiyonunu kullanın
 Aşağıdaki durumlarda Microsoft Office Excel koleksiyonu aracılığıyla çalışma sayfalarına erişin <xref:Microsoft.Office.Interop.Excel.Sheets> :

- Bir VSTO eklentisinin çalışma sayfasını silmek istiyorsunuz.

- Silmek istediğiniz çalışma sayfası, çalışma zamanında belge düzeyi özelleştirmesinde oluşturulmuştur.

  Aşağıdaki **kod, sayfa koleksiyonunun Dizin** numarası aracılığıyla sayfaya başvurarak çalışma kitabından bir çalışma sayfasını siler. Bu kod, yeni bir çalışma sayfasının programlı bir şekilde oluşturulduğunu varsayar.

> [!IMPORTANT]
> Bu görevi başka bir proje türünde gerçekleştirmek istiyorsanız, **Microsoft. Office. Interop. Excel** derlemesine bir başvuru eklemeniz ve ardından çalışma kitabını açmak ve bir çalışma sayfasını silmek için bu derlemedeki sınıfları kullanmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma derlemeleri](how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Excel 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md)aracılığıyla Office uygulamalarını hedefleme.

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabının sayfalar koleksiyonunu kullanarak bir çalışma sayfasını silmek için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A>Koleksiyonun yöntemini çağırın <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme](how-to-programmatically-select-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Çalışma sayfası konak öğesi](worksheet-host-item.md)
- [Office Projelerindeki Nesnelere Genel erişim](global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](programmatic-limitations-of-host-items-and-host-controls.md)
