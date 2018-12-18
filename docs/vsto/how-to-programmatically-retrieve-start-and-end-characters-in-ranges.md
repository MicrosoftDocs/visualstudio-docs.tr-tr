---
title: 'Nasıl yapılır: program aracılığıyla aralıkta başlangıç ve bitiş karakterlerini alma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1244fb2ba0a9e902d4dd853e7bef25376a205a0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676879"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Nasıl yapılır: program aracılığıyla aralıkta başlangıç ve bitiş karakterlerini alma
  Bu örnek aralığının başlangıç ve bitiş konumları karakter konumlarını nasıl aldığını gösterir.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesinde aralığın başlangıç ve bitiş karakterlerini almak için  
  
1.  Değerlerini alın <xref:Microsoft.Office.Interop.Word.Range.Start%2A> ve <xref:Microsoft.Office.Interop.Word.Range.End%2A> özelliklerini <xref:Microsoft.Office.Interop.Word.Range> nesne. Aşağıdaki kod örneği, ikinci cümlenin belgedeki başlangıç ve bitiş konumları alır. Bu kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Aralığın başlangıç ve bitiş karakterlerini bir VSTO eklentisi kullanarak almak için  
  
1.  Değerlerini alın <xref:Microsoft.Office.Interop.Word.Range.Start%2A> ve <xref:Microsoft.Office.Interop.Word.Range.End%2A> özelliklerini <xref:Microsoft.Office.Interop.Word.Range> nesne. Aşağıdaki kod örneği, etkin belgedeki ikinci cümle başlangıç ve bitiş konumu alır. Bu kod örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Nasıl yapılır: Word belgelerinde aralıkları'program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Nasıl yapılır: aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla paragraf işaretlerini aralık oluştururken hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Nasıl yapılır: program aracılığıyla karakter sayma sayısı](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  