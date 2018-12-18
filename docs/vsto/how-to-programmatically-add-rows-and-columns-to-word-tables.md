---
title: 'Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fca44524c3a7c7f10e855eaf62e8b77dc225ae01
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818685"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme
  Bir Microsoft Office Word tablodaki hücre satırlar ve sütunlar halinde düzenlenir. Kullanabileceğiniz <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Rows> tabloya satır eklemek için nesne ve <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Columns> sütunlar eklenecek nesne.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Belge düzeyi özelleştirmesi örnekleri  
 Aşağıdaki kod örnekleri, belge düzeyi özelleştirmesinde kullanılabilir. Bu örnekleri kullanmak için bunları çalıştırmak `ThisDocument` projenizdeki sınıfı. Bu örnekler, Özelleştirmenizde zaten ilişkili belge en az bir tablo olduğunu varsayar.  
  
> [!IMPORTANT]
>  Şu proje şablonlarını kullanarak oluşturduğunuz projelerde bu kodu çalıştırır:  
> 
> - Word 2013 belgesi  
> - Word 2013 şablonu  
> - Word 2010 Belgesi  
> - Word 2010 Şablonu  
> 
>   Bu görev başka bir türü proje içinde gerçekleştirmek istiyorsanız, bir başvuru eklemelisiniz **Microsoft.Office.Interop.Word** derleme ve daha sonra bu derleme sınıflardan satır ve sütun tablolarına ekleme için kullanmalısınız. Daha fazla bilgi için [nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Word 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> tabloya satır eklemek için yöntemi.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Tabloya bir sütun eklemek için  
  
1.  Kullanma <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> yöntemi ve ardından <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> tüm sütunları aynı genişliğe yapmak için yöntemi.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>VSTO eklenti örnekleri  
 Aşağıdaki kod örnekleri, VSTO eklentisi içinde kullanılabilir. Örnekleri kullanmak için bunları çalıştırmak `ThisAddIn` projenizdeki sınıfı. Bu örnekler, etkin belgeyi en az bir tablo zaten sahip olduğunu varsayın.  
  
> [!IMPORTANT]  
>  Bu kod, Word VSTO eklentisi şablonları kullanarak oluşturduğunuz projeleri çalıştırır.  
>   
>  Bu görev başka bir türü proje içinde gerçekleştirmek istiyorsanız, bir başvuru eklemelisiniz **Microsoft.Office.Interop.Word** derleme ve daha sonra bu derleme sınıflardan satır ve sütun tablolarına ekleme için kullanmalısınız. Daha fazla bilgi için [nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) ve [Word 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Tabloya satır eklemek için  
  
1.  Kullanım <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> tabloya satır eklemek için yöntemi.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Tabloya bir sütun eklemek için  
  
1.  Kullanma <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> yöntemi ve ardından <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> tüm sütunları aynı genişliğe yapmak için yöntemi.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla Word tabloları oluşturma](../vsto/how-to-programmatically-create-word-tables.md)   
 [Nasıl yapılır: program aracılığıyla metin ve Word tablolarında hücrelere biçimlendirme ekleme](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Nasıl yapılır: belge özellikleriyle Word tablolarını program aracılığıyla doldurma](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  