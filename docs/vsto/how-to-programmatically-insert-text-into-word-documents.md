---
title: 'Nasıl yapılır: Word belgelerine program aracılığıyla metin ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a602f50e9d3c439fc450c286923341dafff1e116
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881670"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Nasıl yapılır: Word belgelerine program aracılığıyla metin ekleme
  Microsoft Office Word belgelerine metin eklemek için başlıca üç yolu vardır:  
  
-   Bir aralıktaki metin ekleyin.  
  
-   Bir aralıktaki metin yeni metinle değiştirir.  
  
-   Kullanım <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> yöntemi bir <xref:Microsoft.Office.Interop.Word.Selection> imlecin veya seçimin metin eklemek için nesne.  
  
> [!NOTE]  
>  Ayrıca, içerik denetimleri ve yer işaretlerine metin ekleyebilirsiniz. Daha fazla bilgi için [içerik denetimleri](../vsto/content-controls.md) ve [yer işareti denetimi](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="insert-text-in-a-range"></a>Bir aralıktaki metin Ekle  
 Kullanım <xref:Microsoft.Office.Interop.Word.Range.Text%2A> özelliği bir <xref:Microsoft.Office.Interop.Word.Range> bir belgede metin eklemek için nesne.  
  
### <a name="to-insert-text-in-a-range"></a>Bir aralıktaki metin eklemek için  
  
1.  Bir belgenin başında bir aralığı belirtin ve metin Ekle **yeni metin**.  
  
     Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir.  
  
     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]  
  
     Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu kod, etkin belgeyi kullanır.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]  
  
2.  Seçin <xref:Microsoft.Office.Interop.Word.Range> bir karakter eklenen metin uzunluğu genişletmiştir nesnesidir.  
  
     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]  
  
## <a name="replace-text-in-a-range"></a>Bir aralıktaki metni Değiştir  
 Belirtilen aralığı metin içeriyorsa, aralıktaki tüm metni eklenen metin ile değiştirilir.  
  
### <a name="to-replace-text-in-a-range"></a>Bir aralıktaki metni değiştirmek için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Interop.Word.Range> belgedeki ilk 12 karakter içeren bir nesne.  
  
     Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir.  
  
     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]  
  
     Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu kod, etkin belgeyi kullanır.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]  
  
2.  Bu karakter dizesi ile değiştirin **yeni metin**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]  
  
3.  Aralık seçin.  
  
     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]  
  
## <a name="insert-text-using-typetext"></a>TypeText kullanarak metin Ekle  
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> Yöntemi seçimi metin ekler. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> kullanıcının bilgisayarında ayarlanan seçeneklere bağlı olarak farklı davranır. Aşağıdaki yordamda kod bildirir bir <xref:Microsoft.Office.Interop.Word.Selection> nesne değişkenini ve kapatır **yazma** seçeneğini açık. Varsa **yazma** seçeneği etkinleştirilirse, sonra imleci yanındaki herhangi bir metin üzerine yazılır.  
  
### <a name="to-insert-text-using-the-typetext-method"></a>TypeText yöntemini kullanarak metin eklemek için  
  
1. Bildirme bir <xref:Microsoft.Office.Interop.Word.Selection> nesne değişkeni.  
  
    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]  
  
2. Devre dışı **yazma** seçeneğini açık.  
  
    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]  
  
3. Geçerli seçimi bir ekleme noktası olup olmadığını test edin.  
  
    Bu durumda, kodu kullanarak bir cümle ekler <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>ve ardından bir paragraf işareti kullanarak <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> yöntemi.  
  
    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]  
  
4. Kodda **ElseIf** block seçimi normal bir seçim olup olmadığını görmek için sınar. İse, başka bir **varsa** block görmek için sınar olmadığını **ReplaceSelection** seçeneği etkinleştirilir. İse, kod kullanır <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> seçimin seçili metin bloğunun başlangıcına bir ekleme noktasını seçimi daraltmak için yöntemi. Metin ve paragraf işareti ekleyin.  
  
    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]  
  
5. Seçimi bir ekleme noktasını veya seçilen metin ve ardından kod bloğu değilse **Else** blok hiçbir şey yapmaz.  
  
    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]  
  
   Ayrıca <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Selection> işlevselliğini taklit eden bir nesne, **geri** klavyenizde anahtar. Ancak, söz konusu olduğunda da ekleme ve metin düzenleme <xref:Microsoft.Office.Interop.Word.Range> nesne daha fazla denetim sağlar.  
  
   Aşağıdaki örnekte tam kod gösterilmektedir. Bu örneği kullanmak için kodu çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: belgelerde program aracılığıyla biçimlendirme metni](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  