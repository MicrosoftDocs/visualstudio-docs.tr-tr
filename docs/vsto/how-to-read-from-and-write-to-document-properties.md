---
title: 'Nasıl yapılır: gelen okuma ve yazma için belge özellikleri'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: de9ae85156f9d272901893c74c5d2c9729a0a3dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924234"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Nasıl yapılır: gelen okuma ve yazma için belge özellikleri
  Bir belge yanı sıra belge özellikleri depolayabilirsiniz. Office uygulamaları birkaç yazar, başlık ve konu gibi yerleşik özellikler sağlar. Bu konu, Microsoft Office Excel ve Microsoft Office Word belgesi özelliklerini ayarlamak gösterilmektedir.  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [ı: erişimi nasıl ve Microsoft Word özel belge özellikleri yöneten?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="set-document-properties-in-excel"></a>Excel belge özelliklerini ayarlama  
 Yerleşik özellikler Excel'de çalışmak için aşağıdaki özellikleri kullanın:  
  
- Bir belge düzeyi projede kullanmak <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> özelliği `ThisWorkbook` sınıfı.  
  
- Bir VSTO eklenti projesinde kullanmak <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> özelliği bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesne.  
  
  Bu özellikleri döndürür bir <xref:Microsoft.Office.Core.DocumentProperties> bir koleksiyon nesne, <xref:Microsoft.Office.Core.DocumentProperty> nesneleri. Kullanabileceğiniz `Item` adı veya dizin koleksiyonundaki belirli bir özelliği almak için koleksiyonun özelliği.  
  
  Aşağıdaki kod örneği, yerleşik değiştirileceği gösterilmektedir **düzeltme numarası** bir belge düzeyi projede özelliği.  
  
### <a name="to-change-the-revision-number-property-in-excel"></a>Özelliğindeki düzeltme numarasını değiştirmek için  
  
1.  Yerleşik belge özellikleri, bir değişkene atayın.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Artırma `Revision Number` bir özellik.  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="set-document-properties-in-word"></a>Word'de belge özelliklerini ayarlama  
 Word yerleşik özellikleri ile çalışmak için aşağıdaki özellikleri kullanın:  
  
- Bir belge düzeyi projede kullanmak <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> özelliği `ThisDocument` sınıfı.  
  
- Bir VSTO eklenti projesinde kullanmak <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> özelliği bir <xref:Microsoft.Office.Interop.Word.Document> nesne.  
  
  Bu özellikleri döndürür bir <xref:Microsoft.Office.Core.DocumentProperties> bir koleksiyon nesne, <xref:Microsoft.Office.Core.DocumentProperty> nesneleri. Kullanabileceğiniz `Item` adı veya dizin koleksiyonundaki belirli bir özelliği almak için koleksiyonun özelliği.  
  
  Aşağıdaki kod örneği, yerleşik değiştirileceği gösterilmektedir **konu** bir belge düzeyi projede özelliği.  
  
### <a name="to-change-the-subject-property"></a>Konu özelliğini değiştirmek için  
  
1.  Yerleşik belge özellikleri, bir değişkene atayın.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Değişiklik `Subject` "Teknik" özelliği.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Örnekler kod yazmış olduğunuz varsayılır `ThisWorkbook` Excel için belge düzeyi projesinde sınıfı ve `ThisDocument` Word için belge düzeyi projesinde sınıfı.  
  
 Microsoft Office, Word ve Excel ve nesneleri ile çalışmanıza rağmen kullanılabilir yerleşik belge özelliklerinin listesini sağlar. Tanımlanmamış bir özelliğe erişmeye çalışırken bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  