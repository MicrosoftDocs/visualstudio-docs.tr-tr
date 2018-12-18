---
title: SharePoint ile özel verileri ilişkilendirme araçları uzantıları | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3e174440411e54d0f3960035874bd3b84b392c57
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939510"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>SharePoint araç uzantıları ile özel verileri ilişkilendirme
  SharePoint araç uzantıları belirli nesneleri özel veri ekleyebilirsiniz. Daha sonra uzantınızı diğer koddan erişmek istediğiniz uzantınızı bir bölümünde veriniz olduğunda bu kullanışlıdır. Depolamak ve verilere erişmek için özel bir yol uygulamak yerine, verileri aynı nesneden daha sonra almak ve verileri uzantınızı bir nesne ile ilişkilendirin.  
  
 Visual Studio'da belirli bir öğe ile ilgili verileri korumak istediğinizde özel veri nesne eklemeyi de yararlıdır. SharePoint araç uzantıları yalnızca Visual Studio'da, bu nedenle uzantınızı birkaç farklı çalışma öğeleri bir kez yüklenir (gibi projeler, proje öğeleri veya **Sunucu Gezgini** düğümleri) dilediğiniz zaman. Yalnızca belirli bir öğe için ilgili olan özel veriler varsa, bu öğeyi temsil eden nesneye veri ekleyebilirsiniz.  
  
 SharePoint araç uzantıları nesneleri özel veri ekleme, verileri kalmaz. Verileri yalnızca nesne kullanım ömrü kullanılabilir. Nesne tarafından çöp toplama geri kazanılır sonra veriler kaybolur.  
  
 SharePoint Proje sisteminin uzantılarında uzantı kaldırılır sonra devam ederse dize veriler kaydedebilirsiniz. Daha fazla bilgi için [SharePoint Proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Özel veriler içeren nesneleri
 Uygulayan SharePoint araçları nesne modelinde herhangi bir nesneye özel veri ekleme <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> arabirimi. Bu arabirim yalnızca bir özelliğini tanımlar <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, özel veri nesneleri koleksiyonu. Aşağıdaki türleri uygulayan <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>Özel veri ekleme ve alma
 SharePoint araçları uzantısının bir nesneye özel veri ekleme, ulaşmak <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> verileri ekleyin ve ardından kullanmak istediğiniz nesne özelliğini <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> veri nesnesine eklemek için yöntemi.  
  
 SharePoint araçları uzantısının bir nesnenin özel veri almak için alın <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> nesnesi ve ardından bir aşağıdaki yöntemlerden birini özelliği:  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Bu yöntem döndürür **true** veri nesnesi varsa veya **false** henüz yoksa. Değer türleri veya başvuru türleri örneklerini almak için bu yöntemi kullanabilirsiniz.  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Bu yöntem, verileri döndüren çıkılıyorsa, nesne veya **null** henüz yoksa. Yalnızca başvuru türleri örneğini almak için bu yöntemi kullanabilirsiniz.  
  
  Aşağıdaki kod örneği, belirli bir veri nesnesi zaten bir proje öğesi ile ilişkili olup olmadığını belirler. Veri nesnesi zaten proje öğesi ile ilişkili değil sonra kod nesnesine ekler <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proje öğesinin özellik. Daha büyük bir örneğin bağlamında bu örnek için bkz [nasıl yapılır: özel bir SharePoint Proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint araç uzantıları için programlama kavramları ve Özellikler](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [İzlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [İzlenecek yol: Sunucu Gezgini, web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Nasıl yapılır: özel bir SharePoint Proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 
