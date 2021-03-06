---
title: 'Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme'
description: Belge düzeyi özelleştirmesinde özel bir XML bölümü oluşturarak bir Microsoft Office Excel çalışma kitabında veya Microsoft Office Word belgesinde XML verilerini nasıl depolayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99374a2daded3c4b49b60053a69cd1ff7c4dffe8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827701"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme
  XML verilerini bir Microsoft Office Excel çalışma kitabında veya Microsoft Office Word belgesinde, belge düzeyi özelleştirmesinde özel bir XML bölümü oluşturarak saklayabilirsiniz. Daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio, PowerPoint Microsoft Office için belge düzeyi projeleri sağlamaz. VSTO eklentisini kullanarak bir PowerPoint sunusuna özel XML bölümü ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Excel çalışma kitabına özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Çalışma kitabındaki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Core.CustomXMLParts> . , <xref:Microsoft.Office.Core.CustomXMLPart> Çalışma kitabında depolamak ISTEDIĞINIZ XML dizesini içerir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Yöntemi, `AddCustomXmlPartToWorkbook` `ThisWorkbook` Excel için belge düzeyindeki bir projede sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı çalışma kitabını açtığında özel XML bölümünü oluşturmak için `ThisWorkbook_Startup` olay işleyicisinden yöntemi çağırın.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word belgesine özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Belgedeki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Core.CustomXMLParts> . , <xref:Microsoft.Office.Core.CustomXMLPart> Belgede depolamak ISTEDIĞINIZ XML dizesini içerir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. `AddCustomXmlPartToDocument` `ThisDocument` Word için belge düzeyindeki bir projede yöntemi sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı belgeyi açtığında özel XML bölümünü oluşturmak için `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

## <a name="robust-programming"></a>Güçlü programlama
 Kolaylık olması için bu örnek, yönteminde yerel değişken olarak tanımlanan bir XML dizesi kullanır. Genellikle, XML dosyasını bir dosya veya veritabanı gibi bir dış kaynaktan edinmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)
- [Nasıl yapılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
