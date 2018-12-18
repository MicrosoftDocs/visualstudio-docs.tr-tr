---
title: 'Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 713657c7df5bfd3dd3f864c15ffc86dd1d531eac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919929"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme
  Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.Chart> tasarım zamanında ve belge düzeyi özelleştirmeleri çalışma zamanında bir Microsoft Office Excel çalışma sayfasına denetimler. Ayrıca ekleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.Chart> VSTO eklentileri çalışma zamanında denetimler.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında grafik denetimleri ekleme](#designtime)  
  
- [Belge düzeyi projesi çalışma zamanında grafik denetimleri ekleme](#runtimedoclevel)  
  
- [Çalışma zamanında VSTO eklenti projesinde grafik denetimleri ekleme](#runtimeaddin)  
  
  Hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.Chart> denetimlerini, [grafik denetimi](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Tasarım zamanında grafik denetimleri ekleme  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.Chart> denetimine ekleme uygulamadan bir grafik aynı şekilde çalışma.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> Denetim kullanılabilir değil **araç kutusu** veya **veri kaynakları** penceresi.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Bir Excel çalışma sayfasında grafik konak denetimi eklemek için  
  
1.  Üzerinde **Ekle** sekmesinde **grafikleri** grubunda **sütun**grafiklerin bir kategoriye tıklayın ve ardından istediğiniz grafik türüne tıklayın.  
  
2.  İçinde **Grafik Ekle** iletişim kutusu, tıklayın **Tamam**.  
  
3.  Üzerinde **tasarım** sekmesinde **veri** grubunda **veri Seç**.  
  
4.  İçinde **veri kaynağı Seç** iletişim kutusu, tıklama **grafik** **veri aralığı** kutusuna ve herhangi bir varsayılan seçimi temizleyin.  
  
5.  İçinde **grafiği için veri** sayfa, grafik verilerini içeren hücre aralığını seçin (hücreleri **A5** aracılığıyla **D8**).  
  
6.  İçinde **veri kaynağı Seç** iletişim kutusu, tıklayın **Tamam**.  
  
##  <a name="runtimedoclevel"></a> Belge düzeyi projesi çalışma zamanında grafik denetimleri ekleme  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.Chart> zamanında dinamik olarak denetim. Dinamik olarak oluşturulan grafikleri belgede sürdürülmez belge kapatıldığında denetimleri gibi. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Grafik denetimi bir çalışma sayfasına programlı olarak eklemek için  
  
1.  İçinde <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> olay işleyicisine `Sheet1`, eklemek için aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Excel.Chart> denetimi.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Çalışma zamanında VSTO eklenti projesinde grafik denetimleri ekleme  
 Ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Excel.Chart> programlı bir şekilde bir VSTO eklenti projesinde herhangi bir açık çalışma sayfasına denetimi. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Dinamik olarak oluşturulan grafik denetimleri, çalışma sayfasında sürdürülmez çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [ekleme denetimleri Office belgelerine çalışma zamanında](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Grafik denetimi bir çalışma sayfasına programlı olarak eklemek için  
  
1.  Açık bir çalışma sayfasına göre ve ardından ekleyen bir çalışma sayfası konak öğesi aşağıdaki kod oluşturur bir <xref:Microsoft.Office.Tools.Excel.Chart> denetimi.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnek aşağıdaki gereksinimlere sahiptir:  
  
-   Grafiği, A5-aralığında D8 çalışma sayfasındaki depolanan veriler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Grafik denetimi](../vsto/chart-control.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  