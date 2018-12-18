---
title: 'Nasıl yapılır: Sunucu Gezgininde SharePoint düğümünü genişletme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f61afe90ed48064c79dd40c0c0975155c956e3e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861845"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Nasıl yapılır: Sunucu Gezgininde SharePoint düğümünü genişletme
  Altındaki düğümleri genişletebilirsiniz **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**. Yeni alt düğümleri, kısayol menü öğeleri ve özellikleri için var olan bir düğüm eklemek istediğinizde bu kullanışlıdır. Daha fazla bilgi için [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Sunucu Gezgininde SharePoint düğümünü genişletme  
  
1.  Bir sınıf kitaplığı projesi oluşturun.  
  
2.  Aşağıdaki derlemelere başvurular ekleyin:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Uygulayan bir sınıf oluşturma <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> arabirimi.  
  
4.  Ekleme <xref:System.ComponentModel.Composition.ExportAttribute> öznitelik sınıfı. Bu öznitelik bulmak ve yüklemek Visual Studio sağlar, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> uygulaması. Geçirmek <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> özniteliği Oluşturucu türü.  
  
5.  Ekleme <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> öznitelik sınıfı. Bu öznitelik, genişletmek istediğiniz düğüm türü için dize tanımlayıcısını belirtir.  
  
     Visual Studio tarafından sağlanan yerleşik düğüm türlerini belirtmek için aşağıdaki numaralandırma değerlerinden biri öznitelik yapıcısına geçirin:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Site bağlantı düğümleri (site URL'leri görüntüleme düğüm) belirtmek için bu değerleri site düğümleri veya diğer tüm üst düğümleri kullanım **Sunucu Gezgini**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Bir SharePoint sitesindeki bir liste, alan veya içerik türünü temsil eden bir düğüm gibi ayrı ayrı bir bileşen temsil eden yerleşik düğümlerinden belirtmek için bu değerleri kullanırsınız.  
  
6.  Uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> yöntemi, kullanım üyeleri *nodeType* düğüme özellikleri eklemek için parametre. Bu parametre bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> tanımlanan olaylara erişim sağlayan nesne <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> arabirimi. Örneğin, aşağıdaki olayları işleyebilir:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Düğüme yeni alt düğümler eklemek için bu olayı işleyin. Daha fazla bilgi için [nasıl yapılır: Sunucu Gezginine özel bir SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Düğümü için özel bir kısayol menü öğesi eklemek için bu olayı işleyin.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Özel özellikler için düğümü eklemek için bu olayı işleyin. Özellikleri görünür **özellikleri** düğümü seçildiğinde penceresi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde iki farklı türde düğüm uzantısı oluşturma işlemini göstermektedir:  
  
- Bir bağlam menüsü öğesi, SharePoint site düğüm ekler bir uzantı. Menü öğesini tıkladığınızda tıklandığını düğümün adını görüntüler.  
  
- Adlı bir özel özellik ekleyen bir uzantı **ContosoExampleProperty** adlı bir alanını temsil eden her düğüme **gövdesi**.  
  
  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
  Bu uzantı, düğüm düzenlenebilir dize özelliği ekler. SharePoint sunucusu salt okunur verileri görüntüleyen özel özellikler de oluşturabilirsiniz. Bunun nasıl yapılacağını gösteren bir örnek için bkz: [izlenecek yol: Sunucu Gezgini web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnek aşağıdaki derlemelere başvurular gerektirir:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>Uzantıyı dağıtmak  
 Dağıtılacak **Sunucu Gezgini** uzantısı oluşturma bir [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı (VSIX) paketini derleme ve uzantısıyla dağıtmak istediğiniz diğer tüm dosyalar için. Daha fazla bilgi için [Visual Studio'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: Sunucu Gezginine özel bir SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [İzlenecek yol: Sunucu Gezgini, web bölümlerini görüntülemek üzere genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [SharePoint araç uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
