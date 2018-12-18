---
title: SharePoint programlama modeline genel bakış araçları uzantıları | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82309d00d45ab6ac801297a55371cf9be5620440
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829488"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Araç uzantılarının programlama modeline SharePoint genel bakış
  Visual Studio'da SharePoint araçları için bir uzantı oluşturduğunuzda, SharePoint araçları tarafından kullanıma sunulan bir veya daha fazla genişletilebilirlik arabirimlerini uygulayarak başlayın. Çoğu durumda, uzantı özellikleri uygulamak için SharePoint araçları tarafından sağlanan diğer türleri de kullanır. Bazı senaryolarda Visual Studio ve SharePoint tarafından sağlanan diğer nesne modellerini türleri de kullanabilirsiniz. Bu nesne modellerinin her biri amacı anlamak ve bunları birbiriyle SharePoint araçları için uzantıları oluşturmak için nasıl kullanılacağını bilmek gerekir.  

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini uygulayarak SharePoint araçlarını genişletmek
 Visual Studio SharePoint araçları için genişletilebilirlik modeli sağlamak için .NET Framework 4'te Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanır. MEF (System.ComponentModel.Composition derlemeye uygulanan) bir API olduğunu genişletilebilirlik noktaları ortaya çıkarmak için keşfetmek ve çalışma zamanında uzantıları yüklemek uygulamalar sağlar. MEF hakkında daha fazla bilgi için bkz: [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).  

 SharePoint araçlarını genişletmek için Visual Studio tarafından sunulan bir veya daha fazla genişletilebilirlik arabirimlerini uygular. Ayrıca uygulamalısınız <xref:System.ComponentModel.Composition.ExportAttribute>, ve ek SharePoint araçları özel öznitelikler, arabirim uygulamasına olarak gerekli. Aşağıdaki tablo, SharePoint araçlarını genişletmek için uygulayabileceğiniz arabirimler listeler.  

|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Yeni bir SharePoint proje öğesi türünü tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlayacağınızı](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Visual Studio'da yüklü SharePoint proje öğesi türünü genişletmek için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: bir SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|SharePoint projeleri genişletmek için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: bir SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Bir SharePoint proje öğesi dağıtılan veya geri çekilebilir yükleyen yürütülebilecek yeni bir dağıtım adımı tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [izlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturmak](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Varolan bir düğümü altında genişletmek için bu arabirimi uygulayan **SharePoint bağlantıları** düğümünde **Sunucu Gezgini** penceresi. Bir örnek için bkz. [nasıl yapılır: Sunucu Gezgininde SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Düğümü altında yeni bir tür tanımlamak için bu arabirimi uygulayan **SharePoint bağlantıları** düğümünde **Sunucu Gezgini** penceresi. Bir örnek için bkz. [nasıl yapılır: Sunucu Gezgininde SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Bir özel özellik doğrulama kuralı tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: özel özellik ve paket doğrulama kuralları için SharePoint çözümleri oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Özel paket doğrulama kuralı tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: özel özellik ve paket doğrulama kuralları için SharePoint çözümleri oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  

 Bir SharePoint araçlarının uzantısına uyguladıktan sonra bulmak ve uzantıyı yüklemek Visual Studio etkinleştirmek için Visual Studio Uzantısı (VSIX) paketini uzantı derlemesini dağıtmanız gerekir. Daha fazla bilgi için [Visual Studio'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>SharePoint araçları uzantılarında kullandığınız nesne modellerini anlama
 SharePoint araçları için uzantıları oluştururken kullanabileceğiniz birçok nesne modeli vardır:  

-   *SharePoint araçları nesne modeli*. Bu nesne modeli, SharePoint araç uzantıları ve diğer ilgili türleri oluşturmak için uygulamadan genişletilebilirlik arabirimleri sağlar.  

-   *Visual Studio Otomasyonu ve tümleştirme nesne modellerini*. SharePoint araçları nesne modeli kapsamı dışındaki bir Visual Studio özelliklerine erişmek için bu nesne modellerini kullanın.  

    > [!NOTE]  
    >  Bazı nesneler Visual Studio Otomasyon nesneleri için SharePoint araçları nesne modeli ve tümleştirme nesne modelleri ve tersi, SharePoint Proje hizmetini kullanarak dönüştürebilirsiniz. Daha fazla bilgi için [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  

-   *SharePoint sunucu ve istemci nesne modellerini*. Bu nesne modeli, bir SharePoint sitesi değiştirmek veya SharePoint Araçlar uzantısından bağlamında bir SharePoint sitesinden veri almak için kullanın.  

### <a name="sharepoint-tools-object-model"></a>SharePoint araçları nesne modeli
 Her SharePoint Araçlar uzantısından uzantının işlevselliği ve çekirdek davranışını tanımlamak için SharePoint araçları nesne modelinde türleri kullanır. Aşağıdaki tablolarda, bu nesne modelinde bunları içeren derleme tarafından dahil edilen ad alanlarını açıklar.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll    

|Ad Alanı|Açıklama|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint>|SharePoint Proje sistemi otomatikleştirmek ve genişletmek için kullandığınız türleri içerir. Örneğin, yerleşik SharePoint projelerini ve proje öğelerini genişletebilir veya kendi Proje öğelerinizi oluşturabilirsiniz. Daha fazla bilgi için [SharePoint Proje sistemini genişletmek](../sharepoint/extending-the-sharepoint-project-system.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Kendi dağıtım adımları ve dağıtım yapılandırmaları oluşturma gibi SharePoint projeleri için dağıtım işlemi genişletmek için kullandığınız türleri içerir. Daha fazla bilgi için [genişletmek SharePoint paketleme ve dağıtım](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Altındaki düğümleri genişletmek için kullandığınız türleri içerir **SharePoint bağlantıları** düğümünde **Sunucu Gezgini** penceresinde veya yeni bir düğüm türlerini tanımlamak için. Daha fazla bilgi için [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Features>|SharePoint projesindeki özellik tanımları erişmek için kullandığınız türleri içerir.|  
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Bir SharePoint çözüm içindeki paket tanımına erişmek için kullandığınız türleri içerir.|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|SharePoint projeleri için özellik ve paket doğrulama davranışını özelleştirmek için kullandığınız türleri içerir. Daha fazla bilgi için [nasıl yapılır: özel özellik ve paket doğrulama kuralları için SharePoint çözümleri oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).| 

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Ad Alanı|Açıklama|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Özel oluşturmak için kullandığınız türleri içerir *SharePoint komutları*. Bir SharePoint komutu bir SharePoint Araçlar uzantısından SharePoint sunucusu nesne modeline çağıran bir yöntemdir. Daha fazla bilgi için [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Ad Alanı|Açıklama|  
|-|-| 
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Yerleşik hakkında bilgi almak için kullandığınız türleri içerir **Sunucu Gezgini** bir liste, alan veya içerik türünü temsil eden bir düğüm gibi bir SharePoint sitesindeki tek tek bileşenleri temsil eden düğümler. Daha fazla bilgi için [Sunucu Gezgininde SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  

### <a name="visual-studio-automation-object-model"></a>Visual Studio Otomasyon nesne modeli
 Visual Studio projelerine otomatikleştirmek için kullanabileceğiniz API'ler ve IDE, Visual Studio Otomasyon nesne modeli sağlar. Visual Studio nesne modeline SharePoint projelerine özgü olmayan bir projeyle ilgili görevleri gerçekleştirmek için ya da Visual Studio'daki diğer genel otomasyon görevleri gerçekleştirmek için kullanın. Geleneksel olarak, bu nesne modeli, genellikle Visual Studio eklentileri ve makroları kullanılır, ancak bunu Ayrıca SharePoint araçları uzantıları kullanabilirsiniz.  

 Visual Studio Otomasyon nesne modeli ana bölümü tanımlanan *EnvDTE.dll* derleme. *EnvDTE\\<version>.dll* derlemeler, Visual Studio'nun belirli sürümlerinde sunulan ek işlevler sağlar. Bu derlemeler, Visual Studio ile eklenmiştir.  

 Otomasyon nesne modeli hakkında daha fazla bilgi için bkz: [Visual Studio SDK başvurusu](../extensibility/visual-studio-sdk-reference.md).  

### <a name="visual-studio-integration-object-model"></a>Visual Studio tümleştirmesi nesne modeli
 Tümleştirme nesne modeli oluşturarak için Visual Studio özellikleri eklemek için kullanabileceğiniz API'ler sağlar bir *VSPackage*. VSPackage araç pencereleri, düzenleyiciler, tasarımcılar, hizmetleri ve projeler gibi özel özellikler sağlayarak Visual Studio IDE genişleten bir modüldür.  

 Yerleşik SharePoint araçları ile kullanılacak yeni bir Visual Studio özelliği eklemek istiyorsanız, tümleştirme nesne modelini kullanabilirsiniz. Örneğin, bir SharePoint sitesi için özel bir eylemi temsil eden özel bir SharePoint proje öğesi oluşturursanız, özel bir eylem için bir tasarımcı uygulayan bir VSPackage'ı da oluşturabilirsiniz. Özel eylem proje öğesi özel eylemi temsil eden bir kısayol menü öğesi ekleyerek Tasarımcı ilişkilendirebilirsiniz **Çözüm Gezgini**. Kısayol menüsünü açarak tasarımcınıza açabilirsiniz (ya da özel bir eylem proje öğesi sağ tıklayarak seçip ardından **Shift**+**F10** anahtarlar) ve ardından **Açık**.  

 Bu nesne modeli, Visual Studio SDK ile birlikte bir derleme kümesi içinde tanımlanır. Bu nesne modelindeki ana derlemeleri bazıları *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*, ve  *Microsoft.VisualStudio.OLE.Interop.dll*.  

 Tümleştirme nesne modeli hakkında daha fazla bilgi için bkz. [Otomasyon modeline genel bakış](/visualstudio/extensibility/internals/automation-model-overview) ve [Visual Studio SDK başvurusu](/visualstudio/extensibility/visual-studio-sdk-reference).  

### <a name="sharepoint-object-models"></a>SharePoint nesne modellerini
 SharePoint araç uzantıları SharePoint API'ları, bir SharePoint sitesi değiştirmek veya bir SharePoint sitesinden verileri almak için kullanabilirsiniz. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] iki farklı nesne modeli sağlar: sunucu nesne modeli ve bir istemci nesne modeli.  

 SharePoint Araçlar uzantısından ya da nesne modelinde, API'leri kullanabilirsiniz, ancak her nesne modeli SharePoint araç uzantıları bağlamında bazı avantajları ve dezavantajları vardır. Daha fazla bilgi için [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).  

|Nesne modeli|Açıklama|  
|------------------|-----------------|  
|Sunucu nesne modeli|Sunucu nesne modeli tüm özelliklere erişim sağlayan [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programlı olarak kullanıma sunar. Bu nesne modeli, SharePoint sunucu üzerinde çalışan SharePoint çözümleri tarafından kullanılmak üzere tasarlanmıştır. Bu nesne modeli çoğunu tanımlanan *Microsoft.SharePoint.dll* derleme. Sunucu nesne modeli hakkında daha fazla bilgi için bkz: [SharePoint Foundation Sunucu tarafı nesne modeli kullanarak](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|İstemci nesne modeli|İstemci nesne modelini SharePoint verilerini uzak bir istemci veya sunucu ile çalışmak için kullanılan sunucu nesne modeli bir alt kümesidir. Ortak görevleri gerçekleştirmek için yürütülmelidir gidiş dönüş sayısını en aza indirmek için tasarlanmıştır. İstemci nesne modelini çoğunu tanımlanan *Microsoft.SharePoint.Client.dll* ve *Microsoft.SharePoint.Client.Runtime.dll* derlemeler. İstemci nesne modeli hakkında daha fazla bilgi için bkz. [yönetilen istemci nesne modelini](http://go.microsoft.com/fwlink/?LinkId=177797).|  

## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint araçlarını Visual Studio'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [SharePoint Proje hizmetini kullanın](../sharepoint/using-the-sharepoint-project-service.md)  

