---
title: 'Nasıl yapılır: ListObject denetimlerinin boyutunu değiştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3608399613063a0fa572fe4de12b77187f8b4b41
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811509"
---
# <a name="how-to-resize-listobject-controls"></a>Nasıl yapılır: ListObject denetimlerinin boyutunu değiştirme
  Boyutunu ayarlamak bir <xref:Microsoft.Office.Tools.Excel.ListObject> Microsoft Office Excel çalışma kitabına eklediğinizde denetimi; ancak daha sonraki bir zamanda yeniden boyutlandırmak isteyebilirsiniz. Örneğin, iki sütunlu bir liste için üç sütun değiştirmek isteyebilirsiniz.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Yeniden <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında veya belge düzeyi projelere çalışma zamanında denetimler. Yeniden <xref:Microsoft.Office.Tools.Excel.ListObject> denetimlerini çalışma zamanında VSTO eklenti projesinde.  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında ListObject denetimlerinin boyutunu değiştirme](#designtime)  
  
- [Çalışma zamanında bir belge düzeyi projede ListObject denetimlerinin boyutunu değiştirme](#runtimedoclevel)  
  
- [Çalışma zamanında VSTO eklenti projesinde ListObject denetimlerinin boyutunu değiştirme](#runtimeaddin)  
  
  Hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.ListObject> denetimlerini, [ListObject denetimine](../vsto/listobject-control.md).  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [ı: ekleme sütunları zamanında verilere bağlı bir liste nesnesi için bunu nasıl?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> ListObject denetimi tasarım zamanında yeniden boyutlandırma  
 Listeyi yeniden boyutlandırmak için tıklayın ve boyutlandırma tutamaçlarından birinin sürükleyin veya boyutunda tanımlayabilirsiniz **listeyi yeniden boyutlandır** iletişim kutusu.  
  
### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Listeyi Yeniden Boyutlandır iletişim kutusunu kullanarak listesini yeniden boyutlandırmak için  
  
  
1.  Herhangi bir yeri tıklatın <xref:Microsoft.Office.Tools.Excel.ListObject> tablo. **Tablo araçları** > **tasarım** Şerit sekmesinde görüntülenir.  
  
2.  Özellikleri bölümünde tıklayarak **yeniden boyutlandırma tablo**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Yeni tablonuza veri aralığını seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
##  <a name="runtimedoclevel"></a> ListObject denetimi bir belge düzeyi projesi çalışma zamanında yeniden boyutlandırma  
 Yeniden bir <xref:Microsoft.Office.Tools.Excel.ListObject> kullanarak çalışma zamanında denetim <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> yöntemi. Taşımak için bu yöntemi kullanamazsınız <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasında yeni bir konuma denetim. Aynı satırda ve yeniden boyutlandırılan kalması gereken üstbilgileri <xref:Microsoft.Office.Tools.Excel.ListObject> denetim özgün liste nesnesiyle çakışmaması gerekir. Yeniden boyutlandırılan <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi, bir üst bilgi satırı ve verilerin en az bir satır içermelidir.  
  
### <a name="to-resize-a-list-object-programmatically"></a>Liste nesnesine programlı olarak yeniden boyutlandırmak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Tools.Excel.ListObject> hücre denetimi **A1** aracılığıyla **B3** üzerinde `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Listeyi hücreleri içerecek şekilde yeniden boyutlandırın **A1** aracılığıyla **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> ListObject çalışma zamanında VSTO eklenti projesinde yeniden boyutlandırma  
 Yeniden bir <xref:Microsoft.Office.Tools.Excel.ListObject> herhangi bir açık çalışma zamanında denetim. Ekleme hakkında daha fazla bilgi için bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetiminin çalışma için VSTO eklentisi kullanarak, bkz: [nasıl yapılır: çalışma sayfalarına ListObject ekleme denetimlerini](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
### <a name="to-resize-a-list-object-programmatically"></a>Liste nesnesine programlı olarak yeniden boyutlandırmak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Tools.Excel.ListObject> hücre denetimi **A1** aracılığıyla **B3** üzerinde `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Listeyi hücreleri içerecek şekilde yeniden boyutlandırın **A1** aracılığıyla **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject denetimi](../vsto/listobject-control.md)   
 [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Nasıl yapılır: yer işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)   
 [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)  
  
  