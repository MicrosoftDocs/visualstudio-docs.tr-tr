---
title: SharePoint Araçları uzantıları ile özel verileri ilişkilendirme | Microsoft Docs
description: SharePoint Araç Uzantıları ile özel verileri ilişkilendirin. Özel veri içerebilen nesnelerin listesini görüntüleyin. Özel veri ekleyin ve alın.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5665fc28bacb76c6887cb7dcb1820ec9dc0d2b3a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215324"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>SharePoint Araç Uzantıları ile özel verileri ilişkilendirme
  SharePoint araçları uzantılarında belirli nesnelere özel veriler ekleyebilirsiniz. Bu, uzantınızın bir bölümünde yer alan ve daha sonra uzantınızın diğer kodundan erişmek istediğiniz veriler olduğunda yararlıdır. Verileri depolamak ve verilere erişmek için özel bir yol uygulamak yerine, verileri uzantınızın bir nesnesiyle ilişkilendirebilir ve ardından verileri aynı nesneden daha sonra alabilirsiniz.

 Nesnelere özel veri eklemek, Visual Studio 'daki belirli bir öğeyle ilgili verileri korumak istediğinizde de yararlıdır. SharePoint Araçları uzantıları Visual Studio 'Ya yalnızca bir kez yüklenir, bu nedenle uzantınızın herhangi bir zamanda çeşitli farklı öğelerle (projeler, proje öğeleri veya **Sunucu Gezgini** düğümleri gibi) çalışması gerekir. Yalnızca belirli bir öğeyle ilgili özel verileriniz varsa, verileri bu öğeyi temsil eden nesneye ekleyebilirsiniz.

 SharePoint araçları uzantılarında nesnelere özel veriler eklediğinizde veriler kalıcı olmaz. Veriler yalnızca nesnenin kullanım ömrü boyunca kullanılabilir. Nesne çöp toplama tarafından geri alındıktan sonra veriler kaybolur.

 SharePoint proje sisteminin uzantılarında, bir uzantı kaldırıldıktan sonra devam eden dize verilerini de kaydedebilirsiniz. Daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Özel veri içerebilen nesneler
 Arabirimi uygulayan SharePoint araçları nesne modelinde herhangi bir nesneye özel veri ekleyebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> . Bu arabirim, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> özel veri nesnelerinin bir koleksiyonu olan yalnızca bir özelliğini tanımlar. Aşağıdaki türler uygular <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Özel veri ekleme ve alma
 Bir SharePoint araçları uzantısı içindeki bir nesneye özel veri eklemek için, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> verileri eklemek istediğiniz nesnenin özelliğini alın ve sonra <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> verileri nesnesine eklemek için yöntemini kullanın.

 Bir SharePoint araçları uzantısı içindeki bir nesneden özel verileri almak için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> nesnesinin özelliğini alın ve aşağıdaki yöntemlerden birini kullanın:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Bu yöntem, veri nesnesi varsa **true** , yoksa **false** döndürür. Bu yöntemi, değer türlerinin veya başvuru türlerinin örneklerini almak için kullanabilirsiniz.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Bu yöntem, çıkış durumunda veri nesnesini veya yoksa **null** değerini döndürür. Bu yöntemi yalnızca başvuru türlerinin örneklerini almak için kullanabilirsiniz.

  Aşağıdaki kod örneği, belirli bir veri nesnesinin zaten bir proje öğesiyle ilişkili olup olmadığını belirler. Veri nesnesi zaten proje öğesiyle ilişkili değilse, kod nesneyi <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proje öğesinin özelliğine ekler. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet13":::
  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint Araçları uzantıları için programlama kavramları ve özellikleri](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: Web bölümlerini göstermek için Sunucu Gezgini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
