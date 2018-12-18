---
title: "&lt;Belge&gt; öğesi (Visual Studio'da Office Geliştirme)"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447341"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Belge&gt; öğesi (Visual Studio'da Office Geliştirme)
  `document` Öğesinin `vstov4` ad alanı için belge düzeyi özelleştirmeleri özelleştirme özgü bilgileri depolar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Öğeleri ve öznitelikleri  
 Yalnızca belge düzeyi özelleştirmeleri için gereklidir. `document` Öğesidir içinde `vstov4` ad alanı. `document` Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`solutionId`|Gerekli. Belge düzeyi çözümü benzersiz şekilde tanımlamak için Office çalışma zamanı için Visual Studio Araçları tarafından kullanılan GUID. Bu değer _AssemblyLocation özel belge özelliği olarak depolanır. Daha fazla bilgi için bkz: [özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md).|  
  
 `document` hiç alt öğe yok.  
  
## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği gösterilmektedir `document` kullanılarak dağıtılan bir belge düzeyi Office çözümü öğesinde [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Bu kod örneği sağlanan daha büyük bir örneğin parçasıdır [uygulama bildirimleri Office çözümleri için](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)   
 [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest)  
  
  