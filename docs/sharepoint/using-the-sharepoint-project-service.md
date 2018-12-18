---
title: SharePoint Proje hizmetini kullanma | Microsoft Docs
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
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5d4c2950754ebbef2920720cf784084b2968a82
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295065"
---
# <a name="use-the-sharepoint-project-service"></a>SharePoint Proje hizmetini kullanın
  SharePoint Proje sistemi proje sistemi için ilgili görevleri gerçekleştirmek için kullanabileceğiniz bir proje hizmeti içerir. Proje hizmeti bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> nesne.  
  
 Tüm SharePoint Araçlar uzantısından SharePoint Proje hizmeti erişebilirsiniz. Visual Studio uzantıları, eklentileri ve VSPackages gibi diğer tür içinde de erişebilirsiniz. Daha fazla bilgi için [nasıl yapılır: SharePoint Proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Proje hizmeti özellikleri
 Aşağıdaki tabloda SharePoint Proje hizmetini kullanarak gerçekleştirebileceğiniz görevleri listeler ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> yöntemi veya özelliği her bir görevi gerçekleştirmek için kullanın.  
  
|Görev|Üye kullanmak için|  
|----------|-------------------|  
|Visual Studio'da açık olduğundan herhangi bir SharePoint projesine erişim.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> özellik.|  
|Tüm SharePoint proje öğesi türleri (yerleşik ve özel proje öğesi türleri dahil) kullanılabilir erişebilirsiniz.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> özellik.|  
|(Yerleşik ve özel dağıtım adımları dahil), SharePoint projeleri için kullanılabilir olan tüm dağıtım adımları erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> özellik.|  
|Bir geliştirici, bir SharePoint proje kodu yeniden düzenler oluşan erişimi olayları.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> özellik.|  
|Özel bir yürütme *SharePoint komutu* SharePoint sunucu nesne modeline çağırır. SharePoint komutları hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> özellik.|  
|Visual Studio Otomasyon nesne modeli veya tümleştirme nesne modeli içerisindeki bir türe SharePoint Proje sistemindeki bir türü dönüştürmek ve bunun tersi de geçerlidir. Daha fazla bilgi için [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> yöntem.|  
|İleti yazıldığını **çıkış** penceresi veya **hata listesi** Visual Studio'daki.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> özellik.|  
|Visual Studio'da sunulan diğer hizmetlerine erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> özellik.|  
|Hata ayıklama çözümü için kullanılan yerel SharePoint sitesi yükleme klasörü yolunu alın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> özellik.|  
|Belirlemek olmadığını [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] veya [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] bilgisayara yüklendi.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> özellik.|  
|Bir özellik ya da bir SharePoint çözüm içindeki paket doğrulayın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> özellik.|  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Nasıl yapılır: SharePoint Proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [SharePoint araçlarını Visual Studio'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Araç uzantılarının programlama modeline SharePoint genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Nasıl yapılır: DTE nesnesinden hizmet alın](https://msdn.microsoft.com/library/bb166401.aspx)  
  
