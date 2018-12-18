---
title: 'Nasıl yapılır: dosyaları derlemeden dışlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2adfd3d571fe16fcbfe273e5513ebea724403cd
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080694"
---
# <a name="how-to-exclude-files-from-the-build"></a>Nasıl yapılır: dosyaları derlemeden dışlama
Bir proje dosyasında tüm dosyaları bir derleme için girdi olarak bir dizin veya iç içe geçmiş bir dizinler kümesi eklemek için joker karakterler kullanabilirsiniz. Ancak, bir dosya dizinine veya bir dizin, iç içe geçmiş bir derleme için giriş olarak dahil etmek istemediğiniz dizinler kümesi olabilir. Açıkça girişleri listesinden söz konusu dosya veya dizin dışlayabilirsiniz. Ayrıca olabilir bir dosyayı yalnızca belirli koşullar altında dahil etmek istediğiniz bir proje. Bir yapı içinde bir dosya dahil koşullar açıkça bildirebilirsiniz.  
  
## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir dosya veya dizin işlemenin dışında bir derleme için girişler  
 Öğe bir derleme için giriş dosyaları listeleridir. Dahil etmek istediğiniz öğeleri ayrı ayrı veya kullanarak bir grup olarak bildirilen `Include` özniteliği. Örneğin:  
  
```xml  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Tüm dosyaları bir derleme için girdi olarak bir dizin veya iç içe geçmiş bir dizinler kümesi eklemek için joker karakterler kullanılıyorsa bir veya daha fazla dosya dizinine veya bir dizinde olabilir dahil etmek istemediğiniz dizinleri iç içe bir dizi. Bir öğeyi öğesi listesinden dışlamak için kullanmak `Exclude` özniteliği.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Tüm içerecek şekilde *.cs* veya *.vb* dışında dosyaları *Form2*  
  
-   Aşağıdakilerden birini kullanın `Include` ve `Exclude` öznitelikleri:  
  
    ```xml  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
    veya
  
    ```xml  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Tüm içerecek şekilde *.cs* veya *.vb* dışında dosyaları *Form2* ve *Form3*  
  
-   Aşağıdakilerden birini kullanın `Include` ve `Exclude` öznitelikleri:  
  
    ```xml  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
    veya
  
    ```xml  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Tüm içerecek şekilde *.jpg* dizinlerindeki dosyaları *görüntüleri* hariç dizin *Version2* dizini  
  
-   Aşağıdaki `Include` ve `Exclude` öznitelikleri:  
  
    ```xml  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Her iki öznitelik yolunu belirtmeniz gerekir. İçinde dosya konumlarını belirtme mutlak yol kullanıyorsanız `Include` özniteliği içinde mutlak bir yol da kullanmanız gerekir `Exclude` göreli bir yol kullanır; öznitelik `Include` özniteliği, göreli bir yol kullanmalısınız`Exclude`özniteliği.  
  
## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir dosya veya dizin bir derleme için girişler dışlanacak kullanım koşulları  
 Dahil etmek istediğiniz öğeleri varsa, örneğin, hata ayıklama derlemesi ancak bir yayın yapısı kullanabileceğiniz `Condition` öğesi dahil edileceği koşullarda belirtmek için özniteliği.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Dosya eklemek için *Formula.vb* yayın derlemeleri de yalnızca  
  
-   Kullanım bir `Condition` özniteliği aşağıdakine benzer:  
  
    ```xml  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir proje tüm derlemeleri *.cs* dışında bir dizindeki dosyaları *Form2.cs*.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
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
 [Öğeleri](../msbuild/msbuild-items.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Nasıl yapılır: derleme dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md)   
