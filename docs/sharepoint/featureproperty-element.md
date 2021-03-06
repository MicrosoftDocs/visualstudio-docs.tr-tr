---
title: FeatureProperty öğesi | Microsoft Docs
description: SharePoint proje öğesi şemasındaki bir öğe olan FeatureProperty öğesi hakkında başvuru bilgilerini görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070866b9dd14d974eb976b22bf7a79907e2c5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876673"
---
# <a name="featureproperty-element"></a>FeatureProperty öğesi
  SharePoint 'e dağıtıldığında bir özelliğe dahil olan özel bir özelliği temsil eder. Bir özellik dağıtıldıktan sonra, kodunuzda özelliğine erişebilirsiniz.

## <a name="syntax"></a>Syntax

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Key**|Gerekli **xs: String** özniteliği.<br /><br /> Özellik değerini depolamak ve almak için kullanılan anahtar. Her özellik, özelliği içinde benzersiz olan bir anahtara sahip olmalıdır.|
|**Değer**|Gerekli **xs: String** özniteliği.<br /><br /> Özellik değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint 'e dağıtıldığında bir özelliğe dahil olan özellik değerlerinin koleksiyonunu temsil eder.|

## <a name="remarks"></a>Açıklamalar
 Özellik özellikleri hakkında daha fazla bilgi için bkz. [Proje öğelerinde paket ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
