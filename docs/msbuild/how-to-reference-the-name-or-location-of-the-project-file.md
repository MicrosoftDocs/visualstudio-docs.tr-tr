---
title: 'Nasıl yapılır: Proje dosyasının konumunu ve adını başvurusu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dceca1e518783f405490d3f2527156bd20bf81aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911531"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Nasıl yapılır: Proje dosyasının konumunu ve adını başvurusu
Kendi özellik oluşturmak zorunda kalmadan proje dosyasının kendisini adına veya konumuna projenin kullanabilirsiniz. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Proje dosya adına başvuran ayrılmış özellikleri ve proje ile ilgili diğer özellikleri sağlar. Ayrılmış özellikler hakkında daha fazla bilgi için bkz. [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="use-the-project-properties"></a>Proje özelliklerini kullanma
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Proje dosyalarınızı her zaman tanımlamadan kullanabileceğiniz bazı ayrılmış özellikleri sağlar. Örneğin, ayrılmış özelliği `MSBuildProjectName` proje dosya adına bir başvuru sağlar. Ayrılmış bir özellik `MSBuildProjectDirectory` proje dosya konumuna yönelik bir başvuru sağlar.
  
#### <a name="to-use-the-project-properties"></a>Proje özelliklerini kullanma
  
- Herhangi bir özellik ile olduğu gibi $ () gösterimi ile proje dosyasındaki bir özelliği başvuru. Örneğin:  
  
  ```xml  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```          
  
  Ayrılmış bir özellik kullanmanın bir avantajı, herhangi bir değişiklik proje dosya adına otomatik olarak eklenen ' dir. Projeyi sonraki açışınızda çıkış dosyası, yapmanız gereken başka bir işlem ile yeni bir ada sahip olacaktır.  
  
> [!NOTE]
>  Ayrılmış özellikler, proje dosyasında tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek proje dosyası, proje adı çıkış için bir ad belirtmek için ayrılmış bir özellik olarak başvurur.  
  
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

## <a name="example"></a>Örnek
 Aşağıdaki örnek proje dosyası kullanan `MSBuildProjectDirectory` ayrılmış bir dosyanın tam yolunu proje dosyası oluşturmak için özellik.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">     
    
    <!-- Build the path to a file in the root of the project -->  
    <PropertyGroup>  
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
[MSBuild](../msbuild/msbuild.md)  
[MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
