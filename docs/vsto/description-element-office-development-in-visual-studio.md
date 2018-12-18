---
title: "&lt;Açıklama&gt; öğesi (Visual Studio'da Office Geliştirme)"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9fcdac1e950d98394b5703322f40dd1823b246f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265121"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Açıklama&gt; öğesi (Visual Studio'da Office Geliştirme)
  `description` Öğesinin `vstov4` ad alanı, Microsoft Office uygulamaları COM eklentileri iletişim kutusunda görünür Office çözümü açıklamasını depolar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Öğeleri ve öznitelikleri  
 İsteğe bağlı. `description` Öğesidir içinde `vstov4` ad alanı. Microsoft Office uygulamaları COM eklentileri iletişim kutusunda görüntülenen eklenti açıklamasını içerir.  
  
 `description` Öğeye sahip hiçbir öznitelik veya öğe.  
  
## <a name="vsto-add-in-example"></a>VSTO eklenti örneği  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği gösterilmektedir `description` öğesi kullanılarak dağıtılan bir uygulama düzeyi çözümü için [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Bu kod örneği sağlanan daha büyük bir örneğin parçasıdır [uygulama bildirimleri Office çözümleri için](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)   
 [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest)  
  
  