---
title: 'Nasıl yapılır: program aracılığıyla Word yerleşik iletişim kutularını kullanın.'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f5ee28b0296037b9b5490ca691a27d613c793228
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676939"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Nasıl yapılır: program aracılığıyla Word yerleşik iletişim kutularını kullanın.
  Microsoft Office Word ile çalışırken, kullanıcı girişi için iletişim kutularını görüntülemek için gerektiğinde zamanlar vardır. Kendi oluşturabilirsiniz, ancak aynı zamanda sunulan yerleşik Word iletişim kutularını, kullanarak yaklaşımı isteyebileceğiniz <xref:Microsoft.Office.Interop.Word.Dialogs> koleksiyonunu <xref:Microsoft.Office.Interop.Word.Application> nesne. Bu, 200'den fazla yerleşik iletişim kutuları, sabit listeleri temsil edilen erişmenize olanak sağlar.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="display-dialog-boxes"></a>Görünen iletişim kutuları  
 Bir iletişim kutusu görüntülemek için değerlerinden kullanın <xref:Microsoft.Office.Interop.Word.WdWordDialog> sabit listesi oluşturmak için bir <xref:Microsoft.Office.Interop.Word.Dialog> görüntülemek istediğiniz iletişim kutusunu temsil eden nesne. Ardından, arama <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Dialog> nesne.  
  
 Aşağıdaki kod örneğinde nasıl görüntüleneceğini gösterir **Dosya Aç** iletişim kutusu. Bu örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Geç bağlama aracılığıyla kullanılabilir olan erişim iletişim kutusu üyeler  
 Bazı özellikleri ve yöntemleri Word iletişim kutularını yalnızca geç bağlama aracılığıyla kullanılabilir. Visual Basic projelerinde **Option Strict** açıktır, bu üyelere erişim için yansıma kullanmalısınız. Daha fazla bilgi için [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md).  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir **adı** özelliği **Dosya Aç** iletişim kutusunda, Visual Basic projelerinde **Option Strict** kapalı veya Visual C# hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Bu örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Aşağıdaki kod örneği, yansıma erişmek için kullanılacak gösterilmiştir **adı** özelliği **Dosya Aç** iletişim kutusunda, Visual Basic projelerinde **Option Strict** olduğu . Bu örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla Word iletişim kutularını gizli modda kullanma](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)   
 [Option strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  