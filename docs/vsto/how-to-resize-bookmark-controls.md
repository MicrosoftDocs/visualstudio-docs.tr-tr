---
title: 'Nasıl yapılır: yer işareti denetimlerini yeniden boyutlandırma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 57b6d6a089570c52607cf73eeed4fc00978ab251
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924843"
---
# <a name="how-to-resize-bookmark-controls"></a>Nasıl yapılır: yer işareti denetimlerini yeniden boyutlandırma
  Boyutunu ayarlamak bir <xref:Microsoft.Office.Tools.Word.Bookmark> Microsoft Office Word belgesine eklediğinizde denetim. Ayrıca daha sonraki bir zamanda boyutlandırabilirsiniz.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Bir yer işareti yeniden boyutlandırmak için üç yolu vardır:  
  
- Metin ekleyip <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi.  
  
   Bir yer işareti olarak metin eklediğinizde, yer işareti boyutu otomatik olarak artar ve yeni metin içeren. Metin sildiğinizde, yer işareti boyutu otomatik olarak azaltır.  
  
- Değişiklik <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> ve <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> özelliklerini <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi.  
  
   Bu seçenek, yalnızca birkaç karakter boyutunu değiştiriyorsanız kullanışlıdır.  
  
- Yeniden <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi.  
  
   Bir yer işaretinin konumunu ve boyutunu önemli bir değişiklik varsa, bu yararlıdır.  
  
  Belge düzeyinde projelerde eklediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> belgenin tasarım zamanında veya çalışma zamanında, projenizdeki denetimler. Projelerinde, VSTO eklentisi, eklediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> herhangi bir açık belgeye çalışma zamanında denetimler. Daha fazla bilgi için [nasıl yapılır: Word belgelerine yer işareti ekleme denetimleri](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>Başlangıç ve bitiş özelliklerini değiştir  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Tasarım zamanında bir belge düzeyi projede yer işareti yeniden boyutlandırmak için  
  
1.  Yer işaretini seçin **özellikleri** penceresi.  
  
2.  Artırma veya azaltma değerini <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> özelliği.  
  
3.  Artırma veya azaltma değerini <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> özelliği.  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Çalışma zamanında bir belge düzeyi projede yer işareti yeniden boyutlandırmak için  
  
1.  Değiştirme <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> ve <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> özelliklerini bir <xref:Microsoft.Office.Tools.Word.Bookmark> tasarım zamanında ya da çalışma zamanında oluşturulan.  
  
     Aşağıdaki kod örneği, adında bir yer işareti başlangıcına kadar beş karakteri ekler `SampleBookmark`. Bu kod, en az beş karakteri yer işaretinden önce gelen metin olduğunu varsayar.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     Aşağıdaki kod örneği, beş karakteri aynı yer işaretinin sonuna ekler. Bu kod, bir yer işaretinden sonra en az beş karakteri metin olduğunu varsayar.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Çalışma zamanında VSTO eklenti projesinde bir yer işareti yeniden boyutlandırmak için  
  
1.  Değiştirme <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> ve <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> özelliklerini bir <xref:Microsoft.Office.Tools.Word.Bookmark> çalışma zamanında oluşturulan.  
  
     Aşağıdaki kod örneği oluşturur bir <xref:Microsoft.Office.Tools.Word.Bookmark> etkin belgenin ilk paragrafa metin içeren ve ardından Başlat ve sonuna beş karakteri kaldırır <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>Yer işareti yeniden oluşturun  
 Mevcut yer işareti ile aynı ada sahip, ancak başka bir boyutu olan yeni bir yer işareti ekleyerek bir belge düzeyi projede yer işareti yeniden boyutlandırabilirsiniz.  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Tasarım zamanında bir belge düzeyi projede yer işareti yeniden oluşturmak için  
  
1.  Yeni konacak metni seçin <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi.  
  
2.  Üzerinde **Ekle** menüsünü tıklatın **yer işareti**.  
  
3.  İçinde **yer işareti** iletişim kutusunda, yeniden boyutlandırın ve istediğiniz yer işaretinin adı seçin **Ekle**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)   
 [Nasıl yapılır: ListObject denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-listobject-controls.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  