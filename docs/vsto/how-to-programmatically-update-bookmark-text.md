---
title: 'Nasıl yapılır: yer işareti metnini program aracılığıyla güncelleştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efa56c94e211a40e314025ae06d263164de1afd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833024"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Nasıl yapılır: yer işareti metnini program aracılığıyla güncelleştirme
  Sonraki bir zamanda ya da yer işaretindeki metnin yerine metnin alabilmeleri Microsoft Office Word belgesindeki bir yer tutucu yer işareti içinde metin ekleyebilirsiniz. Ayrıca belge düzeyinde özelleştirme geliştiriyorsanız metinde güncelleştirebilirsiniz bir <xref:Microsoft.Office.Tools.Word.Bookmark> veriye bağlı denetim. Daha fazla bilgi için [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Yer işareti nesnesi iki türden biri olabilir:  
  
- A <xref:Microsoft.Office.Tools.Word.Bookmark> konak kontrolü.  
  
   <xref:Microsoft.Office.Tools.Word.Bookmark> denetimleri uzatma yerel <xref:Microsoft.Office.Interop.Word.Bookmark> veri bağlamayı ve olayları açığa etkinleştirerek nesneleri. Konak denetimleri hakkında daha fazla bilgi için bkz: [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
- Yerel <xref:Microsoft.Office.Interop.Word.Bookmark> nesne.  
  
   <xref:Microsoft.Office.Interop.Word.Bookmark> olayları ya da veri bağlama becerileri nesneleri yoktur.  
  
  Yer işaretine metin atadığınızda, davranış arasındaki farklı bir <xref:Microsoft.Office.Interop.Word.Bookmark> ve <xref:Microsoft.Office.Tools.Word.Bookmark>. Daha fazla bilgi için [yer işareti denetimi](../vsto/bookmark-control.md).  
  
## <a name="use-host-controls"></a>Konak denetimleri kullanın  
  
### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Bir yer işareti denetimi kullanarak yer işareti içeriklerini güncelleştirmek için  
  
1.  İsteyen bir yordamı oluşturmak bir `bookmark` yer işaretinin adı bağımsız değişkeni ve `newText` atamak dize bağımsız değişkeni <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> özelliği.  
  
    > [!NOTE]  
    >  Metne atama <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> veya <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> özelliği bir <xref:Microsoft.Office.Tools.Word.Bookmark> silinecek yer işareti denetimi neden olmaz.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Ata *newText* dizesinden <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> özelliği <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="use-word-objects"></a>Word nesneleri kullanma  
  
### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Bir Word yer işareti nesnesini kullanarak yer işareti içeriği güncelleştirmek için  
  
1.  Sahip bir yordam oluşturma bir `bookmark` bağımsız değişken adını <xref:Microsoft.Office.Interop.Word.Bookmark>ve `newText` atamak dize bağımsız değişkeni <xref:Microsoft.Office.Interop.Word.Range.Text%2A> yer işaretinin özelliği.  
  
    > [!NOTE]  
    >  Yerel bir sözcüğe metin atama <xref:Microsoft.Office.Interop.Word.Bookmark> nesnenin silinmesi yer işareti neden olur.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Ata *newText* dizesinden <xref:Microsoft.Office.Interop.Word.Range.Text%2A> özelliği yer işaretinin otomatik olarak siler. Yer işaretine yeniden eklersiniz <xref:Microsoft.Office.Interop.Word.Bookmarks> koleksiyonu.  
  
     Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Yer işareti denetimi](../vsto/bookmark-control.md)  
  
  