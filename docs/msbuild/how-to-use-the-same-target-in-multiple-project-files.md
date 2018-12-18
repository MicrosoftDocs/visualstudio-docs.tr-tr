---
title: 'Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fe68d4d6d970ee0c1e5db566caf7c812436589c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077526"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma
Birkaç yazdıysanız [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyaları, olduğunu keşfetti., aynı görevleri ve hedefleri, farklı proje dosyalarında kullanmanız gerekebilir. Bu görevler veya hedefleri eksiksiz bir açıklaması her proje dosyasında dahil olmak üzere yerine ayrı proje dosyasında hedef kaydedebilir ve sonra proje hedef kullanması gereken diğer proje alın.  
  
## <a name="use-the-import-element"></a>İçeri aktarma öğesi kullanma  
 `Import` Öğesi, bir proje dosyası başka bir proje dosyasına eklemek için kullanılır. İçeri aktarılan proje dosyası geçerli bir olmalıdır [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası ve doğru biçimlendirilmiş XML içeriyor. `Project` Özniteliği, içeri aktarılan proje dosyasının yolunu belirtir. Daha fazla bilgi için `Import` öğesi bkz [içeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Bir projeye içeri aktarmak için  
  
1.  İçeri aktarma proje dosyası, tüm özellikleri ve özellikler için parametre olarak kullanılan öğeleri ve içeri aktarılan projedeki öğeleri tanımlar.  
  
2.  Kullanım `Import` projeyi içeri aktarmak için öğesi. Örneğin:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Aşağıdaki `Import` öğe, içeri aktarılan projedeki tüm özelliklerini ve özelliklerinin varsayılan tanımları geçersiz kılmanız gerekir öğeleri ve öğeleri tanımlar.  
  
## <a name="order-of-evaluation"></a>Değerlendirme sırası  
 Zaman [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ulaştığında bir `Import` öğe, içeri aktarılan proje konumda alma projesine eklenen etkili bir şekilde `Import` öğesi. Bu nedenle, konumunu `Import` öğesi özellikleri ve öğeleri değerlerini etkileyebilir. İçeri aktarılan proje ve özellikleri ve öğeleri tarafından içeri aktarılan proje kullandığı ayarlanmış olan öğeleri ve özellikleri anlamak önemlidir.  
  
 Projeyi oluşturduğunda, öğeleri tarafından izlenen tüm özellikler ilk olarak değerlendirilir. Örneğin, aşağıdaki XML içeri aktarılan proje dosyası tanımlar *MyCommon.targets*:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Aşağıdaki XML tanımlar *MyApp.proj*, hangi içeri aktarmalar *MyCommon.targets*:  
  
```xml  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Projeyi oluşturduğunda, aşağıdaki ileti görüntülenir:  
  
 `Name="MyCommon"`  
  
 Proje özelliği sonra içeri aktarılmış olduğundan `Name` içinde tanımlanan *MyApp.proj*, tanımını `Name` içinde *MyCommon.targets* tanımındageçersizkılmalar*MyApp.proj*. Proje adı tanımlanan özellik önce aldıysanız, derleme şu iletiyi görüntüler:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri içeri aktarılırken aşağıdaki yaklaşımı kullanın.  
  
1.  , Proje dosyası, tüm özellikleri ve özellikler için parametre olarak kullanılan öğeleri ve içeri aktarılan projedeki öğeleri tanımlar.  
  
2.  Projeyi içeri aktarın.  
  
3.  Proje dosyasında tüm özellikleri ve özelliklerinin varsayılan tanımları geçersiz kılmanız gerekir öğeleri ve içeri aktarılan projedeki öğeleri tanımlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği kod *MyCommon.targets* ikinci kod örneğinde aktarır dosya. *.Targets* dosya özelliklerini alma projeden yapı yapılandırmak için değerlendirir.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği içeri aktarmalar *MyCommon.targets* dosya.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Hedefler](../msbuild/msbuild-targets.md)