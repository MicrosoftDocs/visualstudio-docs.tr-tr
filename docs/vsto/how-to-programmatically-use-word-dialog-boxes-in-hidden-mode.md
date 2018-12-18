---
title: 'Nasıl yapılır: program aracılığıyla Word iletişim kutularını gizli modda kullanma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5b123f1b58e61dffc64b5df912092edfd3fbf53
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677227"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Nasıl yapılır: program aracılığıyla Word iletişim kutularını gizli modda kullanma
  Microsoft Office Word yerleşik iletişim kutularında kullanıcıya görüntülenmeden çağırarak bir yöntem çağrısı ile karmaşık işlemleri gerçekleştirebilir. Kullanarak bunu yapabilirsiniz <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Dialog> çağırmadan nesne <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> yöntemi.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren **sayfa yapısı** iletişim kutusunda birden fazla sayfası kullanıcı girişi gerektirmeyen kurulum özellikleri ayarlamak için gizli modu. Örneklerde bir <xref:Microsoft.Office.Interop.Word.Dialog> nesnenin özel bir sayfa boyutu yapılandırın. Üst kenar boşluğu, alt kenar boşluğu ve benzeri gibi sayfa yapısı için özel ayarlar geç bağlama özellikleri olarak kullanılabilir <xref:Microsoft.Office.Interop.Word.Dialog> nesne. Bu özellikler, Word tarafından çalışma zamanında dinamik olarak oluşturulur.  
  
 Aşağıdaki örnek, Visual Basic projelerinde bu görevi gerçekleştirmek gösterilmiştir burada **Option Strict** hedefleyen devre dışı ve Visual C# projelerinde olduğu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Bu projeler Visual Basic ve Visual C# Derleyicileri geç bağlama özellikleri kullanabilirsiniz. Bu örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 Aşağıdaki örnek, Visual Basic projelerinde bu görevi gerçekleştirmek gösterilmiştir burada **Option Strict** açıktır. Bu projeler, geç bağlanan özelliklerine erişmek için yansıma kullanmanız gerekir. Bu örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla Word yerleşik iletişim kutularını kullanın.](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md)   
 [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  