---
title: 'Nasıl yapılır: SharePoint komutu yürütme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce195dd34c7c0b509f9de4cbe2cfd14d9a477f87
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120612"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Nasıl yapılır: SharePoint komutu yürütme
  Sunucu nesne modeli bir SharePoint araçları uzantısı'nda kullanmak istiyorsanız, özel bir oluşturmalısınız *SharePoint komutu* API'yi çağırmak için. Komut tanımlayın ve SharePoint araçları uzantısı ile dağıttıktan sonra uzantınızı SharePoint sunucusu nesne modeline çağırmak için komutu çalıştırabilirsiniz. Komutu yürütmek için ExecuteCommand yöntemlerinden birini kullanın bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> nesnesi.  
  
 SharePoint komutları amacı hakkında daha fazla bilgi için bkz: [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Bir SharePoint komutu yürütülemedi  
  
1.  SharePoint araçları uzantısı'nda alma bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> nesnesi. Size yol bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> nesne oluşturmakta uzantısı türüne bağlıdır:  
  
    -   Bir SharePoint Proje sisteminin uzantısında kullanmak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> özelliği.  
  
         Proje sistem uzantıları hakkında daha fazla bilgi için bkz: [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   Bir uzantısına **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**, kullanın <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> özelliği. Alınacak bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> nesne, kullanın <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> özelliği.  
  
         Hakkında daha fazla bilgi için **Sunucu Gezgini** uzantıları bkz [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Uzantı projesi Şablon Sihirbazı gibi SharePoint Araçları'nın bir parçası değil kodu kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> özelliği.  
  
         Proje hizmetini alma hakkında daha fazla bilgi için bkz: [SharePoint Proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  ExecuteCommand yöntemlerinden birini çağrı <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> nesnesi. ExecuteCommand yönteminin ilk bağımsız değişkeni için çalıştırmak istediğiniz komutun adını geçirin. Özel parametre komutunuzu varsa, bu parametrenin ExecuteCommand yönteminin ikinci bağımsız değişkeni geçirin.  
  
     Her desteklenen komutu imza için farklı bir ExecuteCommand aşırı yoktur. Aşağıdaki tabloda, desteklenen imzalar ve hangi her imza olarak kullanmak için aşırı listeler.  
  
    |Komut imza|Kullanılacak ExecuteCommand aşırı yüklemesi|  
    |-----------------------|------------------------------------|  
    |Komutu yalnızca varsayılan sahip <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametre ve dönüş değeri yok.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Komutu yalnızca varsayılan sahip <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametre ve dönüş değeri.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Komut iki parametreye sahiptir (varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve özel parametresi) ve dönüş değeri yok.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Komut, iki parametre ve dönüş değeri vardır.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> çağırmak için aşırı `Contoso.Commands.UpgradeSolution` açıklanan komut [nasıl yapılır: bir SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute` Bu örnekte gösterilen uygulaması yöntemdir <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> yöntemi <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> özel bir dağıtım adımı arabiriminde. Bu kodu daha büyük bir örneğin bağlamında görmek için bkz: [izlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Çağrı aşağıdaki ayrıntılarını Not <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> yöntemi:  
  
-   İlk parametre aramak istediğiniz komutu tanımlar. Bu dize için geçirdiğiniz değerle <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> komut tanımı üzerinde.  
  
-   İkinci parametre için özel ikinci parametresi, komut geçirmek istediğiniz değerdir. Bu durumda, tam yolunu olan *.wsp* SharePoint sitesine yükseltilmekte olan dosya.  
  
-   Kod örtük iletmez <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> komut parametresi. SharePoint Proje sisteminin uzantı ya da bir uzantısı olarak komutu çağırdığınızda Bu parametre komutu otomatik olarak geçirilen **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**. Çözümler, uygulayan bir proje şablonu Sihirbazı olduğu gibi diğer tür <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimdir, bu parametre **null**.  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnek Microsoft.VisualStudio.SharePoint derlemesine başvuru gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Nasıl yapılır: bir SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [İzlenecek yol: Web bölümlerini görüntülemek için Sunucu Gezgini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
