---
title: Office çözümlerinde isteğe bağlı parametreler
description: Varsayılan değerler eksik her parametre için otomatik olarak kullanıldığından, isteğe bağlı parametreler için bir değer geçirmeniz gerekmez.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c95842ac2c6d77a2312ac5c4c197ba22ed2020e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825426"
---
# <a name="optional-parameters-in-office-solutions"></a>Office çözümlerinde isteğe bağlı parametreler
  Microsoft Office uygulamaların nesne modellerindeki birçok yöntem isteğe bağlı parametreleri kabul eder. Visual Studio 'da bir Office çözümü geliştirmek için Visual Basic kullanıyorsanız, varsayılan değerler eksik her parametre için otomatik olarak kullanıldığından isteğe bağlı parametreler için bir değer geçirmeniz gerekmez. Çoğu durumda, Visual C# projelerinde isteğe bağlı parametreleri de atlayabilirsiniz. Ancak,  `ThisDocument` belge düzeyi Word projelerinde sınıfının isteğe bağlı başvuru parametrelerini atlayamazsınız.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual C# ve Visual Basic projelerinde isteğe bağlı parametrelerle çalışma hakkında daha fazla bilgi için, bkz. [adlandırılmış ve isteğe bağlı bağımsız değişkenler &#40;C&#35; programlama kılavuzu&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) ve [isteğe bağlı parametreler &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;.

> [!NOTE]
> Visual Studio 'nun önceki sürümlerinde, Visual C# projelerindeki her isteğe bağlı parametre için bir değer geçirmeniz gerekir. Kolaylık olması için bu projeler, `missing` parametresinin varsayılan değerini kullanmak istediğinizde isteğe bağlı bir parametreye geçirebilmeniz adlı genel bir değişken içerir. Visual Studio 'da Office için Visual C# projeleri hala değişkeni içerir `missing` , ancak [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]  `ThisDocument` Word için belge düzeyi projelerindeki isteğe bağlı başvuru parametrelerine sahip yöntemleri çağırdığınızda, genellikle ' de Office çözümlerini geliştirirken kullanmanız gerekmez.

## <a name="example-in-excel"></a>Excel 'de örnek
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>Yönteminde birçok isteğe bağlı parametre vardır. Bazı parametrelerin değerlerini belirtebilir ve aşağıdaki kod örneğinde gösterildiği gibi başkalarının varsayılan değerini kabul edebilirsiniz. Bu örnek, adlı bir çalışma sayfası sınıfına sahip bir belge düzeyi projesi gerektirir `Sheet1` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb" id="Snippet1":::

## <a name="example-in-word"></a>Word 'de örnek
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>Yönteminde birçok isteğe bağlı parametre vardır. Bazı parametrelerin değerlerini belirtebilir ve aşağıdaki kod örneğinde gösterildiği gibi başkalarının varsayılan değerini kabul edebilirsiniz.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet1":::

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Word için Visual C# belge düzeyi projelerindeki ThisDocument sınıfında isteğe bağlı yöntemlerin parametrelerini kullanın
 Word nesne modeli, değerleri kabul eden isteğe bağlı **başvuru** parametrelerine sahip birçok yöntem içerir <xref:System.Object> . Ancak  `ThisDocument` Word Için Visual C# belge düzeyi projelerinde oluşturulan sınıfın yöntemlerinin isteğe bağlı başvuru parametrelerini atlayamazsınız. Visual C# isteğe bağlı **başvuru** parametrelerini yalnızca sınıfların değil arayüzlerin yöntemlerine atlamanızı sağlar. Örneğin, aşağıdaki kod örneği derlenmez, çünkü sınıfının yönteminin isteğe bağlı **başvuru** parametrelerini atlayamazsınız <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> `ThisDocument` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet3":::

 Sınıfının yöntemlerini çağırdığınızda `ThisDocument` Şu yönergeleri izleyin:

- İsteğe bağlı bir **ref** parametresinin varsayılan değerini kabul etmek için, `missing` değişkeni parametresine geçirin. `missing`Değişkeni, Visual C# Office projelerinde otomatik olarak tanımlanır ve <xref:System.Type.Missing> oluşturulan proje kodundaki değere atanır.

- İsteğe bağlı bir **başvuru** parametresi için kendi değerini belirtmek için, belirtmek istediğiniz değere atanan bir nesne bildirin ve sonra nesneyi parametreye geçirin.

  Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> *ıgnorebüyük* parametresi için bir değer belirtilerek ve diğer parametrelerin varsayılan değerini kabul ederek yönteminin nasıl çağrılacağını gösterir.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet4":::

  Sınıftaki bir yöntemin isteğe bağlı **başvuru** parametrelerini atlayan bir kod yazmak isterseniz `ThisDocument` , alternatif olarak <xref:Microsoft.Office.Interop.Word.Document> özelliği tarafından döndürülen nesnede aynı yöntemi çağırabilirsiniz <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> ve bu yöntemden parametreleri atlayabilirsiniz. Bu <xref:Microsoft.Office.Interop.Word.Document> , bir sınıf yerine bir arabirim olduğundan bunu yapabilirsiniz.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet5":::

  Değer ve başvuru türü parametreleri hakkında daha fazla bilgi için bkz. [bağımsız değişkenleri değere göre ve başvuruya göre geçirme &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic için) ve [&#40;C&#35; Programlama Kılavuzu&#41;parametrelerini geçirin ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
