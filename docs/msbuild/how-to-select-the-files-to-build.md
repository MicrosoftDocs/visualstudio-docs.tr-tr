---
title: 'Nasıl yapılır: derlenecek dosyaları seçme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ef956b94ca263dac5ce57c7b122576060bb7a05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820674"
---
# <a name="how-to-select-the-files-to-build"></a>Nasıl yapılır: derleme dosyaları seçin
Bir proje oluşturduğunuzda bazı dosyaları içeren, her dosya proje dosyasında ayrı olarak listeleyebilirsiniz veya tüm dosyaları bir dizin veya iç içe geçmiş bir dizinler kümesi eklemek için joker karakterler kullanabilirsiniz.  
  
## <a name="specify-inputs"></a>Girişleri belirtin  
 Öğeleri bir derleme için girişler temsil eder. Öğeler hakkında daha fazla bilgi için bkz. [öğeleri](../msbuild/msbuild-items.md).  
  
 Bir derleme için dosyaları eklemek için bir öğe listesinde eklenmelidir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası. Birden çok dosya öğesi listeleri için tek tek dosyalar dahil olmak üzere veya aynı anda çok sayıda dosya eklemek için joker karakterler kullanılarak eklenebilir.  
  
#### <a name="to-declare-items-individually"></a>Bildirmek için ayrı ayrı öğeler  
  
-   Kullanım `Include` öznitelikleri benzer aşağıdaki:  
  
     `<CSFile Include="form1.cs"/>`  
  
     veya 
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Proje dosyası ile aynı dizinde bir öğe koleksiyonu öğeleri emin değilseniz, öğenin tam veya göreli yol belirtmeniz gerekir. Örneğin: `Include="..\..\form2.cs"`  
  
#### <a name="to-declare-multiple-items"></a>Birden çok öğe bildirmek için  
  
-   Kullanım `Include` öznitelikleri benzer aşağıdaki:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     veya 
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specify-inputs-with-wildcards"></a>Joker karakter olarak girişleri belirtin  
 Ayrıca bir yapı için girdi olarak yinelemeli olarak joker karakterler tüm dosyaları veya yalnızca belirli dosyaları alt dizinleri. Joker karakterler hakkında daha fazla bilgi için bkz: [öğeleri](../msbuild/msbuild-items.md)  
  
 Aşağıdaki örnekler grafikleri dosyaları aşağıdaki dizinlerde içeren bir proje temel alır ve alt dizinleri, proje dosyasıyla birlikte bulunan *proje* dizini:  
  
 *Project\Images\BestJpgs*  
  
 *Project\Images\ImgJpgs*  
  
 *Project\Images\ImgJpgs\Img1*  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Tüm içerecek şekilde *.jpg* dosyalar *görüntüleri* dizin ve alt dizinleri  
  
-   Aşağıdaki `Include` özniteliği:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Tüm içerecek şekilde *.jpg* dosyaları başlayarak *img*  
  
-   Aşağıdaki `Include` özniteliği:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Sonlanan adlara sahip dizinlerinde tüm dosyaları eklenip eklenmeyeceğini *jpg formatından*  
  
-   Aşağıdakilerden birini kullanın `Include` öznitelikleri:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     veya
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="pass-items-to-a-task"></a>Bir göreve geçiş öğeleri  
 Bir proje dosyasında kullanabileceğiniz @ görevler bir derleme için giriş olarak bir tüm öğe listesini belirtmek için () gösterimi. Bu gösterim, tüm dosyaları ayrı ayrı listelemek veya joker karakter kullanabilirsiniz.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Tüm Visual C# veya Visual Basic dosyalarını girdi olarak kullanmak için  
  
-   Kullanım `Include` öznitelikleri aşağıdakine benzer:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     veya 
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Bir derleme için girişler belirtmek için öğeleriyle joker karakterler kullanmanız gerekir; kullanarak girişleri belirtemezsiniz `Sources` özniteliğini [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] gibi görevleri [Csc](../msbuild/csc-task.md) veya [Vbc](../msbuild/vbc-task.md). Aşağıdaki örnek bir proje dosyasında geçerli değil:  
> 
>  `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tüm giriş dosyalarını ayrı olarak içeren bir proje gösterir.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tüm içerecek şekilde bir joker karakter kullanır. *.cs* dosyaları.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: dosyaları derlemeden dışlama](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Öğeler](../msbuild/msbuild-items.md)
