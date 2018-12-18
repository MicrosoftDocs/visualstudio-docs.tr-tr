---
title: SharePoint tarafından desteklenen MSBuild özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1695a23ba9dddc27a37f23c714678fe6b779d328
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676895"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint tarafından desteklenen MsBuild özellikleri
  Tüm [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Microsoft.VisualStudio.SharePoint.targets dosyası, proje dosyası veya proje kullanıcı dosyası içinde tanımlanan bir özellik kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projeleri. Ortak yanı sıra [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] SharePoint Proje tarafından sağlanan özellikleri SharePoint projelerine özgü ek özellikleri tanımlar.  
  
 Ortak bir listesi için [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] özellikleri görmek [yaygın MSBuild proje özellikleri](http://go.microsoft.com/fwlink/?LinkID=168687). Programlama diliniz tarafından desteklenen özelliklerin tam listesi için konum *.targets* dosyası, proje dosyası (*.csproj* veya *.vbproj*), ya da proje kullanıcı dosyası () *csproj.user* veya *. vbproj.user*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint'e özgü MsBuild özellikleri
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] SharePoint projeleri için özel olarak uygulanan Özellikler [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Diğer özellikler var, ancak bunlar dahili kullanım içindir.  
  
|Özellik adı|Açıklama|  
|-------------------|-----------------|  
|SharePointSiteUrl|Temsil eden bir dize [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint sitesi.|  
|SandboxedSolution|Çözüm bir korumalı çözüm olup olmadığını belirten bir Boole değeri.|  
|ActiveDeploymentConfiguration|Etkin dağıtım yapılandırması.|  
|IncludeAssemblyInPackage|Derleme paket dosyasını dahil edilip edilmediğini belirten bir Boole değeri.|  
|PreDeploymentCommand|Dağıtım öncesi komutu adımda çalıştırılacak komutu temsil eden bir dize değeri.|  
|PostDeploymentCommand|Dağıtım sonrası komutu adımda çalıştırılacak komutu temsil eden bir dize değeri.|  
|CustomBeforeSharePointTargets|Yolu temsil eden bir dize bir [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] hedefler dosyası. Hedef dosya varsa ve tanımlanan herhangi bir SharePoint hedefleri veri önce içeri aktarılır. Bu özellik paket işlemi önceden tanımlanması paketlemeyle ilgili özellikleri tarafından sevk edilen SharePoint hedefleri dosyayı değiştirmeden özelleştirmenize olanak sağlar, ancak hedefler dosyasındaki tüm SharePoint projeleri için geçerli olacaktır.|  
|CustomAfterSharePointTargets|Yolu temsil eden bir dize bir [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] hedefler dosyası. Hedef dosya varsa ve tanımlanır, SharePoint hedefleri verilerinin bir tüm olarak içeri aktarılır. Bu özellik paketlemeyle ilgili özelliklerin ve hedeflerin sevk edilen SharePoint hedefleri dosyasını değiştirmek zorunda kalmadan kılarak paket işlemi özelleştirmenizi sağlar, ancak hedefler dosyasındaki tüm SharePoint projeleri için geçerli olacaktır.|  
|LayoutPath|Burada paketlenmesi dosyaların her biri geçici olarak yerleştirilir eklenen önce kök dizinini temsil eden bir dize *.wsp* dosya. Bu yol eklemek, kaldırmak veya içeriğini değiştirmek için kullanabileceğiniz için paketlenecek şekilde dosyaları değiştirmek için BeforeLayout ve AfterLayout hedefleri geçersiz kılma zaman bilmek de yararlı olabilir. *.wsp* dosya.|  
|BasePackagePath|Paket yerleştirildiği klasör temsil eden bir dize. Bu değer Bin\Debug gibi bir projenin çıkış dizinine kullanır.|  
|PackageExtension|Pakete eklenecek dosya adı uzantısını temsil eden bir dize. Wsp varsayılan değerdir.|  
|AssemblyDeploymentTarget|Proje derleme SharePoint sunucusu üzerinde dağıtıldığı konum temsil eden bir dize. Kendi GlobalAssemblyCache (varsayılan) ya da WebApplication değerdir. Bu özelliği de Özellikler penceresinde ayarlayabilirsiniz.|  
|PackageWithValidation|Doğrulama önce paketleme yapılıp yapılmayacağını belirten bir Boole değeri. Bu özellik paketleri oluşturulurken doğrulama hatalarını yoksay olanak sağlar.|  
|ValidatePackageDependsOn|Ek hedefler ValidatePackage hedeften önce yürütülecek tanımlayan bir dize.|  
|TokenReplacementFileExensions|Paketleme sırasında değiştirilen belirteçleriyle dosyaları tanımlayan bir dize.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>MsBuild özellikleri özellikleri sayfasını kullanın.
 Esneklik, sabit kodlanmış dizeleri kullanmak yerine **dağıtım öncesi komut satırını** ve **dağıtım sonrası komut satırı** kutuları SharePoint Özellikler sayfasında SharePoint kullanabilirsiniz. bağımsız değişkenler olarak özellikleri. Örneğin, belirli bir belirtme yerine [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dize SharePoint sitesi için bunların yerine kullanabileceğiniz `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Kullanabilirsiniz [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] değişkeni sözdizimini `$(` *propertyName* `)` veya ortam değişkeni sözdizimini `%` *propertyName* `%` bir özellik belirtmek için.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [MSBuild Başvurusu](/visualstudio/msbuild/msbuild-reference)  
  