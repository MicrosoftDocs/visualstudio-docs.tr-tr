---
title: 'Nasıl yapılır: program aracılığıyla, belgelerdeki metni biçimlendirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: baf6f49b0347aa4a770b4f7a47c7fa8195d5ede5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257416"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Nasıl yapılır: program aracılığıyla, belgelerdeki metni biçimlendirme
  Kullanabileceğiniz <xref:Microsoft.Office.Interop.Word.Range> Microsoft Office Word belgesinde biçimi metne nesne.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Aşağıdaki örnek ilk paragrafa belgede seçer ve yazı tipi boyutunu, yazı tipi adı ve hizalamayı değiştirir. Aralık seçilir ve kodun sonraki bölümü yürütmeden önce duraklatmak için bir ileti kutusu görüntüler. Sonraki bölümde geri alma yöntemini çağıran <xref:Microsoft.Office.Tools.Word.Document> ana öğe (için belge düzeyi özelleştirmeleri için) veya <xref:Microsoft.Office.Interop.Word.Document> (bir VSTO eklentisi için) üç kez sınıfı. Normal Girinti stili uygular ve kod duraklatmak için bir ileti kutusu görüntüler. Ardından kod çağrıları <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> yöntemi bir kere ve ileti kutusu görüntüler.  
  
## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örnek  
  
### <a name="to-format-text-using-a-document-level-customization"></a>Belge düzeyi özelleştirme kullanarak metin biçimlendirme  
  
1.  Aşağıdaki örnek bir belge düzeyi özelleştirmelerinde kullanılabilir. Bu kodu kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>VSTO eklentileri örneği  
  
### <a name="to-format-text-using-a-vsto-add-in"></a>Bir VSTO eklentisini kullanarak metin biçimlendirme  
  
1.  Aşağıdaki örnek, bir VSTO eklenti kullanılabilir. Bu örnek etkin belgeyi kullanır. Bu kodu kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Nasıl yapılır: program aracılığıyla arama ve belgelerdeki metni değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  