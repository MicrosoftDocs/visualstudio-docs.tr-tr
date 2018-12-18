---
title: ProjectOutputFile öğesi | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 99f8173da22f631a1be74c18d4312f74958259e9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120436"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile öğesi
  SharePoint için dağıtıldığında ile proje öğesi eklemek için ayrı bir proje çıktısını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Tür  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**ProjectId**|Gerekli **xs: String** özniteliği.<br /><br /> GUID bağımlı projenin dahil etmek istediğiniz çıktıyı içerir. Bu karşılık **ProjectGuid** bağımlı proje öğesi.|  
|**ProjectPath**|Gerekli **xs: String** özniteliği.<br /><br /> Proje dosyası adını dahil etmek istediğiniz çıkış sahip bağımlı projeyi de dahil olmak üzere, göreli yol. SharePoint proje öğesi içeren SharePoint Proje kök klasörüne görelidir yoludur.|  
|**Hedef**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bağımlı proje çıktı dağıtım kök klasöre göreli SharePoint sunucusuna dağıtılması bulunduğu yolu. Dağıtım kök klasörü tarafından belirtilen dağıtım türü tarafından belirlenir **türü** özniteliği.<br /><br /> Açıklamaları için daha fazla bilgi için bkz **dağıtım yolu** ve **dağıtım kök** SharePoint özelliklerini proje öğelerinde [geliştirmek SharePoint çözümlerini](../sharepoint/developing-sharepoint-solutions.md).|  
|**Türü**|Gerekli **xs: String** özniteliği.<br /><br /> Bağımlı proje çıktı için kullanılacak dağıtım türü. Olası değerler hakkında daha fazla bilgi için açıklama için bkz **dağıtım türü** SharePoint Proje öğeleri özelliğinin [geliştirmek SharePoint çözümlerini](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Alt öğeleri
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Dosyalar](../sharepoint/files-element.md)|SharePoint için dağıtıldığında ile SharePoint proje öğesi eklenecek dosyaları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım **ProjectOutputFile** bir proje çıktı SharePoint proje öğesi dağıtımda öğesi. Farklı bir proje veya proje öğesi içeren aynı projeye belirtebilirsiniz. Daha fazla bilgi için bkz: [proje öğelerinde paketleme ve dağıtım bilgileri sağlayan](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Öğe bilgileri
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointTools/2010/SharePointProjectItemModel|  
|**Şema adı**|SharePoint proje öğesi şeması|  
|**Dosya doğrulama**|ProjectItemModelSchema.xsd|  
|**Boş olamaz**|Hayır|  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Proje öğelerinde paketleme ve dağıtım bilgileri sağlayın](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
