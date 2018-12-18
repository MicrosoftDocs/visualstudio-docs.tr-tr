---
title: 'Nasıl yapılır: derlemeyi temizleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9d039d6f6f5593538063e751348148786667000
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879063"
---
# <a name="how-to-clean-a-build"></a>Nasıl yapılır: derlemeyi temizleme
Derlemeyi temizleme, yalnızca proje ve bileşen dosyalarını bırakarak tüm ara ve Çıkış dosyalarını silinir. Proje ve bileşen dosyalarından yeni örneklerini Ara ve çıkış dosyalarının sonra oluşturulabilir. Kitaplığı ile sağlanan ortak görevler [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] içeren bir [Exec](../msbuild/exec-task.md) sistem komutlarını çalıştırmak için kullanabileceğiniz bir görev. Görevleri Kitaplığı hakkında daha fazla bilgi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
## <a name="create-a-directory-for-output-items"></a>Çıktı öğeleri için bir dizin oluşturun  
 Varsayılan olarak, *.exe* oluşturulan bir projeyi derlediğinizde dosyası, proje ve kaynak dosyalarıyla aynı dizine yerleştirilir. Genellikle, Bununla birlikte, çıkış öğeleri farklı bir dizinde oluşturulur.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Çıktı öğeleri için bir dizin oluşturmak için  
  
1.  Kullanım `Property` dizinin adını ve konumunu tanımlamak için. Örneğin, adında bir dizin oluşturma *BuiltApp* proje ve kaynak dosyaları içeren dizine:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Kullanım [MakeDir](../msbuild/makedir-task.md) dizini mevcut değilse dizini oluşturmak için görev. Örneğin:  
  
     ```xml
     <MakeDir Directories = "$(builtdir)"  
      Condition = "!Exists('$(builtdir)')" />
     ```
  
## <a name="remove-the-output-items"></a>Çıktı öğeleri Kaldır  
 Ara ve çıkış dosyalarının yeni kopyalarını oluşturmadan önce önceki tüm ara ve çıkış dosyalarının örneklerini silmek isteyebilirsiniz. Kullanım [RemoveDir](../msbuild/removedir-task.md) görev bir dizin ve tüm dosyaları ve dizinleri içeren bir diskten silinecek.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Bir dizin ve dizinde bulunan tüm dosyaları kaldırmak için  
  
-   Kullanım `RemoveDir` görev dizini kaldırılamıyor. Örneğin:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod projesini içeren yeni bir hedef örneği `Clean`, kullanan `RemoveDir` bir dizin ve tüm dosyaları ve içerdiği dizinleri silmek için görev. Ayrıca bu örnekte, `Compile` hedef derleme temizlendiğinde silinir çıktı öğeleri için ayrı bir dizin oluşturur.  
  
 `Compile` varsayılan hedef olarak tanımlanır ve farklı bir hedef veya hedefleri belirtmediğiniz sürece bu nedenle otomatik olarak kullanılır. Komut satırı anahtarını kullanmanız **-hedef** farklı bir hedef belirtmek için. Örneğin:  
  
 `msbuild <file name>.proj -target:Clean`  
  
 **-Hedef** anahtarı kısalttık için **-t** ve birden fazla hedef belirtebilirsiniz. Örneğin, hedef kullanılacak `Clean` hedef `Compile`, türü:  
  
 `msbuild <file name>.proj -t:Clean;Compile`  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yürütme görevi](../msbuild/exec-task.md)   
 [MakeDir görevi](../msbuild/makedir-task.md)   
 [RemoveDir görevi](../msbuild/removedir-task.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Hedefler](../msbuild/msbuild-targets.md)