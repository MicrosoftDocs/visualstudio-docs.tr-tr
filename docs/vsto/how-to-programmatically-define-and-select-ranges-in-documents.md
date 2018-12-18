---
title: 'Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8770871bfdc361e29d7ac7c2fc984477b1ec0ea1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833141"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin
  Kullanarak Microsoft Office Word belgesindeki bir aralığın tanımlayabilirsiniz bir <xref:Microsoft.Office.Interop.Word.Range> nesne. Kullanarak, örneğin, bir çeşitli yollarla, tüm belgede seçebilirsiniz <xref:Microsoft.Office.Interop.Word.Range.Select%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Range> içerik özelliğini kullanarak veya nesne <xref:Microsoft.Office.Tools.Word.Document> sınıfta (belge düzeyi özelleştirmeleri için) veya <xref:Microsoft.Office.Interop.Word.Document> sınıfı (içinde bir VSTO eklenti).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="define-a-range"></a>Bir aralığı tanımlayın  
 Aşağıdaki örnek, yeni bir oluşturma işlemi gösterilmektedir <xref:Microsoft.Office.Interop.Word.Range> karakterleri yazdırılamayan karakterleri dahil olmak üzere etkin belgede ilk yedi içeren nesne. Ardından, metin aralığı içinde seçer.  
  
### <a name="to-define-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığını tanımlamak için  
  
1.  Aralığın başlangıç ve bitiş karakteri geçirerek belgeye eklediğiniz <xref:Microsoft.Office.Tools.Word.Document.Range%2A> yöntemi <xref:Microsoft.Office.Tools.Word.Document> sınıfı. Bu kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Bir VSTO eklentisi kullanarak bir aralığını tanımlamak için  
  
1.  Aralığın başlangıç ve bitiş karakteri geçirerek belgeye eklediğiniz <xref:Microsoft.Office.Interop.Word._Document.Range%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Document> sınıfı. Aşağıdaki kod örneği, etkin belgeye bir aralığı ekler. Bu kod örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="select-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralık seçin  
 Aşağıdaki örnekler kullanarak tüm belgeyi Seç nasıl <xref:Microsoft.Office.Interop.Word.Range.Select%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Range> kullanarak veya nesne <xref:Microsoft.Office.Tools.Word.Document.Content%2A> özelliği <xref:Microsoft.Office.Tools.Word.Document> sınıfı.  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Tüm belgeyi Seç yöntemi kullanarak bir aralık olarak seçmek için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Word.Range.Select%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Range> , belgenin tamamını içerir. Aşağıdaki kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>İçerik özelliği kullanarak tüm belgenin bir aralık olarak seçmek için  
  
1. Kullanım <xref:Microsoft.Office.Tools.Word.Document.Content%2A> belgenin tamamını kapsayan bir aralığını tanımlamak üzere özelliği.  
  
    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
   Bir aralığını tanımlamak için diğer nesnelerin özelliklerini ve yöntemlerini kullanabilirsiniz.  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>Etkin belgeye bir cümle seçmek için  
  
1. Aralığı kullanarak ayarlayın <xref:Microsoft.Office.Interop.Word.Sentences> koleksiyonu. Seçmek istediğiniz cümle dizinini kullanın.  
  
    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
   Bir cümle seçmek için başka bir aralık için başlangıç ve bitiş değerlerini el ile ayarlamak için yoludur.  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>El ile başlangıç ve bitiş değerleri ayarlayarak bir cümle seçmek için  
  
1.  Aralık değişkeni oluşturun.  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  Belgede, en az iki cümle olup olmadığını görmek için onay ayarlayın *Başlat* ve *son* aralığı tıklayın ve ardından aralık bağımsız değişkenleri.  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="select-a-range-by-using-a-vsto-add-in"></a>Bir VSTO eklentisi kullanarak bir aralık seçin  
 Aşağıdaki örnekler kullanarak tüm belgeyi Seç nasıl <xref:Microsoft.Office.Interop.Word.Range.Select%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Range> kullanarak veya nesne <xref:Microsoft.Office.Interop.Word._Document.Content%2A> özelliği <xref:Microsoft.Office.Interop.Word.Document> sınıfı.  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Tüm belgeyi Seç yöntemi kullanarak bir aralık olarak seçmek için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Word.Range.Select%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Range> , belgenin tamamını içerir. Aşağıdaki kod örneği, etkin belgenin içeriğini seçer. Bu kod örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>İçerik özelliği kullanarak tüm belgenin bir aralık olarak seçmek için  
  
1. Kullanım <xref:Microsoft.Office.Interop.Word._Document.Content%2A> belgenin tamamını kapsayan bir aralığını tanımlamak üzere özelliği.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
   Bir aralığını tanımlamak için diğer nesnelerin özelliklerini ve yöntemlerini kullanabilirsiniz.  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>Etkin belgeye bir cümle seçmek için  
  
1. Aralığı kullanarak ayarlayın <xref:Microsoft.Office.Interop.Word.Sentences> koleksiyonu. Seçmek istediğiniz cümle dizinini kullanın.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
   Bir cümle seçmek için başka bir aralık için başlangıç ve bitiş değerlerini el ile ayarlamak için yoludur.  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>El ile başlangıç ve bitiş değerleri ayarlayarak bir cümle seçmek için  
  
1.  Aralık değişkeni oluşturun.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  Belgede, en az iki cümle olup olmadığını görmek için onay ayarlayın *Başlat* ve *son* aralığı tıklayın ve ardından aralık bağımsız değişkenleri.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla aralıkta başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Nasıl yapılır: Word belgelerinde aralıkları'program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Nasıl yapılır: aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla paragraf işaretlerini aralık oluştururken hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  