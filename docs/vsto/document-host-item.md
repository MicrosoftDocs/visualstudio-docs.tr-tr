---
title: Belge konak öğesi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10dabdf0cf2db043a5df1b21f5f780645864ae8c
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448382"
---
# <a name="document-host-item"></a>Belge konak öğesi
  <xref:Microsoft.Office.Tools.Word.Document> Konak öğesi türüdür genişleten bir <xref:Microsoft.Office.Interop.Word.Document> Word için birincil birlikte çalışma derlemesinden türü. <xref:Microsoft.Office.Tools.Word.Document> Konak öğesi tüm özellikleri, yöntemleri ve olayları olarak sağlayan bir <xref:Microsoft.Office.Interop.Word.Document> nesnesi, ancak ayrıca ek olayları gösterir ve ana bilgisayar denetimleri ve Windows Forms denetimleri için kapsayıcı görevi görür.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Belge düzeyi projelerine bir varsayılan yok <xref:Microsoft.Office.Tools.Word.Document> projenizdeki belge temsil eden konak öğesi. VSTO eklenti projelerinde oluşturabileceğiniz <xref:Microsoft.Office.Tools.Word.Document> konak öğelerini çalışma zamanında.  
  
## <a name="understand-the-document-host-item-in-document-level-projects"></a>Belge konak öğesi belge düzeyi projelerine anlama  
 Projenizdeki belgeye erişmek için `ThisDocument` sınıfı. Belge düzeyi projesi oluşturduğunuzda, Visual Studio'nun oluşturduğu `ThisDocument` Word ve özelleştirme kodunuz arasında iletişimi bağlantı olarak hizmet verecek sınıfı. `ThisDocument` Sınıf üyelerine erişim sağlar <xref:Microsoft.Office.Tools.Word.Document> belge açıldığında ya da kapalı olduğunda kodu çalıştırma gibi özelleştirme, temel görevlerini gerçekleştirmek için konak öğesi. Sınıfı, denetimleri belgeye eklemek için de kullanabilirsiniz. Farklı denetim kümelerini birleştirerek ve denetimleri veriye bağlayabilirsiniz kod, yazma, kullanıcıdan bilgi toplamak ve kullanıcı eylemlerine yanıt. Daha fazla bilgi için bkz: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
 `ThisDocument` Sınıfı başlangıç projenizde kod yazma bir konum sağlar. Sınıfın tüm özellikleri, yöntemleri ve olayları olarak sağladığından <xref:Microsoft.Office.Interop.Word.Document> nesne Word için birincil birlikte çalışma derlemesindeki de kullanabilir `ThisDocument` Word nesne modeline erişmek için. Daha fazla bilgi için bkz: [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Belge düzeyi projelerine belge konak öğesi sınırlamaları  
 Belge düzeyi projesi yalnızca bir tane içerebilir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi (diğer bir deyişle, `ThisDocument` sınıfı). Yeni ekleyemezsiniz <xref:Microsoft.Office.Tools.Word.Document> konak öğeleri projenize tasarım zamanında ve yeni oluşturamazsınız <xref:Microsoft.Office.Tools.Word.Document> konak öğelerini bir belge düzeyi özelleştirmesinde çalışma zamanında.  
  
 Çalışma zamanında yeni bir Word belgesi oluşturursanız, türü olacaktır <xref:Microsoft.Office.Interop.Word.Document>. Bir konak öğesi olmadığı için herhangi bir ana bilgisayar denetimleri veya Windows Forms denetimleri içeremez. Çalışma zamanında belgeler oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understand-document-host-items-in-application-level-projects"></a>Uygulama düzeyi projelerinde belge konak öğeleri anlama  
 VSTO eklenti projelerinde oluşturabileceğiniz bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi zamanında herhangi bir belgede Word'de açın. Kullanabileceğiniz <xref:Microsoft.Office.Tools.Word.Document> konak öğesi ilgili belgeye denetimleri eklemek veya üzerindeki kullanılabilir değil olayları işlemek için <xref:Microsoft.Office.Interop.Word.Document> nesneleri.  
  
 Oluşturulacak bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesi, kullanım `GetVstoObject` yöntemi. Daha fazla bilgi için bkz: [genişletmek Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Word otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)   
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  