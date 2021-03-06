---
title: Şekilleri Visio belgesinde program aracılığıyla kopyalayıp yapıştırma
description: Bir belgenin bir sayfasında program aracılığıyla şekilleri nasıl kopyalayabileceğinizi ve bunları aynı belgede yeni bir sayfaya yapıştırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7cda46330967ef2b2b08db2109a030bbef8cace
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828559"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Nasıl yapılır: Visio belgesine program aracılığıyla şekilleri kopyalama ve yapıştırma
  Bir belgenin bir sayfasında program aracılığıyla şekilleri kopyalayabilir ve bunları aynı belgede yeni bir sayfaya yapıştırabilirsiniz. Bunları varsayılan konuma (etkin pencerenin Merkezi) veya orijinal sayfada sahip oldukları şekliyle aynı koordinat konumlarına yapıştırmayı seçebilirsiniz.

## <a name="copy-and-paste-shapes"></a>Şekilleri Kopyala ve Yapıştır
 Nesne modeli hakkında daha fazla bilgi için, [Microsoft. Office. Interop. Visio. Shape. DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), Microsoft. Office. Interop. Visio. Shape. [DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft. Office. Interop.](/office/vba/api/Visio.Shape.Copy)Visio. Shape. Copy, ve [Microsoft. Office. Interop. Visio. Shape. Paste](/office/vba/api/Visio.Shape.Paste) yöntemleri ve [Microsoft. Office. ıNTEROP. Visio. VisCutCopyPasteCodes. visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) bayrağını için VBA başvuru belgelerine bakın.

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Şekilleri başka bir sayfanın merkezine kopyalamak için

- Aşağıdaki örnek, ilk sayfadan şekillerin nasıl kopyalanacağını ve ikinci sayfanın ortasına yapıştırılacağını gösterir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet14":::

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Aynı pozisyonlarla şekilleri Kopyala ve Yapıştır
 Nesne modeliyle ilgili ayrıntılar için bkz. Microsoft için VBA başvuru belgeleri [. Office. Interop. Visio. Shape. DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft. Office. Interop. Visio. Shape. DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft. Office. Interop. Visio](/office/vba/api/Visio.Shape.Copy). Shape. Copy, ve [Microsoft. Office. Interop. Visio. Shape. Paste](/office/vba/api/Visio.Shape.Paste) yöntemleri ve [Microsoft. Office. Interop. Visio. VisCutCopyPasteCodes. visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) bayrağı.

 Yapıştırılan bilgilerin biçimini denetetmeniz ve (isteğe bağlı olarak) bir kaynak dosyaya bağlantı kurmak (örneğin, bir Microsoft Office Word belgesi) için, PasteSpecial yöntemini kullanın.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Şekilleri ve şekil konumlarını başka bir sayfaya kopyalamak için

- Aşağıdaki örnek, ilk sayfadan şekillerin nasıl kopyalanacağını ve özgün koordinat konumlarına sahip ikinci sayfaya nasıl yapıştırılacağını gösterir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md)
- [Nasıl yapılır: Visio belgesine program aracılığıyla şekiller ekleme](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
