---
title: 'Nasıl yapılır: program aracılığıyla Excel aralıklarında veri değerlerini metin formatında depolayabileceği ve'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f1abe0e797a65886f595913f8e6495ec084b7e2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677255"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Nasıl yapılır: program aracılığıyla Excel aralıklarında veri değerlerini metin formatında depolayabileceği ve
  Değerleri depolanıp bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi veya yerel Excel range nesnesi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Tarihinde veya sonrasında 1/1/1900 Visual Studio'da Office geliştirme araçlarını kullanarak bir aralıkta kalan bir tarih değeri depolarsanız, OLE Otomasyon (OA) biçiminde depolanır. Kullanmalısınız <xref:System.DateTime.FromOADate%2A> OLE Otomasyon (OA) tarih değerini almak için yöntemi. Tarih 1/1/1900'den eskiyse, bir dize olarak depolanır.  
  
> [!NOTE]  
>  OLE Otomasyonu tarihleri 1900 ilk iki ay boyunca Excel tarihleri farklıdır. Ayrıca farklar vardır, **1904 sistem tarihi** seçeneği denetlenir. Aşağıdaki kod örnekleri, bu farklılıkları içermez.  
  
## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma  
  
-   Bu örnek için belge düzeyi özelleştirmeleri içindir. Aşağıdaki kod, bir sayfa sınıfında değil yerleştirilmelidir `ThisWorkbook` sınıfı.  
  
### <a name="to-store-a-date-value-in-a-named-range"></a>Adlandırılmış aralıkta bir tarih değeri depolamak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim hücresinde **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Değeri olarak bugünün tarihini ayarlayın `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Adlandırılmış bir aralıktan bir tarih değerini almak için  
  
1.  Tarih değerini almak `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="use-native-excel-ranges"></a>Yerel Excel aralıkları kullanın  
  
### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Yerel bir Excel range nesnesinde bir tarih değeri depolamak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Interop.Excel.Range> hücreyi temsil eden **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Değeri olarak bugünün tarihini ayarlayın `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Yerel bir Excel range nesnesinden bir tarih değerini almak için  
  
1.  Tarih değerini almak `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Aralıklarla çalışma](../vsto/working-with-ranges.md)   
 [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla bakma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  