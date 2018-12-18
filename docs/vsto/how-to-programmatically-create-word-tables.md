---
title: 'Nasıl yapılır: program aracılığıyla Word tabloları oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a65c42f19602929b546bf105f148bf80e2d9b2db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914196"
---
# <a name="how-to-programmatically-create-word-tables"></a>Nasıl yapılır: program aracılığıyla Word tabloları oluşturma
  <xref:Microsoft.Office.Interop.Word.Tables> Koleksiyon üyesi olduğu <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, ve <xref:Microsoft.Office.Interop.Word.Range> sınıflarıyla bu içeriklerden herhangi birinde bir tablo oluşturabileceğiniz anlamına gelir. Kullandığınız <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Tables> belirli bir aralıkta bir tablo eklemek için koleksiyonu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="create-tables-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerde tabloları oluşturma  
  
### <a name="to-add-a-table-to-a-document"></a>Bir belge için bir tablo eklemek için  
  
- Kullanım <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> üç satır ve belgenin başına dört sütun içeren bir tablo eklemek için yöntemi.  
  
   Aşağıdaki kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
  Bir tablo oluşturduğunuzda, otomatik olarak eklenir <xref:Microsoft.Office.Interop.Word.Tables> koleksiyonunu <xref:Microsoft.Office.Tools.Word.Document> konak öğesi. Ardından tabloda öğe numarası kullanarak başvurabilirsiniz <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> özelliği, aşağıdaki kodda gösterildiği gibi.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Öğe numarasına göre bir tabloya başvurmak için  
  
1. Kullanım <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> özelliği ve tedarik başvurmak istediğiniz tabloyu öğe sayısı.  
  
    Aşağıdaki kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
   Her <xref:Microsoft.Office.Interop.Word.Table> nesne de sahip bir <xref:Microsoft.Office.Interop.Word.Table.Range%2A> biçimlendirme ayarlamanıza olanak sağlayan özellik öznitelikleri.  
  
### <a name="to-apply-a-style-to-a-table"></a>Bir tabloya bir stil uygulamak için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Word.Table.Style%2A> tabloya Word yerleşik stil uygulamak için özellik.  
  
     Aşağıdaki kod örneği kullanmak için çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="create-tables-in-vsto-add-ins"></a>VSTO eklentileri tablo oluşturma  
  
### <a name="to-add-a-table-to-a-document"></a>Bir belge için bir tablo eklemek için  
  
- Kullanım <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> üç satır ve belgenin başına dört sütun içeren bir tablo eklemek için yöntemi.  
  
   Aşağıdaki kod örneği, etkin belgeye bir tablo ekler. Bu örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
  Bir tablo oluşturduğunuzda, otomatik olarak eklenir <xref:Microsoft.Office.Interop.Word.Tables> koleksiyonunu <xref:Microsoft.Office.Interop.Word.Document>. Ardından tabloda öğe numarası kullanarak başvurabilirsiniz <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> özelliği, aşağıdaki kodda gösterildiği gibi.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Öğe numarasına göre bir tabloya başvurmak için  
  
1. Kullanım <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> özelliği ve tedarik başvurmak istediğiniz tabloyu öğe sayısı.  
  
    Aşağıdaki kod örneği, etkin belgeyi kullanır. Bu örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
   Her <xref:Microsoft.Office.Interop.Word.Table> nesne de sahip bir <xref:Microsoft.Office.Interop.Word.Table.Range%2A> biçimlendirme ayarlamanıza olanak sağlayan özellik öznitelikleri.  
  
### <a name="to-apply-a-style-to-a-table"></a>Bir tabloya bir stil uygulamak için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Word.Table.Style%2A> tabloya Word yerleşik stil uygulamak için özellik.  
  
     Aşağıdaki kod örneği, etkin belgeyi kullanır. Bu örneği kullanmak için çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla metin ve Word tablolarında hücrelere biçimlendirme ekleme](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Nasıl yapılır: belge özellikleriyle Word tablolarını program aracılığıyla doldurma](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  