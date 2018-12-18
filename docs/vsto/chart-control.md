---
title: Grafik denetimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 439d31b05a861a7c83a10fa728a1e8d3defb305f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248091"
---
# <a name="chart-control"></a>Grafik denetimi
  <xref:Microsoft.Office.Tools.Excel.Chart> Olayları ortaya koyan bir çizelge nesnesine bir denetimdir. Visual Studio bir grafik çalışma sayfasına eklediğinizde, oluşturur bir <xref:Microsoft.Office.Tools.Excel.Chart> Microsoft Office Excel nesne modeline geçiş yapmak zorunda kalmadan doğrudan programlayabileceğiniz, nesne.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Denetim oluşturma  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.Chart> tasarım zamanında veya çalışma zamanında bir belge düzeyi projesi bir Microsoft Office Excel çalışma sayfasına denetimler.  
  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.Chart> denetimlerini çalışma zamanında VSTO eklenti. Daha fazla bilgi için [nasıl yapılır: Çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Dinamik olarak oluşturulan grafik nesneleri çalışma sayfasında sürdürülmez çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Biçimlendirme  
 Tüm biçimlendirme, uygulanabilir bir <xref:Microsoft.Office.Interop.Excel.Chart> için de uygulanabilir bir <xref:Microsoft.Office.Tools.Excel.Chart> denetimi. Bu, kenarlıkların, yazı tipleri, grafik türü, kılavuz çizgileri, gösterge ve veri etiketleri içerir.  
  
## <a name="events"></a>Olaylar  
 Aşağıdakiler için kullanılabilir <xref:Microsoft.Office.Tools.Excel.Chart> denetimi:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Nasıl yapılır: Çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  