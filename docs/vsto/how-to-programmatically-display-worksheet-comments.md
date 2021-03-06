---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme'
description: Belge düzeyinde veya uygulama düzeyinde Microsoft Excel çalışma sayfasındaki açıklamaları program aracılığıyla nasıl gösterip gizleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828676"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme
  Microsoft Office Excel çalışma sayfalarındaki açıklamaları programlı bir şekilde gösterebilir ve gizleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasındaki tüm açıklamaları göstermek için

1. <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>Açıklamaları göstermek istiyorsanız özelliği **true** olarak ayarlayın; Aksi takdirde **false**. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Uygulama düzeyindeki bir VSTO eklentisinin çalışma sayfasındaki tüm açıklamaları görüntüleme

1. <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>Açıklamaları göstermek istiyorsanız özelliği **true** olarak ayarlayın; Aksi takdirde **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
