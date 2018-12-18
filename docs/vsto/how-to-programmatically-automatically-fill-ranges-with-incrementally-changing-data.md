---
title: 'Nasıl yapılır: aralıkları artımlı şekilde değişen verilerle program aracılığıyla otomatik doldurma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4fff7eb59ff2fe5e17ddf500bf546502492634d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256409"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Nasıl yapılır: aralıkları artımlı şekilde değişen verilerle program aracılığıyla otomatik doldurma
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Yöntemi <xref:Microsoft.Office.Interop.Excel.Range> nesne çalışma sayfasındaki bir aralığı değerlerle otomatik olarak doldurmanıza olanak sağlar. Çoğu zaman <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> yöntemi rutin olarak artan veya azalan bir aralık değerleri depolamak için kullanılır. Sabit listesinden isteğe bağlı bir sabit sağlayarak için davranış belirtebilirsiniz <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> numaralandırması.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 İki aralıkları kullanırken belirtmelisiniz <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Çağıran aralık <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> dolgunun başlangıç noktasını belirler ve bir başlangıç değeri içeren yöntemi.  
  
-   Bir parametre olarak geçirilen doldurmak istediğiniz aralık <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> yöntemi. Bu hedef aralığın başlangıç değerini içeren aralığı eklemeniz gerekir.  
  
    > [!NOTE]  
    >  Geçiremezsiniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> yerine kontrol <xref:Microsoft.Office.Interop.Excel.Range>. Daha fazla bilgi için bkz: [konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 İlk hücrenin doldurmak istediğiniz aralığın başlangıç değeri içermelidir.  
  
 Örnek, üç bölgeyi doldurmanızı gerektirir:  
  
-   B sütunundaki beş hafta eklemektir. İlk değer için türü **Pazartesi** B1 hücresindeki.  
  
-   Sütun C beş ay eklemektir. İlk değer için türü **Ocak** C1 hücresindeki.  
  
-   Sütun D numaraları, iki her satır için olarak artan bir dizi eklemektir. İlk değerlerini yazın **4** D1 hücresinde ve **6** D2 hücresine.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Aralıkları ile çalışma](../vsto/working-with-ranges.md)   
 [Nasıl yapılır: program aracılığıyla çalışma sayfası aralıklarına başvuran](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stilleri uygulayın](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Nasıl yapılır: Excel hesaplarını program aracılığıyla çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  