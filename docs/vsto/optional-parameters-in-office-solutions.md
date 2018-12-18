---
title: Office çözümlerinde isteğe bağlı parametreler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4a9737ae9e256cdc9862c0d7725e9bffda5b633
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882580"
---
# <a name="optional-parameters-in-office-solutions"></a>Office çözümlerinde isteğe bağlı parametreler
  Çoğu Microsoft Office uygulamasının nesne modellerini yöntemlere, isteğe bağlı parametreleri kabul eder. Office çözümünü Visual Studio'da geliştirme için Visual Basic kullanıyorsanız, her eksik parametre için varsayılan değerleri otomatik olarak kullanıldığından isteğe bağlı parametreler için bir değer geçirmek zorunda değildir. Çoğu durumda, Visual C# projelerinde isteğe bağlı parametreler atlayabilirsiniz. Ancak, isteğe bağlı atlayamazsınız **ref** parametrelerinin `ThisDocument` belge düzeyi Word projelerinde sınıfı.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual C# ve Visual Basic projelerinde isteğe bağlı parametreler ile çalışma hakkında daha fazla bilgi için bkz. [adlandırılmış ve isteğe bağlı bağımsız değişkenler &#40;C&#35; Programlama Kılavuzu&#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) ve [ &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  Visual Studio'nun önceki sürümlerini, Visual C# projelerinde isteğe bağlı her parametre için bir değer geçmesi gerekir. Kolaylık olması için bu projeleri adlı bir genel değişken dahil `missing` parametresinin varsayılan değeri kullanmak istediğinizde isteğe bağlı bir parametre geçirebilirsiniz. Visual Studio'da Office için Visual C# projeleri yine de dahil `missing` değişkeni, ancak genellikle zorunda kalmadan Office çözümleri geliştirirken kullanmak [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], isteğe bağlı olan yöntemleri olarak çağırdığınızda dışında **ref** parametrelerinde `ThisDocument` Word için belge düzeyi projelere sınıf.  
  
## <a name="example-in-excel"></a>Örnek Excel  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> Yöntemi birçok isteğe bağlı parametreye sahiptir. Bazı parametreler için değerleri belirtin ve aşağıdaki kod örneğinde gösterildiği gibi diğer varsayılan değerini kabul edebilirsiniz. Bu örnek, bir çalışma sayfası sınıf adlı bir belge düzeyi projesi gerektirir `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Word'de bir örnek  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Yöntemi birçok isteğe bağlı parametreye sahiptir. Bazı parametreler için değerleri belirtin ve aşağıdaki kod örneğinde gösterildiği gibi diğer varsayılan değerini kabul edebilirsiniz.  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Word için belge düzeyi Visual C# projelerinde sınıfındaki yöntemleri kullanmak isteğe bağlı parametreler  
 Word nesne modeli ile isteğe bağlı birçok yöntem içerir **ref** kabul parametreleri <xref:System.Object> değerleri. Ancak, isteğe bağlı atlayamazsınız **ref** oluşturulan yöntemlerin parametreleri `ThisDocument` Word için belge düzeyi projeler Visual C# sınıfı. Visual C# sayesinde isteğe bağlı atlamak **ref** sınıfların parametreleri yalnızca arabirimlerin, yöntemler için değil. Atlayamazsınız çünkü Örneğin, aşağıdaki kod örneği, derleme yapmaz **ref** parametrelerinin <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> yöntemi `ThisDocument` sınıfı.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 Yöntemlerini çağırdığınızda `ThisDocument` sınıfında, aşağıdaki yönergeleri izleyin:  
  
- İsteğe bağlı varsayılan değerini kabul etmek üzere **ref** parametre, pass `missing` değişken parametre. `missing` Değişken Visual C# Office projelerinde otomatik olarak tanımlanır ve değer atanmış <xref:System.Type.Missing> oluşturulan proje kod.  
  
- İsteğe bağlı kendi değerinizi **ref** parametresi, belirtmek istediğiniz değer atanmış bir nesne bildirme ve nesneyi parametresini geçirin.  
  
  Aşağıdaki kod örneğinde nasıl çağrılacağını gösterir <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> yöntemi için bir değer belirterek *ignoreUppercase* parametresi ve diğer parametreler için varsayılan değeri kabul etme.  
  
  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
  İsteğe bağlı atlayarak kod yazmak istiyorsanız **ref** bir yöntemin parametre `ThisDocument` sınıfı, alternatif olarak çağırabilirsiniz aynı yöntem üzerinde <xref:Microsoft.Office.Interop.Word.Document> tarafından döndürülen nesne <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> özelliği ve çıkarın Bu yöntem parametreleri. Çünkü bunu yapabilirsiniz <xref:Microsoft.Office.Interop.Word.Document> bir sınıf yerine bir arabirim olduğundan.  
  
  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
  Değer ve başvuru türü parametreleri hakkında daha fazla bilgi için bkz. [bağımsız değişkenleri değere ve başvuruya göre geçirme &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic için) ve [parametreleri geçirmek &#40;C&#35; Programlama Kılavuzu&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)  
  
  