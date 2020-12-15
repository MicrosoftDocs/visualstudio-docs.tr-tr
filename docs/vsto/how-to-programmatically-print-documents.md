---
title: 'Nasıl yapılır: program aracılığıyla belgeleri yazdırma'
description: Bir Microsoft Word belgesinin tamamını veya bir belgenin bir bölümünü varsayılan yazıcınıza nasıl yazdırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e17976c86a519db3c5edcd60c426b5d20e84b526
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523923"
---
# <a name="how-to-programmatically-print-documents"></a>Nasıl yapılır: program aracılığıyla belgeleri yazdırma
  Bir Microsoft Office Word belgesinin tamamını veya bir belgenin bir kısmını varsayılan yazıcınıza yazdırabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi yazdırma

### <a name="to-print-the-entire-document"></a>Tüm belgeyi yazdırmak için

1. <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> `ThisDocument` Tüm belgeyi yazdırmak için projenizdeki sınıfının yöntemini çağırın. Bu örneği kullanmak için, sınıfından kodu çalıştırın `ThisDocument` .

     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]

### <a name="to-print-the-current-page-of-the-document"></a>Belgenin geçerli sayfasını yazdırmak için

1. <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> `ThisDocument` Projenizdeki sınıfının yöntemini çağırın ve geçerli sayfanın bir kopyasının yazdırılacağını belirtin. Bu örneği kullanmak için, sınıfından kodu çalıştırın `ThisDocument` .

     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]

## <a name="print-a-document-by-using-a-vsto-add-in"></a>VSTO eklentisini kullanarak belge yazdırma

### <a name="to-print-an-entire-document"></a>Belgenin tamamını yazdırmak için

1. Yazdırmak istediğiniz <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> nesnenin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> . Aşağıdaki kod örneği etkin belgeyi yazdırır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]

### <a name="to-print-the-current-page-of-a-document"></a>Belgenin geçerli sayfasını yazdırmak için

1. Yazdırmak istediğiniz <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> nesnenin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> ve geçerli sayfanın bir kopyasının yazdırılacağını belirtin. Aşağıdaki kod örneği etkin belgeyi yazdırır. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
