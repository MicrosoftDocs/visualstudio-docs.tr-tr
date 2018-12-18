---
title: Çalışma sayfası konak öğesi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4052e7d9b096d9bae6671834369ece6d31bee4a0
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258924"
---
# <a name="worksheet-host-item"></a>Çalışma sayfası konak öğesi
  <xref:Microsoft.Office.Tools.Excel.Worksheet> Konak öğesi türüdür genişleten bir <xref:Microsoft.Office.Interop.Excel.Worksheet> Excel için birincil birlikte çalışma derlemesinden türü. <xref:Microsoft.Office.Tools.Excel.Worksheet> Konak öğesi tüm özellikleri, yöntemleri ve olayları olarak sağlayan bir <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnesi, ancak ayrıca ek olayları gösterir ve ana bilgisayar denetimleri ve Windows Forms denetimleri için kapsayıcı görevi görür.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Belge düzeyi projelerine eklediğiniz <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğelerini projenize tasarım zamanında. VSTO eklenti projelerinde oluşturabileceğiniz <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğelerini çalışma zamanında.  
  
## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Belge düzeyi projelerine çalışma sayfası konak öğeleri anlama  
 Excel için belge düzeyi projesi oluşturduğunuzda, Visual Studio otomatik olarak üç oluşturur <xref:Microsoft.Office.Tools.Excel.Worksheet> konak proje öğelerini. Çalışma sayfaları varsayılan adlarının `Sheet1`, `Sheet2`, ve `Sheet3`. Var olan bir çalışma kitabına bağlı bir proje oluşturduğunuzda, ana öğe sayısı çalışma kitabındaki sayısına bağlıdır.  
  
 Bu çalışma sayfası sınıfları üyelerine erişmenizi <xref:Microsoft.Office.Tools.Excel.Worksheet> bir çalışma kitabının içeriğini değiştirme gibi özelleştirme, temel görevlerini gerçekleştirmek için konak öğesi. Bu sınıfları, çalışma sayfasına denetimler ekleme için de kullanabilirsiniz. Farklı denetim kümelerini birleştirerek ve denetimleri veriye bağlayabilirsiniz kod, yazma, kullanıcıdan bilgi toplamak ve kullanıcı eylemlerine yanıt. Daha fazla bilgi için bkz: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
 Çalışma sayfaları sınıfları projenizde kod yazmaya başlayabilirsiniz bir konum sağlar. Sınıfın tüm özellikleri, yöntemleri ve olayları olarak sağladığından <xref:Microsoft.Office.Interop.Excel.Worksheet> nesne Excel için birincil birlikte çalışma derlemesindeki de bu sınıfların Excel nesne modeline erişmek için kullanabilirsiniz. Daha fazla bilgi için bkz: [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  
  
 Belge düzeyi projelerine ek ekleyebileceğiniz <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğelerini projeye tasarım zamanında Tasarımcısı'nda çalışma kitabına yeni bir çalışma sayfası ekleyerek.  
  
### <a name="rename-worksheets"></a>Çalışma sayfaları yeniden adlandır  
 Belge düzeyi projede çalışma sayfaları Visual Studio Tasarımcısı'nda yeniden adlandırabilirsiniz, ancak bu yalnızca çalışma görünen adını değiştirir. Program adı hala çalışma sayfasının varsayılan addır. Çalışma sayfasına yeniden adlandırırsanız **özellikleri** penceresinde, sadece programlı ad değiştirilir.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Belge düzeyi projelerine çalışma sayfası konak öğesi sınırlamaları  
 Yeni oluşturulamıyor <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğelerini belge düzeyi projesindeki çalışma zamanında. Yeni bir Excel çalışma zamanında oluşturursanız, türü olacaktır <xref:Microsoft.Office.Interop.Excel.Worksheet>. Bir konak öğesi olmadığı için herhangi bir ana bilgisayar denetimleri veya Windows Forms denetimleri içeremez. Çalışma zamanında belgeler oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: program aracılığıyla yeni çalışma sayfaları çalışma kitaplarına ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Çalışma sayfası konak öğeleri VSTO eklentisi projelerine anlama  
 Uygulama düzeyi projelerinde oluşturabileceğiniz bir <xref:Microsoft.Office.Tools.Excel.Worksheet> Excel'de açık olan herhangi bir çalışma sayfasında çalışma zamanında konak öğesi. Kullanabileceğiniz <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi ilgili çalışma sayfasına denetimler ekleme ya da üzerindeki kullanılabilir değil olayları işlemek için <xref:Microsoft.Office.Interop.Excel.Worksheet> nesneleri.  
  
 Oluşturulacak bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi, kullanım `GetVstoObject` yöntemi. Daha fazla bilgi için bkz: [genişletmek Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  