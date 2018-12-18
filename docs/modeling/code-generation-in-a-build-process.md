---
title: Derleme Sürecinde Kod Oluşturma
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ef7c49c514c9104ee4659db983b04c27036df889
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281829"
---
# <a name="code-generation-in-a-build-process"></a>Derleme sürecinde kod oluşturma

[Metin dönüştürme](../modeling/code-generation-and-t4-text-templates.md) parçası olarak çağrılabilir [derleme işlemi](/azure/devops/pipelines/index) Visual Studio çözümünün. Metin dönüştürme için özelleştirilmiş yapı görevleri vardır. T4 yapı görevleri tasarım zamanı metin şablonlarını çalıştırır ve aynı zamanda çalışma zamanı (önişlenmiş) metin şablonlarını derler.

Kullandığınız oluşturma motoruna bağlı olarak, yapı görevleri farklı işlevleri yerine getirebilirler. Visual Studio'da bir çözüm derlediğinizde, bir metin şablonunda Visual Studio API'ya (EnvDTE) erişebilirsiniz [hostspecific = "true"](../modeling/t4-template-directive.md) özniteliği. Ancak, çözümü komut satırından oluşturduğunuzda veya Visual Studio üzerinden sunucu yapısını başlattığınızda bu geçerli değildir. Bu durumlarda, yapı MSBuild tarafından oluşturulur ve farklı bir T4 ana bilgisayar kullanılır.

Başka bir deyişle, MSBuild içinde metin şablonu oluşturduğunuzda, proje dosyası adları gibi şeyler aynı şekilde erişemezsiniz. Ancak, [ortam bilgilerini yapı parametrelerini kullanarak metin şablonlarına ve yönerge işlemcilerine geçirmek](#parameters).

##  <a name="buildserver"></a> Makinelerinizi yapılandırma

Geliştirme bilgisayarınızda yapı görevlerini etkinleştirmek için Visual Studio için modelleme SDK'sını yükleyin.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Varsa [yapı sunucunuzu](/azure/devops/pipelines/agents/agents) üzerinde Visual Studio yüklü değil, bir bilgisayarda çalıştırır geliştirme makinenizden yapı bilgisayarına aşağıdaki dosyaları kopyalayın. En son sürüm numaraları yerine ' *'.

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    - Microsoft.TextTemplating.Build.Tasks.dll

    - Microsoft.TextTemplating.targets

- $(ProgramFiles) \Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    - Microsoft.VisualStudio.TextTemplating.*.0.dll

    - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (several files)

    - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles) \Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Projeyi dosyasını düzenlemek için

Msbuild'de bazı özellikleri yapılandırmak için proje dosyanızı düzenlemeniz gerekir.

İçinde **Çözüm Gezgini**, seçin **kaldırma** projenizin bağlam menüsünden. Bu .csproj veya .vbproj dosyasını XML düzenleyicisinde düzenlemenize olanak tanır.

Düzenlemeyi bitirdiğinizde seçin **yeniden**.

## <a name="import-the-text-transformation-targets"></a>Metin dönüşüm hedeflerini alma

.Vbproj veya .csproj dosyasında şöyle bir satır bulun:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- veya -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Bu satırın ardından, Metin Şablon Oluşturma almayı ekleyin:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version - defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>Şablonları bir yapıda dönüştürme

Dönüştürme görevini kontrol etmek için proje dosyanızın içine ekleyebileceğiniz bazı özellikler vardır:

- Dönüştürme görevini her yapı başlangıcında çalıştır:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Salt okunur dosyaların üzerine yaz (ör. kullanıma alınmamış oldukları için): 

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Her şablonu her zaman dönüştür:

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

## <a name="source-control"></a>Kaynak denetimi

Kaynak denetim sistemi ile yerleşik herhangi bir tümleştirme yoktur. Ancak, örneğin oluşturulmuş bir dosyayı kullanıma almak ve iade etmek için, kendi uzantılarınızı ekleyebilirsiniz. Varsayılan olarak, metin dönüştürme görevi salt okunur işaretli bir dosyanın üzerine yazmaktan kaçınır ve bu tür bir dosyayla karşılaşıldığında Visual Studio hata listesinde bir hata günlüğe kaydedilir ve görev başarısız olur.

Salt okunur dosyaların üzerine yazılması gerektiğini belirtmek için bu özelliği ekleyin:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Son işleme adımını özelleştirmediğiniz sürece, herhangi bir dosyanın üzerine yazıldığında, hata listesinde bir uyarı günlüğe kaydedilir.

## <a name="customize-the-build-process"></a>Yapı işlemini özelleştirme

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

Ayrıca tüm dönüştürme kullanarak ya da tek dosya oluşturucuyu çalıştırıyorsanız VS içinde şablonları dönüştürüyorsanız bir OutputFileName veya outputfilepath belirtmeniz önerilmez. Dönüştürme işlemini nasıl tetiklediğinizde bağlı olarak, farklı dosya yolları elde edebilirsiniz. Bu çok kafa karıştırıcı olabilir.

## <a name="add-reference-and-include-paths"></a>Başvuru ekleme ve yolları dahil etme

Ana bilgisayar, şablonlarda başvurulan derlemeler için arama yaptığı varsayılan bir grup yola sahiptir. Bu gruba ekleme yapmak için:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Ekleme kodu dosyalarının aranacağı klasörleri ayarlamak için, noktalı virgülle ayrılmış bir liste sağlayın. Genellikle varolan klasör listesine eklersiniz.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

##  <a name="parameters"></a> Şablonlara yapı bağlamı verilerini geçirme

Proje dosyasında parametre değerlerini ayarlayabilirsiniz. Örneğin, geçirebilirsiniz [derleme](../msbuild/msbuild-properties.md) özellikleri ve [ortam değişkenlerini](../msbuild/how-to-use-environment-variables-in-a-build.md):

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

Bir yönerge işlemcisi çağırabilirsiniz [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` öğesinden veri alır `T4ParameterValues` yalnızca MSBuild kullandığınızda. Visual Studio kullanarak şablon dönüştürdüğünüzde, parametrelerin varsayılan değerleri olacaktır.

##  <a name="msbuild"></a> Derlemede proje özelliklerini kullanmak ve ekleme yönergelerinde

Visual Studio Makroları ister **$(SolutionDir)** MSBuild içinde çalışmaz. Bunun yerine, proje özelliklerini kullanabilirsiniz.

Düzenleme, *.csproj* veya *.vbproj* dosya bir proje özelliği tanımlamak için. Bu örnek adlı bir özellik tanımlar **myLibFolder**:

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

Eklenen bir dosyanın veya şablon tarafından Okunmuş başka bir dosyayı güncelleştirirseniz, Visual Studio dosyayı otomatik olarak dönüştürmez. Yapının bir parçası olarak şablonları dönüştürme her şeyin güncel durumda.

**Diğer seçenekler yok metin şablonlarını dönüştürmeyle ilgili nelerdir?**

- [TextTransform yardımcı programı](../modeling/generating-files-with-the-texttransform-utility.md) komut dosyalarında kullanılabilir. Çoğu durumda, MSBuild kullanmak daha kolay olur.

- [Bir VS Uzantısında Metin Dönüştürmeyi Çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Tasarım zamanı metin şablonları](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Visual Studio tarafından dönüştürülür.

- [Çalıştırma zamanı metin şablonları](../modeling/run-time-text-generation-with-t4-text-templates.md) uygulamanızdaki çalışma zamanında dönüştürülür.

## <a name="see-also"></a>Ayrıca bkz.

- T4 MSbuild şablonundaki Rehber yoktur *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets*
- [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md)
