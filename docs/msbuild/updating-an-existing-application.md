---
title: MSBuild 15 mevcut bir uygulamayı güncelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4da159ae0fcb4347052efcea5d0dbd24d5ccd8f1
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219243"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15 için var olan bir uygulamayı güncelleştirme

MSBuild sürümlerinde 15.0 önce Genel Derleme Önbelleği (GAC) gelen MSBuild yüklendi ve MSBuild uzantıları kayıt defterinde yüklendi. Bu, tüm uygulamaları kullanılan MSBuild aynı sürümü ve aynı araç takımları erişebildiği, ancak Visual Studio'nun farklı sürümlerini yan yana yüklemesini engelleyen olmasını sağladı.

Daha hızlı, daha küçük ve yan yana yükleme desteklemek için Visual Studio 2017 artık MSBuild GAC'de yerleştirir veya kayıt defteri değiştirir. Ne yazık ki bu değerlendirme veya projeleri derlemek için MSBuild API kullanmak istediğiniz uygulamalar Visual Studio yüklemesini örtük olarak güvenemezsiniz anlamına gelir.

## <a name="use-msbuild-from-visual-studio"></a>Visual Studio'da MSBuild kullanma

Visual Studio içinden yapılan derlemeleri programlama yapıları uygulamanızdan eşleşmesini sağlamak için veya *MSBuild.exe*, Visual Studio'dan MSBuild derlemeler yüklemek ve Visual Studio içinde kullanılabilir SDK'lar kullanın. Microsoft.Build.Locator NuGet paketi, bu işlemi kolaylaştırır.

## <a name="use-microsoftbuildlocator"></a>Microsoft.Build.Locator kullanın

Dağıtırsanız, *Microsoft.Build.Locator.dll* uygulamanız ile diğer MSBuild derlemeleri dağıtmak gerekmez.

MSBuild 15 ve Bulucu API kullanmak üzere bir proje güncelleştiriliyor, projenizde, aşağıda açıklanan bazı değişiklikler gerektirir. Bir proje güncelleştirmek için gereken değişiklikleri bir örneğini görmek için bkz: [örnek projesinde MSBuildLocator depoya yapılan işlemeler](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>MSBuild başvuruları değiştirme

MSBuild merkezi bir konumdan yükler emin olmak için kendi derlemeleri uygulamanızla dağıtmalısınız değil.

MSBuild merkezi bir konumdan yüklenmesini önlemek için projenizi değiştirme mekanizması, MSBuild nasıl başvuru bağlıdır.

#### <a name="use-nuget-packages-preferred"></a>NuGet paketleri (tercih edilir) kullanma

Bu yönergeler, kullanmakta olduğunuz varsayılır [stili Packagereference'a NuGet başvuruları](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files).

MSBuild derlemeleri kendi NuGet paketleri başvurmak için proje dosyalarınızı değiştirin. Belirtin `ExcludeAssets=runtime` derlemeler yalnızca derleme sırasında gereklidir ve çıkış dizinine kopyalanıp olmamalıdır NuGet söylemek için.

Birincil ve ikincil sürüm MSBuild paketlerin bir bölümünü ya da Visual Studio, desteklemek istediğiniz en düşük sürümü eşit olmalıdır. Visual Studio 2017'in herhangi bir sürümünü desteklemek isterseniz, Paket sürümü başvuru `15.1.548`.

Örneğin, bu XML kullanabilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uzantı derlemeleri kullanma

NuGet paketlerini kullanamıyorsanız, Visual Studio ile dağıtılmış MSBuild derlemelere başvurabilir. Bu, çıkış dizinine ayarlayarak kopyalanmaz, MSBuild'ı doğrudan başvuruda bulunursanız sağlamak `Copy Local` için `False`. Bu ayar, proje dosyasında şu kod gibi görünür:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Bağlama yönlendirmeleri

Uygulamanızı otomatik olarak gerekli bağlama kullanmasını sağlamak için Microsoft.Build.Locator paket yönlendiren MSBuild derlemeleri sürüm tüm sürümlerinin başvuru `15.1.0.0`.

### <a name="ensure-output-is-clean"></a>Çıkış temiz olduğundan emin olun

Projenizi oluşturun ve bunu tüm içermediğinden emin olmak için çıktı dizini inceleyin *Microsoft.Build.\*.dll* dışındaki derlemelerin *Microsoft.Build.Locator.dll*sonraki adımda eklendi.

### <a name="add-package-reference"></a>Paket başvurusu ekleme

Bir NuGet paket başvurusu ekleme [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>MSBuild çağırmadan önce örneğini Kaydet

MSBuild kullanan herhangi bir yöntemini çağırmadan önce Bulucu API'sine yapılan bir çağrı ekleyin.

En basit yolu Bulucu API çağrısı eklemek için bir çağrı eklemektir.

```csharp
MSBuildLocator.RegisterDefaults();
```

Uygulama başlangıç kodunuzda.

MSBuild yüklenmesini üzerinde daha ayrıntılı denetim isterseniz, bir sonucu seçebilirsiniz `MSBuildLocator.QueryVisualStudioInstances()` geçirilecek `MSBuildLocator.RegisterInstance()` el ile ancak bu genellikle gerekli değildir.
