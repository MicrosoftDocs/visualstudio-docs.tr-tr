---
description: Vstov4 ad alanının formRegion öğesi, bir VSTO eklentisi ile ilişkili Microsoft Office Outlook form bölgesini tanımlar.
title: "&lt;formRegion &gt; öğesi (Visual Studio 'Da Office geliştirme)"
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0851ba9e117b464d3a2fbb9ad9903af17ceda0c4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221086"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `formRegion`Ad alanının öğesi, `vstov4` bir VSTO eklentisi ile Ilişkili Microsoft Office Outlook form bölgesini tanımlar.

## <a name="syntax"></a>Syntax

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `formRegion`Ad alanı öğesi, `vstov4` Outlook VSTO eklentisi ile ilişkili bir form bölgesini tanımlar. Yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir.

 `formRegion`Tek BIR VSTO eklentisi için bir öğe içinde tanımlanmış birden fazla öğe olabilir `formRegions` .

 `formRegion`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Form bölgesinin adını tanımlar.|

 `formRegion`Öğesi aşağıdaki alt öğeleri içerir.

### <a name="messageclass"></a>messageClass
 `messageClass`Öğesi, form bölgesiyle Ilişkili Outlook formunu tanımlar.

 `messageClass`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Form bölgesiyle ilişkili formu tanımlar.|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `formRegion` kullanılarak dağıtılan bir Outlook VSTO eklentisi için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu tek form bölgesiyle ilişkili üç ileti sınıfı vardır. Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
