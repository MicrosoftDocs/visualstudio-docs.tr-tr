---
title: XMLNodes denetimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18b1a9cf6028b02d16b15b17950b9918b7b79d89
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258544"
---
# <a name="xmlnodes-control"></a>XMLNodes denetimi
  **Önemli** Microsoft Word ile ilgili bu konudaki ayarlanan bilgileri avantajı ve kişiler ve kimlerin bulunur Amerika Birleşik Devletleri ve alt bölgeleri dışında veya kullanan kuruluşlar için özel olarak sunulan ya da geliştirme çalışan programlar Ocak Microsoft uygulaması belirli işlevlerin ne zaman kaldırıldı 2010'dan önce Microsoft tarafından lisanslanan Microsoft Word ürünleri için özel XML Microsoft Word içinden ilgili. Bu bilgiler Microsoft Word ile ilgili okumak veya kişiler veya Amerika Birleşik Devletleri ya da kimin kullanarak veya Microsoft tarafından 10 Ocak 2010 sonra lisanslı Microsoft Word ürünleri hakkında çalışan programlar geliştirme kendi bölgeleri kuruluşlar tarafından kullanılan ; Bu ürün bu tarihten önce lisanslı veya satın alınan ve Amerika Birleşik Devletleri dışında kullanmak için lisanslı ürünleri ile aynı davranır değil.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Denetimidir olaylar ortaya çıkaran eşlenmiş XML düğüm nesneleri koleksiyonu. <xref:Microsoft.Office.Tools.Word.XMLNodes> Denetimi yalnızca tekrarlanan bir şema öğesi bir Microsoft Office Word belgesine eşlendiğinde oluşturulur. Yinelenen öğesi alt öğe varsa, alt öğelerin her biri de olarak oluşturulan bir <xref:Microsoft.Office.Tools.Word.XMLNodes> denetim.  
  
 Visual Studio XML düğümü koleksiyonunu oluşturduktan sonra Word nesne modeline çapraz geçiş yapmak zorunda kalmadan doğrudan denetimi karşı programlama yapabilirsiniz. <xref:Microsoft.Office.Tools.Word.XMLNodes> Denetimi belgeden sadece öğe eşlemesi kaldırılarak silinebilir.  
  
> [!NOTE]  
>  Bir alt öğesi erişirseniz <xref:Microsoft.Office.Tools.Word.XMLNodes> aracılığıyla kontrol <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> özelliği, onu döndürür bir <xref:Microsoft.Office.Interop.Word.XMLNode> nesne yerine bir <xref:Microsoft.Office.Tools.Word.XMLNode> denetim. Daha fazla bilgi için bkz: [konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="bind-data-to-the-control"></a>Denetimlere veri bağlama  
 Bir <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimi, veri bağlamayı desteklemez. Bunun nedeni, <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimi karmaşık veri bağlama yeteneğine sahip değil ve basit veri bağlama temsil edemez yinelenen veriler.  
  
## <a name="formatting"></a>Biçimlendirme  
 Belge içinde metin uygulanabilir her biçimlendirme uygulanabilir bir <xref:Microsoft.Office.Tools.Word.XMLNodes> denetim.  
  
## <a name="events"></a>Olaylar  
 İçin kullanılabilir olan olaylar <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimi:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="compare-events"></a>Olayları karşılaştırma  
 Kullanıcının belirli bir bağlam içinde bilgilendirilmesine imleç taşındığında bir olay yakalayabilirsiniz <xref:Microsoft.Office.Tools.Word.XMLNodes> denetim. Örneğin, olabilir bir <xref:Microsoft.Office.Tools.Word.XMLNodes> adlı Denetim `Customer` bir alt öğesi olan <xref:Microsoft.Office.Tools.Word.XMLNodes> adlı Denetim `Company`, ve `Company` iki alt sahip <xref:Microsoft.Office.Tools.Word.XMLNodes> adlı denetimleri `CompanyName` ve `CompanyRegion` gibi:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Eylemler bölmesindeki denetim göstermek istiyorsanız her imleci taşındığı içine `Company` düğümü, onu önemli değildir imlecin bulunduğu olup olmadığını `CompanyName` veya `CompanyRegion` bağlamında, her ikisi de olduklarından `Company`. Bu durumda, kodunuzu yazabileceğiniz <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> olayı `Company`.  
  
 Çoğu durumda, imleç girdiğinde bir <xref:Microsoft.Office.Tools.Word.XMLNodes> denetlemek, her ikisi de <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> ve <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> olayları ortaya çıkar. Aşağıdaki tabloda bu olaylar arasındaki farklar gösterilmektedir.  
  
|Olay seçin|ContextEnter olayı|  
|------------------|------------------------|  
|İmleç düğümlerinin birini yerleştirildiğinde meydana gelir <xref:Microsoft.Office.Tools.Word.XMLNodes> koleksiyonu.|İmleç birini düğümleri veya alt düğümleri yerleştirildiğinde meydana gelir <xref:Microsoft.Office.Tools.Word.XMLNodes> düğümün bağlamının dışında bir alandan koleksiyonu. Diğer bir deyişle, yalnızca bağlam değiştiğinde tetiklenir ve birden çok iç içe geçmiş olarak yükseltilmiş <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrol eder.|  
  
 Örneğin, dışında imleci taşıdığınızda `Customer` içine `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> olaylarını `Customer`, `Company`, ve `CompanyName` ortaya çıkar. Ardından imleci taşırsanız `CompanyName` için `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> yalnızca olay `CompanyRegion` tetiklenir, bağlam her ikisi için de aynı olduğundan `Company` ve `Customer`. Birden çok olabilir `Company` belgenizi düğümler. İmleci taşırsanız `CompanyName` bir düğüm `Company` için `CompanyName` başka bir düğüm `Company`, içerik, bu nedenle yalnızca aynıdır <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> olayı oluşturulur.  
  
 Aynı arasındaki farklar <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> olay ve <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> olay.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Word otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode denetimi](../vsto/xmlnode-control.md)   
 [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  