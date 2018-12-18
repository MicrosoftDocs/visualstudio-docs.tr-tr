---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9f065a32fc26d372b97a31eb70836451b31fa00
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670734"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme
  Microsoft Office Visio belgelerini kaydetme için birkaç yol vardır:  
  
- Varolan bir belgeyi değişiklikleri kaydedin.  
  
- Yeni bir belge kaydetme ya da bir belgeyi yeni bir adla kaydedin.  
  
- Belge, belirtilen bağımsız değişkenler ile kaydedin.  
  
  Daha fazla bilgi için bkz: VBA başvuru belgelerine [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) yöntemi [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) yöntemi ve [ Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) yöntemi.  
  
## <a name="save-an-existing-document"></a>Var olan bir belgeyi Kaydet  
  
### <a name="to-save-a-document"></a>Bir belgeyi kaydetme  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Document.Save` yöntemi `Microsoft.Office.Tools.Visio.Document` önceden kaydedilmiş bir belgenin sınıfı.  
  
     Bu kod örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
    > [!NOTE]  
    >  `Microsoft.Office.Interop.Visio.Document.Save` Yöntemi yeni bir Visio belgesi henüz kaydedilmedi, bir özel durum oluşturur.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Belgeye yeni bir adla kaydet  
 Kullanım `Microsoft.Office.Interop.Visio.Document.SaveAs` yeni bir belge ya da yeni bir ada sahip bir belge kaydetmek için yöntemi. Bu yöntem, yeni dosya adı belirtmeniz gerekir.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Etkin Visio belgesini yeni bir adla kaydetmek için  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Document.SaveAs` yöntemi `Microsoft.Office.Tools.Visio.Document` bir dosya adı dahil tam nitelenmiş bir yol kullanarak kaydetmek istediğiniz. Bu klasörde zaten o adda bir dosya varsa dosyanın sessizce üzerine yazılır.  
  
     Bu kod örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Belgeye yeni bir ad ve belirtilen bağımsız değişkenler ile Kaydet  
 Kullanım `Microsoft.Office.Interop.Visio.Document.SaveAsEx` yöntemi, bir belgeyi yeni bir adla kaydedin ve belgeye uygulamak için uygulanabilir tüm bağımsız değişkenleri belirtin.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Belgeyi yeni bir ad ve belirtilen bağımsız değişkenler ile kaydetmek için  
  
-   Çağrı `Microsoft.Office.Interop.Visio.Document.SaveAsEx` yöntemi `Microsoft.Office.Tools.Visio.Document` bir dosya adı dahil tam nitelenmiş bir yol kullanarak kaydetmek istediğiniz. Bu klasörde zaten o adda bir dosya ise bir özel durum oluşturulur.  
  
     Aşağıdaki kod örneği etkin belgeyi yeni adla kaydeder, belgeyi salt okunur olarak işaretler ve belgelerin en son kullanılan listede belge gösterir. Bu kod örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu kod örneği için aşağıdakiler gereklidir:  
  
-   Yeni bir ada sahip bir belge kaydetmek için adında bir dizin `Test` bulunmalıdır *Belgelerim* klasöründe (Windows XP ve daha önce) veya *belgeleri* klasöründe (Windows Vista için).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
 [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Nasıl yapılır: Visio belgelerini program aracılığıyla kapatma](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  