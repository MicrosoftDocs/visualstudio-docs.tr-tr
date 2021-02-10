---
title: 'Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama'
description: Visual Studio 'Yu kullanarak bir Microsoft Word belgesinde varolan bir aralığı programlı olarak yeniden boyutlandırma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 562b4dab6c26af12760190b01ff460c7080a3bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958784"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama
  <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A>Microsoft Office Word belgesinde mevcut bir aralığı yeniden boyutlandırmak için yöntemini kullanın.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Mevcut bir aralığı sıfırlamak için

1. Belgedeki ilk yedi karakterle başlayan bir başlangıç aralığı ayarlayın.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu kod etkin belgeyi kullanır.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A>Aralığı ikinci tümcede başlatmak ve beşinci tümcenin sonunda sonlandırmak için kullanın.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Document-Level özelleştirme örneği

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki mevcut bir aralığı sıfırlamak için

1. Aşağıdaki örnekte, belge düzeyi özelleştirmesi için tam örnek gösterilmektedir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>VSTO eklentideki mevcut bir aralığı sıfırlamak için

1. Aşağıdaki örnekte, VSTO eklentisi için tam örnek gösterilmektedir. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: aralıklarda program aracılığıyla başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl yapılır: belgelerde aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
