---
title: 'Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 402e7f80ea208d714b31bd61e25b352494310487
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949259"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme
  Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında ve belge düzeyi projelere çalışma zamanında bir Microsoft Office Excel çalışma sayfasına denetimler.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Ayrıca ekleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject> VSTO eklentisi projeleri çalışma zamanında denetimler.  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında ListObject denetimleri ekleme](#designtime)  
  
- [Çalışma zamanında bir belge düzeyi projede ListObject denetimleri ekleme](#runtimedoclevel)  
  
- [Çalışma zamanında VSTO eklenti projesinde ListObject denetimleri ekleme](#runtimeaddin)  
  
  Hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.ListObject> denetimlerini, [ListObject denetimine](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Tasarım zamanında ListObject denetimleri ekleme  
 Eklemek için çeşitli yollar vardır <xref:Microsoft.Office.Tools.Excel.ListObject> denetimlerini çalışma zamanında bir belge düzeyi projede: gelen Visual Studio'dan Excel'den **araç kutusu**, gelen ve giden **veri kaynakları** penceresi.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>Excel'de Şerit kullanma  
  
1.  Üzerinde **Ekle** sekmesinde **tabloları** grubunda **tablo**.  
  
2.  Veya daha fazla hücreyi tıklatın ve listeye eklemek istediğiniz seçin **Tamam**.  
  
#### <a name="to-use-the-toolbox"></a>Araç kutusunu kullanmak için  
  
1.  Gelen **Excel denetimleri** sekmesinde **araç kutusu**, sürükleyin bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma.  
  
     **ListObject Denetimi Ekle** iletişim kutusu görüntülenir.  
  
2.  Veya daha fazla hücreyi tıklatın ve listeye eklemek istediğiniz seçin **Tamam**.  
  
     Varsayılan adı bırakın istemiyorsanız adı değiştirebilirsiniz **özellikleri** penceresi.  
  
#### <a name="to-use-the-data-sources-window"></a>Veri kaynakları penceresi kullanmak için  
  
1.  Açık **veri kaynakları** penceresi ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için [yeni bağlantı ekleme](../data-tools/add-new-connections.md).  
  
2.  Bir tablodan sürükleyin **veri kaynakları** çalışma penceresine.  
  
     Verilere bağlı <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi çalışma sayfasına eklenir. Daha fazla bilgi için [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Çalışma zamanında bir belge düzeyi projede ListObject denetimleri ekleme  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.ListObject> zamanında dinamik olarak denetim. Bu olaylara yanıt olarak konak denetimleri oluşturmanıza olanak sağlar. Dinamik olarak oluşturulan listenin nesneler, çalışma sayfasında sürdürülmez çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>ListObject denetimi bir çalışma sayfasına programlı olarak eklemek için  
  
1.  İçinde <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> olay işleyicisine `Sheet1`, eklemek için aşağıdaki kodu ekleyin bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim hücrelere **A1** aracılığıyla **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Çalışma zamanında VSTO eklenti projesinde ListObject denetimleri ekleme  
 Ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Excel.ListObject> programlı bir şekilde bir VSTO eklenti projesinde herhangi bir açık çalışma sayfasına denetimi. Dinamik olarak oluşturulan listenin nesneler, çalışma sayfasında sürdürülmez çalışma kaydedilir ve sonra kapalı olduğunda denetimleri gibi. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>ListObject denetimi bir çalışma sayfasına programlı olarak eklemek için  
  
1.  Açık bir çalışma sayfasına göre ve ardından ekleyen bir çalışma sayfası konak öğesi aşağıdaki kod oluşturur bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim hücrelere **A1** aracılığıyla **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [ListObject denetimi](../vsto/listobject-control.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Nasıl yapılır: ListObject denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-listobject-controls.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  