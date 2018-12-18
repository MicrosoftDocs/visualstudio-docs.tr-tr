---
title: ProjectItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ca0c295410caffb476d6c1e796864c47520a2f56
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120617"
---
# <a name="projectitem-element"></a>ProjectItem öğesi
  Bir SharePoint proje öğesi temsil eder. Bu öğe gerekli kök öğesi, *.spdata* dosya.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**DefaultFile**|İsteğe bağlı **xs: dize** özniteliği.<br /><br /> SharePoint proje öğesi açtığınızda, Visual Studio düzenleyicisinde açar dosyasının dosya adı dahil olmak üzere, göreli yol **Çözüm Gezgini**. Yolun içeren klasörün göreli *.spdata* dosya.|  
|**FeatureReceiverClass**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Özellik alıcısı sınıfı bu SharePoint proje öğesi için tam adı. Özellik alıcıları hakkında daha fazla bilgi için bkz: [proje öğelerinde paketleme ve dağıtım bilgileri sağlayan](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesi için bir özellik alıcısı tanımlayan derleme tam olarak nitelenmiş adını belirtir. Özellik alıcıları hakkında daha fazla bilgi için bkz: [proje öğelerinde paketleme ve dağıtım bilgileri sağlayan](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Tam nitelikli derleme adları hakkında daha fazla bilgi için bkz: [derleme adları](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesi destekleyen güven düzeyleri belirtir. Bu değer aşağıdaki dizelerden biri olabilir: Korumalı alan, FullTrust veya tüm. Değer Sandboxed ve FullTrust tüm belirtir.<br /><br /> Atadığınız değerine karşılık gelen bir özel SharePoint proje öğesi türü, bu özniteliğin değeri <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> uygulamanızda özelliği <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> yöntemi. Bu öznitelik için farklı bir değer belirtirseniz, böylece belirttiğiniz aynı güven düzeyine belirtir Visual Studio değerin üzerine yazar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> özelliği.|  
|**SupportedDeploymentScopes**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesi destekleyen dağıtım kapsamları belirtir. Bu değer, bir veya daha fazla aşağıdaki dizelerden oluşan bir virgülle ayrılmış dizedir: Grup, Site, Web, WebApplication veya paket. Örneğin: `Web, Site`<br /><br /> Atadığınız değerine karşılık gelen bir özel SharePoint proje öğesi türü, bu özniteliğin değeri <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> uygulamanızda özelliği <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> yöntemi. Bu öznitelik için farklı bir değer belirtirseniz, böylece belirttiğiniz aynı güven düzeyine belirtir Visual Studio değerin üzerine yazar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> özelliği.|  
|**Türü**|Gerekli **xs: String** özniteliği.<br /><br /> SharePoint proje öğesi tanımlayıcısı. Bir özel SharePoint proje öğesi türü, geçişi için dize tanımlayıcısıdır <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Daha fazla bilgi için bkz: [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Visual Studio ile dahil yerleşik SharePoint Proje öğeleri için tanımlayıcıları listesi için bkz: [genişletmek SharePoint Proje öğeleri](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Alt öğeleri
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|İsteğe bağlı öğe.<br /><br /> SharePoint proje öğesi ile ilişkili olan özel veri öğeleri koleksiyonunu temsil eder.<br /><br /> Yalnızca bir tane içerebilir **ExtensionData** öğesi.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|İsteğe bağlı öğe.<br /><br /> SharePoint için dağıtıldığında sahip bir özellik dahil olan özellik değerlerini koleksiyonunu temsil eder.<br /><br /> Yalnızca bir tane içerebilir **FeatureProperties** öğesi.|  
|[Dosyalar](../sharepoint/files-element.md)|İsteğe bağlı **FileCollectionType** öğesi.<br /><br /> SharePoint proje öğesi özellik öğesi dosyaları gibi ve SharePoint olmayan bağımlı projeleri çıktısını dağıtmak için dosyaları belirtir.<br /><br /> Ya da dahil bir **dosyaları** veya **Projectıtemfolder** öğesi, ancak ikisini birden değil.|  
|[Projectıtemfolder](../sharepoint/projectitemfolder-element.md)|İsteğe bağlı **ProjectItemFolderType** öğesi.<br /><br /> Eşlenmiş bir klasörde temsil eder.<br /><br /> Ya da dahil bir **dosyaları** veya **Projectıtemfolder** öğesi, ancak ikisini birden değil.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|İsteğe bağlı öğe.<br /><br /> ASPX denetimleri ve SharePoint sitesindeki herhangi bir ASPX sayfasında erişmek herhangi bir kullanıcı için güvenli olarak tasarlanmış Web Bölümleri koleksiyonunu temsil eder.<br /><br /> Yalnızca bir tane içerebilir **SafeControls** öğesi.|  
  
### <a name="parent-elements"></a>Üst öğeler
 Yok.  
  
## <a name="element-information"></a>Öğe bilgileri
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointTools/2010/SharePointProjectItemModel|  
|**Şema adı**|SharePoint proje öğesi şeması|  
|**Dosya doğrulama**|ProjectItemModelSchema.xsd|  
|**Boş olamaz**|Hayır|  
  
## <a name="see-also"></a>Ayrıca bkz.
[SharePoint proje öğesi şema rseference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
