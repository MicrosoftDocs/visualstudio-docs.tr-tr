---
title: Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0b7e45ed9ba8e9fcd42d57a1cc6aaf34ce3e3711
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693389"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları
  Her konak öğesi ve konak kontrolü ek işlevsellik ile ilgili yerel Microsoft Office Word veya Microsoft Office Excel nesnesi gibi davranacak şekilde tasarlanmıştır. Ancak, konak denetimlerinin ve konak öğelerinin davranışını ve çalışma zamanında yerel Office nesneleri arasındaki bazı temel farklar vardır.  
  
 Konak denetimlerinin ve konak öğeleri hakkında genel bilgi için bkz: [konak öğelerini ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>Konak öğeleri program aracılığıyla oluşturma  
 Program aracılığıyla oluşturduğunuzda veya bir belge, çalışma kitabını veya çalışma zamanında Word veya Excel nesne modelini kullanarak projeyi açtığınızda öğe konak öğesi değil. Bunun yerine, yeni bir yerel Office nesnesi nesnesidir. Kullanırsanız, örneğin, <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> en yeni bir Word belgesi oluşturmak için yöntemi çalışma zamanında, yerel olacaktır <xref:Microsoft.Office.Interop.Word.Document> nesne yerine bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi. Benzer şekilde, oluşturduğunuzda, yeni bir çalışma zamanında kullanarak <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> yöntemi, bir yerel alma <xref:Microsoft.Office.Interop.Excel.Worksheet> nesne yerine bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi.  
  
 Belge düzeyi projelerine çalışma zamanında konak öğeleri oluşturamazsınız. Belge düzeyi projelerine tasarım zamanında yalnızca ana bilgisayar öğeleri oluşturulabilir. Daha fazla bilgi için bkz: [belge konak öğesi](../vsto/document-host-item.md), [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md), ve [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).  
  
 VSTO eklenti projelerinde oluşturduğunuz <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, veya <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğelerini çalışma zamanında. Daha fazla bilgi için bkz: [genişletmek Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-create-host-controls"></a>Program aracılığıyla ana bilgisayar denetimleri oluşturma  
 Konak denetimleri için programlı olarak ekleyebilirsiniz bir <xref:Microsoft.Office.Tools.Word.Document> veya <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma zamanında konak öğesi. Daha fazla bilgi için bkz: [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Yerel ana bilgisayar denetimleri ekleyemezsiniz <xref:Microsoft.Office.Interop.Word.Document> veya <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
> [!NOTE]  
>  Aşağıdaki ana bilgisayar denetimleri program aracılığıyla çalışma sayfaları veya belgeler eklenemiyor: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, ve <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Konak öğeleri, ana bilgisayar denetimleri ve yerel Office nesneleri arasındaki türü farkları anlamak  
 Her konak öğesi ve konak kontrolü için temel alınan yerel Microsoft Office Word veya Microsoft Office Excel nesne yok. Temel alınan nesnede konak öğesi veya konak kontrolünün InnerObject özelliğini kullanarak erişebilirsiniz. Ancak, kendi ilgili konak öğesi veya konak kontrolü yerel Office nesnesi yayınlanamıyor yolu yoktur. Yerel Office nesnesini konak öğesi veya konak kontrolü türüne dönüştürmeyi denerseniz bir <xref:System.InvalidCastException> oluşturulur.  
  
 Konak denetimlerinin ve konak öğelerinin türleri ve arka plandaki yerel Office nesneleri arasındaki farklar kodunuzu nereye etkileyebilir birkaç senaryo vardır.  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>Konak denetimleri yöntemlere ve özelliklere geçirme  
 Word'de bir yöntem veya bir parametre olarak yerel bir Word nesnesi gerektirir özellik için bir konak kontrolü geçiremezsiniz. Arka plandaki yerel Word nesnesini döndürmek için konak kontrolü InnerObject özelliğini kullanmanız gerekir. Örneğin, geçirebilirsiniz bir <xref:Microsoft.Office.Interop.Word.Bookmark> geçirerek bir yöntem nesnesine <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> özelliği <xref:Microsoft.Office.Tools.Word.Bookmark> konak kontrolü yöntemi.  
  
 Excel'de, yöntemi veya özelliği Excel nesnesini beklediği zaman bir yöntemi veya özelliği konak kontrolü geçirmek için konak kontrolü InnerObject özelliğini kullanmanız gerekir.  
  
 Aşağıdaki örnekte bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetlemek ve buna ileten <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> yöntemi. Kod kullanan <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> arka plandaki Office döndürmek için adlandırılmış aralığın özelliği <xref:Microsoft.Office.Interop.Excel.Range> tarafından gerekli <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> yöntemi.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Dönüş türleri yerel Office yöntemleri ve özellikleri  
 Çoğu yöntemleri ve konak öğelerinin özelliklerini konak öğesi temel aldığı yerel Office nesnesini döndürür. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> özelliği bir <xref:Microsoft.Office.Tools.Excel.NamedRange> konak kontrolü Excel döndürür bir <xref:Microsoft.Office.Interop.Excel.Worksheet> nesne yerine bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi. Benzer şekilde, <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> özelliği bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> konak kontrolü Word döndürür bir <xref:Microsoft.Office.Interop.Word.Document> nesne yerine bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi.  
  
### <a name="access-collections-of-host-controls"></a>Konak denetimleri erişim koleksiyonları  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Her ana denetim türü için ayrı koleksiyonlar sağlamaz. Bunun yerine, tüm yönetilen denetimler (ana bilgisayar denetimleri ve Windows Forms denetimleri) belge veya çalışma sayfası üzerinde yinelemek için konak öğesinin denetimleri özelliğini kullanın ve ilgilendiğiniz konak kontrolü türüyle eşleşen öğeleri arayın. Aşağıdaki kod örneğinde bir Word belgesi üzerindeki her denetim inceler ve denetimi olup olmadığını belirleyen bir <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Konak öğeleri denetimleri özelliği hakkında daha fazla bilgi için bkz: [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Word ve Excel nesne modelleri belgeler ve çalışma sayfası üzerinde yerel denetimlere koleksiyonları kullanıma özellikleri içerir. Bu özellikleri kullanarak yönetilen denetimler erişemiyor. Örneğin, her numaralandırmak mümkün değil <xref:Microsoft.Office.Tools.Word.Bookmark> konak kontrolü belgede kullanarak <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> özelliği bir <xref:Microsoft.Office.Interop.Word.Document> veya <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> özelliği bir <xref:Microsoft.Office.Tools.Word.Document>. Bu özellikler yalnızca dahil <xref:Microsoft.Office.Interop.Word.Bookmark> denetimlerini belgede; içeremez <xref:Microsoft.Office.Tools.Word.Bookmark> konak denetimlerini belgede.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Word otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)   
 [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)   
 [Belge konak öğesi](../vsto/document-host-item.md)  
  
  