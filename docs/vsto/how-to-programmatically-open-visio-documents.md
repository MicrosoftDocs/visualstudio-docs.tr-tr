---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini açma'
description: Visual Studio 'Yu kullanarak Open veya OpenEx yöntemleriyle bir Visio belgesini programlı bir şekilde nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f96efd41eb91551fe3cf7c03b55a44b7a9e1bf1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824750"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini açma
  Mevcut Microsoft Office Visio belgelerini açmak için iki yöntem vardır: Open ve OpenEx. OpenEx yöntemi, Open yöntemiyle aynıdır, ancak çağıranın belgenin nasıl açıldığını belirtebileceğiniz bağımsız değişkenler sağlar.

 Nesne modeli hakkında daha fazla bilgi için bkz.Microsoft.Office.Interop.Visio.Docilgili VBA başvuru belgeleri [ . ](/office/vba/api/Visio.Documents.Open) Yöntem ve [Microsoft.Office.Interop.Visio.Documtları açın. OpenEx](/office/vba/api/Visio.Documents.OpenEx) yöntemi.

## <a name="open-a-visio-document"></a>Bir Visio belgesi açın

### <a name="to-open-a-visio-document"></a>Bir Visio belgesi açmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.Open` ve Visio belgesinin tam yolunu sağlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>Belirtilen bağımsız değişkenlerle bir Visio belgesi açın

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Visio belgesini salt okunurdur ve sabitlenmiş olarak açmak için

- Yöntemi çağırın `Microsoft.Office.Interop.Visio.Documents.OpenEx` , Visio belgesinin tam yolunu sağlayın ve kullanmak istediğiniz bağımsız değişkenleri (Bu örnekte, sabitlenmiş ve salt okunurdur) dahil edin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- Adlı bir Visio belgesi `myDrawing.vsd` `Test` , Belgelerim klasöründe (Windows XP ve önceki sürümler  için) veya *Belgeler* klasöründe (Windows Vista için) adlı bir dizinde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
