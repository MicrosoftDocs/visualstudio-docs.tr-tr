---
title: SharePoint proje öğelerini genişletme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b83d5f92a54d58aae2d4c7860e6648920615d63f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823638"
---
# <a name="extend-sharepoint-project-items"></a>SharePoint proje öğelerini genişletme
  Visual Studio'da yüklü SharePoint proje öğesi türü için işlevsellik eklemek istediğinizde bir proje öğesi uzantısı oluşturma. Örneğin, yerleşik bir uzantı oluşturabilirsiniz **olay alıcısı** veya **liste tanımı** proje öğelerini Visual Studio'da ya da özel proje öğesi türü için bir uzantı oluşturabilirsiniz. Bir uzantı tüm SharePoint proje öğesi türleri için de oluşturabilirsiniz.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>SharePoint proje öğelerini genişletme ile ilgili görevler
 Bir proje öğesi genişletmek için uygulayan bir Visual Studio uzantısı derleme <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> arabirimi. Daha fazla bilgi için [nasıl yapılır: bir SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Bir proje öğesi genişlettiğinizde, proje öğesi için aşağıdaki işlevler de ekleyebilirsiniz:  
  
- Bir kısayol menü öğesi için proje öğesi ekleyin. Proje öğesi için kısayol menüsünü açtığınızda, menü öğesi görünür **Çözüm Gezgini**. Proje öğesi sağ tıklayarak veya bunu seçerek ve ardından kısayol menüsünü açın **Shift**+**F10** anahtarları. Daha fazla bilgi için [nasıl yapılır: bir SharePoint Proje öğe uzantısına bir kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
- Özel bir özellik için proje öğesi ekleyin. Özellik görünür **özellikleri** proje öğesinde seçtiğinizde penceresi **Çözüm Gezgini**. Daha fazla bilgi için [nasıl yapılır: bir SharePoint Proje öğe uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
  Oluşturmanıza, dağıtmanıza ve proje öğesi uzantısını test yapmayı gösteren bir kılavuz için bkz. [izlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Proje öğesi uzantıları ve proje öğesi örnekleri arasındaki ilişkiyi anlamak
 Bir proje öğesi uzantısını oluşturduğunuzda, Visual Studio bir proje öğesi türüyle bir SharePoint projesine eklendiğinde uzantınızı yükler. Örneğin, bir uzantı için oluşturursanız **olay alıcısı** proje öğeleri, Visual Studio yükler uzantınızı bir kullanıcı eklendiğinde bir **olay alıcısı** projesine bir proje. Visual Studio, ilişkili proje öğesi türünün tüm örnekleri için uzantınızı aynı örneğini kullanır. Önceki örnekte kullanıcı ikinci eklerse **olay alıcısı** projeye proje öğesi, uzantınızı'nın aynı örneğine ikinci proje öğesi özelleştirmek için kullanılır.  
  
 Genişletme proje öğesi türü belirli bir örneğine erişmek için bir tanıtıcı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> olayları *Projectıtemtype* uygulamanızda parametresi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> yöntemi. Örneğin, bir proje öğesi genişletme türü bir projeye eklendiğinde belirlemek için tanıtıcı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> olay. Daha fazla bilgi için [nasıl yapılır: bir SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint Proje öğeleri için tanımlayıcılar
 Her SharePoint proje öğesi karşılık gelen bir dize tanımlayıcısı var. Aşağıdaki görevleri gerçekleştirmek istiyorsanız, bir proje öğesi için olan tanımlayıcıyla bilmeniz gerekir:  
  
- Proje öğesi için bir uzantı oluşturun. Bu durumda, oluşturucuya genişletmek istediğiniz proje öğesi için olan tanımlayıcıyla geçmelidir <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Bir uzantı tüm öğe türlerine proje oluşturmak için geçirmek **\\*** dize değeri.  
  
- Proje öğesi, program aracılığıyla bir projeye ekleyin. Bu durumda, proje öğesine tanımlayıcısı geçmelidir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> yöntemi.  
  
  Aşağıdaki tablo, Visual Studio'da SharePoint Proje öğeleri için tanımlayıcılar listeler.  
  
|Proje öğesi adı|Dize tanımlayıcı|  
|-----------------------|-----------------------|  
|İş Verileri katalog modeli|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|İçerik türü|Microsoft.VisualStudio.SharePoint.ContentType|  
|Olay alıcısı|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Boş öğe|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Liste tanımı<br /><br /> İçerik türünden liste tanımı|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Liste örneği|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modül|Microsoft.VisualStudio.SharePoint.Module|  
|Sıralı iş akışı<br /><br /> Durum makinesi iş akışı|Microsoft.VisualStudio.SharePoint.Workflow|  
|Site tanımı|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Görsel Web Bölümü|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web Kısmı|Microsoft.VisualStudio.SharePoint.WebPart|  
|İş akışı ilişkilendirme formu|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Nasıl yapılır: bir SharePoint Proje öğe uzantısına bir kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Nasıl yapılır: bir SharePoint Proje öğe uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)  
  
