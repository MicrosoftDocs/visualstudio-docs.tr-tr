---
title: 'Nasıl yapılır: Visio belgesine program aracılığıyla şekiller ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 94e8b43830c26aad82937cc0533ca19e109f33d0
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671878"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Nasıl yapılır: Visio belgesine program aracılığıyla şekiller ekleme
  Microsoft Office Visio belgesine şekiller, asıl kalıptan alma ve etkin sayfada şekilleri bırakarak ekleyebilirsiniz.  
  
 Daha fazla bilgi için bkz: VBA başvuru belgelerine [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) yöntemi [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) özelliği ve [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) yöntemi.  
  
## <a name="add-shapes-to-a-visio-document"></a>Bir Visio belgesine şekiller ekleme  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Visio belgesine şekilleri eklemek için  
  
-   Etkin belge, asıl Documents.Masters koleksiyondan ve şekiller etkin belgede bırakın. Bir ana dizin veya ana adı kullanarak alabilirsiniz.  
  
     Aşağıdaki kod örneği boş bir Visio belgesi oluşturur ve sonra açıyor **temel şekilleri** yerleşik bir şablon. Kod birkaç şekil alır ve bunları etkin sayfada bırakır.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
 [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md)   
 [Nasıl yapılır: program aracılığıyla kopyalayın ve bir Visio belgesinde şekiller yapıştırın](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  