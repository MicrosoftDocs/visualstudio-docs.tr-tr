---
title: 'Nasıl yapılır: program aracılığıyla belgeleri kaydetme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e794a995d1e978cf5aae8d1b6ec9c1711436af73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883483"
---
# <a name="how-to-programmatically-save-documents"></a>Nasıl yapılır: program aracılığıyla belgeleri kaydetme
  Microsoft Office Word belgeleri kaydetmek için çeşitli yollar vardır. Belge adını değiştirmeden bir belgeyi kaydedebilirsiniz veya yeni bir adla bir belgeyi kaydedebilirsiniz.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>Bir belge, adını değiştirmeden kaydedin  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Belge düzeyi özelleştirme ile ilişkilendirilmiş belgeyi kaydetme  
  
1.  Çağrı <xref:Microsoft.Office.Tools.Word.Document.Save%2A> yöntemi <xref:Microsoft.Office.Tools.Word.Document> sınıfı. Bu kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>Etkin belgeyi kaydetmek için  
  
1. Çağrı <xref:Microsoft.Office.Interop.Word._Document.Save%2A> etkin belge için yöntemi. Bu kod örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
   Etkin belgeyi kaydetmek istediğiniz belge olup emin değilseniz adıyla başvurabilir.  
  
### <a name="to-save-a-document-specified-by-name"></a>Belirtilen ada göre bir belgeyi kaydetmek için  
  
1.  Belge adı bağımsız değişkeni olarak kullanma <xref:Microsoft.Office.Interop.Word.Documents> koleksiyonu. Bu kod örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>Belgeye yeni bir adla kaydet  
 Belgeye yeni bir adla kaydetmek için Farklı Kaydet yöntemi kullanın. Bu yöntemi kullanabilirsiniz <xref:Microsoft.Office.Tools.Word.Document> Word belge düzeyi projesi veya yerel konak öğesi <xref:Microsoft.Office.Interop.Word.Document> herhangi bir sözcük projede nesne. Bu yöntem, yeni dosya adı belirtin, ancak diğer bağımsız değişken isteğe bağlı gerektirir.  
  
> [!NOTE]  
>  Gösteriyorsa, **Farklı Kaydet** iletişim kutusu içine <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> olay işleyicisine `ThisDocument` ve *iptal* parametresi **false**, uygulamadan beklenmedik bir şekilde çıkın. Ayarlarsanız *iptal* parametresi **true**, otomatik kaydetme devre dışı olduğunu belirten bir hata iletisi görüntülenir.  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Belge düzeyi özelleştirmesinde yeni bir adla ilişkilendirilmiş belgeyi kaydetme  
  
1.  Çağrı <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> yöntemi `ThisDocument` tam yol ve dosya adı kullanarak, projenizdeki sınıfı. Bu klasörde zaten o adda bir dosya varsa dosyanın sessizce üzerine yazılır. Bu kod örneği kullanmak için çalıştırın `ThisDocument` sınıfı.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Yöntemi, bir hedef dizin mevcut değil veya dosya kaydetme diğer sorunları varsa bir özel durum oluşturur. Kullanmak için iyi bir uygulamadır bir **try... catch** geçici olarak engellemek <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> yöntemi veya içinde bir çağırma yöntemi.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>Yerel belgeyi yeni bir adla kaydetmek için  
  
1.  Çağrı <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Document> kaydetmek bir tam yol ve dosya adını kullanarak istediğiniz. Bu klasörde zaten o adda bir dosya varsa dosyanın sessizce üzerine yazılır.  
  
     Aşağıdaki kod örneği, etkin belgeyi yeni bir adla kaydeder. Bu kod örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Yöntemi, bir hedef dizin mevcut değil veya dosya kaydetme diğer sorunları varsa bir özel durum oluşturur. Kullanmak için iyi bir uygulamadır bir **try... catch** geçici olarak engellemek <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> yöntemi veya içinde bir çağırma yöntemi.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu kod örneği için aşağıdakiler gereklidir:  
  
-   Ada göre bir belgeyi kaydetmek için bir belge adlı *NewDocument.doc* adlı bir dizinde bulunmalıdır *Test* c sürücüsünün  
  
-   Belgeye yeni bir adla kaydetmek için adında bir dizin *Test* c sürücüsünde bulunan mevcut olması gerekir  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla belgeleri kapatma](../vsto/how-to-programmatically-close-documents.md)   
 [Nasıl yapılır: varolan belgeleri program aracılığıyla açma](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Belge konak öğesi](../vsto/document-host-item.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  