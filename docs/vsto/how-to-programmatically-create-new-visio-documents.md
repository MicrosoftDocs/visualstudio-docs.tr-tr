---
title: 'Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4142ebe86ea69fbb0a74f25c2a7053a60c527cdb
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671566"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma
  Yeni Microsoft Office Visio çizim belgesi oluşturduğunuzda, ona ekleme `Microsoft.Office.Interop.Visio.Documents` açık Visio belgeleri koleksiyonu. Sonuç olarak, `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi yeni bir Visio çizim belgesi oluşturur. Daha fazla bilgi için bkz: VBA başvuru belgelerine [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) yöntemi.  
  
## <a name="create-new-blank-documents"></a>Yeni bir boş belge oluşturma  
  
### <a name="to-create-a-new-document"></a>Yeni bir belge oluşturmak için  
  
-   Kullanım `Microsoft.Office.Interop.Visio.Documents.Add` şablona dayalı yeni, boş bir belge oluşturmak için yöntemi.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Mevcut belgelerden kopyalanmış belgeler oluşturma  
 `Microsoft.Office.Interop.Visio.Documents.Add` Yöntemi, mevcut bir Visio belgesini kopyası olan yeni bir belge oluşturabilirsiniz. Diyagramın tam yolunu ve dosya adını sağlamanız gerekir.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Mevcut bir belgesinden kopyalanan bir yeni belge oluşturma  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi ve bir Visio diyagramını yolunu belirtin.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Mevcut örnekleri kopyalanan şablon oluşturma  
 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) yöntemi, mevcut bir Visio Kalıbı kopyası olan yeni bir şablon oluşturabilirsiniz. Şablon tam yolunu ve dosya adını sağlamanız gerekir.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Varolan kalıptan kopyalanır ve yeni bir şablon oluşturmak için  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi ve şablon yolunu belirtin.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Var olan şablonları temel alan belgeler oluşturma  
 `Microsoft.Office.Interop.Visio.Documents.Add` Yöntemi yeni bir belge oluşturabilirsiniz (bir *.vsd* dosya) mevcut bir Visio şablonunu temel alarak (bir *.vst* dosyası). Bu yöntem, şablonlar, stillerini ve şablon çalışma alanının parçası olan ayarları kopyalar. Şablonun tam yolunu ve dosya adını sağlamanız gerekir.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Mevcut bir şablonu temel alan yeni bir belge oluşturmak için  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Documents.Add` yöntemi ve şablonun yolunu belirtin.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu kod örneği için aşağıdakiler gereklidir:  
  
-   Adlı bir Visio belgesini `myDrawing.vsd` adlı bir dizinde bulunmalıdır `Test` içinde *Belgelerim* klasöründe (Windows XP ve daha önce) veya *belgeleri* klasöründe (Windows Vista için).  
  
-   Adlı bir Visio belgesini `myStencil.vss` adlı bir dizinde bulunmalıdır `Test` içinde *Belgelerim* klasöründe (Windows XP ve daha önce) veya *belgeleri* klasöründe (Windows Vista için).  
  
-   Adlı bir Visio belgesini `myTemplate.vst` adlı bir dizinde bulunmalıdır `Test` içinde *Belgelerim* klasöründe (Windows XP ve daha önce) veya *belgeleri* klasöründe (Windows Vista için).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Nasıl yapılır: Visio belgelerini program aracılığıyla kapatma](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  