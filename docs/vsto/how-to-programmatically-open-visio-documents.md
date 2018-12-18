---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini açma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 28f882510e2370c0fb31645da5023e865afd667e
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672684"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini açma
  Mevcut Microsoft Office Visio belgelerini açma için iki yöntem vardır: açık ve OpenEx. OpenEx yöntemi, çağırana nasıl belge açılır belirtebilirsiniz bağımsız değişkenleri sağlar dışında açık yönteme aynıdır.  
  
 Nesne modeli hakkında daha fazla ayrıntı için VBA başvuru belgelerine bakın [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Documents.Open) yöntemi ve [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) yöntem.  
  
## <a name="open-a-visio-document"></a>Bir Visio belgesini açın  
  
### <a name="to-open-a-visio-document"></a>Visio belgelerini açma  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Documents.Open` yöntemi ve tedarik Visio belgenin tam yolu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Belirtilen bağımsız değişkenlerle bir Visio belgesini açın  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Salt okunur ve dayalı olarak bir Visio belgelerini açma  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Documents.OpenEx` yöntemi, Visio belgesi tam yolunu girin ve kullanmak istediğiniz bağımsız değişkenleri ekleyin; bu durum, yerleşik ve salt okunur.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu kod örneği için aşağıdakiler gereklidir:  
  
-   Adlı bir Visio belgesini `myDrawing.vsd` adlı bir dizinde bulunmalıdır `Test` içinde *Belgelerim* klasöründe (Windows XP ve daha önce) veya *belgeleri* klasöründe (Windows Vista için).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
 [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Nasıl yapılır: Visio belgelerini program aracılığıyla kapatma](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  