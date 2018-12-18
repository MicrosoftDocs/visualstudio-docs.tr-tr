---
title: 'Nasıl yapılır: SharePoint Proje hizmetini alma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8f9faa0ca539c3b5381aca4159cc4653543087a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880604"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Nasıl yapılır: SharePoint Proje hizmetini alma
  SharePoint Proje hizmeti çözümleri aşağıdaki türden erişebilirsiniz:  
  
-   SharePoint Proje sistemi proje uzantısı, proje öğesi uzantısını veya proje öğesi tür tanımı gibi bir uzantısıdır. Bu tür uzantılar hakkında daha fazla bilgi için bkz: [SharePoint Proje sistemini genişletmek](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   ' In bir uzantısı **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**. Bu tür uzantılar hakkında daha fazla bilgi için bkz: [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Visual Studio uzantısı olan bir VSPackage gibi başka bir tür.  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>Proje sisteminin uzantılarında hizmetini alma  
 Tüm SharePoint Proje sistemi uzantısında kullanarak proje hizmeti erişebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> özelliği bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesne.  
  
 Proje hizmeti, aşağıdaki yordamları kullanarak da alabilirsiniz.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Bir proje uzantısı hizmetinde almak için  
  
1.  Uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> bulun, arabirim <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> yöntemi.  
  
2.  Kullanım *projectService* hizmete erişmek için parametre.  
  
     Aşağıdaki kod örneği, proje hizmeti için ileti yazmak için kullanılacak gösterilmiştir **çıkış** penceresi ve **hata listesi** Basit Proje uzantısı penceresinde.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Proje uzantıları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Bir proje öğesi uzantısını hizmetinde almak için  
  
1.  Uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> bulun, arabirim <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> yöntemi.  
  
2.  Kullanım <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> özelliği *Projectıtemtype* hizmete almak için parametre.  
  
     Aşağıdaki kod örneği, proje hizmeti için ileti yazmak için kullanılacak gösterilmiştir **çıkış** penceresi ve **hata listesi** basit bir uzantısı penceresinde **listetanımı** proje öğesi.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Proje öğesi uzantılarınızı oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Bir proje öğesi türü tanımındaki hizmet almak için  
  
1.  Uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> bulun, arabirim <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> yöntemi.  
  
2.  Kullanım <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> özelliği *typeDefinition* hizmete almak için parametre.  
  
     Aşağıdaki kod örneği, proje hizmeti için ileti yazmak için kullanılacak gösterilmiştir **çıkış** penceresi ve **hata listesi** basit bir proje öğesi türü tanımı penceresinde.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Proje öğesi türleri tanımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlayacağınızı](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Sunucu Gezgini uzantıları hizmetini alma  
 ' In bir uzantısı olarak **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**, proje hizmeti kullanarak erişebileceğiniz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> özelliği bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> nesne.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Sunucu Gezgini uzantısında hizmet almak için  
  
1.  Alma bir <xref:System.IServiceProvider> nesnesinden <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> özelliği bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> uzantınızı nesnesi.  
  
2.  Kullanım <xref:System.IServiceProvider.GetService%2A> istemek için yöntemi bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> nesne.  
  
     Aşağıdaki kod örneği, proje hizmeti için ileti yazmak için kullanılacak gösterilmiştir **çıkış** penceresi ve **hata listesi** listesidüğümlereuzantıekleyenbirkısayolmenüsündenpencere**Sunucu Gezgini**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Genişletme hakkında daha fazla bilgi için **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**, bkz: [nasıl yapılır: Sunucu Gezgininde SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Diğer Visual Studio Uzantıları'nda hizmetini alma  
 Proje hizmeti erişimi olan herhangi bir Visual Studio uzantısına veya vspackage'ta alabilirsiniz bir <xref:EnvDTE80.DTE2> uygulayan bir proje şablonu Sihirbazı gibi Otomasyon nesne modelindeki <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi.  
  
 VSPackage içinde talep edebilir bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> aşağıdaki yöntemlerden birini kullanarak nesne:  
  
- <xref:System.IServiceProvider.GetService%2A> Türetildiği yönetilen bir VSPackage yöntemi <xref:Microsoft.VisualStudio.Shell.Package> sınıfı. Daha fazla bilgi için [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).  
  
- Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntemi. Daha fazla bilgi için [kullanım GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
  Erişimi olan bir Visual Studio Uzantısında bir <xref:EnvDTE80.DTE2> nesnesi isteyebilir bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> kullanarak nesne <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> yöntemi bir <xref:Microsoft.VisualStudio.Shell.ServiceProvider> nesne. Daha fazla bilgi için [DTE nesneden bir hizmet alma](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint Proje hizmetini kullanın](../sharepoint/using-the-sharepoint-project-service.md)   
 [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md)   
 [Nasıl yapılır: sihirbazları proje şablonlarıyla kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
