---
title: 'Nasıl yapılır: Sunucu Gezginine özel bir SharePoint düğümü ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb0ba7f09ae564a794792ad6f7a60f53f6f6422e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755647"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Nasıl yapılır: Sunucu Gezginine özel bir SharePoint düğümü ekleme
  Özel düğümlerinde ekleyebilirsiniz **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**. Görüntülenmeyen ek SharePoint bileşenlerini görüntülemek istediğinizde bu kullanışlıdır **Sunucu Gezgini** varsayılan olarak. Daha fazla bilgi için bkz: [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Özel bir düğüm eklemek için önce yeni düğümü tanımlayan bir sınıf oluşturun. Ardından var olan bir düğümün bir alt öğesi olarak düğüm ekler uzantı oluşturun.  
  
### <a name="to-define-the-new-node"></a>Yeni düğümü tanımlamak için  
  
1.  Bir sınıf kitaplığı projesi oluşturun.  
  
2.  Aşağıdaki derlemelere başvurular ekleyin:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Arabirimini uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> arabirimi.  
  
4.  Aşağıdaki öznitelikler sınıfına ekleyin:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik bulmak ve yüklemek Visual Studio sağlar, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> uygulaması. Geçirmek <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> öznitelik oluşturucunun türü.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. Bir düğüm tanımında bu öznitelik yeni düğümü dize tanımlayıcısını belirtir. Biçimini kullanmanızı öneririz *şirket adı*. *düğüm adı* tüm düğümleri benzersiz bir tanımlayıcı olup olmadığından emin olun.  
  
5.  Uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> yöntemi, kullanım üyeleri *typeDefinition* yeni düğümü davranışını yapılandırmak için parametre. Bu parametre bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> tanımlanan olayları erişimi sağlayan nesne <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> arabirimi.  
  
     Aşağıdaki kod örneği, yeni bir düğüm tanımlamak gösterilmiştir. Bu örnek, projenizin CustomChildNodeIcon katıştırılmış bir kaynağı olarak adlandırılan bir simge içerdiğini varsayar.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Varolan bir düğümün bir alt öğesi olarak yeni düğüm eklemek için  
  
1.  Düğüm tanımınızı aynı projede uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimi.  
  
2.  Ekleme <xref:System.ComponentModel.Composition.ExportAttribute> öznitelik sınıfı. Bu öznitelik bulmak ve yüklemek Visual Studio sağlar, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> uygulaması. Geçirmek <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> öznitelik oluşturucunun türü.  
  
3.  Ekleme <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> öznitelik sınıfı. Bir düğüm uzantısı'nda, bu öznitelik, genişletmek istediğiniz düğümünün türü dizesi tanımlayıcısını belirtir.  
  
     Visual Studio tarafından sağlanan yerleşik düğüm türlerini belirtmek için aşağıdaki numaralandırma değerlerinden biri özniteliği oluşturucuya geçirin:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Site bağlantı düğümleri (site URL'leri görüntüleme düğümler) belirtmek için bu değerleri site düğümleri veya diğer tüm üst düğümler kullanım **Sunucu Gezgini**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Bir SharePoint sitesinde bir listesi, alan veya içerik türünü temsil eden bir düğüm gibi tek tek bir bileşen temsil eden yerleşik düğümleri birini belirtmek için bu değerleri kullanın.  
  
4.  Uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> yöntemi, tanıtıcı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> olayı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametresi.  
  
5.  İçinde <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> olay işleyicisi, yeni düğümün alt düğümleri koleksiyonuna eklemek <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> olay bağımsız değişkenleri parametresi tarafından sunulan nesne.  
  
     Aşağıdaki kod örneğinde SharePoint sitesini düğümünde alt olarak yeni düğüm eklemek gösterilmiştir **Sunucu Gezgini**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Tam örnek
 Aşağıdaki kod örneğinde add içinde SharePoint sitesi düğümün alt öğesi olarak ve basit bir düğüm tanımlamak için tam bir kod sağlar **Sunucu Gezgini**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Kod derleme  
 Bu örnek, projenizin CustomChildNodeIcon katıştırılmış bir kaynağı olarak adlandırılan bir simge içerdiğini varsayar. Bu örnek ayrıca aşağıdaki derlemelere başvuruları gerektirir:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploy-the-extension"></a>Uzantısı dağıtma  
 Dağıtmak için **Sunucu Gezgini** uzantısı oluşturma bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı (VSIX) paketini derleme ve uzantısıyla dağıtmak istediğiniz diğer dosyalar için. Daha fazla bilgi için bkz: [Visual Studio'da SharePoint araçları için uzantıları dağıtmak](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Nasıl yapılır: Sunucu Gezgininde SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [İzlenecek yol: Web bölümlerini görüntülemek için Sunucu Gezgini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  
