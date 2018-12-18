---
title: Visual Studio'da çalışma alanları | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865836"
---
# <a name="workspaces"></a>Çalışma Alanları

Nasıl Visual Studio tüm dosyaları koleksiyonunu temsil eder bir çalışma alanıdır [Klasör Aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), ve tarafından temsil edilen <xref:Microsoft.VisualStudio.Workspace.IWorkspace> türü. Klasördeki dosyaları için ilgili özellikler ve içeriği tek başına çalışma anlamıyor. Bunun yerine, genel üretmek ve diğer işlem yapabileceğimiz veri kullanmak için özellikler ve uzantılar için API kümesi sağlar. Üreticiler arasında oluşan [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) kullanarak çeşitli öznitelikler verme.

## <a name="workspace-providers-and-services"></a>Çalışma alanı sağlayıcıları ve Hizmetleri

Çalışma alanı sağlayıcıları ve Hizmetleri veri ve bir çalışma alanının içeriğini tepki vermek için işlevsellik sağlar. Bağlamsal dosya bilgilerini, kaynak dosyaları, simgeler veya yapı işlevselliği.

Her iki kavramları kullanarak bir [Fabrika deseni](https://en.wikipedia.org/wiki/Factory_method_pattern) ve çalışma alanı tarafından MEF üzerinden aktarılır. Tüm verme öznitelikleri uygulamak `IProviderMetadataBase` veya `IWorkspaceServiceFactoryMetadata`, vardır, ancak uzantıları, dışarı aktarılan türler için kullanması gereken somut türler.

Sağlayıcıları ile hizmetler arasında bir fark ilişkilerini çalışma alanına olmasıdır. Bir çalışma alanı belirli bir türün birçok sağlayıcı olabilir ancak yalnızca bir hizmeti belirli bir türün çalışma alanı oluşturulur. Örneğin, bir çalışma alanı birçok dosya tarayıcı sağlayıcıları ancak çalışma çalışma alanı yalnızca bir dizin oluşturma hizmeti içeriyor.

Başka bir anahtar sağlayıcıları ve hizmetlerden veri tüketimini farktır. Çalışma alanını birkaç nedenlerle sağlayıcılardan veri almak için giriş noktasıdır. İlk olarak, sağlayıcılar genellikle bazı dar oluşturdukları veri kümesine sahip olursunuz. Veriler için Sembol olabilir bir C# kaynak dosyası veya dosya bağlamları yapı bir _CMakeLists.txt_ dosya. Çalışma alanı olan meta verileri hizalama istekle sağlayıcıları için bir tüketicinin isteği eşleşir. İkinci olarak, bazı senaryolar için birçok izin diğerlerinin isteğine senaryoları katkıda bulunmak için sağlayıcıları kullanan sağlayıcı en yüksek öncelik.

Buna karşılık, uzantılar örneklerini alma ve çalışma alanı hizmetleriyle doğrudan etkileşim. Uzantı yöntemleri `IWorkspace` gibi Visual Studio tarafından sağlanan hizmetleri için kullanılabilir <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Uzantınızı bileşenleri uzantınız içinde veya diğer uzantıları kullanmak için bir çalışma hizmet sunabilir. Tüketiciler kullanması gereken <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> veya sağladığınız üzerinde bir genişletme yöntemi `IWorkspace` türü.

>[!WARNING]
> Visual Studio ile çakışan hizmetlerin Yazar değil. Bu beklenmeyen sorunlarına yol açabilir.

## <a name="disposal-on-workspace-closure"></a>Çalışma alanını kapatma çıkışında

Üzerinde kapanış bir çalışma alanının Genişleticileri dispose ancak zaman uyumsuz çağrı gerekebilir kod. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Arabirimidir bu kodları yazmak kullanılabilir.

## <a name="related-types"></a>İlgili türleri

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> açılan bir klasörü gibi açık bir çalışma alanı için merkezi varlıktır.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Çalışma alanı örneği başına bir sağlayıcı oluşturur.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Çalışma alanı örneği başına bir hizmet oluşturur.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> sağlayıcılar ve çıkarma sırasında zaman uyumsuz kodu çalıştırmak için gereken hizmetleriniz uygulanmalıdır.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> iyi bilinen hizmetleri veya rastgele Hizmetleri erişmek için yardımcı yöntemleri sağlar.

## <a name="workspace-settings"></a>Çalışma alanı ayarları

Çalışma alanına sahip bir <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> basit ama güçlü bir çalışma alanı denetime sahip hizmet. Ayarları temel bir genel bakış için bkz [yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Çoğu ayarları `SettingsType` türleridir _.json_ dosyaları, gibi _VSWorkspaceSettings.json_ ve _tasks.vs.json_.

Çalışma alanı ayarlarını gücünü yalnızca çalışma alanı içinde yolları "kapsamların" etrafında ortalar. Bir tüketici çağırdığında <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, istenen yol ve ayar türünü içeren tüm kapsamlar toplanır. Kapsam toplama öncelik aşağıdaki gibidir:

1. "Çalışma alanı kökün genellikle olan yerel ayarları", `.vs` dizin.
1. İstenen yolun kendisindeki.
1. İstenen yol üst dizini.
1. Tüm dizinler için ayarlama ve çalışma alanı kök dahil olmak üzere daha fazla üst.
1. "Bir kullanıcı dizinde genel ayarları".

Sonuç örneğidir <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Bu nesne, belirli bir tür için ayarları içerir ve olarak depolanan anahtar adlarını ayarlamak için sorgulanabilir `string`. <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Yöntemleri ve <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> genişletme yöntemleri, istenen ayar değeri türünü bilmeniz çağıran beklediğiniz. Çoğu ayarları dosyası olarak kalıcı olarak _.json_ dosyaları, birçok çağrılarını kullanacağı `string`, `bool`, `int`ve bu türlerin dizileri. Nesne türleri de desteklenir. Bu gibi durumlarda, kullandığınız `IWorkspaceSettings` tür bağımsız değişkeni olarak kendisini. Örneğin:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Bu ayarların olduğunu düşünerek olan bir kullanıcının _VSWorkspaceSettings.json_, veri olarak erişilebilir:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Kullanılabilir API'ler için bu ayarları API'leri ilişkisizdir `Microsoft.VisualStudio.Settings` ad alanı. Çalışma alanı ayarlarını ana bilgisayarının dilden bağımsız ve özel çalışma ayarları dosya veya dinamik ayarları sağlayıcıları kullanır.

### <a name="providing-dynamic-settings"></a>Dinamik ayarlarını sağlama

Uzantıları sağlayabilir <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Bu bellek içi sağlayıcıları ayarlar eklemek veya başkalarının geçersiz kılmak uzantılar sağlar.

Dışarı aktarma bir `IWorkspaceSettingsProvider` diğer çalışma alanı sağlayıcıları farklı. Fabrika değil `IWorkspaceProviderFactory` ve özel öznitelik türü yoktur. Bunun yerine, uygulama <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> ve `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Döndüren yöntemler uygularken `IWorkspaceSettingsSource` (gibi `IWorkspaceSettingsProvider.GetSingleSettings`), bir örneğini döndürür `IWorkspaceSettings` yerine `IWorkspaceSettingsSource`. `IWorkspaceSettings` bazı ayarları toplamalar sırasında yararlı olabilir. daha fazla bilgi sağlar.

### <a name="settings-related-apis"></a>Ayarları ilgili API'ler

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> okur ve çalışma alanı ayarlarını toplar.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> alır `IWorkspaceSettingsManager` bir çalışma alanı için.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Çakışan tüm kapsamlarda toplanan belirli bir kapsam için ayarları alır.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> belirli bir kapsam için ayarlar içerir.

## <a name="workspace-suggested-practices"></a>Çalışma alanı önerilen uygulamalar

- Nesnelerden dönüş `IWorkspaceProviderFactory.CreateProvider` veya unutmayın benzer API'leri kendi `Workspace` oluştururken bağlamı. Bu nesne oluşturma tutulur bekleniyor sağlayıcıları arabirimleri yazılır.
- Çalışma alanı özgü önbellekler veya "Yerel ayarları" yol çalışma alanının içinde ayarları kaydedin. Kullanarak dosya için bir yol oluşturmak `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` Visual Studio 2017 sürüm 15.6 veya üzeri. 15.6. sürümden önceki sürümler için aşağıdaki kod parçacığını kullanın:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Çözüm olayları ve paket otomatik yükle

Yüklü paketleri uygulayabilirsiniz `IVsSolutionEvents7` ve çağırma `IVsSolution.AdviseSolutionEvents`. Bu olay, açma ve kapatma Visual Studio'da bir klasör içerir.

UI bağlamı otomatik yükle paketiniz için kullanılabilir. Değer `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Sorun giderme

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage paketi düzgün şekilde yüklenmedi

Çalışma alanı genişletilebilirlik yoğun MEF tabanlı ve yüklenmesi başarısız açık klasörü barındıran paket oluşturma hatalara neden olur. Örneğin, bir uzantı türü ile dışarı aktarır `ExportFileContextProviderAttribute`, ancak yalnızca türün uyguladığı `IWorkspaceProviderFactory<IFileContextActionProvider>`, Visual Studio'da bir klasör açılmaya çalışılırken bir hata meydana gelir. Hata ayrıntıları bulunabilir _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Uzantınız tarafından uygulanan türleri için hataları giderin.

## <a name="next-steps"></a>Sonraki adımlar

* [Dosya bağlamları](workspace-file-contexts.md) -dosya bağlam sağlayıcıları Klasör Aç çalışma alanları için kod zeka getirin. 
* [Dizin oluşturma](workspace-indexing.md) -çalışma dizinini toplar ve çalışma alanı hakkında bilgileri kalıcıdır.
