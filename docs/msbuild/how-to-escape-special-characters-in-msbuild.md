---
title: 'Nasıl yapılır: MSBuild özel karakterleri kaçış | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 701db598872f6dde5a07740ef7601a6c8de7c5f0
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443408"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl yapılır: özel msbuild'de kaçış karakterleri

Belirli karakterler özel bir anlamı olmayan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyaları. Karakterler örnekleri noktalı virgül (`;`) ve yıldız işaretlerini (`*`). Bu özel karakterlerin tam bir listesi için bkz. [MSBuild özel karakterleri](../msbuild/msbuild-special-characters.md).
  
Bu özel karakterlerin bir proje dosyasında sabit değer olarak kullanmak için bunlar sözdizimi kullanılarak belirtilmelidir `%<xx>`burada `<xx>` karakter ASCII onaltılık değerini temsil eder.
  
## <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

 Bir özel karakter kullanıldığı örnek konusu `Include` öğesi listeleri özniteliği. Örneğin, aşağıdaki madde listesini iki öğe bildirir: *dosyam.cs* ve *MyClass.cs*.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
Noktalı virgül adını içeren bir öğe bildirmek istiyorsanız, kullanmanız gerekir `%<xx>` noktalı virgül kaçış ve önlemek için söz dizimi [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] gelen iki ayrı öğeleri bildirme. Örneğin, aşağıdaki öğe noktalı virgül çıkışları ve bir öğe adlı bildirir `MyFile.cs;MyClass.cs`.
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  

Ayrıca bir [özelliği işlevi](../msbuild/property-functions.md) kaçış dizeleri. Örneğin, bu yukarıdaki örneğe eşdeğerdir.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>MSBuild özel karakter değişmez değer olarak kullanmak için

Gösterimini kullanın `%<xx>` özel karakter yerine burada `<xx>` ASCII karakter onaltılık değerini temsil eder. Örneğin bir yıldız işareti kullanın (`*`) değerini sabit karakter olarak kullanın `%2A`.

 
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Öğeler](../msbuild/msbuild-items.md)   
