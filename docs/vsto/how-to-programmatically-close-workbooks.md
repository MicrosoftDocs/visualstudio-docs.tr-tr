---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma'
description: Etkin çalışma kitabını nasıl kapatabileceğinizi veya program aracılığıyla kapatılacak bir çalışma kitabı belirtebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d09cbff06b1bb7048316629b7b958ee299029ec8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825270"
---
# <a name="how-to-programmatically-close-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma
  Etkin çalışma kitabını kapatabilir veya kapatılacak bir çalışma kitabı belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Etkin çalışma kitabını kapatma
 Etkin çalışma kitabını kapatmak için iki yordam vardır: biri belge düzeyinde özelleştirmeler ve VSTO eklentileri için bir tane.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki etkin çalışma kitabını kapatmak için

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A>Özelleştirme ile ilişkili çalışma kitabını kapatmak için yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `Sheet1` Excel için belge düzeyi projesi içindeki sınıfında çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Bir VSTO eklentisinin etkin çalışma kitabını kapatmak için

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A>Etkin çalışma kitabını kapatmak için yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `ThisAddIn` Excel IÇIN VSTO eklenti projesindeki sınıfında çalıştırın.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Ada göre belirttiğiniz bir çalışma kitabını kapatma
 Ada göre belirttiğiniz bir çalışma kitabını kapatmanıza olanak, VSTO eklentileri ve belge düzeyi özelleştirmeleri için aynıdır.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Adına göre belirttiğiniz çalışma kitabını kapatmak için

1. Çalışma kitabı adını koleksiyona bir bağımsız değişken olarak belirtin <xref:Microsoft.Office.Interop.Excel.Workbooks> . Aşağıdaki kod örneği, **NewWorkbook** adlı bir çalışma kitabının Excel 'de açık olduğunu varsayar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
