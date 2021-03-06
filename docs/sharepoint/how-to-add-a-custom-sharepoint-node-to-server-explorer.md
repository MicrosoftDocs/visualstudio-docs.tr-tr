---
title: 'Nasıl yapılır: Sunucu Gezgini için özel bir SharePoint düğümü ekleme | Microsoft Docs'
titleSuffix: ''
description: Visual Studio 'da Sunucu Gezgini özel bir SharePoint düğümü ekleyin. Varsayılan olarak Sunucu Gezgini görüntülenmeyen ek SharePoint bileşenlerini görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e7c0a13879850bbd31112ddcb3193d027abeb5d1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216364"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Nasıl yapılır: Sunucu Gezgini için özel bir SharePoint düğümü ekleme
  **Sunucu Gezgini**' de **SharePoint bağlantıları** düğümünün altına özel düğümler ekleyebilirsiniz. Bu, varsayılan olarak **Sunucu Gezgini** görüntülenmeyen ek SharePoint bileşenlerini göstermek istediğinizde yararlıdır. Daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Özel bir düğüm eklemek için ilk olarak yeni düğümü tanımlayan bir sınıf oluşturun. Ardından, düğümü mevcut bir düğümün alt öğesi olarak ekleyen bir uzantı oluşturun.

### <a name="to-define-the-new-node"></a>Yeni düğümü tanımlamak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System. ComponentModel. Composition

    - System. Drawing

3. Arabirimini uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> .

4. Sınıfına aşağıdaki öznitelikleri ekleyin:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik, Visual Studio 'Nun uygulamanızı bulmasını ve yüklemesini sağlar <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>Türü öznitelik oluşturucusuna geçirin.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. Düğüm tanımında, bu öznitelik yeni düğümün dize tanımlayıcısını belirtir. *Şirket adı* biçimini kullanmanızı öneririz. Tüm düğümlerin benzersiz bir tanımlayıcıya sahip olduğundan emin olmak için *düğüm adı* .

5. <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>Yöntemi uygulamanızda, yeni düğümün davranışını yapılandırmak Için *typeDefinition* parametresinin üyelerini kullanın. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> arabirimde tanımlanan olaylara erişim sağlayan bir nesnedir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> .

     Aşağıdaki kod örneği, nasıl yeni bir düğüm tanımlanacağını göstermektedir. Bu örnekte, projenizin katıştırılmış kaynak olarak CustomChildNodeIcon adlı bir simge içerdiğini varsaymaktadır.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet6":::

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Yeni düğümü var olan bir düğümün alt öğesi olarak eklemek için

1. Düğüm tanımınız ile aynı projede, arabirimini uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> .

2. <xref:System.ComponentModel.Composition.ExportAttribute>Özniteliğini sınıfına ekleyin. Bu öznitelik, Visual Studio 'Nun uygulamanızı bulmasını ve yüklemesini sağlar <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>Türü öznitelik oluşturucusuna geçirin.

3. <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>Özniteliğini sınıfına ekleyin. Düğüm uzantısında, bu öznitelik genişletmek istediğiniz düğüm türünün dize tanımlayıcısını belirtir.

     Visual Studio tarafından sunulan yerleşik düğüm türlerini belirtmek için aşağıdaki numaralandırma değerlerinden birini öznitelik oluşturucusuna geçirin:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Site bağlantı düğümlerini (site URL 'Lerini görüntüleyen düğümler), site düğümlerini veya **Sunucu Gezgini** tüm diğer üst düğümleri belirtmek için bu değerleri kullanın.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Bir liste, alan veya içerik türünü temsil eden bir düğüm gibi bir SharePoint sitesindeki tek bir bileşeni temsil eden yerleşik düğümlerden birini belirtmek için bu değerleri kullanın.

4. Yöntemi uygulamanızda, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> parametresinin olayını işleyin <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> .

5. <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>Olay işleyicisinde, yeni düğümü, <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> olay bağımsız değişkenleri parametresi tarafından açığa çıkarılan nesnenin alt düğümler koleksiyonuna ekleyin.

     Aşağıdaki kod örneği, yeni düğümü **Sunucu Gezgini** SharePoint site düğümünün bir alt öğesi olarak nasıl ekleneceğini gösterir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet7":::

## <a name="complete-example"></a>Örnek Tamam
 Aşağıdaki kod örneği, basit bir düğüm tanımlamak ve **Sunucu Gezgini**' de SharePoint site düğümünün bir alt öğesi olarak eklemek için tüm kodu sağlar.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet5":::

## <a name="compiling-the-code"></a>Kod derleme
 Bu örnekte, projenizin katıştırılmış kaynak olarak CustomChildNodeIcon adlı bir simge içerdiğini varsaymaktadır. Bu örnek ayrıca aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

- System. Drawing

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 **Sunucu Gezgini** uzantısını dağıtmak için, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için BIR uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Nasıl yapılır: Sunucu Gezgini bir SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
