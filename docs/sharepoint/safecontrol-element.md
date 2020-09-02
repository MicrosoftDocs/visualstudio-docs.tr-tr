---
title: SafeControl öğesi | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c9936054c5cc622e6f335d81d1568ebed16518f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547933"
---
# <a name="safecontrol-element"></a>SafeControl öğesi
  Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimi veya Web bölümü temsil eder.

## <a name="syntax"></a>Syntax

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Bütünleştirilmiş Kod**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> ASPX denetiminin veya Web bölümünün tanımlandığı derlemenin adı. Varsayılan olarak, bu öznitelik derleme adı için **$SharePoint. Project. AssemblyFullName $** değiştirilebilen parametresini kullanır. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).|
|**IsSafe**|İsteğe bağlı **xs: Boolean** özniteliği.<br /><br /> ASPX denetiminin veya Web bölümünün güvenilmeyen kullanıcıların erişmesi için güvenli olup olmadığını belirtir.|
|**Issafeagaınstscript**|İsteğe bağlı **xs: Boolean** özniteliği.<br /><br /> Güvenilmeyen kullanıcıların ASPX denetiminin veya Web bölümünün özelliklerini görüntüleyip görüntüleyemeyeceğini veya düzenleyip düzenleyemeyeceğini belirtir.|
|**Ad**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Koleksiyondaki bu güvenli denetim girişinin adı.|
|**Ad Alanı**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> ASPX denetiminin veya Web bölümünün ad alanı.|
|**'Ta**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> ASPX denetiminin veya Web bölümünün tür adı.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimleri ve Web Bölümleri koleksiyonunu temsil eder.|

## <a name="remarks"></a>Açıklamalar
 Güvenli denetimler hakkında daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
