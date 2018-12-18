---
title: 'Nasıl yapılır: belgelere program aracılığıyla resim ve Word Art ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 61399df32ef0f22d1d0aacf23dea45c1357c7579
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255112"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Nasıl yapılır: belgelere program aracılığıyla resim ve Word Art ekleme
  Tasarım zamanında veya çalışma zamanında belgelere resimler ve çizim nesneleri ekleyebilirsiniz. WordArt, Microsoft Office Word belgelerine dekoratif metin eklemenize olanak tanır. Bu özel metin efektleri çizim özelleştirebilir ve belgenize eklemek nesneleridir.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="add-a-picture-at-design-time"></a>Tasarım zamanında resim ekleme  
 Belge düzeyi özelleştirme geliştiriyorsanız, tasarım zamanında belgeye resim ekleyebilirsiniz.  
  
### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Tasarım zamanında bir Word belgesi için bir resim eklemek için  
  
1.  İmlecinizi resmi belgede eklemek istediğiniz yere yerleştirin.  
  
2.  Tıklatın **Ekle** Şerit sekmesi.  
  
3.  İçinde **çizimler** grubunda **resim**.  
  
4.  İçinde **resim** iletişim kutusunda, eklemek istediğiniz resme gidin ve tıklayın **Ekle**.  
  
     Resim belgenizi geçerli imleç konumu eklenir.  
  
## <a name="add-a-picture-at-runtime"></a>Çalışma zamanında resim ekleme  
 Geçerli imleç konumundaki belgeye resim ekleyebilirsiniz.  
  
### <a name="to-add-a-picture-at-the-cursor-location"></a>İmleç konumuna resim eklemek için  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> yöntemi <xref:Microsoft.Office.Interop.Word.InlineShapes> koleksiyonu ve dosya adına geçirin.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="add-wordart-at-design-time"></a>Tasarım zamanında WordArt ekleme  
 Belge düzeyi özelleştirme geliştiriyorsanız, tasarım zamanında belgeye WordArt ekleyebilirsiniz.  
  
### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Tasarım zamanında bir Word belgesi WordArt eklemek için  
  
1.  İmlecinizi WordArt belgede eklemek istediğiniz yere yerleştirin.  
  
2.  Tıklatın **Ekle** Şerit sekmesi.  
  
3.  İçinde **metin** grubunda **WordArt**ve ardından bir WordArt stili seçin.  
  
4.  Belgede görünmesini istediğiniz metni ekleyin **WordArt Metnini Düzenle** iletişim kutusu ve tıklatın **Tamam**.  
  
     Metin belgenize Seçili WordArt stili ile eklenir.  
  
## <a name="add-wordart-at-runtime"></a>Çalışma zamanında WordArt ekleme  
 Geçerli imleç konumundaki belgeye WordArt ekleyebilirsiniz. Belge düzeyi özelleştirmeleri ve VSTO eklentileri için farklı bir yordamdır.  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Belge düzeyi özelleştirmelerinde İmleç konumuna WordArt eklemek için  
  
1.  Geçerli imleç konumu sol ve üst konumunu alın.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Çağrı <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Shapes> belgedeki nesne.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Bir VSTO eklentisi imleç konumu WordArt eklemek için  
  
1.  Geçerli imleç konumu sol ve üst konumunu alın.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Çağrı <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Shapes> nesne etkin belge (veya belirttiğiniz farklı bir belge).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compile-the-code"></a>Kod derleme  
  
-   Adlı bir resim *SamplePicture.jpg* c sürücüsünde bulunan mevcut olması gerekir  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: varolan belgeleri program aracılığıyla açma](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Nasıl yapılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Nasıl yapılır: program aracılığıyla aramalardan sonra seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Nasıl yapılır: program aracılığıyla belgeleri kaydetme](../vsto/how-to-programmatically-save-documents.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  