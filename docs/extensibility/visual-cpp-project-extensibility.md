---
title: Visual C++ proje genişletilebilirliği
ms.custom: ''
ms.date: 09/12/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 913ad2e785fcdb2067f89d0d4de2b250db40468b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349682"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ proje sistemi genişletilebilirlik ve araç takımı tümleştirmesi

*Visual C++ proje sistemi* .vcxproj dosyaları için kullanılır. Dayanır [Visual Studio ortak proje System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) ve ek, yeni araç takımları, derleme mimarileri ve Hedef platformlar kolay tümleştirme için C++ özgü genişletilebilirlik noktaları sağlar. 

## <a name="c-msbuild-targets-structure"></a>C++ MSBuild hedefleri yapısı

Tüm .vcxproj dosyaları bu dosyalarını içeri aktarın:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Bu dosyaların çok az tanımlama başlarına. Bunun yerine, bu özellik değerlerine göre diğer dosyaları Al:

- `$(ApplicationType)`

   Örnekler: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Bu, formu major.minor[.build[.revision bir geçerli sürüm dizesi olmalıdır]].

   Örnek: 1,0, 10.0.0.0

- `$(Platform)`

   Yapı mimarisi, geçmiş nedenlerle "Platformu" adlı.

   Örnekler: Win32 x86, x64, ARM   

- `$(PlatformToolset)`

   Örnekler: v140, v141, v141_xp, llvm

Bu özellik değerleri, altında klasör adları belirtin `$(VCTargetsPath)` kök klasörü:

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*Uygulama türü*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platformları*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;Platformları\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(kullanılabilir `$(ApplicationType)` boş Windows Masaüstü projeleri için)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>Yeni bir platform araç kümesi Ekle

Örneğin, "MyToolset" var olan Win32 platformu için yeni bir araç eklemek için oluşturun bir *MyToolset* klasörü altında `$(VCTargetsPath)`  *\\platformları\\Win32\\ PlatformToolsets\\*, oluşturup *Toolset.props* ve *Toolset.targets* dosyaları.

Her bir klasör adı altında *PlatformToolsets* görünür **proje özellikleri** iletişim kutusu kullanılabilir olarak **Platform araç takımını** belirtilen platform için burada gösterildiği gibi:

![Proje özellik sayfaları iletişim kutusu Platform araç takımı özelliğinde](media/vc-project-extensibility-platform-toolset-property.png "Platform araç takımı özelliği proje özellik sayfaları iletişim kutusu")

Benzer oluşturma *MyToolset* klasörleri ve *Toolset.props* ve *Toolset.targets* mevcut her platform klasöründe bulunan dosyaları bu araç takımı destekler.

### <a name="add-a-new-platform"></a>Yeni platform Ekle

Örneğin, "MyPlatform", yeni bir platformda eklemek için oluşturun bir *MyPlatform* klasörü altında `$(VCTargetsPath)`  *\\platformları\\*, oluşturup  *Platform.default.props*, *Platform.props*, ve *Platform.targets* dosyaları. Ayrıca bir `$(VCTargetsPath)`  *\\platformları\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets\\*  klasöründe ve en az bir araç takımı oluşturun.

Tüm klasör adları altında *platformları* her klasör `$(ApplicationType)` ve `$(ApplicationTypeRevision)` IDE kullanılabilir olarak görünen **Platform** seçimleri için bir proje.

![Yeni Proje platformu iletişim kutusunda yeni platform seçimi](media/vc-project-extensibility-new-project-platform.png "yeni proje platformu iletişim kutusunda yeni platform seçimi")

### <a name="add-a-new-application-type"></a>Yeni bir uygulama türü Ekle

Yeni bir uygulama türünü eklemek için oluşturun bir *MyApplicationType* klasörü altında `$(VCTargetsPath)` *\\uygulama türü\\* oluşturup bir *Defaults.props* içindeki dosya. Bir uygulama türü için en az bir gözden geçirme gerekiyor, bu nedenle de oluşturma bir `$(VCTargetsPath)`  *\\uygulama türü\\MyApplicationType\\1.0* klasör oluşturup bir  *Defaults.props* içindeki dosya. Ayrıca oluşturmalısınız bir `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\platformları* klasörü ve en az bir platform oluşturun.

`$(ApplicationType)` ve `$(ApplicationTypeRevision)` özellikleri olmayan görünür kullanıcı arabiriminin. Bunlar, proje şablonları içinde tanımlanan ve Proje oluşturulduktan sonra değiştirilemez.


## <a name="the-vcxproj-import-tree"></a>.Vcxproj alma ağacı

Microsoft C++ özellikler ve hedefler dosyaları için içeri aktarmalar Basitleştirilmiş ağacının şuna benzer:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*varsayılan*\\\*. *Özellikler*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama türü*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama türü*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama türü*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*platformları* \\ `$(Platform)` \\  *Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*varsayılan*\\\*. *Özellikler*  

Windows Masaüstü projeleri olmayan tanımlama `$(ApplicationType)`, yalnızca Al

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*varsayılan*\\\*. *Özellikler*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platformları*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*varsayılan*\\\*. *Özellikler*  

Kullanacağız `$(_PlatformFolder)` tutacak özelliği `$(Platform)` platform klasörü konumları. Bu özellik. 

> `$(VCTargetsPath)`\\*Platformları*\\`$(Platform)`

Windows Masaüstü uygulamaları için ve 

> `$(VCTargetsPath)`\\*Uygulama türü*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*platformları*\\`$(Platform)`

her şey için.

Özellik dosyaları şu sırayla alınır:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *Özellikler*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *Özellikler*  

MSBuild şu sırayla alınır:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *hedefleri*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *hedefleri*  

Araç takımı, bazı varsayılan özelliklerini tanımlamak gerekiyorsa, uygun ImportBefore ve ImportAfter klasörlere dosyaları ekleyebilirsiniz.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Yazar Toolset.props ve Toolset.targets dosyaları

*Toolset.props* ve *Toolset.targets* dosyaları bu araç takımı kullanıldığında, bir yapı sırasında ne üzerinde tam denetime sahiptir. Kullanılabilir hata ayıklayıcılar, bazı içeriği gibi IDE kullanıcı arabirimi de denetleyebilirsiniz **özellik sayfaları** iletişim ve diğer yönlerini bir proje davranışı.

Bir araç takımı, tüm derleme işlemi geçersiz kılabilirsiniz olsa da, genellikle yalnızca değiştirme veya bazı derleme adımları ekleme veya farklı bir derleme araçları, mevcut bir yapı işleminin bir parçası kullanmak için araç takımını kullanmanız gerekir. Bu hedefe ulaşmak için bir dizi ortak özellikler ve hedefler dosyaları, araç takımı aktarabilirsiniz vardır. Yapmak için araç takımı istediğinize bağlı olarak, bu dosyaları içeri aktarmaları veya örnekleri olarak kullanmak yararlı olabilir:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Bu dosya yerel yapı işleminin ana bölümleri tanımlar ve aynı zamanda içeri aktarır:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Microsoft derleyicileri kullanın ve Windows hedef araç takımları için varsayılan değerleri ayarlar.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Bu dosya, Windows SDK konumunu belirler ve Windows hedefleyen uygulamalar için bazı önemli özellikleri tanımlar.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Özel araç takımı hedefleri varsayılan C++ yapı işlemi ile tümleştirin 

C++ yapı işlemi varsayılan tanımlanan *Microsoft.CppCommon.targets*. Hedefleri var. herhangi bir özel derleme aracı çağırmaz; Bunlar, ana derleme adımları, sırası ve bağımlılıkları belirtin.

C++ yapı aşağıdaki hedefler tarafından temsil edilen üç ana adım vardır:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Her derleme adımı birbirinden bağımsız olarak çalıştırılabilir olduğundan, tek bir adımda çalıştıran hedef öğesi grupları ve farklı bir adım, bir parçası olarak çalıştırmak hedefleri içinde tanımlanan özellikler güvenemezsiniz. Bu bölme, belirli yapı performans iyileştirmelerini sağlar. Varsayılan olarak kullanılmıyor olsa da, bu ayrımı uymanız yine de önerilir.

Her bir adımın Çalıştır hedefleri, bu özellikleri tarafından denetlenir:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Her adım, önce ve sonra özellikleri de vardır. 

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Bkz: *Microsoft.CppBuild.targets* her adımda dahil edilen hedefleri örnekleri için dosya:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Hedef gibi görünüyorsa `_ClCompile`, doğrudan başlarına hiçbir şey yapma ancak bunun yerine dahil olmak üzere diğer hedeflerde bağımlı göreceğiniz `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` ve diğer yapı araç-özel hedefleri boş hedef olarak tanımlanan *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Çünkü `ClCompile` hedef boşsa, araç takımı tarafından geçersiz kılınmadığı sürece, herhangi bir gerçek derleme eylemi gerçekleştirilir. Araç takımı hedefleri geçersiz kılabilirsiniz `ClCompile` hedef, diğer bir deyişle, başka bir içerebilir `ClCompile` tanımı içeri aktardıktan sonra *Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Visual Studio'nun platformlar arası destek uygulanmadı önce oluşturulduğu, adına rağmen `ClCompile` hedef CL.exe çağırmak yok. Bu ayrıca Clang, gcc ve diğer derleyiciler uygun MSBuild görevleri kullanarak çağırabilirsiniz.

`ClCompile` Hedef dışında herhangi bir bağımlılık olmamalıdır `SelectClCompile` IDE içinde çalışma için tek dosyalı derleme komutu için gerekli olan hedef.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Araç takımı hedeflerin kullanılacak MSBuild görevleri

Bir gerçek derleme aracı çağırmak için hedef bir MSBuild görevi çağırması gerekir. Temel bir yoktur [Exec görevi](../msbuild/exec-task.md) çalıştırılacak bir komut satırı belirtmenize olanak verir. Ancak, derleme araçları, genellikle girişleri birçok seçeneğiniz vardır. Giriş ve çıkışları artımlı derlemeler için bunlar için özel görevler sağlamak için daha anlamlı olur böylece izlemek için. Örneğin, `CL` görev MSBuild özellikleri CL.exe anahtarları çevirir, bunları bir yanıt dosyasına yazar ve CL.exe çağırır. Ayrıca, daha sonra artımlı derlemeleri için tüm giriş ve çıkış dosyaları izler. Daha fazla bilgi için [Artımlı derleme ve güncellik denetimi](#incremental-build-and-up-to-date-check).

Bu görevleri Microsoft.Cpp.Common.Tasks.dll uygular:

- `BSCMake`

- `CL`

- `ClangCompile` (clang gcc anahtarlar)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (Exec gibi ancak giriş ve çıkış izleme ile)

- `SetEnv`

Bir aracı varsa, var olan bir aracı aynı eylemi gerçekleştirir ve (clang-cl ve CL olduğu gibi) benzer bir komut satırı anahtarları olan, aynı görevi ikisinin için kullanabilirsiniz.

Bir derleme aracı için yeni bir görev oluşturmanız gerekiyorsa, aşağıdaki seçeneklerden birini seçebilirsiniz:

1. Bu görevi nadiren kullanın veya yapılandırmanız için birkaç saniye önemli değildir, MSBuild 'inline' görevleri kullanabilirsiniz:

   - XAML görevi (özel derleme kuralı)

     Xaml görevi bildirimi bir örnek için bkz: `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*ve kullanımı için bkz: `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Kod görevi](../msbuild/msbuild-inline-tasks.md)

1. Daha iyi görev performans istediğiniz veya daha karmaşık işlevselliği yeterlidir, normal Msbuild'i kullanma [görev yazma](../msbuild/task-writing.md) işlem.

   Tüm girişler ve çıkışlar aracının aracı komut satırında olarak listeleniyorsa `CL`, `MIDL`, ve `RC` durumlarda ve otomatik girdi ve çıktı dosya izleme ve .tlog dosya oluşturma istiyorsanız, görev türetilen`Microsoft.Build.CPPTasks.TrackedVCToolTask`sınıfı. Şu an için temel belgelere varken [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) örnekler veya ayrıntılar için sınıf `TrackedVCToolTask` sınıfı. İlginizi çeken olacaksa, kendi sesinizi üzerinde ekleyin [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Artımlı derlemeleri ve güncel denetimleri

Varsayılan MSBuild Artımlı derleme hedefi kullanım `Inputs` ve `Outputs` öznitelikleri. Bunları belirtirseniz, yalnızca herhangi biri varsa, tüm çıktılar daha yeni bir zaman damgası MSBuild hedefi çağırır. Kaynak dosyaları genellikle eklemek veya diğer dosyalarını içeri aktarın ve yapı araçları üretim aracı seçeneklere bağlı olarak farklı çıkışları olduğundan, tüm olası girişleri belirtin zordur ve MSBuild hedeflerini çıkarır.

Bu sorunu yönetmek için C++ derleme artımlı derlemeleri desteklemek için farklı bir teknik kullanır. Çoğu hedefleri olmayan girişler ve çıkışlar belirtin ve sonuç olarak, derleme sırasında her zaman çalıştır. Giriş ve çıkışları içine tüm hakkında bilgi hedeflerini adlı görevler yazma *tlog* .tlog uzantısına sahip dosyalar. Güncel nedir ve .tlog dosyaları daha sonra derleme tarafından ne değişti ve yeniden oluşturulması gerekiyor denetlemek için kullanılır.

Tüm girişler ve çıkışlar belirlemek için yerel aracı görevleri tracker.exe kullanın ve [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) MSBuild tarafından sağlanan sınıfı.

Microsoft.Build.CPPTasks.Common.dll tanımlar `TrackedVCToolTask` genel soyut temel sınıf. Yerel aracı görevlerin çoğunu sınıfından türetilir.

## <a name="tlog-files"></a>.TLOG dosyaları

Üç tür .tlog dosyası vardır: *okuma*, *yazma*, ve *komut satırı*. Okuma ve yazma .tlog dosyaları, artımlı derlemeleri ve IDE'de güncellik denetimi tarafından kullanılır. Komut satırı .tlog dosyaları yalnızca artımlı yapılarında kullanılır.

MSBuild .tlog dosyalarını okuma ve yazma için bu yardımcı sınıflar sağlar:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) sınıfı, hem okuma hem de erişim .tlog dosyalarını yazmak ve çıkışları ya da bir çıktı eksik yeni girişler tanımlamak için kullanılabilir. Bu güncellik denetimi içinde kullanılır.

Komut satırı .tlog dosyaları, komut satırları yapıda kullanılan hakkında bilgi içerir. İç biçimi bunları üreten MSBuild görevi tarafından belirlenir. Bu nedenle bunlar yalnızca artımlı derlemeleri, güncel değil denetimleri için kullanılır.

Bir görev tarafından .tlog dosyaları oluşturduysanız, bu yardımcı sınıfları oluşturmak için kullanmak en iyisidir. Varsayılan güncellik denetimi artık yalnızca .tlog dosyalarda kullandığından, ancak bazen, bunları bir hedef olmadan bir görev oluşturmak daha uygundur. Bunları kullanarak yazdığınız `WriteLinesToFile` görev. Bkz: `_WriteMasmTlogs` hedeflemek `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* örnek olarak.

### <a name="read-tlog-format"></a>Okuma .tlog biçimi

*Okuma* .tlog dosyaları (\*.read.\*. TLOG) kaynak dosyaları ve bunların bağımlılıklarını hakkındaki bilgileri içerir.

Şapka işareti (**^**) bir satırın başında bir veya daha fazla kaynağı belirtir. Aynı bağımlılıklara kaynakları bir çubukla ayrılan (**\|**).

Kaynakların her biri kendi satırında sonra bağımlılık dosyalar listelenir. Tüm adlar tam yollardır.

Örneğin, proje kaynaklarınızı bulunur varsayın *F:\\test\\ConsoleApplication1\\ConsoleApplication1*. Varsa, kaynak dosyanızın *Class1.cpp*, bunlar sahip içeren

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

ardından *CL.read.1.tlog* dosya iki bağımlılıklarını tarafından izlenen bir kaynak dosya içerir:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Dosya adları büyük harfle yazmak için gerekli değildir, ancak bazı araçları bir kolaylık sağlamaya yöneliktir.

### <a name="write-tlog-format"></a>.TLOG biçimi yazma

*Yazma* .tlog (\*.write.\*. TLOG) dosyaları, kaynaklar ve çıkış bağlanın.

Şapka işareti (**^**) bir satırın başında bir veya daha fazla kaynağı belirtir. Birden çok kaynaktan bir çubukla ayrılan (**\|**).

Kaynakların her biri kendi satırında sonra kaynaklarından oluşturulan çıkış dosyaları listelenmelidir. Tüm dosya adları, tam yolu olmalıdır.

Bir ek kaynak dosyasının Örneğin, bir basit ConsoleApplication projesi *Class1.cpp*, *link.write.1.tlog* dosyası içerebilir:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Tasarım zamanı derleme

IDE'de, .vcxproj proje MSBuild hedefleri birtakım projeden ek bilgi almak için çıkış dosyalarının yeniden oluşturmak için kullanır. Bu hedefler bazıları yalnızca tasarım zamanı yapılarında kullanılır, ancak bunların çoğu, düzenli yapılar hem tasarım zamanı derlemeleri de kullanılır.

CPS belgeleri için tasarım zamanı derlemeleri hakkında genel bilgi için bkz. [tasarım zamanı derlemeleri](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Bu belgeleri yalnızca kısmen Visual C++ projeleri için geçerlidir.

`CompileDesignTime` Ve `Compile` tasarım zamanında belirtilen hedefleri için .vcxproj proje çalıştırılmadı belgeleri oluşturur. Visual C++ .vcxproj projeleri farklı tasarım zamanı hedef IntelliSense bilgilerini almak için kullanın.

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense bilgisi için tasarım zamanı hedefleri

.Vcxproj projelerinde kullanılan tasarım zamanı hedef tanımlanan `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

`GetClCommandLines` Target derleyici seçenekleri IntelliSense toplar:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – Tasarım zamanı başlatma için tasarım zamanı gereken hedefleri, yapı yalnızca. Diğerlerinin yanı sıra bu hedefler performansını artırmak için normal yapı işlevselliğinde bazı devre dışı bırakın.

- `ComputeCompileInputsTargets` – derleyici seçenekleri ve öğeleri değiştiren bir dizi hedefler. Tasarım zamanı hem normal yapılarda bu hedefleri çalıştırın.

Hedef çağrıları `CLCommandLine` IntelliSense için kullanılacak komut satırını oluşturmak için görev. Yeniden adını rağmen CL seçenekleri ancak yalnızca Clang ve gcc seçeneği de başa çıkabilir. Derleyici anahtarları türü tarafından denetlenir `ClangMode` özelliği.

Şu anda, komut satırı tarafından üretilen `CLCommandLine` görev her zaman kullanan CL anahtarları (hatta Clang modunda) ayrıştırmak IntelliSense altyapısı için daha kolay olduğundan.

Normal veya tasarım zamanı çalışmadan önce derleme sonu gelmez emin olun bir hedef ekliyorsanız tasarım zamanı derlemeleri veya performansını etkiler. Bir geliştirici komut istemi açın ve bu komutu çalıştırmak için en basit yolu, hedef test verilmiştir:

> MSBuild /p:SolutionDir =*çözüm-directory-ile-sondaki-ters eğik çizgi*; Yapılandırma hata ayıklama; = Platform Win32; = BuildingInsideVisualStudio = true; DesignTimebuild = true/t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj

Bu komutu bir ayrıntılı yapı günlüğüne üretir *msbuild.log*, sonunda bir performans hedefleri ve görevleri için Özet sahip.

Kullandığınızdan emin olun `Condition ="'$(DesignTimeBuild)' != 'true'"` yalnızca normal yapılarda ve tasarım zamanı derlemeleri için anlamlı tüm işlemlerde.

### <a name="design-time-targets-that-generate-sources"></a>Kaynakları oluşturan tasarım zamanı hedefleri

*Bu özellik, yerel Masaüstü projeleri için varsayılan olarak devre dışıdır ve önbelleğe alınan projeler üzerinde şu anda desteklenmeyen*.

Varsa `GeneratorTarget` meta verileri bir proje öğesi için tanımlanan, hedef hem de otomatik olarak çalıştırılan projeyi ne zaman yüklendiği ve kaynak dosya değiştirildiğinde.

Örneğin, .cpp veya .h otomatik olarak oluşturacak şekilde dosyaları .xaml dosyalarını, `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* dosyaları bu tanımlama Varlıklar:

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Kullanılacak `Task.HostObject` kaydedilmemiş kaynak dosyaların içeriğini almak için hedef ve görev olarak kaydedilmelidir [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) belirli bir pkgdef projeleri için:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual Studio IDE, Visual C++ proje genişletilebilirliği

Visual C++ proje sistemi dayanır [VS proje sistemi](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)ve onun genişletilebilirlik noktaları kullanır. Ancak, proje hiyerarşisi uygulama Visual C++'a özgüdür ve CPS alarak değil, bu nedenle hiyerarşi genişletilebilirlik proje öğeleri için sınırlıdır.

### <a name="project-property-pages"></a>Proje özellik sayfaları

Genel tasarım bilgileri için bkz. [Platform genişletilebilirliği - 1. bölüm](https://blogs.msdn.microsoft.com/vsproject/2009/06/09/platform-extensibility-part-1/) ve [Platform genişletilebilirliği - 2. bölüm](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/).

Basit bir deyişle, özellik sayfaları gördüğünüz **proje özellikleri** iletişim kutusu için bir C++ projesi tarafından tanımlanan *kural* dosyaları. Bir kural dosyası bir özellik sayfasında göster ve nasıl ve bunlar projede kaydedileceği dosya için özellikler kümesini belirtir. Kural, Xaml biçimini kullanan .xml dosyaları dosyalarıdır. Bunları serileştirmek için kullanılan türleri açıklanan [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Kural proje dosyalarında kullanımı hakkında daha fazla bilgi için bkz. [özellik sayfası XML kural dosyaları](/cpp/ide/property-page-xml-files).

Kural dosyaları eklenmeli `PropertyPageSchema` öğesi grubu:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` meta verileri de kural türü tarafından denetlenir ve şu değerlerden biri olabilir kuralı görünürlük sınırları:

> `Project` | `File` | `PropertySheet`

CPS, içerik türü için diğer değerleri destekler, ancak bunlar Visual C++ projelerinde kullanılmaz.

Kural birden fazla bağlamda görünür olmalıdır, noktalı virgül kullanın. (**;**) burada gösterildiği gibi bağlam değerlerini ayırmak için:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Kural biçimi ve ana türleri

Kural biçimi doğrudan olduğundan bu bölüm, yalnızca kural kullanıcı arabiriminin nasıl göründüğünü etkiler öznitelikleri açıklar.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate` Özniteliği, kural nasıl görüntüleneceğini tanımlar **özellik sayfaları** iletişim. Özniteliği şu değerlerden biri olabilir:


| Öznitelik | Açıklama |
|------------| - |
| `generic` | Tüm özelliklerini kategoriye başlıklar altında tek bir sayfada gösterilir<br/>Kural için görünür `Project` ve `PropertySheet` bağlamı, ama `File`.<br/><br/> Örnek: `$(VCTargetsPath)` \\ *1033*\\*general.xml* |
| `tool` | Kategoriler, alt gösterilir.<br/>Kural tüm bağlamlarda görüntülenebilir: `Project`, `PropertySheet` ve `File`.<br/>Yalnızca proje öğeleriyle varsa kural proje özelliklerinde görülebilir `ItemType` tanımlanan `Rule.DataSource`kural adı dahil sürece `ProjectTools` öğesi grubu.<br/><br/>Örnek: `$(VCTargetsPath)` \\ *1033*\\*clang.xml* |
| `debugger` | Sayfanın hata ayıklama sayfası bir parçası olarak gösterilir.<br/>Kategorileri şu anda göz ardı edilir.<br/>Kural adı hata ayıklama başlatıcısı MEF nesnenin eşleşmelidir `ExportDebugger` özniteliği.<br/><br/>Örnek: `$(VCTargetsPath)` \\ *1033*\\*hata ayıklayıcı\_yerel\_windows.xml* |
| *custom* | Özel bir şablon. Şablon adı eşleşmelidir `ExportPropertyPageUIFactoryProvider` özniteliği `PropertyPageUIFactoryProvider` MEF nesne. Bkz: **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Örnek: `$(VCTargetsPath)` \\ *1033*\\*userMacros.xml* |

Kural özellik kılavuzunda tabanlı şablonlardan birini kullanıyorsa, bu genişletilebilirlik noktaları için özelliklerini kullanabilirsiniz:

- [Özellik değeri düzenleyicileri](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dinamik sabit listesi değerleri sağlayıcısı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Bir kural genişletme

Mevcut bir kuralı kullanabilirsiniz, ancak eklemek veya kaldırmak gerekir (yani Gizle) istiyorsanız birkaç özelliği, oluşturduğunuz bir [uzantısı kuralı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Bir kuralı geçersiz kıl

Belki de, araç takımı proje varsayılan kuralları çoğunu kullanmak için ancak yalnızca bir veya birkaç tanesi değiştirmek için istediğiniz. Örneğin, yalnızca farklı derleyici anahtarları göstermek için C/C++ kuralını değiştirmek istediğinizi varsayalım. Aynı ada sahip yeni bir kural sağlayın ve var olan bir kural olarak görünen adı ve olmasını `PropertyPageSchema` varsayılan cpp hedefler içe sonra öğesi grubu. Projede kullanılan belirli bir ada sahip yalnızca bir kural ve sonuncu içine dahil `PropertyPageSchema` grubu WINS öğesi.

#### <a name="project-items"></a>Proje öğeleri

*ProjectItemsSchema.xml* dosyası tanımlar `ContentType` ve `ItemType` proje öğeleri kabul edilir öğeleri için değerler ve tanımlar `FileExtension` yeni bir dosya eklendiğinde hangi öğe grubunu belirlemek için öğeleri.

Varsayılan ProjectItemsSchema dosya bulunan `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*. Genişletmek için bir şema dosyası yeni bir adla gibi oluşturmalısınız *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Ardından hedefleri dosyasına ekleyin:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Örnek: `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Hata ayıklayıcılar

Visual Studio'da hata ayıklama hizmeti için hata ayıklama altyapısı genişletilebilirliği destekler. Daha fazla bilgi için bu örnekler bakın:

- [MIEngine, hata ayıklama lldb destekleyen açık kaynaklı proje](https://github.com/Microsoft/MIEngine)

- [Visual Studio hata ayıklama altyapısı örneği](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Hata ayıklama oturumu için hata ayıklama altyapıları ve diğer özellikleri belirtmek için uygulamanız gereken bir [hata ayıklama başlatıcısı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) MEF Bileşeni ve bir `debugger` kuralı. Bir örnek için bkz. `$(VCTargetsPath)` \\1033\\hata ayıklayıcı\_yerel\_windows.xml dosya.

### <a name="deploy"></a>Dağıt

.vcxproj proje kullanmak için Visual Studio Proje sistemi genişletilebilirlik [dağıtma sağlayıcıları](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Güncellik denetimi oluşturma

Varsayılan olarak oluşturulması için okuma .tlog ve yazma .tlog dosyaları derleme güncellik denetimi gerektirir `$(TlogLocation)` tüm yapı girişleri ve çıkışları için derleme sırasında klasör.

Özel bir güncellik denetimi kullanmak için:

1. Ekleyerek varsayılan güncellik denetimi devre dışı `NoVCDefaultBuildUpToDateCheckProvider` özelliği *Toolset.targets* dosyası:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Kendi uygulama [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Proje yükseltme

### <a name="default-vcxproj-project-upgrader"></a>Varsayılan .vcxproj proje Yükseltici

Varsayılan .vcxproj proje Yükseltici değişiklikleri `PlatformToolset`, `ApplicationTypeRevision`, MSBuild araç takımı sürümü ve .net framework. Son iki Visual Studio sürümü varsayılan olarak her zaman değişir ancak `PlatformToolset` ve `ApplicationTypeRevision` özel MSBuild özellikleri tarafından denetlenebilir.

Yükseltici, bir proje veya yükseltilebilir olup olmadığını karar vermek için aşağıdaki ölçütleri kullanır:

1. Tanımlama projeleri için `ApplicationType` ve `ApplicationTypeRevision`, mevcut olandan daha yüksek bir düzeltme numarası ile bir klasör bulunur.

1. Özellik `_UpgradePlatformToolsetFor_<safe_toolset_name>` geçerli araç takımı için tanımlanır ve değeri geçerli bir araç takımı için eşit değil.

   Bu özellik adlarının  *\<safe_toolset_name >* bir alt çizgi yerine tüm alfasayısal olmayan karakterleri içeren bir araç takımı adı temsil eder (**\_**).

Bir proje yükseltilebilir, katıldığı *çözümü yeniden hedefleme*. Daha fazla bilgi için [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Proje adlarında adorn istiyorsanız **Çözüm Gezgini** projeleri, belirli bir araç kümesi kullandığınızda, tanımlamak bir `_PlatformToolsetShortNameFor_<safe_toolset_name>` özelliği.

Örnekler için `_UpgradePlatformToolsetFor_<safe_toolset_name>` ve `_PlatformToolsetShortNameFor_<safe_toolset_name>` özellik tanımları bkz *Microsoft.Cpp.Default.props* dosya. Kullanım örnekleri için bkz: `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* dosya.

### <a name="custom-project-upgrader"></a>Özel proje Yükseltici

Özel proje Yükseltici nesnesini kullanmak için bir MEF Bileşeni burada gösterildiği şekilde uygulayın:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Kodunuzu alabilir ve varsayılan .vcxproj Yükseltici nesne arayın:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` tanımlanan *Microsoft.VisualStudio.ProjectSystem.VS.dll* ve benzer `IVsRetargetProjectAsync`.

Tanımlama `VCProjectUpgraderObjectName` özelliği, özel Yükseltici nesnesini kullanmak için proje sistemi bildirmek için:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Proje yükseltme devre dışı bırak

Proje yükseltme devre dışı bırakmak için bir `NoUpgrade` değeri:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Proje önbelleği ve genişletilebilirlik

Visual Studio 2017, büyük C++ çözümlerle çalışırken performansı artırmak için [proje önbellek](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/) kullanıma sunulmuştur. Proje doldurulmuş ve ardından belleğe CPS ya da MSBuild projeleri yüklemeden projeleri yüklemek için kullanılan bir SQLite veritabanı olarak uygulanır.

CPS nesne önbellekten yüklendi .vcxproj projeler için mevcut olduğundan, bu uzantının MEF Bileşenleri alma `UnconfiguredProject` veya `ConfiguredProject` oluşturulamaz. Bir proje kullanır (kullanma olasılıkları olan ister) MEF uzantıları Visual Studio algıladığında genişletilebilirlik desteklemek için proje önbelleği kullanılmaz.

Bu proje türleri her zaman tam olarak yüklenir ve tüm MEF uzantıları için oluşturulacak şekilde CPS nesneler bellekte sahiptir:

- Başlangıç projeleri

- Diğer bir deyişle bir özel Proje Yükseltici olan projelerin tanımlarlar bir `VCProjectUpgraderObjectName` özelliği

- Windows Masaüstü, yani hedefleyen olmayan projeleri tanımlarlar bir `ApplicationType` özelliği

- Öğe projeleri (.vcxitems) ve tüm projelerin paylaşılan bu başvurusu .vcxitems projeleri tarafından aktarın.

Bu koşulların hiçbiri algılanırsa, bir proje önbelleği oluşturulur. Önbellek MSBuild Projesi yanıtlamak için gereken tüm verileri içeren `get` üzerinde sorgular `VCProjectEngine` arabirimleri. Bu MSBuild özellikler, tüm değişiklikleri anlamına gelir ve hedef dosya düzeyinde bir uzantısı tarafından yapılan önbellekten yüklendi projelerinde çalışmaya devam etmelidir.

## <a name="shipping-your-extension"></a>Uzantınızı aktarma

VSIX dosyaları oluşturma hakkında daha fazla bilgi için bkz: [sevkiyat Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md). Özel yükleme konumları için dosyaları ekleme, örneğin, altında dosyaları ekleme hakkında bilgi için `$(VCTargetsPath)`, bkz: [uzantılar klasörünün dışına yükleme](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Ek kaynaklar

Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) proje dosyaları için derleme altyapısı ve XML tabanlı Genişletilebilir biçimi sağlar. Tanımanız gerekir basic ile [MSBuild kavramları](../msbuild/msbuild-concepts.md) ile nasıl [Visual C++ için MSBuild](/cpp/build/msbuild-visual-cpp-overview) proje sistemi Visual C++ genişletebilmek için çalışır.

Yönetilen Genişletilebilirlik Çerçevesi ([MEF](/dotnet/framework/mef/)) uzantı CPS ve Visual C++ proje sistemi tarafından kullanılan API'ler sağlar. MEF CPS tarafından nasıl kullanıldığını genel bakış için bkz: [CPS ve MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) içinde [MEF VSProjectSystem bakış](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Derleme adımları veya yeni bir dosya türleri eklemek için var olan yapı sistemi özelleştirebilirsiniz. Daha fazla bilgi için [MSBuild (Visual C++) genel bakış](/cpp/build/msbuild-visual-cpp-overview) ve [Working with project properties](/cpp/ide/working-with-project-properties).
