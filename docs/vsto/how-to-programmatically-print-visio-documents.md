---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6beed729ed670d5f34c645575795b625e03e9583
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671228"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma
  Tam bir Microsoft Office Visio belgesi ya da yalnızca belirli bir sayfa yazdırabilir.  
  
 Yazdırma yöntemleri hakkında daha fazla ayrıntı için VBA başvuru belgelerine bakın [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) yöntemi ve [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) yöntemi .  
  
## <a name="print-a-visio-document"></a>Visio belgelerini yazdırma  
  
### <a name="to-print-a-complete-document"></a>Belgenin tamamını yazdırmak için  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Document.Print` yöntemi `Microsoft.Office.Interop.Visio.Document` yazdırmak istediğiniz nesne.  
  
     Aşağıdaki kod örneği, etkin belgeyi yazdırır. Bu örneği kullanmak için kodu çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Visio belgesi bir sayfayı yazdır  
  
### <a name="to-print-a-page-of-a-document"></a>Belgenin bir sayfasını yazdırmak için  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Pages.Print` yöntemi `Microsoft.Office.Interop.Visio.Pages` yazdırmak istediğiniz nesne.  
  
     Aşağıdaki kod örneği, ilk sayfa etkin belgenin yazdırır. Bu örneği kullanmak için kodu çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
 [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Nasıl yapılır: Visio belgelerini program aracılığıyla kapatma](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  