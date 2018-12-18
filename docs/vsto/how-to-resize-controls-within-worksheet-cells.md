---
title: 'Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma'
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
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91a7e66e085408b35f0ce1d8f7d4783e0c4715a8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677286"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma
  Çalışma sayfasında satırları veya sütunları yeniden boyutlandırdığınızda, hücreleri içinde herhangi bir ana bilgisayar denetimleri yeniden boyutlandırılmış hücre genişliği veya yüksekliği otomatik olarak yeniden boyutlandırın. Windows Forms denetimleri varsayılan olarak otomatik olarak yeniden boyutlandırma değil.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Tasarım zamanında denetimleri eklerseniz, her denetimi için seçenekleri konumlandırma ayarlamanız gerekir.  
  
 Program aracılığıyla bir Windows Forms denetimi ekleyin ve bir aralığı bağımsız değişken sağlayın, bir hücre aralığı içinde yeniden boyutlandırıldığında denetimi otomatik olarak yeniden boyutlandırır. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resize-controls-at-design-time"></a>Tasarım zamanında denetimleri yeniden boyutlandırma  
  
### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Denetimleri tasarım zamanında hücreleri yeniden boyutlandırmak için  
  
1.  Gelen **araç kutusu**, çalışma için bir Windows Forms denetimi sürükleyin.  
  
2.  Denetime sağ tıklayın ve ardından **biçim denetimi**.  
  
3.  İçinde **biçim denetimi** iletişim kutusu, tıklayın **özellikleri** sekmesi.  
  
4.  Altında **Nesne konumlandırma**seçin **taşıyın ve hücrelerle** seçeneğini ve ardından **Tamam**.  
  
     Denetimi içeren hücreye yeniden boyutlandırdığınızda, denetimin hücreye sığacak şekilde yeniden boyutlandırır.  
  
## <a name="resize-controls-at-runtime"></a>Çalışma zamanı denetimleri yeniden boyutlandırma  
 Çalışma zamanında Windows Forms Denetim ekleme ve geçirin bir <xref:Microsoft.Office.Interop.Excel.Range> aralığı içeren çalışma sayfası hücresi yeniden boyutlandırıldığında denetimin konumu denetimi otomatik olarak yeniden boyutlandırılır.  
  
### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Denetimleri hücrelerle çalışma zamanında yeniden boyutlandırmak için  
  
1.  A1 aralığı için bir denetim ekleyin.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Denetimi içeren hücreye yeniden boyutlandırdığınızda, denetimin hücreye sığacak şekilde yeniden boyutlandırır.  
  
## <a name="reset-control-placement"></a>Denetim yerleşimini Sıfırla  
 Yerleştirme ve denetimin ayarlayarak yeniden boyutlandırma sıfırlayabilirsiniz `Placement` aşağıdakilerden birini özelliğini <xref:Microsoft.Office.Interop.Excel.XlPlacement> değerleri:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Böylece bırakmaz yeniden boyutlandırmak veya hücrenin taşıma denetiminin davranışını değiştirmek için  
  
1.  Denetimin yerleşimi özelliğini çağırın ve değeri <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Nasıl yapılır: yazdırırken çalışma sayfası denetimlerini gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  