---
title: NamedRange denetimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c9bc4ff5b3515d5dcd4dab1eef81bf5c9abf979
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677781"
---
# <a name="namedrange-control"></a>NamedRange denetimi
  <xref:Microsoft.Office.Tools.Excel.NamedRange> Verilere bağlı benzersiz bir ada sahip ve olayları ortaya koyan bir aralığı denetimidir. Daha fazla bilgi için [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Denetim oluşturma  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> tasarım zamanında veya belge düzeyi projelere çalışma zamanında bir Microsoft Office Excel çalışma sayfasına denetimler.  
  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimlerini çalışma zamanında VSTO eklenti. Daha fazla bilgi için [nasıl yapılır: çalışma sayfalarına NamedRange ekleme denetimlerini](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Varsayılan olarak, çalışma sayfasında dinamik olarak oluşturulan adlandırılmış aralıklar sürdürülmeyen çalışma kapatıldığında denetimleri gibi. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimleri yalnızca belirli sayfalardaki aralıklarının oluşabilir. <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimleri, tüm sayfalara geçerli göreli adlara sahip olamaz ve bir çalışma kitabı (3-b aralıkları) iki veya daha fazla çalışma sayfalarına yayılamaz.  
  
## <a name="bind-data-to-the-control"></a>Veriyi denetime bağlama  
 Adlandırılmış aralık birçok hücreleri olabileceğinden, karmaşık veri bağlama için iyi bir aday olarak görünebilir; Ancak, bir aralık yalnızca bir kolayca bir veri kümesinden belirli bir sütunla eşlenemez hücreleri koleksiyonudur. Bu nedenle, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimleri yalnızca basit veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Excel.ListObject> Denetimi karmaşık veri bağlama için kullanılabilir. Daha fazla bilgi için [ListObject denetimine](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetimi kullanarak bir veri kaynağına bağlanabilir <xref:System.Windows.Forms.Control.DataBindings%2A> özellikleri. Varsayılan veri bağlama özelliğini <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Herhangi bir mekanizma aracılığıyla ilişkili veri kümesindeki veriler güncelleştirilirse <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi değişiklikleri yansıtır.  
  
## <a name="formatting"></a>Biçimlendirme  
 Uygulanabilir biçimlendirme bir <xref:Microsoft.Office.Interop.Excel.Range> uygulanabilir bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi. Bu, kenarlıkların, yazı tipleri, sayı biçimlerini ve stilleri içerir.  
  
## <a name="rename-the-control"></a>Denetimi yeniden adlandırma  
 Eklediğinizde bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfanızdaki denetimine **araç kutusu**, Visual Studio denetim için bir ad otomatik olarak oluşturur. Adı değiştirebilirsiniz **özellikleri** penceresi.  
  
## <a name="events"></a>Olaylar  
 Aşağıdakiler için kullanılabilir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [İzlenecek yol: Program NamedRange denetimi olaylarına karşı](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  