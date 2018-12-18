---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfası aralıklarında metin arama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a323336979e16be376cfcd3da44cbc9b12bd73ea
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671969"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Nasıl yapılır: program aracılığıyla çalışma sayfası aralıklarında metni arayın
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Yöntemi <xref:Microsoft.Office.Interop.Excel.Range> nesne aralık içinde metin araması olanak sağlar. Bu metin herhangi bir çalışma sayfası hücresinde gibi görünebilir hata dizelerini de olabilir `#NULL!` veya `#VALUE!`. Hata dizeleri hakkında daha fazla bilgi için bkz. [hücre hata değerlerini](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Aşağıdaki örnekte adlı bir aralık arar `Fruits` ve "apples" sözcüğünü içeren hücrelerin yazı tipi değiştirir. Ayrıca, bu yordamı kullanır <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> önceden ayarlanmış kullanan yöntemi aramak için arama tekrarlama için ayarlar. Aramanın yapılacağı hücreyi belirtin ve <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> yöntemi rest işler.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Yöntemin arama aralığın sonuna ulaştıktan sonra geri arama aralığının başlangıcına kadar kaydırır. Kodunuzu arama sonsuz bir döngüde sarma olmayan emin emin olmanız gerekir. Örnek yordamı kullanarak bu durumu çözmek için bir yol gösterir <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> özelliği.  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [ı: kullanmak bir Excel eklenti bulma yönteminde bunu nasıl?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>Bir çalışma sayfası aralıktaki metni aramak için  
  
1. Aralığın tamamı, ilk bulunan aralığı ve geçerli bulunan aralığı izlemek için değişkenleri bildirin.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. Sonra aramak için hücre dışındaki tüm parametreler belirterek ilk eşleşme arayın.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. Eşleşme vardır sürece aramaya devam edin.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. İlk bulunan aralığı Karşılaştır (`firstFind`) için **hiçbir şey**. Varsa `firstFind` bulunan aralığı değeri hemen kod depoları içeren (`currentFind`).  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. Bulunan aralığı adresi adresinin ilk bulunan aralığı eşleşiyorsa döngüden çıkma.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. Bulunan aralığı görünümünü ayarlayın.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. Başka bir arama gerçekleştirin.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   Aşağıdaki örnek, ayrıntılı bir yöntemi gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Aralıklarla çalışma](../vsto/working-with-ranges.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara biçimler uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla bakma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  