---
title: '&lt;RelatedProducts&gt; öğesi (Önyükleyici) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c541a9775025183a3b3ffbf21ef5b72c3f00cc87
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077817"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; öğesi (Önyükleyici)
`RelatedProducts` Öğe bağlı ya da geçerli ürün dahil diğer ürünleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `RelatedProducts` Öğesi alt öğesi olan `Product` öğesi. Bu öznitelikleri yok.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct` Öğesi geçerli ürün adlandırılmış ürüne bağlı bağlıdır ve önce geçerli bir adlandırılmış ürünün yüklenmesi gerektiğini belirtir. Bir alt öğesidir `RelatedProducts` öğesi. A `RelatedProducts` öğesi bir veya daha fazla olabilir `DependsOnProduct` öğeleri.  
  
 `DependsOnProduct` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Code`|Kod adı tarafından belirtilen bulunan ürünün `ProductCode` özniteliği `Product` öğesi. Daha fazla bilgi için [ \<ürün > öğesi](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts` Sıfır veya daha fazla öğe tanımlar `DependsOnProduct` öğeleri ve öznitelikleri yok. En az bir `DependsOnProduct` bu kümesinde geçerli bir ürün önce yüklenmelidir. A `RelatedProducts` öğesi sıfır veya daha fazla olabilir `EitherProducts` öğeleri.  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct` Öğeyi belirten bir ürünün geçerli yükleme işlemine dahildir ve ayrı bir yükleme gerektirmez. Bir alt öğesidir `RelatedProducts` öğesi. A `RelatedProducts` öğesi bir veya daha fazla olabilir `IncludesProduct` öğeleri.  
  
 `IncludesProduct` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Code`|Kod adı tarafından belirtilen bulunan ürünün `ProductCode` özniteliği `Product` öğesi. Daha fazla bilgi için [ \<ürün > öğesi](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği ile Microsoft Installer yüklendiğini belirtir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]ve bu nedenle ayrı bir yükleme gerekmez.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [\<Ürün > öğesi](../deployment/product-element-bootstrapper.md)