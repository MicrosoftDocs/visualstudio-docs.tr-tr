---
title: SafeControls öğesi | Microsoft Docs
description: Bir SharePoint sitesinin ASPX sayfasında erişim için güvenli olarak işaretlenmiş bir ASPX denetimleri veya Web bölümleri koleksiyonu tutan SafeControls öğesi hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 23e31e3df59d6d580ac94ffcb83f7a17e186a267
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889453"
---
# <a name="safecontrols-element"></a>SafeControls öğesi
  Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimleri ve Web Bölümleri koleksiyonu.

## <a name="syntax"></a>Syntax

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|İsteğe bağlı öğe.<br /><br /> Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimi veya Web bölümü temsil eder.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir SharePoint proje öğesini temsil eder. Bu öğe *. spdata* dosyasının gerekli kök öğesi.|

## <a name="remarks"></a>Açıklamalar
 Güvenli denetimler hakkında daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
