---
title: Derleme sistemini özelleştirme
description: Bu makale MSBuild kısa bir giriş derleme sistemi Mac için Visual Studio tarafından kullanılan yöneliktir.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 7fbd275e3e946461559db41668a749cd6631ba09
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296313"
---
# <a name="customizing-the-build-system"></a>Derleme sistemini özelleştirme

MSbuild, Microsoft tarafından geliştirilen bir derleme, altyapısıdır, için öncelikle .NET uygulamalarının oluşturulmasını sağlar. Mono framework ayrıca Microsoft Build Engine çağrılır, kendi uygulaması olan **xbuild**. Ancak, xbuild tüm işletim sistemlerinde MSBuild kullanmak lehine aşamalı.

**MSbuild** öncelikle için yapı sistemi olarak Visual Studio'da projeler için Mac için kullanılır

MSBuild, kaynak dosyaları gibi girişler, bir dizi yararlanarak çalışır ve bunları çıktılarına, yürütülebilir dosyalar gibi dönüştürür. Bu çıkış, derleyici gibi araçların çağırarak ulaşır.

## <a name="msbuild-file"></a>MSBuild dosyası

MSBuild tanımlayan bir proje dosyası olarak da bilinen bir XML dosyası kullanır *öğeleri* (örneğin, resim kaynakları), projenizin bir parçası olan ve *özellikleri* projenizi yapılandırmak için gereklidir. Bu proje dosyası her zaman iki rakamla biten bir dosya uzantısına sahip olacaktır `proj`, gibi `.csproj` C# projeleri için.

### <a name="viewing-the-msbuild-file"></a>MSBuild dosyasını görüntüleme

MSBuild dosyası proje adınıza sağ tıklatıp seçerek bulun **Finder'da Göster**. Tüm dosya ve klasörler, projenizle ilgili Bulucu pencere görüntüler dahil olmak üzere `.csproj` aşağıdaki görüntüde gösterildiği gibi dosya:

![Finder csproj konumu](media/customizing-build-system-image1.png)

Görüntülenecek `.csproj` Mac için Visual Studio'da yeni bir sekmede, proje adınıza sağ tıklayın ve göz atın **Araçlar > Dosya Düzenle**:

![csproj Kaynak Düzenleyicisi'nde açma](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>MSBuild dosyası oluşturma

Zorunlu kök tüm MSBuild dosyaları içeren `Project` öğe, şu şekilde:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Genellikle, proje de içeri aktaracak bir `.targets` dosya. Bu dosya, çoğu ve çeşitli dosyaları derleme nasıl işleneceğini açıklayan kurallar içerir. İçeri aktarma, genellikle sonuna doğru görünür, `proj` dosya ve C# projeleri için şunun gibi bakın:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Hedef dosyanın başka bir MSBuild dosyasıdır. Bu dosya, birden fazla proje tarafından yeniden kullanılabilir MSBuild kod içerir. Örneğin, `Microsoft.CSharp.targets` tarafından temsil edilen bir dizinde bulunan dosya `MSBuildBinPath` özelliği (veya değişken) C# derlemeleri üzerinde C# kaynak dosyalarından oluşturmaya yönelik mantık içerir.

### <a name="items-and-properties"></a>Öğeleri ve özellikleri

Msbuild'de iki temel veri türü vardır: *öğeleri* ve *özellikleri*, hangi aşağıdaki bölümlerde daha ayrıntılı açıklanmıştır.

#### <a name="properties"></a>Özellikler

Özellikleri derleme, derleyici seçenekleri gibi etkileyen ayarları depolamak için kullanılan anahtar/değer çiftleridir.

Bunlar bir PropertyGroup kullanarak ayarlayın ve herhangi bir sayıda özellikler içerebilen PropertiesGroups herhangi bir sayıda içerebilir.

Örneğin, basit bir konsol uygulaması için PropertyGroup aşağıdaki XML gibi görünebilir:

```xml
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

Gelen ifadeleri kullanarak Özellikler başvuru yapılabilir `$()` söz dizimi. Örneğin, `$(Foo)` değeri olarak değerlendirilecek `Foo` özelliği. Özelliği ayarlı değil, herhangi bir hata olmadan boş bir dize olarak değerlendirir.

#### <a name="items"></a>Öğeler

Öğeleri listeler veya ayarlar yapı sistemine girdi uğraşmanızı bir yol sağlar ve genelde dosyaları temsil ederler. Her öğe bir öğe olan *türü*, öğeyi *spec*ve isteğe bağlı rastgele *meta verileri*. MSBuild, tek tek öğelere işletmek değil, tüm öğeleri üzerinde alan unutmayın bir öğenin türü adı verilen *ayarlayın*

Öğeleri bildirerek oluşturulan bir `ItemGroup`. Herhangi bir sayıda öğe içerebilir Itemgroups'un, herhangi bir sayıda olabilir.

Örneğin, aşağıdaki kod parçacığını başlatma ekranları iOS oluşturur. Başlatma ekranları yapı türüne sahip `BundleResource`, görüntü yolu olarak belirtimi ile:

```xml
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```

 Kümeleri gelen ifadeleri kullanarak başvurulabilen öğesi `@()` söz dizimi. Örneğin, `@(BundleResource)` BundleResource öğelerin tümünü anlamına gelir BundleResource öğesi kümesi değerlendirilir. Bu tür öğe varsa, herhangi bir hata boş olacaktır.

## <a name="resources-for-learning-msbuild"></a>MSBuild için kaynaklar

MSBuild hakkında daha ayrıntılı bilgi edinmek için aşağıdaki kaynakları kullanılabilir:

* [MSBuild'e genel bakış](/visualstudio/msbuild/msbuild)
* [MSBuild Kavramları](/visualstudio/msbuild/msbuild-concepts)
