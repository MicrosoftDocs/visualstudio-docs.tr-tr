---
title: 'Nasıl yapılır: belgelerde metni program aracılığıyla gizleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 83b25c37ee2ce4dd9cb1ffeda21fbda1b5f3f139
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677789"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Nasıl yapılır: belgelerde metni program aracılığıyla gizleme
  Bir belgede metin ayarlayarak gizleyebilirsiniz <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> özelliği <xref:Microsoft.Office.Interop.Word.Range.Font%2A> metin belirli bir dizi.  
  
 İçinde bulunan metinde Örneğin, geçici olarak gizleyebilirsiniz bir <xref:Microsoft.Office.Tools.Word.Bookmark> (belge düzeyi özelleştirmesindeki) veya bir <xref:Microsoft.Office.Interop.Word.Bookmark> (içinde bir VSTO eklenti) bir belgeyi yazıcıya göndermeden önce.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Belgeyi yazdırılırken yer işareti denetimdeki metin gizlemek için  
  
1.  Belirtilen bir aralıktaki tüm metni gizleyen bir yordamı oluşturun.  
  
     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]  
  
2.  Belirli bir aralıktaki tüm metinleri gösteren bir yordamı oluşturun.  
  
     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]  
  
3.  Yer işaretine aralığını geçirmek `HideText` yöntemi, belgeyi yazdır ve ardından aynı aralığa geçmesi `UnhideText` yöntemi.  
  
     Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir. Bu örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]  
  
     Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır. Örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu kod örneği, belgenin içerdiğini varsaymaktadır bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi (belge düzeyi özelleştirmeleri için) veya <xref:Microsoft.Office.Interop.Word.Bookmark> adlı denetimi (bir VSTO eklenti) `bookmark1`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md)   
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: Word belgelerinde aralıkları'program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Nasıl yapılır: yer işareti metnini program aracılığıyla güncelleştirme](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  