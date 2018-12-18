---
title: Özellik işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a238e0bb35efd3ddf984a692a032535c37dfd88
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468705"
---
# <a name="property-functions"></a>Özellik işlevleri

.NET Framework sürüm 4 ve 4.5, MSBuild komut değerlendirilecek özellik işlevleri kullanılabilir. Özellik işlevleri özellikleri görünür her yerde kullanılabilir. Görevleri farklı özellik işlevleri hedefleri dışında kullanılabilir ve tüm hedef çalışmadan önce değerlendirilir.

 MSBuild görevlerini kullanmadan, sistem saatini okuyabilir, dizeleri karşılaştırmak, normal ifadeleri eşleştirebilir ve derleme betiğinizin diğer eylemleri gerçekleştirin. MSBuild, dize ve numarası dizeye Dönüştür ve gerektiği gibi diğer dönüştürme yapmak çalışacaktır.

## <a name="property-function-syntax"></a>Özellik işlevi sözdizimi

Özellik işlevleri üç tür şunlardır; Her işlev, farklı bir sözdizimi vardır:

- Dize (örnek) özellik işlevleri
- Statik özellik işlevleri
- MSBuild özellik işlevleri

### <a name="string-property-functions"></a>Dize özelliği işlevleri

Tüm yapı özelliği yalnızca dize değerleri değerlerdir. Herhangi bir özelliğin üzerinde çalışılacak dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam yolu temsil eden bir yapı özelliğinden sürücü adı (ilk üç karakter) ayıklayın:

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Statik özellik işlevleri

Derleme betiğinizin statik özelliklerine ve birçok sistem sınıfının yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın burada \<sınıfı > Sistem sınıf adıdır ve \<özellik > özelliği adıdır.

```fundamental
$([Class]::Property)
```

Örneğin, geçerli tarih ve saat için bir yapı özelliğini ayarlamak için aşağıdaki kodu kullanın.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Statik bir yöntemi çağırmak için aşağıdaki sözdizimini kullanın burada \<sınıfı > sistem sınıfı adı \<yöntemi > yöntemi adıdır ve (\<Parametreler >) yöntemi için parametre listesi:

```fundamental
$([Class]::Method(Parameters))
```

Örneğin, yeni bir GUID ile bir yapı özelliğini ayarlamak için bu betiği kullanabilirsiniz:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Statik özelliği işlevleri'nde herhangi bir statik yöntem veya özellik bu sistem sınıfların kullanabilirsiniz:

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.String
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Ayrıca, aşağıdaki statik yöntemleri ve özellikleri kullanabilirsiniz:

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Statik özellikler üzerinde örnek yöntemleri çağırma

Bir nesne örneğini döndüren statik özelliğe erişirse, o nesnenin örnek yöntemler çağırabilirsiniz. Bir örnek yöntemi çağırmak için aşağıdaki sözdizimini kullanın burada \<sınıfı > sistem sınıfı adı \<özellik > özellik adı \<yöntemi > yöntemi adıdır ve (\<parametreleri >) yöntemi için parametre listesi verilmiştir:

```fundamental
$([Class]::Property.Method(Parameters))
```

Sınıfın adı, ad alanı ile tam olarak nitelenmiş olmalıdır.

Örneğin, geçerli tarihi bugün bir yapı özelliğini ayarlamak için aşağıdaki kodu kullanın.

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild özellik işlevleri

Aritmetik, bit düzeyinde sağlamak için derleme çeşitli statik yöntemler erişilebilir mantıksal ve kaçış karakteri desteği. Aşağıdaki söz dizimini kullanarak bu yöntemlere erişmek burada \<yöntemi > yöntemi adıdır ve (\<Parametreler >) yöntemi için parametre listesi.

```fundamental
$([MSBuild]::Method(Parameters))
```

Örneğin, birlikte sayısal değerlere sahip iki özellik eklemek için aşağıdaki kodu kullanın.

```fundamental
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

MSBuild özellik işlevlerin bir listesi aşağıda verilmiştir:

|İşlev imzası|Açıklama|
|------------------------|-----------------|
|çift (double double b) Ekle|İki çiftten ekleyin.|
|uzun süre (uzun uzun a, b) Ekle|İki Integer ekleyin.|
|çift (double double b) çıkarma|İki çiftten çıkarın.|
|uzun süre (uzun uzun a, b) çıkarma|İki Integer çıkarın.|
|çift (double double b) çarpın.|İki çiftten çarpın.|
|uzun süre (uzun uzun b) çarpın.|İki Integer çarpın.|
|çift (double double b) Böl|İki çiftten bölün.|
|uzun süre (uzun uzun b) Böl|İki Integer bölün.|
|çift (double double b) mod|İki çiftten.|
|uzun süre (uzun uzun b)|İki Integer.|
|dize Escape(string unescaped)|MSBuild kaçış kurallara göre dize çıkış.|
|Unescape (Atlanan dizesini) dize|MSBuild kaçış kurallara göre dize unescape.|
|int BitwiseOr (int ilk, int saniye)|Bit düzeyinde gerçekleştirmek `OR` ilk ve ikinci (ilk &#124; ikinci).|
|int BitwiseAnd (int ilk, int saniye)|Bit düzeyinde gerçekleştirmek `AND` ilk ve (ilk ve ikinci) saniye.|
|int BitwiseXor (int ilk, int saniye)|Bit düzeyinde gerçekleştirmek `XOR` ilk ve ikinci (ilk ^ ikinci).|
|int BitwiseNot(int first)|Bit düzeyinde gerçekleştirmek `NOT` (~ ilk).|
|bool IsOsPlatform (dize platformString)|Geçerli işletim sistemi platformu olup olmadığını belirtin `platformString`. `platformString` bir üyesi olmanız gerekir <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike|Geçerli işletim sistemi bir Unix sistem geçerlidir.|
|dize NormalizePath (yol parametreleri dize [])|Sağlanan yol Kurallaştırılan tam yolunu alır ve geçerli işletim sistemi için doğru dizin Ayırıcı karakterler içerdiği sağlar.|
|dize NormalizeDirectory (yol parametreleri dize [])|Sağlanan dizin Kurallaştırılan tam yolunu alır ve doğru dizin ayırıcı karakterleri geçerli içerdiği sağlar sağlarken, işletim sistemi sonunda eğik çizgi içeriyor.|
|dize EnsureTrailingSlash(string path)|Belirtilen yolla bir ekleme sonunda bir eğik çizgi yoksa. Yol boş bir dize ise, bunu değiştirmez.|
|dize GetPathOfFileAbove (dize dosya, dize startingDirectory)|Bir dosyayı arar geçerli derleme dosyanın konumuna göre veya temel `startingDirectory`, belirtilmişse.|
|GetDirectoryNameOfFileAbove (dize startingDirectory, dize dosya adı)|Belirtilen dizin veya bu dizinin üzerindeki dizin yapısı bir konumda bir dosyasını bulun.|
|Makerelatıve (dize basePath, dize yolu) dize|Yapar `path` göreli `basePath`. `basePath` mutlak bir dizin olmalıdır. Varsa `path` olamaz göreli yapılmadı, bu harfi harfine döndürülür. Benzer şekilde `Uri.MakeRelativeUri`.|
|dize ValueOrDefault (dize conditionValue, dize defaultValue)|Yalnızca parametre 'conditionValue' else boşsa, dize 'defaultValue' parametresinde döndürür, değer conditionValue dönün.|

##  <a name="nested-property-functions"></a>İç içe özellik işlevleri

Özellik işlevleri aşağıdaki örnekte gösterildiği gibi daha karmaşık, işlev forma birleştirebilirsiniz.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnekte değerini döndürür <xref:System.IO.FileAttributes> `Archive` bit (32 ya da 0) yolu tarafından belirtilen dosyanın `tempFile`. Numaralandırılmış veri değerlerini özelliği işlevlerdeki adıyla görünemez dikkat edin. Sayısal değer (32) bunun yerine kullanılmalıdır.

Meta veri özellik iç içe geçmiş işlevlerde de görünebilir. Daha fazla bilgi için [toplu işleme](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

`DoesTaskHostExist` MSBuild özelliği işlevinde bir görev ana bilgisayarı için belirtilen çalışma zamanı ve mimari değerleri yüklü olup olmadığını döndürür.

Bu özellik işlev sözdizimi aşağıdaki gibidir:

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

`EnsureTrailingSlash` MSBuild özelliği işlevinde zaten yoksa sonunda eğik çizgi ekler.

Bu özellik işlev sözdizimi aşağıdaki gibidir:

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` özelliği işlevi, bir dosya yolunda geçerli dizinin üzerindeki dizinlerde arar.

 Bu özellik işlev sözdizimi aşağıdaki gibidir:

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Aşağıdaki kod, bu sözdizimini örneğidir.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

`GetPathOfFileAbove` MSBuild özelliği işlevinde bunu hemen önceki dosyasının yolunu döndürür. Arama için işlevsel olarak eşdeğerdir

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Bu özellik işlev sözdizimi aşağıdaki gibidir:

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` özelliği işlevi bir kayıt defteri anahtarı değerini döndürür. Bu işlev, iki bağımsız değişkeni, anahtar adı ve değeri adını alır ve kayıt defterinden değeri döndürür. Değer adı belirtmezseniz, varsayılan değer döndürülür.

Aşağıdaki örnekler, bu işlevin nasıl kullanıldığını açıklar:

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` özelliği işlevi alır sistem kayıt defteri verilerini verilen kayıt defteri anahtarı, değer ve bir veya daha fazla kayıt görünümleri sıralı. Bunlar bulunmayana kadar sırayla her bir kayıt defteri görünümü'nde anahtar ve değer aranır.

Bu özelliği işlevi için sözdizimi aşağıdaki gibidir:

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bit işletim sistemi tutan bir **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node** sunan kayıt defteri anahtarı bir **HKEY_LOCAL_MACHINE\SOFTWARE** 32-bit uygulamalar için kayıt defteri görünümü.

Varsayılan olarak, 32 bitlik bir uygulama WOW64 üzerinde çalışan 32-bit kayıt defteri görünümü erişir ve 64 bitlik bir uygulama 64-bit kayıt defteri görünümü erişir.

Aşağıdaki kayıt defteri görünümleri kullanılabilir:

|Kayıt defteri görünümü|Tanım|
|-------------------|----------------|
|RegistryView.Registry32|32 bit uygulama kayıt defteri görünümü.|
|RegistryView.Registry64|Uygulama 64-bit kayıt defteri görünümü.|
|RegistryView.Default|Uygulamanın üzerinde çalıştığı işlem eşleşen kayıt defteri görünümü.|

Bir örnek verilmiştir.

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

alır **SLRuntimeInstallPath** verilerin **Referenceassembly'ler** anahtarı, 64-bit kayıt defteri görünümü ve ardından 32-bit kayıt defteri görünümü ilk aranıyor.

## <a name="msbuild-makerelative"></a>MSBuild Makerelatıve

MSBuild `MakeRelative` özelliği işlevi ilk yol göreli ikinci yol göreli yolunu döndürür. Her yol, dosya veya klasör olabilir.

Bu özellik işlev sözdizimi aşağıdaki gibidir:

```fundamental
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Aşağıdaki kod, bu sözdizimini örneğidir.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

MSBuild `ValueOrDefault` özelliği işlevi, null veya boş değilse ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boş ise, işlev, ikinci bağımsız değişkeni döndürür.

Aşağıdaki örnek, bu işlevin nasıl kullanıldığını gösterir.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="see-also"></a>Ayrıca bkz.

[MSBuild özellikleri](../msbuild/msbuild-properties.md)

[MSBuild'e genel bakış](../msbuild/msbuild.md)
