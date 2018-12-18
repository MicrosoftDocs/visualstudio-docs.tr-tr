---
title: 'Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme'
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
- NamedRange control, resizing
- ranges, resizing in Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d785aba9d08f71aa8530bc2edd015f497caafef
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676700"
---
# <a name="how-to-resize-namedrange-controls"></a>Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme
  Boyutu ayarlayabileceğiniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Microsoft Office Excel belgeye eklediğiniz zaman denetimi; ancak daha sonraki bir zamanda yeniden boyutlandırmak isteyebilirsiniz.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Adlandırılmış aralık tasarım zamanında veya belge düzeyi projelere çalışma zamanında yeniden boyutlandırabilirsiniz. Ayrıca, çalışma zamanında uygulama düzeyi VSTO eklentileri adlandırılmış aralıklar boyutlandırabilirsiniz.  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
-   [Tasarım zamanında NamedRange denetimlerinin boyutunu değiştirme](#designtime)  
  
-   [Çalışma zamanında bir belge düzeyi projede NamedRange denetimlerinin boyutunu değiştirme](#runtimedoclevel)  
  
-   [Çalışma zamanında VSTO eklenti projesinde NamedRange denetimlerinin boyutunu değiştirme](#runtimeaddin)  
  
##  <a name="designtime"></a> Tasarım zamanında NamedRange denetimlerinin boyutunu değiştirme  
 Adlandırılmış aralık boyutunda tanımlayarak boyutlandırabilirsiniz **tanımlayan adı** iletişim kutusu.  
  
### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Adlandırılmış aralık tanımlayan adı iletişim kutusunu kullanarak yeniden boyutlandırmak için  
  
1.  Sağ bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi.  
  
2.  Tıklayın **adlandırılmış aralıkları Yönet** kısayol menüsünde.  
  
     **Tanımlayan adı** iletişim kutusu görüntülenir.  
  
3.  Yeniden boyutlandırmak istediğiniz adlandırılmış aralık seçin.  
  
4.  NET **başvurduğu** kutusu.  
  
5.  Adlandırılmış aralık boyutu tanımlamak için kullanmak istediğiniz alanları seçin.  
  
6.  **Tamam**'ı tıklatın.  
  
##  <a name="runtimedoclevel"></a> Çalışma zamanında bir belge düzeyi projede NamedRange denetimlerinin boyutunu değiştirme  
 Kullanarak, program aracılığıyla bir adlandırılmış aralık boyutlandırabilirsiniz <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> özelliği.  
  
> [!NOTE]  
>  İçinde **özellikleri** penceresinde <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> özelliği salt okunur olarak işaretlenmiş.  
  
### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış aralık programlı olarak yeniden boyutlandırmak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **A1** , `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Adlandırılmış aralık hücre içerecek şekilde yeniden boyutlandırın **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Çalışma zamanında VSTO eklenti projesinde NamedRange denetimlerinin boyutunu değiştirme  
 Yeniden bir <xref:Microsoft.Office.Tools.Excel.NamedRange> herhangi bir açık çalışma zamanında denetim. Ekleme hakkında daha fazla bilgi için bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetiminin çalışma için VSTO eklentisi kullanarak, bkz: [nasıl yapılır: çalışma sayfalarına NamedRange ekleme denetimlerini](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış aralık programlı olarak yeniden boyutlandırmak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **A1** , `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Adlandırılmış aralık hücre içerecek şekilde yeniden boyutlandırın **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Nasıl yapılır: yer işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)   
 [Nasıl yapılır: ListObject denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-listobject-controls.md)  
  
  