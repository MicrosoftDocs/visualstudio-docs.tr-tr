---
title: 'Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35febfa4c4d13b3f5d3d279f7d1c35e96051d54b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867123"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme
  Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> tasarım zamanında ve belge düzeyi projelere çalışma zamanında bir Microsoft Office Excel çalışma sayfasına denetimler.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Ayrıca ekleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> VSTO eklentisi projeleri çalışma zamanında denetimler.  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında NamedRange denetimleri ekleme](#designtime)  
  
- [Çalışma zamanında bir belge düzeyi projede NamedRange denetimleri ekleme](#runtimedoclevel)  
  
- [Çalışma zamanında VSTO eklenti projesinde NamedRange denetimleri ekleme](#runtimeaddin)  
  
  Hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimlerini, [NamedRange denetimi](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Tasarım zamanında NamedRange denetimleri ekleme  
 Eklemek için çeşitli yollar vardır <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimlerini çalışma zamanında bir belge düzeyi projede: gelen Visual Studio'dan Excel'den **araç kutusu**, gelen ve giden **veri kaynakları** penceresi.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Ad kutusuna Excel kullanarak çalışma sayfasındaki NamedRange denetimi eklemek için  
  
1.  Veya daha fazla adlandırılmış aralıkta dahil etmek istediğiniz hücreyi seçin.  
  
2.  İçinde **adı kutusuna**, tuşuna basın ve aralığı için bir ad yazın **Enter**.  
  
     **Adı kutusuna** sütun hemen üstündeki formül çubuğunun yanında bulunan **A** çalışma sayfası.  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>NamedRange Denetimi Araç kutusunu kullanarak çalışma sayfasına eklemek için  
  
1.  Açık **araç kutusu** tıklatıp **Excel denetimleri** sekmesi.  
  
2.  Tıklayın <xref:Microsoft.Office.Tools.Excel.NamedRange> ve çalışma sayfasına sürükleyin.  
  
     **Ekle adlandırılmış aralık** iletişim kutusu görüntülenir.  
  
3.  Veya daha fazla adlandırılmış aralıkta dahil etmek istediğiniz hücreyi seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
     Denetime verilen varsayılan adı istemiyorsanız adı değiştirebilirsiniz **özellikleri** penceresi.  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>NamedRange denetimi veri kaynakları penceresini kullanarak çalışma sayfasına eklemek için  
  
1.  Açık **veri kaynakları** penceresi ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için [yeni bağlantı ekleme](../data-tools/add-new-connections.md).  
  
2.  Tek alanlardan birini sürükleyip **veri kaynakları** çalışma penceresine.  
  
     Verilere bağlı <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi çalışma sayfasına eklenir. Daha fazla bilgi için [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Çalışma zamanında bir belge düzeyi projede NamedRange denetimleri ekleme  
 Ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> programlı bir şekilde çalışma zamanında denetim. Bu olaylara yanıt olarak konak denetimleri oluşturmanıza olanak sağlar. Dinamik olarak oluşturulan adlandırılmış aralıklar çalışma sayfasında sürdürülmez çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>NamedRange denetimi bir çalışma sayfasına programlı olarak eklemek için  
  
1.  İçinde <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> olay işleyicisine `Sheet1`, eklemek için aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **A1** ve kendi <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliği `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Çalışma zamanında VSTO eklenti projesinde NamedRange denetimleri ekleme  
 Ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> programlı bir şekilde bir VSTO eklenti projesinde herhangi bir açık çalışma sayfasına denetimi. Dinamik olarak oluşturulan adlandırılmış aralıklar çalışma sayfasında sürdürülmez çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>NamedRange denetimi bir çalışma sayfasına programlı olarak eklemek için  
  
1.  Açık bir çalışma sayfasına göre ve ardından ekleyen bir çalışma sayfası konak öğesi aşağıdaki kod oluşturur bir <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **A1** ve ayarlar, <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğini `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  