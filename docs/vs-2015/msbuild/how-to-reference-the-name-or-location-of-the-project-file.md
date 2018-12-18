---
title: 'Nasıl yapılır: Proje dosyasının konumunu ve adını başvurusu | Microsoft Docs'
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
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8631d10d56a35f8cf4ef6024d087bf94ec89b9d9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845738"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Nasıl Yapılır: Proje Dosyasının Adına veya Konumuna Başvurma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Kendi özellik oluşturmak zorunda kalmadan proje dosyasının kendisini adına veya konumuna projenin kullanabilirsiniz. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosya adına başvuran ayrılmış özellikleri ve proje ile ilgili diğer özellikleri sağlar. Ayrılmış özellikler hakkında daha fazla bilgi için bkz. [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>MSBuildProjectName özelliği kullanma  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyalarınızı her zaman tanımlamadan kullanabileceğiniz bazı ayrılmış özellikleri sağlar. Örneğin, ayrılmış özelliği `MSBuildProjectName` proje dosya adına bir başvuru sağlar.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>MSBuildProjectName özelliği kullanmak için  
  
- Herhangi bir özellik ile olduğu gibi $ () gösterimi ile proje dosyasındaki bir özelliği başvuru. Örneğin:  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  Ayrılmış bir özellik kullanmanın bir avantajı, herhangi bir değişiklik proje dosya adına otomatik olarak eklenen ' dir. Projeyi sonraki açışınızda çıkış dosyası, yapmanız gereken başka bir işlem ile yeni bir ada sahip olacaktır.  
  
> [!NOTE]
>  Ayrılmış özellikler, proje dosyasında tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek proje dosyası, proje adı çıkış için bir ad belirtmek için ayrılmış bir özellik olarak başvurur.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBuild](msbuild.md)  
 [MSBuild Ayrılmış ve Tanınmış Özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)


