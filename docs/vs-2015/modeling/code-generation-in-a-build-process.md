---
title: Kod oluşturma, derleme sürecinde | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e7cadbf9d4d99fa9deaf4d71545f43d2bf49a3f3
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281816"
---
# <a name="code-generation-in-a-build-process"></a>Derleme Sürecinde Kod Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Metin dönüştürme bir Visual Studio çözümü derleme sürecinin bir parçası olarak çağrılabilir. Metin dönüştürme için özelleştirilmiş yapı görevleri vardır. T4 yapı görevleri tasarım zamanı metin şablonlarını çalıştırır ve aynı zamanda çalışma zamanı (önişlenmiş) metin şablonlarını derler.

Kullandığınız oluşturma motoruna bağlı olarak, yapı görevleri farklı işlevleri yerine getirebilirler. Visual Studio'da bir çözüm derlediğinizde, bir metin şablonunda Visual Studio API'ya (EnvDTE) erişebilirsiniz [hostspecific = "true"](../modeling/t4-template-directive.md) özniteliği. Ancak, çözümü komut satırından yapılandırdığınızda veya Visual Studio üzerinden sunucu yapısını başlattığınızda bu geçerli değildir. Bu durumlarda, yapı MSBuild tarafından oluşturulur ve farklı bir T4 ana bilgisayar kullanılır.

Başka bir deyişle, MSBuild içinde metin şablonu oluşturduğunuzda, proje dosyası adları gibi şeylere aynı şekilde erişemezsiniz. Ancak, [ortam bilgilerini yapı parametrelerini kullanarak metin şablonlarına ve yönerge işlemcilerine geçirmek](#parameters).

##  <a name="buildserver"></a> Makinelerinizi yapılandırma

Geliştirme bilgisayarınızda yapı görevlerini etkinleştirmek için yükleme [Visual Studio için modelleme SDK](http://www.microsoft.com/download/details.aspx?id=40754).

Varsa [yapı sunucunuzu](http://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) üzerinde Visual Studio yüklü değil, bir bilgisayarda çalıştırır geliştirme makinenizden yapı bilgisayarına aşağıdaki dosyaları kopyalayın. En son sürüm numaraları yerine ' *'.

-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    -   Microsoft.TextTemplating.Build.Tasks.dll

    -   Microsoft.TextTemplating.targets

-   $(ProgramFiles) \Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    -   Microsoft.VisualStudio.TextTemplating.*.0.dll

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (several files)

    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

-   $(ProgramFiles) \Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Projeyi dosyasını düzenlemek için

MSBuild içindeki bazı özellikleri yapılandırmak için proje dosyanızı düzenlemeniz gerekir.

Çözüm Gezgini'nde **kaldırma** projenizin bağlam menüsünden. Bu .csproj veya .vbproj dosyasını XML düzenleyicisinde düzenlemenize olanak tanır.

Düzenlemeyi bitirdiğinizde seçin **yeniden**.

## <a name="import-the-text-transformation-targets"></a>Metin Dönüşüm Hedeflerini Alma

.Vbproj veya .csproj dosyasında şöyle bir satır bulun:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- veya -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Bu satırın ardından, Metin Şablon Oluşturma almayı ekleyin:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Şablonları bir yapıda dönüştürme

Dönüştürme görevini kontrol etmek için proje dosyanızın içine ekleyebileceğiniz bazı özellikler vardır:

-   Dönüştürme görevini her yapı başlangıcında çalıştır:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

-   Salt okunur dosyaların üzerine yaz (ör. kullanıma alınmamış oldukları için): 

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

-   Her şablonu her zaman dönüştür:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Varsayılan olarak, T4 MSBuild görevi, kendi şablon dosyasından ya da içerdiği dosyaların herhangi birinden veya şablon ya da kullandığı yönerge işlemcisi tarafından önceden okunmuş herhangi bir dosyadan eski ise, bir çıktı dosyası oluşturur. Bunun, Visual Studio'da bulunan ve yalnızca şablon ve çıktı dosyası tarihlerini karşılaştıran Tüm Şablonları Dönüştür komutu tarafından kullanılandan daha güçlü bir bağımlılık testi olduğuna dikkat edin.

Projenizde yalnızca metin dönüştürmeleri gerçekleştirmek için TransformAll görevini çağırın:

`msbuild myProject.csproj /t:TransformAll`

Belirli metin şablonu dönüştürmek için:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

TransformFile içinde joker karakterler kullanabilirsiniz:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Kaynak Denetimi

Kaynak denetim sistemi ile yerleşik herhangi bir tümleştirme yoktur. Ancak, örneğin oluşturulmuş bir dosyayı kullanıma almak ve iade etmek için, kendi uzantılarınızı ekleyebilirsiniz. Varsayılan olarak, metin dönüştürme görevi salt okunur işaretli bir dosyanın üzerine yazmaktan kaçınır ve bu tür bir dosyayla karşılaşıldığında Visual Studio hata listesinde bir hata günlüğe kaydedilir ve görev başarısız olur.

Salt okunur dosyaların üzerine yazılması gerektiğini belirtmek için bu özelliği ekleyin:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Son işleme adımını özelleştirmediğiniz sürece, herhangi bir dosyanın üzerine yazıldığında, hata listesinde bir uyarı günlüğe kaydedilir.

## <a name="customizing-the-build-process"></a>Oluşturma işlemini özelleştirme

Oluşturma işleminde diğer görevlerden önce metin dönüştürme gerçekleşir. Özelliklerini ayarlayarak önce ve dönüştürme sonra çağrılan görevleri tanımlayabilirsiniz `$(BeforeTransform)` ve `$(AfterTransform)`:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

İçinde `AfterTransform`, dosyaların listelerine başvurabilirsiniz:

- GeneratedFiles - işlem tarafından yazılan dosyaların listesi. Varolan salt okunur dosyaların üzerine yazan bu dosyalar için, %(GeneratedFiles.ReadOnlyFileOverwritten) doğru olacaktır. Bu dosyalar kaynak denetiminden denetlenebilir.

- NonGeneratedFiles - üzerine yazılmamış, salt okunur dosyaların listesi.

  Örneğin, GeneratedFiles'ı kullanıma almak için bir görev tanımlarsınız.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath ve OutputFileName

Bu özellikler yalnızca MSBuild tarafından kullanılır. Visual Studio'da kod üretimi etkilemez. Bunlar, oluşturulan çıktı dosyasını farklı bir klasör veya dosyaya yeniden yönlendirir. Hedef klasörün zaten bulunması gerekir.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Yeniden yönlendirmek için kullanışlı bir klasör: `$(IntermediateOutputPath).`

Dosya adını belirtir ve çıktısını alırsanız, şablonlardaki çıktı yönergesinde belirtilen uzantıdan öncelikli olur.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Aynı zamanda Tüm Şablonları Dönüştür'ü kullanarak VS içinde şablonları dönüştürüyorsanız ya da tek dosya oluşturucuyu çalıştırıyorsanız, OutputFileName veya OutputFilePath belirtmeniz önerilmez. Dönüştürme işlemini nasıl tetiklediğinizde bağlı olarak, farklı dosya yolları elde edebilirsiniz. Bu çok kafa karıştırıcı olabilir.

## <a name="adding-reference-and-include-paths"></a>Başvuru ekleme ve yolları dahil etme

Ana bilgisayar, şablonlarda başvurulan derlemeler için arama yaptığı varsayılan bir grup yola sahiptir. Bu gruba ekleme yapmak için:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Ekleme kodu dosyalarının aranacağı klasörleri ayarlamak için, noktalı virgülle ayrılmış bir liste sağlayın. Genellikle varolan klasör listesine eklersiniz.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

##  <a name="parameters"></a> Şablonlara yapı bağlamı verilerini geçirme

Proje dosyasında parametre değerlerini ayarlayabilirsiniz. Örneğin, derleme özellikleri geçirebilirsiniz ve [ortam değişkenlerini](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

Bir metin şablonunda ayarlanan `hostspecific` şablon yönergesinde. Kullanım [parametre](../modeling/t4-parameter-directive.md) yönergesi değerlerini almak için:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

##  <a name="msbuild"></a> Proje özelliklerini kullanma derlemede ve ekleme yönergelerinde

$(SolutionDir) gibi Visual Studio makroları MSBuild içinde çalışmaz. Bunun yerine, proje özelliklerini kullanabilirsiniz.

Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek adlı bir özellik tanımlar `myLibFolder`:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Artık derlemede ve ekleme yönergelerinde proje özelliklerini kullanabilirsiniz:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

 Bu yönergeler, hem MSBuild içinde hem de Visual Studio ana bilgisayarlarında T4parameterValues değerlerini alır.

## <a name="q--a"></a>Soru - Yanıt

**Neden yapı sunucusunda şablonları dönüştürmek istiyor? Ben kodumu iade önce ben zaten Visual Studio şablonları dönüştürülür.**

Şablon tarafından okunmuş eklenen bir dosyayı veya başka bir dosyayı güncelleştirirseniz, Visual Studio dosyayı otomatik olarak dönüştürmez. Oluşturma işleminin bir parçası olarak şablonları dönüştürdüğünüzde her şey daima güncel olur.

**Diğer seçenekler yok metin şablonlarını dönüştürmeyle ilgili nelerdir?**

-   [TextTransform yardımcı programı](../modeling/generating-files-with-the-texttransform-utility.md) komut dosyalarında kullanılabilir. Çoğu durumda, MSBuild kullanmak daha kolay olur.

-   [Bir VS Uzantısında Metin Dönüştürmeyi Çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md)

-   [Tasarım zamanı metin şablonları](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Visual Studio tarafından dönüştürülür.

-   [Çalıştırma zamanı metin şablonları](../modeling/run-time-text-generation-with-t4-text-templates.md) uygulamanızdaki çalışma zamanında dönüştürülür.

## <a name="read-more"></a>Daha fazla bilgi edinin

T4 MSbuild şablonundaki rehber oldukça kullanışlıdır: $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets

- [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)
- [Visual Studio Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185579)
- [Oleg Sych: T4 tümleştirmeyi anlama](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)