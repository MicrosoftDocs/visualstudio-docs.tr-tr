---
title: 'Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 810f65cbb021845c4fa659cd785e83e8c979376d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888677"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme
  Tanımladıktan sonra bir <xref:Microsoft.Office.Interop.Word.Range> değiştirmeniz, başlangıç ve bitiş noktalarını kullanarak bir Microsoft Office Word belgesinde nesne <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> ve <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> yöntemleri. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> Ve <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> yöntemleri aynı iki bağımsız değişkeni alır *birim* ve *sayısı*. *Sayısı* değişkendir taşımak için birim sayısını ve *birim* bağımsız değişkeni, aşağıdakilerden biri olabilir <xref:Microsoft.Office.Interop.Word.WdUnits> değerleri:  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  Aşağıdaki örnek, bir yedi karakter aralığı tanımlar. Özgün konum başlattığınızda ardından yedi aralığın karakter başlangıç konumunu taşır. Aralığın bitiş konumu da yedi karakterini başlangıç konumundan sonra olduğundan, sonuç sıfır karakterden oluşan bir aralıktır. Kod, ardından geçerli bitiş konumu sonra bitiş konumu yedi karakterini taşır.  
  
## <a name="to-extend-a-range"></a>Bir aralığı genişletmek için  
  
1.  Karakter aralığı tanımlayın. Daha fazla bilgi için [nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Kullanım <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Range> aralığın başlangıç konumunu taşımak için nesne.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Kullanım <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Range> aralığın bitiş konumu taşımak için nesne.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>Belge düzeyi özelleştirmesi kod  
  
### <a name="to-extend-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığı genişletmek için  
  
1.  Aşağıdaki örnek, bir belge düzeyi özelleştirmesi için tam kod gösterilir. Bu kodu kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>VSTO eklenti kodu  
  
### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Bir uygulama düzeyinde VSTO eklentisi bir aralıktaki genişletmek için  
  
1.  Aşağıdaki örnek, VSTO eklentisi için tam kod gösterilmektedir. Bu kodu kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Word belgelerinde aralıkları'program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Nasıl yapılır: aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla aralıkta başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Nasıl yapılır: program aracılığıyla paragraf işaretlerini aralık oluştururken hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  