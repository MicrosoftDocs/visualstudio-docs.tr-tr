---
title: XMLNode denetimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd047814f11b5fddad868bd65b84deba369facd5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258895"
---
# <a name="xmlnode-control"></a>XMLNode denetimi
  **Önemli** Microsoft Word ile ilgili bu konudaki ayarlanan bilgileri avantajı ve kişiler ve kimlerin bulunur Amerika Birleşik Devletleri ve alt bölgeleri dışında veya kullanan kuruluşlar için özel olarak sunulan ya da geliştirme çalışan programlar Ocak Microsoft uygulaması belirli işlevlerin ne zaman kaldırıldı 2010'dan önce Microsoft tarafından lisanslanan Microsoft Word ürünleri için özel XML Microsoft Word içinden ilgili. Bu bilgiler Microsoft Word ile ilgili okumak veya kişiler veya Amerika Birleşik Devletleri ya da kimin kullanarak veya Microsoft tarafından 10 Ocak 2010 sonra lisanslı Microsoft Word ürünleri hakkında çalışan programlar geliştirme kendi bölgeleri kuruluşlar tarafından kullanılan ; Bu ürün bu tarihten önce lisanslı veya satın alınan ve Amerika Birleşik Devletleri dışında kullanmak için lisanslı ürünleri ile aynı davranır değil.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Denetimidir olayları gösterir ve verilere bağlı eşlenen bir XML düğüm nesnesi. <xref:Microsoft.Office.Tools.Word.XMLNode> Denetimi yalnızca bir yinelenmeyen şema öğesi bir Microsoft Office Word belgesine eşlendiğinde oluşturulur. Visual Studio XML düğümünü oluşturduktan sonra Word nesne modeline çapraz geçiş yapmak zorunda kalmadan doğrudan karşı programlama yapabilirsiniz.  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Denetimi Word'de sadece öğe eşlemesi kaldırılarak silinebilir.  
  
## <a name="bind-data-to-the-control"></a>Denetimlere veri bağlama  
 Bir <xref:Microsoft.Office.Tools.Word.XMLNode> basit veri bağlama denetimi destekler. XML düğümü kullanarak bir veri kaynağına bağlanmalıdır <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> özelliği. İlişkili veri kümesindeki veriler güncelleştirdiyseniz <xref:Microsoft.Office.Tools.Word.XMLNode> denetimi değişiklikleri yansıtır.  
  
## <a name="formatting"></a>Biçimlendirme  
 Uygulanabilir biçimlendirme bir <xref:Microsoft.Office.Interop.Word.XMLNode> nesne uygulanabilir bir <xref:Microsoft.Office.Tools.Word.XMLNode> denetim. Bu yazı, alt çizgi stillerini ve karakter stilleri içerir.  
  
## <a name="events"></a>Olaylar  
 Aşağıdaki olaylar kullanılabilir <xref:Microsoft.Office.Tools.Word.XMLNode> denetimi:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="compare-events"></a>Olayları karşılaştırma  
 Kullanıcının belirli bir bağlam içinde bilgilendirilmesine imleç taşındığında bir olay yakalayabilirsiniz <xref:Microsoft.Office.Tools.Word.XMLNode> denetim. Örneğin, olabilir bir <xref:Microsoft.Office.Tools.Word.XMLNode> adlı Denetim `Customer` bir alt öğesi olan <xref:Microsoft.Office.Tools.Word.XMLNode> adlı Denetim `Company`, ve `Company` iki alt sahip <xref:Microsoft.Office.Tools.Word.XMLNode> adlı denetimleri `CompanyName` ve `CompanyRegion` gibi:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Eylemler bölmesindeki denetim göstermek istiyorsanız her imleci taşındığı içine `Company` düğümü, onu önemli değildir imlecin bulunduğu olup olmadığını `CompanyName` veya `CompanyRegion` bağlamında, her ikisi de olduklarından `Company`. Bu durumda, kodunuzu yazabileceğiniz <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> olayı `Company`.  
  
 Çoğu durumda, imleç girdiğinde bir <xref:Microsoft.Office.Tools.Word.XMLNode> denetlemek, her ikisi de <xref:Microsoft.Office.Tools.Word.XMLNode.Select> ve <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> olayları ortaya çıkar. Aşağıdaki tabloda bu olaylar arasındaki farklar gösterilmektedir.  
  
|Olay seçin|ContextEnter olayı|  
|------------------|------------------------|  
|İmleç içine yerleştirildiğinde meydana gelir bir <xref:Microsoft.Office.Tools.Word.XMLNode>.|İmleç içine yerleştirildiğinde meydana gelir bir <xref:Microsoft.Office.Tools.Word.XMLNode> veya düğümün bağlamının dışında bir alandan alt düğümlerinden biri. Diğer bir deyişle, yalnızca bağlam değiştiğinde tetiklenir.|  
  
 Örneğin, dışında imleci taşıdığınızda `Customer` içine `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> olayı için `Customer`, `Company`, ve `CompanyName` tetiklenir. Ardından imleci taşırsanız `CompanyName` için `CompanyRegion`, yalnızca <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> olayı için `CompanyRegion` hala hem bağlamı içinde olduğundan tetiklenir `Company` ve `Customer`.  
  
 Aynı arasındaki farklar <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> olay ve <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> olay.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Word otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes denetimi](../vsto/xmlnodes-control.md)   
 [Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  