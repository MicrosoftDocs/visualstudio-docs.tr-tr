---
title: 'Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b886c4865d715c4fee4e9385288f2e4eb15baa5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223346"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl Yapılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Birkaç yazdıysanız [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyaları, olduğunu keşfetti., aynı görevleri ve hedefleri, farklı proje dosyalarında kullanmanız gerekebilir. Bu görevler veya hedefleri eksiksiz bir açıklaması her proje dosyasında dahil olmak üzere yerine ayrı proje dosyasında hedef kaydedebilir ve sonra proje hedef kullanması gereken diğer proje alın.  
  
## <a name="using-the-import-element"></a>İçeri aktarma öğesi kullanma  
 `Import` Öğesi, bir proje dosyası başka bir proje dosyasına eklemek için kullanılır. İçeri aktarılan proje dosyası geçerli bir olmalıdır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası ve doğru biçimlendirilmiş XML içeriyor. `Project` Özniteliği, içeri aktarılan proje dosyasının yolunu belirtir. Daha fazla bilgi için `Import` öğesi bkz [içeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Bir projeye içeri aktarmak için  
  
1.  İçeri aktarma proje dosyası, tüm özellikleri ve özellikler için parametre olarak kullanılan öğeleri ve içeri aktarılan projedeki öğeleri tanımlar.  
  
2.  Kullanım `Import` projeyi içeri aktarmak için öğesi. Örneğin:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Aşağıdaki `Import` öğe, içeri aktarılan projedeki tüm özelliklerini ve özelliklerinin varsayılan tanımları geçersiz kılmanız gerekir öğeleri ve öğeleri tanımlar.  
  
## <a name="order-of-evaluation"></a>Değerlendirme Sırası  
 Zaman [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ulaştığında bir `Import` öğe, içeri aktarılan proje konumda alma projesine eklenen etkili bir şekilde `Import` öğesi. Bu nedenle, konumunu `Import` öğesi özellikleri ve öğeleri değerlerini etkileyebilir. İçeri aktarılan proje ve özellikleri ve öğeleri tarafından içeri aktarılan proje kullandığı ayarlanmış olan öğeleri ve özellikleri anlamak önemlidir.  
  
 Projeyi oluşturduğunda, öğeleri tarafından izlenen tüm özellikler ilk olarak değerlendirilir. Örneğin, aşağıdaki XML, içeri aktarılan proje dosyası MyCommon.targets tanımlar:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Aşağıdaki XML MyCommon.targets alır, MyApp.proj tanımlar:  
  
```  
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
  
 Proje özelliği sonra içeri aktarılmış olduğundan `Name` tanımını MyApp.proj içinde tanımlanan `Name` MyCommon.targets MyApp.proj tanımında geçersiz kılar. Özellik adı tanımlı önce projeyi içeri aktarılırsa, derleme şu iletiyi görüntüler:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri içeri aktarılırken aşağıdaki yaklaşımı kullanın.  
  
1.  , Proje dosyası, tüm özellikleri ve özellikler için parametre olarak kullanılan öğeleri ve içeri aktarılan projedeki öğeleri tanımlar.  
  
2.  Projeyi içeri aktarın.  
  
3.  Proje dosyasında tüm özellikleri ve özelliklerinin varsayılan tanımları geçersiz kılmanız gerekir öğeleri ve içeri aktarılan projedeki öğeleri tanımlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ikinci kod örneğinde aktarır MyCommon.targets dosyasını gösterir. .Targets dosyasının özelliklerini alma projeden yapı yapılandırmak için değerlendirir.  
  
```  
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
 Aşağıdaki kod örneği MyCommon.targets dosyasını içeri aktarır.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Hedefler](../msbuild/msbuild-targets.md)



