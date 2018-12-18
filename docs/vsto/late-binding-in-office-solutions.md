---
title: Office çözümlerinde geç bağlama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5616ce958747f90c8015df858f657299ba52852b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572556"
---
# <a name="late-binding-in-office-solutions"></a>Office çözümlerinde geç bağlama
  Nesne modelleri Office uygulamalarının bazı türleri geç bağlama özellikleriyle kullanılabilir olan işlevsellik sağlar. Örneğin, bazı yöntemler ve özellikler farklı türde nesne Office uygulama bağlı olarak döndürebilir ve bazı türleri farklı yöntemler ve farklı bağlamdan özellikler getirebilir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic projeleri **Option Strict** kapalı ve Visual C# projeleri hedefleyen [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] doğrudan bu geç bağlama özellikleri uygulamadığınız türleriyle çalışabilirsiniz.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Örtük ve açık atama nesnesinin dönüş değerleri  
 Birçok yöntem ve Microsoft Office birincil birlikte çalışma derlemeleri (PIA) dönüş özelliklerinde <xref:System.Object> birkaç farklı türde nesne döndürebildiğinden değerleri. Örneğin, <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> özelliği döndürür bir <xref:System.Object> dönüş değeri olabilir çünkü bir <xref:Microsoft.Office.Interop.Excel.Worksheet> veya <xref:Microsoft.Office.Interop.Excel.Chart> etkin sayfanın ne olduğuna bağlı olarak nesne.  
  
 Bir yöntemi veya özelliği döndüğünde bir <xref:System.Object>, açıkça (Visual Basic'te) nesne Visual Basic projeleri içinde doğru türüne dönüştürmeniz gerekir nerede **Option Strict** açıktır. Açıkça cast gerekmez <xref:System.Object> Visual Basic projelerinde dönüş değerleri nerede **Option Strict** kapalıdır.  
  
 Çoğu durumda, başvuru belgeleri olası dönüş değerini döndüren bir üye türlerini için listeler bir <xref:System.Object>. Dönüştürme ya da nesne atama Kod Düzenleyicisi'nde nesnesi için IntelliSense sağlar.  
  
 Visual Basic'te dönüştürme hakkında daha fazla bilgi için bkz: [dolaylı ve açık dönüştürmeler &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) ve [CType işlevi &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Örnekler  
 Aşağıdaki kod örneği, bir Visual Basic projesinde bir nesne belirli bir türüne yayınlanamıyor gösterilmiştir nerede **Option Strict** açıktır. Bu proje türünde, açıkça atamalısınız <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> özelliğine bir <xref:Microsoft.Office.Interop.Excel.Range>. Bu örnek bir belge düzeyi Excel projesi adlı bir çalışma sayfası sınıfıyla birlikte gerektirir `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 Aşağıdaki kod örneği, bir Visual Basic projesinde bir nesne belirli bir türüne örtük olarak yayınlanamıyor gösterilmiştir nerede **Option Strict** devre dışı veya hedefleyen Visual C# projesinde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Projeleri, bu tür <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> özelliği örtük olarak atandığında bir <xref:Microsoft.Office.Interop.Excel.Range>. Bu örnek bir belge düzeyi Excel projesi adlı bir çalışma sayfası sınıfıyla birlikte gerektirir `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Sadece geç bağlama aracılığıyla kullanılabilir olan erişim üyeleri  
 Bazı özellikleri ve yöntemleri Office PIA sadece geç bağlama aracılığıyla kullanılabilir. Visual Basic projeleri **Option Strict** kapalı veya Visual C# projeleri hedefleyen olan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], geç bağlama üyelere erişmek için bu dillerde geç bağlama özelliklerini kullanabilirsiniz. Visual Basic projeleri **Option Strict** olduğundan, bu üyeler erişmek için yansıma kullanmalısınız.  
  
### <a name="examples"></a>Örnekler  
 Aşağıdaki kod örneğinde, Visual Basic projesinde geç bağlama üyelere erişmek gösterilmiştir nerede **Option Strict** devre dışı veya hedefleyen Visual C# projesinde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Bu örnek geç bağlama erişen **adı** özelliği **Dosya Aç** Word iletişim kutusu. Bu örneği kullanmak için çalıştırın `ThisDocument` veya `ThisAddIn` Word projesindeki sınıfı.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Aşağıdaki kod örneğinde yansıma Visual Basic projesinde aynı görevi gerçekleştirmek için nasıl kullanılacağı gösterilmektedir nerede **Option Strict** açıktır.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)   
 [Kullanım türü dinamik &#40;C&#35; Programlama Kılavuzu&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Tasarlama ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md)  
  
  