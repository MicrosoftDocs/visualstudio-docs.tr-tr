---
title: 'Nasıl yapılır: bir SharePoint komutu oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89384a1bf095b27f97be46ae303148ab5f8c7d1f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117143"
---
# <a name="how-to-create-a-sharepoint-command"></a>Nasıl yapılır: bir SharePoint komutu oluşturma
  Sunucu nesne modeli bir SharePoint araçları uzantısı'nda kullanmak istiyorsanız, özel bir oluşturmalısınız *SharePoint komutu* API'yi çağırmak için. SharePoint komutu sunucusu nesne modeline doğrudan çağırabilir miyim bir derlemede tanımlayın.  
  
 SharePoint komutları amacı hakkında daha fazla bilgi için bkz: [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Bir SharePoint komutu oluşturmak için  
  
1.  Aşağıdaki yapılandırmaya sahip bir sınıf kitaplığı projesi oluşturun:  
  
    -   .NET Framework 3.5 hedefler. Hedef Framework'ü seçme hakkında daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   AnyCPU veya x64 hedefler platform. Varsayılan olarak, hedef için Sınıf Kitaplığı projelerinde AnyCPU platformudur. Hedef platform seçme hakkında daha fazla bilgi için bkz: [nasıl yapılır: projeleri hedef platformlar yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  .NET Framework 3.5 ve SharePoint araçları uzantıları hedef SharePoint komutları hedeflemek için SharePoint araçları uzantısı tanımlar projede bir SharePoint komutu uygulayamaz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Ayrı bir proje uzantı tarafından kullanılan herhangi bir SharePoint komut tanımlamanız gerekir. Daha fazla bilgi için bkz: [Visual Studio'da SharePoint araçları için Uzantılar dağıtmak](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Aşağıdaki derlemelere başvurular ekleyin:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Projedeki bir sınıfta SharePoint komutunuzu tanımlayan bir yöntem oluşturma. Yöntemi, aşağıdaki yönergelere uygun olmalıdır:  
  
    -   Bir veya iki parametre olabilir.  
  
         İlk parametre olmalıdır bir <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> nesnesi. Bu nesne Microsoft.SharePoint.SPSite ya da komut yürütüldüğü Microsoft.SharePoint.SPWeb sağlar. Ayrıca sağlar bir <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> iletileri yazmak için kullanılan nesne **çıkış** penceresi veya **hata listesi** Visual Studio'daki.  
  
         İkinci parametre türü tercih ettiğiniz olabilir, ancak bu parametre isteğe bağlıdır. Komutu, SharePoint araçları uzantısını verileri geçirmek gerekiyorsa, bu parametre SharePoint komutunuzu ekleyebilirsiniz.  
  
    -   Dönüş değeri olabilir, ancak bu isteğe bağlıdır.  
  
    -   İkinci parametre ve dönüş değeri Windows Communication Foundation (WCF) tarafından seri hale getirilebilir bir türü olmalıdır. Daha fazla bilgi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) ve [XmlSerializer sınıfını kullanma](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Tüm görünürlük yöntemi olabilir (**ortak**, **iç**, veya **özel**), ve statik veya statik olmayan olabilir.  
  
4.  Uygulama <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> yöntemi. Bu öznitelik komutu için benzersiz bir tanımlayıcı belirtir; Yöntem adı ile eşleşmesi Bu tanımlayıcıya sahip değil.  
  
     SharePoint araçları uzantısından komutu çağırdığınızda, aynı benzersiz tanımlayıcısını belirtmeniz gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Örnek  
 Tanımlayıcı sahip bir SharePoint komutu aşağıdaki kod örneğinde gösterilmektedir `Contoso.Commands.UpgradeSolution`. Bu komut, dağıtılan bir çözüme yükseltmek için sunucusu nesne modelinde API'lerini kullanır.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Örtük ilk yanı sıra <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi, bu komut ayrıca SharePoint sitesine yükseltiliyor .wsp dosyasının tam yolunu içeren özel bir dize parametresine sahiptir. Bu kodu daha büyük bir örneğin bağlamında görmek için bkz: [izlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Kod derleme  
 Bu örnekte aşağıdaki derlemelere başvuruları gerektirir:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>Komut dağıtma  
 Komut dağıtmak için komut derleme aynı dahil [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı (*VSIX*) komutunu kullanan uzantı derlemesi paketiyle. Ayrıca, extension.vsixmanifest dosyasındaki komutu derleme için bir giriş eklemeniz gerekir. Daha fazla bilgi için bkz: [Visual Studio'da SharePoint araçları için Uzantılar dağıtmak](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [İzlenecek yol: Web bölümlerini görüntülemek için Sunucu Gezgini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
