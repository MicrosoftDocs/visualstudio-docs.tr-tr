---
title: Derlemenizi özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31856366712da0a2287f73906c6e3a5f81f63a00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857594"
---
# <a name="customize-your-build"></a>Derlemenizi özelleştirme

Standart MSBuild projelerinin yapı işlemi (içeri aktarma *Microsoft.Common.props* ve *Microsoft.Common.targets*) derleme özelleştirmek için kullanabileceğiniz çeşitli genişletilebilirlik kancaları sahip işlem.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Projeniz için komut satırı MSBuild çağrılarına bağımsız değişkenlerini ekleyin

A *Directory.Build.rsp* ya da üzeri kaynak dizin dosyası projenizin komut satırı derlemeleri için uygulanır. Ayrıntılar için bkz [MSBuild yanıt dosyaları](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props ve Directory.Build.targets

MSBuild 15 sürümü önce çözümünüzdeki projelerine yeni, özel bir özellik sağlamak isterseniz bu özellik bir başvuru çözümdeki her proje dosyasında el ile ekleyin gerekiyordu. Ya da özelliği tanımlamak olan bir *.props* dosya ve açıkça alma *.props* çözümdeki diğer özelliklerin yanı sıra her bir proje dosyasında.

Bununla birlikte, artık yeni bir özellik tek bir adımda her proje için bir tek dosyalı çağrılan içinde tanımlayarak ekleyebilirsiniz *Directory.Build.props* kaynağınızı içeren kök klasörü içinde. MSBuild çalıştığında *Microsoft.Common.props* dizin yapınızı arar *Directory.Build.props* dosyası (ve *Microsoft.Common.targets* arar *Directory.Build.targets*). Bulursa, özelliği alır. *Directory.Build.props* özelleştirmeleri bir dizin altında projelerine sağlayan kullanıcı tanımlı bir dosya.

> [!NOTE]
> Linux tabanlı bir dosya sistemi büyük/küçük harfe duyarlıdır. Büyük/küçük harf Directory.Build.props adının tam olarak eşleşen emin olun veya derleme işlemi sırasında algılanmaz.
>
> Bkz: [bu GitHub sorunu](https://github.com/dotnet/core/issues/1991#issue-368441031) daha fazla bilgi için.

### <a name="directorybuildprops-example"></a>Directory.Build.props örneği

Örneğin, tüm projelerinizi yeni Roslyn erişmek için etkinleştirmek istiyorsanız **/ deterministic** özelliği (Roslyn içinde sunulan `CoreCompile` hedef özelliği tarafından `$(Deterministic)`), aşağıdakileri yapabilirsiniz.

1. Adlı deponuzun kök dizininde yeni bir dosya oluşturun *Directory.Build.props*.
2. Aşağıdaki XML dosyasına ekleyin.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```
3. MSBuild Çalıştır. Projenizin mevcut aktarımlarının *Microsoft.Common.props* ve *Microsoft.Common.targets* dosyasını bulun ve içe aktarın.

### <a name="search-scope"></a>Arama kapsamı

Aranırken bir *Directory.Build.props* dosya, MSBuild gezer dizin yapısı yukarı doğru proje konumunuzdan (`$(MSBuildProjectFullPath)`), bunu bulduktan sonra durduruluyor bir *Directory.Build.props* dosya. Örneğin, varsa, `$(MSBuildProjectFullPath)` olduğu *c:\users\username\code\test\case1*MSBuild var. arama başlangıç ve ardından arama dizin yapısı yukarı kadar bulunan bir *Directory.Build.props* aşağıdaki dizin yapısını olduğu gibi bir dosya.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Çözüm dosyasının konumunu ilgisizdir *Directory.Build.props*.

### <a name="import-order"></a>İçeri aktarma sırası

*Directory.Build.props* uygulamasında çok erken alınan *Microsoft.Common.props*, ve daha sonra tanımlanmış özellikler için kullanılamaz. Bu nedenle, henüz tanımlanmamış (ve boş olarak değerlendirmek) özellikleri için söz konusu kaçının.

*Directory.Build.targets* öğesinden alınan *Microsoft.Common.targets* içeri aktardıktan sonra *.targets* NuGet paketlerini dosyaları. Bu nedenle, özellikleri ve yapı mantığı çoğunu tanımlanmış hedefleri geçersiz kılabilirsiniz ancak bazen son içeri aktardıktan sonra proje dosyasını özelleştirmeniz gerekebilir.

### <a name="use-case-multi-level-merging"></a>Kullanım örneği: çok düzeyli birleştirme

Bu standart çözüm yapı olduğunu varsayalım:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Ortak özellikler tüm projeler için etmesi olabilir *(1)*, ortak özellikler için *src* projeleri *(2-src)* ve ortak özelliklerini  *Test* projeleri *(2-test)*.

Doğru "İç" dosyaları birleştirme MSBuild yapmak (*2 src* ve *2 test*) "dış" dosyasıyla (*1*), bir kez MSBuild bir bulduğunudikkatealmanızgerekir*Directory.Build.props* dosyasını durdurur daha ayrıntılı tarama. Taramaya devam etmek ve dış dosyaya birleştirmek için bu kodu her iki iç dosyalarına yerleştirin:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild'ın genel yaklaşım özetini aşağıdaki gibidir:

- Verilen herhangi bir proje için MSBuild ilk bulur *Directory.Build.props* yukarı isteğe bağlı olarak çözüm yapısında varsayılanlar ile birleştirir ve daha fazla bilgi için taramayı durdurur
- Bulundu ve ardından, birleştirilen için birden çok düzeyi isteyip istemediğinizi [ `<Import...>` ](../msbuild/property-functions.md#msbuild-getpathoffileabove) (yukarıda gösterilmiştir) "dış" dosya "İç" dosyasından
- "Dış" dosyasının kendisi varsa, üzerinde bir şey de içe, ardından tarama var. durdurur
- Tarama/birleştirme işlemini denetlemek için kullanmak `$(DirectoryBuildPropsPath)` ve `$(ImportDirectoryBuildProps)`

Ya da daha basit: ilk *Directory.Build.props* herhangi bir şey içe aktarmaz olduğu yere MSBuild durdurur.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Varsayılan olarak, *Microsoft.Common.props* aktarır `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` ve *Microsoft.Common.targets* aktarır `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Varsayılan değer olan `MSBuildProjectExtensionsPath` olduğu `$(BaseIntermediateOutputPath)`, `obj/`. NuGet paketleri ile sunulan mantıksal yapı başvurmak için bu mekanizma kullanır; diğer bir deyişle, geri yükleme sırasında oluşturduğu `{project}.nuget.g.props` paket içeriğini başvuran dosyaları.

Özelliğini ayarlayarak bu genişletilebilirlik mekanizması devre dışı bırakabilirsiniz `ImportProjectExtensionProps` için `false` içinde bir *Directory.Build.props* veya içeri aktarmadan önce *Microsoft.Common.props*.

> [!NOTE]
> MSBuildProjectExtensionsPath içeri aktarmalar devre dışı bırakma, projenize uygulanmasından NuGet paketleri gelen derleme mantığını engeller. NuGet paketlerinden bazıları işlevleri gerçekleştirmek için bir derleme mantık gerektirir ve bu devre dışı bırakıldığında gereksiz işlenir.

## <a name="user-file"></a>.user dosyasını

*Microsoft.Common.CurrentVersion.targets* aktarır `$(MSBuildProjectFullPath).user` yanındaki projenize ek uzantıya sahip bir dosya oluşturmak için mevcut değilse. Gelecekteki maintainers, bu uzantı mekanizması hakkında bilmeniz gerekmez. böylece uzun vadeli değişiklikler kaynak denetimine iade planladığınız için projenin kendi değiştirme tercih eder.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath ve MSBuildUserExtensionsPath

> [!WARNING]
> Bu uzantı mekanizmalarını kullanarak, makineler arasında yinelenebilir derlemeleri almak zorlaştırır. Kaynak Denetim sisteminize işaretli ve temelinizin tüm geliştiricileri arasında paylaşılan bir yapılandırması kullanmayı deneyin.

Kural gereği, birçok derleme mantığını dosyaları içeri aktarma çekirdek

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

önce bunların içeriğini ve

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Daha sonra. Bu derleme mantığının ortak proje türleri genişletmek yüklenmiş SDK'ları sağlar.

Aynı dizin yapısını içinde aranması `$(MSBuildUserExtensionsPath)`, kullanıcı başına klasör *%LOCALAPPDATA%\Microsoft\MSBuild*. Bu kullanıcının kimlik bilgileri altında çalışıyor ilgili proje türünün tüm derlemeler için bu klasöre yerleştirilen dosyaları içeri aktarılır. İçeri aktarma dosyası deseninde sonra adlı özelliklerini ayarlayarak kullanıcı uzantılarını devre dışı bırakabilirsiniz `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Örneğin, ayarlamak `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` için `false` alma önleyen `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Çözüm yapı özelleştirme

> [!IMPORTANT]
> Çözüm yapı bu şekilde özelleştirme yalnızca için komut satırı yapılarıyla birlikte geçerlidir *MSBuild.exe*. Bunu **yok** Visual Studio içindeki derlemeler için geçerlidir.

MSBuild bir çözüm dosyası oluşturduğunda, önce bir proje dosyasının dahili olarak çeviren ve, oluşturur. Oluşturulan proje dosyasını içeri aktarır `before.{solutionname}.sln.targets` önce tüm aracıların tanımlama ve `after.{solutionname}.sln.targets` hedefleri için yüklü hedefleri içeri aktardıktan sonra dahil olmak üzere `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` ve `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` dizinleri.

Örneğin, derlemeden sonra özel günlük ileti yazmak için yeni bir hedef tanımlayabilirsiniz *MyCustomizedSolution.sln* aynı dizinde adlı bir dosya oluşturarak *sonra. MyCustomizedSolution.sln.targets* içeren

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

[MSBuild kavramları](../msbuild/msbuild-concepts.md)

[MSBuild başvurusu](../msbuild/msbuild-reference.md)
