---
title: 'Nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1d36b049aefe9eb574809cfedf4aa1f2ebddbc4c
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120580"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Nasıl yapılır: özel özellik ve paket doğrulama kuralları SharePoint çözümleri için oluşturma
  Visual Studio tarafından üretilen çözüm paketi doğrulamak için özel doğrulama kuralları oluşturabilirsiniz. Seçerek bir özelliğin tamamı veya paket tam doğrulama gerçekleştirebilirsiniz **doğrulama** bir paket veya özelliği bağlam menüsünden **PackagingExplorer**. Paket ya da özellik geçerli bir durumda olacaktır, belirlemek için projeye yeni SharePonit proje öğeleri veya özellikleri eklediğinizde, kısmi doğrulama gerçekleştirilir.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Özel paket doğrulama kuralı oluşturmak için  
  
1.  Bir sınıf kitaplığı projesi oluşturun.  
  
2.  Aşağıdaki derlemelere başvurular ekleyin:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Aşağıdaki arabirimlerinden biri, uygulayan bir sınıf oluşturun:  
  
    -   Bir paket doğrulama kuralı oluşturmak için uygulaması <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> arabirimi.  
  
    -   Bir özellik doğrulama kuralı oluşturmak için uygulaması <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> arabirimi.  
  
4.  Ekleme <xref:System.ComponentModel.Composition.ExportAttribute> sınıfa. Bu öznitelik bulmak ve doğrulama kuralı yüklemek Visual Studio sağlar. Geçirmek <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> veya <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> öznitelik oluşturucunun türü.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir özel özellik doğrulama kuralının nasıl oluşturulacağı gösterilmektedir.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnekte aşağıdaki derlemelere başvuruları gerektirir:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploy-the-extension"></a>Uzantısı dağıtma  
 Uzantıyı dağıtmak için oluşturma bir [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı (VSIX) paketini derleme ve uzantısıyla dağıtmak istediğiniz diğer dosyalar için. Daha fazla bilgi için bkz: [dağıtmak uzantıları SharePoint için Visual Studio Araçları](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
