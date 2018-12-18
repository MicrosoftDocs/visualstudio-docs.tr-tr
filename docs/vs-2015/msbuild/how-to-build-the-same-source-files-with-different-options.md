---
title: 'Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme | Microsoft Docs'
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
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c46d0577d19a3b3ad0fcd150f33d400e76d550d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831009"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Nasıl Yapılır: Farklı Seçeneklerle Aynı Kaynak Dosyaları Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Projeleri oluşturduğunuzda, farklı bir derleme seçenekleri ile aynı bileşenleri sık derleyin. Örneğin, sembol bilgisi veya bir yayın yapısı sembol bilgisi ancak iyileştirmeler ile hata ayıklama derlemesi oluşturabilirsiniz. Veya, x86 gibi belirli bir platformda çalıştırmak için bir proje oluşturabilirsiniz veya [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]. Bu durumlarda, aynı derleme seçeneklerin çoğu kalır; yalnızca birkaç seçeneği, derleme yapılandırmasını kontrol etmek için değiştirilir. İle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], özellikleri ve koşulları farklı derleme yapılandırmalarında oluşturmak için kullanın.  
  
## <a name="using-properties-to-modify-projects"></a>Projeleri değiştirmek için özellikleri kullanma  
 `Property` Öğesi birkaç kez geçici bir dizine konumu gibi bir proje dosyası olarak başvurulan bir değişkeni tanımlar veya kullanılan özellik değerlerini ayarlamak için hata ayıklama derleme ve yayın gibi çeşitli yapılandırmalar oluşturun. Özellikleri hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](msbuild-properties1.md).  
  
 Proje dosyasını değiştirmek zorunda kalmadan yapı yapılandırmasını değiştirmek için Özellikler'i kullanabilirsiniz. `Condition` Özniteliği `Property` öğesi ve `PropertyGroup` öğesi özelliklerin değerini değiştirmenize olanak sağlar. Hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] koşullar bkz [koşullar](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Bir grubu başka bir özelliğe dayalı özellikleri ayarlamak için  
  
-   Kullanım bir `Condition` özniteliğini bir `PropertyGroup` öğesi şuna benzer:  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Başka bir özelliğe dayalı bir özelliği tanımlamak için  
  
-   Kullanım bir `Condition` özniteliğini bir `Property` öğesi şuna benzer:  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Komut satırında özelliklerini belirtme  
 Birden çok yapılandırmaları kabul etmek için proje dosyanızı yazıldıktan sonra projenizi oluşturduğunuzda, bu yapılandırmaları değiştirme olanağına sahip gerekir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özellikleri kullanarak komut satırı belirtilmesine olanak tanıyarak bu özelliği sağlar **/Property** veya **/p** geçin.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Komut satırında bir proje özelliğini ayarlamak için  
  
-   Kullanım **/Property** özellik ve özellik değeri ile geçiş yapın. Örneğin:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - veya -  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Komut satırında birden fazla proje özelliği belirtmek için  
  
- Kullanma **/Property** veya **/p** özellik ve özellik değerleri ile birden çok kez geçin veya kullanın **/Property** veya **/p** geçin ve birden çok özellik noktalı virgülle (;) ayırın. Örneğin:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   - veya -  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  Ortam değişkenlerini de özellik olarak kabul edilir ve tarafından otomatik olarak eklenen [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Ortam değişkenlerini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir yapı içinde kullanımı ortam değişkenlerini](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  Komut satırında belirtilen özellik değeri, aynı özelliği proje dosyasında ayarlanır ve değer proje dosyasında bir ortam değişkeni değeri önceliklidir herhangi bir değer daha önceliklidir.  
  
  Kullanarak bu davranışı değiştirebilirsiniz `TreatAsLocalProperty` öznitelik bir proje etiketinde. Bu öznitelik ile listelenen özellik adları için komut satırında belirtilen özellik değeri değer proje dosyasında öncelikli değil. Bu konuda daha sonra bir örnek bulabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, "Hello World" projenin hata ayıklama derleme ve yayın derlemesi oluşturmak için kullanılan iki yeni özellik gruplarını içerir.  
  
 Bu projede hata ayıklama sürümünü oluşturmak için şunu yazın:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Bu proje perakende sürümünü oluşturmak için şunu yazın:  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `TreatAsLocalProperty` özniteliği. `Color` Özellik değerine sahip `Blue` proje dosyasında ve `Green` komut satırında. İle `TreatAsLocalProperty="Color"` proje etiketinde, komut satırı özelliği (`Green`) proje dosyasında tanımlanan özellik geçersiz kılmaz (`Blue`).  
  
 Projeyi oluşturmak için aşağıdaki komutu girin:  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBuild](msbuild.md)  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Proje Öğesi (MSBuild)](../msbuild/project-element-msbuild.md)


