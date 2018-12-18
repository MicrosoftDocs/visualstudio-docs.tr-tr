---
title: "&lt;Güncelleştirme&gt; öğesi (Visual Studio'da Office Geliştirme)"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ac15ee59299653c71c2d1036e8318a0fee2b693c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927573"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Güncelleştirme&gt; öğesi (Visual Studio'da Office Geliştirme)
  `update` Öğesi çözüm denetleyecek güncelleştirmeleri aralığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `update` Öğesi gereklidir ve içinde `vstav3` ad alanı.  
  
 `update` Öğesinde şu öznitelikler bulunur.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli. Aşağıdaki değerlerden biri etkin ayarlayın:<br /><br /> -   **doğru** güncelleştirmeleri denetlemek için.<br />-   **false** güncelleştirmeleri denetleme önlemek için.|  
  
 `update` Öğesi şu alt öğelerden sahiptir.  
  
### <a name="expiration"></a>süre sonu  
 `expiration` Öğesi gereklidir ve içinde `vstav3` ad alanı. Bu öğe çözüm denetleyen güncelleştirmeleri aralığını belirtir.  
  
 `expiration` Öğesinde şu öznitelikler bulunur.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maximumAge`| Gerekli. Bu, bir tamsayıya eşit ayarlayın.|  
|`unit`|Gerekli. Ayarlama `unit` aşağıdaki değerlerden biri olarak:<br /><br /> -   **saat**<br />-   **gün**<br />-   **Hafta**|  
  
## <a name="example-of-always-checking-for-updates"></a>Her zaman güncelleştirmeleri denetleme örneği  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneğinde gösterilmiştir bir `update` her zaman Office çözümlerinde güncelleştirmeleri denetlemek için ayarlanmış olan öğe.  
  
### <a name="code"></a>Kod  
  
```xml  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Varsayılan güncelleştirme aralığını ayarlama örneği  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneğinde gösterilmiştir bir `update` Office çözümleri için uygulama bildiriminde öğesi. Bu kod örneği, sağlanan daha büyük bir örneğin parçasıdır [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)   
 [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest)  
  
  