---
title: "Nasıl yapılır: MSBuild projesi SDK 'sına başvurma | Microsoft Docs"
description: Özellikler ve hedeflerin içeri aktarılmasını gerektiren yazılım geliştirme setlerini kullanmayı basitleştirmek için MSBuild proje SDK 'larını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6303efce016a9e678e4c9e8aa62c91aa116e44f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914227"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Nasıl yapılır: MSBuild proje SDK 'larını kullanma

MSBuild 15,0, özellik ve hedeflerin içeri aktarılmasını gerektiren yazılım geliştirme setleri kullanımını kolaylaştıran "proje SDK" kavramını sunmuştur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Proje değerlendirmesi sırasında MSBuild, proje dosyasının en üstünde ve altında örtük içeri aktarmalar ekler:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Proje SDK 'Sı başvurusu

Proje SDK 'sına başvurmak için üç yol vardır:

- `Sdk`Öğesindeki özniteliğini kullanın `<Project/>` :

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Daha önce anlatıldığı gibi projenin üst ve alt kısmına örtük bir içeri aktarma eklenir.
    
    SDK 'nın belirli bir sürümünü belirtmek için, `Sdk` özniteliğe ekleyin:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- En üst düzey öğeyi kullanın `<Sdk/>` :

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Daha önce anlatıldığı gibi projenin üst ve alt kısmına örtük bir içeri aktarma eklenir.
   
   `Version`Öznitelik gerekli değil.

- `<Import/>`Öğesini projenizde herhangi bir yerde kullanın:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   İçeri aktarmaların projenize açıkça dahil edilmesi, sipariş üzerinde tam denetim sağlar.

   `<Import/>`Öğesini kullanırken, isteğe bağlı bir `Version` özniteliği de belirtebilirsiniz. Örneğin, belirtebilirsiniz `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />` .

## <a name="how-project-sdks-are-resolved"></a>Proje SDK 'Ları nasıl çözümlenir

İçeri aktarma değerlendirilirken, MSBuild, belirtilen adı ve sürümü temel alarak proje SDK 'sının yolunu dinamik olarak çözer.  MSBuild Ayrıca, makinenizde proje SDK 'larını belirleyen eklentiler olan kayıtlı SDK çözümleyicilerine sahiptir. Bu eklentiler şunları içerir:

- Belirttiğiniz SDK 'nın KIMLIĞI ve sürümüyle eşleşen NuGet paketleri için yapılandırılmış paket akışlarınızı sorgulayan bir NuGet tabanlı çözümleyici.

   Bu çözümleyici yalnızca isteğe bağlı bir sürüm belirttiyseniz etkindir. Bu, herhangi bir özel proje SDK 'Sı için kullanılabilir.
   
- [.NET SDK](/dotnet/core/sdk/)Ile yüklenen MSBuild SDK 'larını çözen BIR .NET SDK Çözümleyicisi.

   Bu çözümleyici, `Microsoft.NET.Sdk` ürününün bir parçası olan ve gibi proje SDK 'larını bulur `Microsoft.NET.Sdk.Web` .
   
- MSBuild ile yüklenen SDK 'Ları çözen varsayılan çözümleyici.

NuGet tabanlı SDK Çözümleyicisi, proje SDK sürümünü her bir proje yerine tek bir yerde denetlemenize olanak tanıyan [global.js](/dotnet/core/tools/global-json) dosyadaki bir sürümü belirtmeyi destekler:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Bir derleme sırasında her bir proje SDK 'sının yalnızca bir sürümü kullanılabilir. Aynı proje SDK 'sının iki farklı sürümüne başvurdıysanız, MSBuild bir uyarı yayar. *global.js* dosyadaki bir sürüm belirtilmişse, projelerinizde bir sürüm **belirtmemelidir** .

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Derlemenizi özelleştirme](../msbuild/customize-your-build.md)
- [Paketler, meta veriler ve çerçeveler](/dotnet/core/packages)
- [.NET Core için csproj biçimine eklemeler](/dotnet/core/tools/csproj)
