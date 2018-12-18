---
title: 'Nasıl yapılır: dosyaları derlemeden dışlama | Microsoft Docs'
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
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 114c973246c325604c79ca248cc3487fd495a19a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230617"
---
# <a name="how-to-exclude-files-from-the-build"></a>Nasıl Yapılır: Dosyaları Derlemeden Dışlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir proje dosyasında tüm dosyaları bir derleme için girdi olarak bir dizin veya iç içe geçmiş bir dizinler kümesi eklemek için joker karakterler kullanabilirsiniz. Ancak, bir dosya dizinine veya bir dizin, iç içe geçmiş bir derleme için giriş olarak dahil etmek istemediğiniz dizinler kümesi olabilir. Açıkça girişleri listesinden söz konusu dosya veya dizin dışlayabilirsiniz. Ayrıca olabilir bir dosyayı yalnızca belirli koşullar altında dahil etmek istediğiniz bir proje. Bir yapı içinde bir dosya dahil koşullar açıkça bildirebilirsiniz.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir dosya veya dizin, bir derleme için girişler hariç  
 Öğe bir derleme için giriş dosyaları listeleridir. Dahil etmek istediğiniz öğeleri ayrı ayrı veya kullanarak bir grup olarak bildirilen `Include` özniteliği. Örneğin:  
  
```  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Tüm dosyaları bir derleme için girdi olarak bir dizin veya iç içe geçmiş bir dizinler kümesi eklemek için joker karakterler kullanılıyorsa bir veya daha fazla dosya dizinine veya bir dizinde olabilir dahil etmek istemediğiniz dizinleri iç içe bir dizi. Bir öğeyi öğesi listesinden dışlamak için kullanmak `Exclude` özniteliği.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Form2 dışındaki tüm .cs veya .vb dosyaları eklemek için  
  
-   Aşağıdakilerden birini kullanın `Include` ve `Exclude` öznitelikleri:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     - veya -  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Form2 ve Form3 hariç tüm .cs veya .vb dosya eklemek için  
  
-   Aşağıdakilerden birini kullanın `Include` ve `Exclude` öznitelikleri:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     - veya -  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Alt dizinlerdeki görüntüleri dizinin Version2 dizin hariç tüm .jpg dosyaları eklemek için  
  
-   Aşağıdaki `Include` ve `Exclude` öznitelikleri:  
  
    ```  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Her iki öznitelik yolunu belirtmeniz gerekir. İçinde dosya konumlarını belirtme mutlak yol kullanıyorsanız `Include` özniteliği içinde mutlak bir yol da kullanmanız gerekir `Exclude` göreli bir yol kullanır; öznitelik `Include` özniteliği, göreli bir yol kullanmalısınız`Exclude`özniteliği.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Girişler, bir dosya veya dizin, bir derleme için hariç tutmak için koşul kullanma  
 Dahil etmek istediğiniz öğeleri varsa, örneğin, hata ayıklama derlemesi ancak bir yayın yapısı kullanabileceğiniz `Condition` öğesi dahil edileceği koşullarda belirtmek için özniteliği.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Yalnızca sürüm yapılarında Formula.vb dosya eklemek için  
  
-   Kullanım bir `Condition` özniteliği aşağıdakine benzer:  
  
    ```  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tüm dizinde Form2.cs dışında .cs dosyaları ile bir proje oluşturur.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğeleri](../msbuild/msbuild-items.md)   
 [MSBuild](msbuild.md) [nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md)


