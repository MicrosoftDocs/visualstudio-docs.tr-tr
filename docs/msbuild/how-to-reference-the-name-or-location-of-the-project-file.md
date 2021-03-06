---
title: Proje dosyasının adına veya konumuna başvurma
description: Kendi özelliklerinizi oluşturmak zorunda kalmadan, proje dosya adına veya konumuna başvurmak için MSBuild ayrılmış özelliklerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6527a4f54abf147d54e73c8f887b57b70ff4243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914181"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Nasıl yapılır: proje dosyasının adına veya konumuna başvurma

Projenin adını veya konumunu, kendi özelliğini oluşturmak zorunda kalmadan proje dosyasında kullanabilirsiniz. MSBuild, proje dosyası adına ve proje ile ilgili diğer özelliklere başvuran ayrılmış özellikler sağlar. Ayrılmış özellikler hakkında daha fazla bilgi için bkz. [MSBuild ayrılmış ve iyi bilinen Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Proje özelliklerini kullanma

 MSBuild, proje dosyalarınızda her seferinde tanımlanmaksızın kullanabileceğiniz bazı ayrılmış özellikleri sağlar. Örneğin, ayrılmış özelliği `MSBuildProjectName` Proje dosyası adına bir başvuru sağlar. Ayrılmış özelliği, `MSBuildProjectDirectory` Proje dosyası konumuna bir başvuru sağlar.

#### <a name="to-use-the-project-properties"></a>Proje özelliklerini kullanmak için

- Herhangi bir özellikle yaptığınız gibi, proje dosyasındaki özelliğine $ () gösterimiyle başvurun. Örneğin:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Ayrılmış bir özellik kullanmanın bir avantajı, proje dosya adında yapılan tüm değişikliklerin otomatik olarak eklenmesine olanak sağlar. Projeyi bir sonraki oluşturduğunuzda, çıkış dosyası, sizin bölüminizdeki başka bir eylemde bulunması gereken yeni bir ada sahip olacaktır.

  Dosya veya Proje başvurularında özel karakterlerin kullanımı hakkında daha fazla bilgi için bkz. [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Ayrılmış Özellikler proje dosyasında yeniden tanımlanamaz.

## <a name="example-1"></a>Örnek 1

 Aşağıdaki örnek proje dosyası, çıkış için adı belirtmek üzere bir ayrılmış özellik olarak proje adına başvurur.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Örnek 2

 Aşağıdaki örnek proje dosyası, `MSBuildProjectDirectory` Proje dosyası konumundaki bir dosyanın tam yolunu oluşturmak için ayrılmış özelliği kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Örnek, statik .NET Framework yöntemini çağırmak için [Özellik işlevi](property-functions.md) sözdizimini kullanır <xref:System.IO.Path.Combine*?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
