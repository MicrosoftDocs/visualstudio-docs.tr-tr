---
title: 'Nasıl yapılır: aralıkları veya seçimleri program aracılığıyla daraltma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fee3c821c0b6a39c8dfb499caa00355aa008d413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906734"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Nasıl yapılır: aralıkları veya seçimleri program aracılığıyla daraltma
  İle çalışıyorsanız bir <xref:Microsoft.Office.Interop.Word.Range> veya <xref:Microsoft.Office.Interop.Word.Selection> nesnesi, metnin üstüne yazarak önlemek için metin eklemeden önce bir ekleme noktasını seçimi değiştirmek isteyebilirsiniz. Hem <xref:Microsoft.Office.Interop.Word.Range> ve <xref:Microsoft.Office.Interop.Word.Selection> nesneleri kullanan bir Daralt yöntemi sahip <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> sabit listesi değerleri:  
  
- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> Seçimi seçimin başına daraltır. Bu, bir sabit listesi değeri belirtmezseniz varsayılan değerdir.  
  
- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> Seçimi, seçim sonuna daraltır.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-collapse-a-range-and-insert-new-text"></a>Bir aralığı daraltmak ve yeni metin eklemek için  
  
1. Oluşturma bir <xref:Microsoft.Office.Interop.Word.Range> belgedeki ilk paragrafa içeren nesne.  
  
    Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir.  
  
    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]  
  
    Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu kod, etkin belgeyi kullanır.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]  
  
2. Kullanım <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> aralığı daraltmak için numaralandırma değeri.  
  
    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]  
  
3. Yeni metin ekleyin.  
  
    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]  
  
4. Seçin <xref:Microsoft.Office.Interop.Word.Range>.  
  
    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
   Kullanırsanız <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> numaralandırma değeri, metin, aşağıdaki paragraf başına eklenir.  
  
   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
   Özgün aralığın paragraf işaretçisini içerdiğinden ekleyerek yeni bir cümle, paragraf işaretçisini, ancak durum önce diğer bir deyişle ekleneceğini bekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: aralık oluştururken program aracılığıyla hariç tutma paragraf işaretlerini](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği  
  
### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığı daraltmak için  
  
1.  Aşağıdaki örnek, bir belge düzeyi özelleştirmesi için ayrıntılı bir yöntemi gösterir. Bu kodu kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## <a name="vsto-add-in-example"></a>VSTO eklenti örneği  
  
### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Bir VSTO eklentisi bir aralıktaki daraltmak için  
  
1.  Aşağıdaki örnek, VSTO eklentisi için ayrıntılı bir yöntemi gösterir. Bu kodu kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla aralıkta başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Nasıl yapılır: program aracılığıyla paragraf işaretlerini aralık oluştururken hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Nasıl yapılır: Word belgelerinde aralıkları'program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  