---
title: Office belgelerine çalışma zamanında denetimler ekleme
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2ad16bc414e6d67b563240bcd2bceb15e9c34e97
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305643"
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Office belgelerine çalışma zamanında denetimler ekleme
  Microsoft Office Word belgesi ve Microsoft Office Excel çalışma zamanında denetimler ekleyebilirsiniz. Ayrıca bunları çalışma zamanında kaldırabilirsiniz. Çalışma zamanında ekleyip denetimleri çağrılır *Dinamik denetimleri*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 Bu konuda aşağıda açıklanmıştır:  

- [Denetimlerini çalışma zamanında denetim koleksiyonu yönetmek](#ControlsCollection).  

- [Konak denetimleri belgelerine ekleme](#HostControls).  

- [Belgelerine Windows Forms denetimleri ekleme](#WindowsForms).  

  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [nasıl ı: ekleme denetimleri belgeye yüzey çalışma zamanında?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Denetimlerini çalışma zamanında denetim koleksiyonu kullanarak yönetme  
 Ekle, Al veya denetimlerini çalışma zamanında kaldırmak için yardımcı yöntemleri kullanmak <xref:Microsoft.Office.Tools.Excel.ControlCollection> ve <xref:Microsoft.Office.Tools.Word.ControlCollection> nesneleri.  

 Bu nesnelere erişme şeklini geliştirdiğiniz projenin türüne bağlıdır:  

-   Excel için belge düzeyi projesinde kullanmak <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> özelliği `Sheet1`, `Sheet2`, ve `Sheet3` sınıfları. Bu sınıflar hakkında daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).  

-   Word için belge düzeyi projede kullanın <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliği `ThisDocument` sınıfı. Bu sınıf hakkında daha fazla bilgi için bkz: [belge konak öğesi](../vsto/document-host-item.md).  

-   Bir VSTO eklenti projesinde Excel veya Word kullanın `Controls` özelliği bir <xref:Microsoft.Office.Tools.Excel.Worksheet> veya <xref:Microsoft.Office.Tools.Word.Document> çalışma zamanında oluşturan. Çalışma zamanında bu nesneleri oluşturma hakkında daha fazla bilgi için bkz. [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Denetimler ekleme  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> Ve <xref:Microsoft.Office.Tools.Word.ControlCollection> türleri, belgeler ve çalışma için konak denetimleri ve ortak Windows Formları denetimleri eklemek için kullanabileceğiniz yardımcı yöntemler içerir. Her yöntem adı şu biçimdedir `Add` *denetim sınıf*burada *denetim sınıf* eklemek istediğiniz denetim sınıf adıdır. Örneğin, eklemek için bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi kullanın, belgeye <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> yöntemi.  

 Aşağıdaki kod örneği bir <xref:Microsoft.Office.Tools.Excel.NamedRange> için `Sheet1` Excel için belge düzeyi projesinde.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Erişim ve silme denetimleri  
 Kullanabileceğiniz `Controls` özelliği bir <xref:Microsoft.Office.Tools.Excel.Worksheet> veya <xref:Microsoft.Office.Tools.Word.Document> belgenizdeki tasarım zamanında eklenen denetimleri de dahil olmak üzere tüm denetim boyunca yineleme yapmak için. Tasarım zamanında ekleme denetimleri de denir *statik denetim*.  

 Çağırarak Dinamik denetimleri kaldırabilirsiniz `Delete` yöntemi çağırarak veya denetimin `Remove` her denetimleri koleksiyonun yöntemi. Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> kaldırmak için yöntemi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> gelen `Sheet1` Excel için belge düzeyi projesinde.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Statik denetimlerini çalışma zamanında kaldırılamıyor. Kullanmayı denerseniz `Delete` veya `Remove` yöntemi statik bir denetimi kaldırmak için bir <xref:Microsoft.Office.Tools.CannotRemoveControlException> oluşturulur.  

> [!NOTE]  
>  Program aracılığıyla denetimlerinde kaldırmayın `Shutdown` belgenin olay işleyicisi. UI öğeleri artık kullanılabilir `Shutdown` olayı oluşturulur. Denetimleri belge kapatılmadan önce kaldırmak isterseniz, kodunuzu başka bir olay için olay işleyicisi aşağıdaki gibi eklemek <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> veya <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> Word için veya <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>, veya <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> Excel için.  

##  <a name="HostControls"></a> Konak denetimleri belgelere ekleme  
 Konak denetimleri program aracılığıyla belgelere eklediğinizde, denetimin benzersiz olarak tanımlayan bir ad sağlamanız gerekir ve belgeye denetim eklemek nereye belirtmeniz gerekir. Ayrıntılı yönergeler için aşağıdaki konulara bakın:  

- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)  

- [Nasıl yapılır: içerik ekleme denetimlerine Word belgeleri](../vsto/how-to-add-content-controls-to-word-documents.md)  

- [Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

  Konak denetimleri hakkında daha fazla bilgi için bkz: [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  

  Bir Belge kaydedildiğinde ve sonra kapalı olduğunda, tüm dinamik olarak oluşturulmuş konak denetimleri, olaylarından kesilir ve kendi veri bağlama işlevselliğini kaybeder. Çözümünüze belge açıldığında konak denetimleri yeniden oluşturmak için kod ekleyebilirsiniz. Daha fazla bilgi için [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Yardımcı yöntemler sağlanmadı aşağıdaki denetimleri barındırmak için bu denetimleri belgeleri program aracılığıyla eklenemez çünkü: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, ve <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Belgelerine Windows Forms denetimleri ekleme  
 Belgeye program aracılığıyla bir Windows Forms denetimi eklediğinizde, konumunu denetimi ve denetimin benzersiz olarak tanımlayan bir ad sağlamanız gerekir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Her denetim için yardımcı yöntemleri sağlar. Bir aralık veya denetimin konumu için belirli bir koordinat geçirebilmeniz bu yöntemler aşırı yüklenmesi sebebiyledir.  

 Bir Belge kaydedildiğinde ve ardından kapatıldığında, dinamik olarak oluşturulan tüm Windows Formları denetimlerini belgeden kaldırılır. Çözümünüze belge açıldığında denetimleri yeniden oluşturmak için kod ekleyebilirsiniz. Bir VSTO eklentisi kullanarak Windows Forms denetimlerini dinamik oluşturursanız, denetimler için ActiveX sarmalayıcısının belgede kalır. Daha fazla bilgi için [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Windows Forms denetimleri için korumalı belgeleri program aracılığıyla eklenemez. Program aracılığıyla bir Word belgesi veya Excel çalışma sayfası, bir denetim eklemek için korumasını, belge kapatıldığında denetimin ActiveX sarmalayıcısının üretimi kaldırmak için ek kod yazmanız gerekir. Denetimin ActiveX sarmalayıcısının üretimi, korumalı belgeleri otomatik olarak silinmez.  

### <a name="add-custom-controls"></a>Özel denetim ekleme  
 Eklemek istiyorsanız bir <xref:System.Windows.Forms.Control> kullanılabilir yardımcı yöntemler gibi özel bir kullanıcı denetimi tarafından desteklenmiyor, aşağıdaki yöntemleri kullanın:  

- Excel için birini <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> yöntemlerinin bir <xref:Microsoft.Office.Tools.Excel.ControlCollection> nesne.  

- Word için birini <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> yöntemlerinin bir <xref:Microsoft.Office.Tools.Word.ControlCollection> nesne.  

  Denetim eklemek için geçirmek <xref:System.Windows.Forms.Control>, bir denetim için konum ve bir denetim için benzersiz olarak tanımlayan ad `AddControl` yöntemi. `AddControl` Yöntemi denetimin çalışma sayfası veya belge ile nasıl etkileşime gireceğini tanımlayan nesneyi döndürür. `AddControl` Yöntemi döndürür bir <xref:Microsoft.Office.Tools.Excel.ControlSite> (Excel için) veya bir <xref:Microsoft.Office.Tools.Word.ControlSite> nesnesi (sözcük).  

  Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> dinamik olarak Excel belge düzeyi projesindeki çalışma sayfasına özel bir kullanıcı denetimi eklemek için yöntemi. Bu örnekte, kullanıcı denetimi adlı `UserControl1`ve <xref:Microsoft.Office.Interop.Excel.Range> adlı `range1`. Bu örneği kullanmak için çalıştırın bir `Sheet` *n* projedeki sınıf.  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Özel denetimler üyeleri kullanın  
 Aşağıdakilerden birini kullandıktan sonra `AddControl` çalışma sayfası ya da belge, artık bir denetim eklemek için yöntemleri olan iki farklı denetim nesnesi:  

- <xref:System.Windows.Forms.Control> , Özel bir denetimi temsil eder.  

- `ControlSite`, `OLEObject`, Veya `OLEControl` çalışma sayfası veya belgeye eklendikten sonra denetimini temsil eden nesne.  

  Çoğu özellikleri ve yöntemleri bu denetimler arasında paylaşılır. Uygun denetimler aracılığıyla bu üyelere erişmek önemlidir:  

- Yalnızca özel denetime ait üyelerinin erişmek için <xref:System.Windows.Forms.Control>.  

- Denetimler tarafından paylaşılan üyeleri erişmek için `ControlSite`, `OLEObject`, veya `OLEControl` nesne.  

  Paylaşılan bir üye erişim <xref:System.Windows.Forms.Control>, uyarı veya bildirim başarısız olabilir veya geçersiz sonuçlara neden olabilir. Her zaman yöntemleri veya özellikleri kullanmak `ControlSite`, `OLEObject`, veya `OLEControl` nesne yöntemi veya özelliği gerek olmadığı sürece kullanılamaz; yalnızca o gereken, başvuru <xref:System.Windows.Forms.Control>.  

  Örneğin, her ikisi de <xref:Microsoft.Office.Tools.Excel.ControlSite> sınıfı ve <xref:System.Windows.Forms.Control> sınıfı bir `Top` özelliği. Alınacak veya ayarlanacak denetimin üst ve belgenin üst kısmında arasındaki uzaklığı için kullanın <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> özelliği <xref:Microsoft.Office.Tools.Excel.ControlSite>değil <xref:System.Windows.Forms.Control.Top%2A> özelliği <xref:System.Windows.Forms.Control>.  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Ayrıca bkz.  
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Windows Forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
