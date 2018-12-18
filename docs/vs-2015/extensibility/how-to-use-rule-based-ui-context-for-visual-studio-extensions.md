---
title: 'Nasıl yapılır: uzantıları için kural tabanlı UI bağlamı kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: 431f9b53fd9b678e16e7fddeeb997ddfcfea6f11
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062544"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Nasıl yapılır: Visual Studio uzantıları için kural tabanlı UI bağlamı kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio VSPackages belirli zaman yüklenmesini sağlayan iyi bilinen <xref:Microsoft.VisualStudio.Shell.UIContext>s etkinleşir. Ancak, bu UI bağlamları sertifikalarıdır, uzantı yazarları bırakarak seçeneği yoktur çok iyi değildir ancak noktasından önce etkinleştirir kullanılabilir bir UI bağlamı seçmek için gerçekten yüklenecek VSPackage'ı istedikleri. İyi bilinen UI bağlamı bir listesi için bkz. <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

 Paketler yüklenirken bir performans etkisi olabilir ve bunlar gerekenden daha çabuk yüklenirken en iyi yöntem değildir. Visual Studio 2015, kural tabanlı UI bağlamı, altında çalışacağı bir UI bağlamı etkinleştirildi ve ilişkili VSPackages yüklenen kesin koşulları tanımlamak uzantı yazarları sağlayan bir mekanizma kavramını sundu.

## <a name="rule-based-ui-context"></a>Kural tabanlı UI bağlamı
 Bir "kural" Yeni kullanıcı Arabirimi bağlamında (GUID) oluşur ve bir veya daha fazla "Terms" başvuran bir Boole ifadesi mantıksal birlikte "ve", "veya", "not" işlemleri. "Terms" çalışma zamanında dinamik olarak değerlendirilir ve kendi koşulları değişiklikleri her ifade tekrar değerlendirilir. İfade doğru olarak değerlendirildiğinde, ilişkili UI bağlamı etkinleştirildi. Aksi takdirde kullanıcı Arabirimi de-activated bağlamıdır.

 Kural tabanlı UI bağlamı çeşitli şekillerde kullanılabilir:

1. Görünürlük kısıtlamaları komutları ve araç pencerelerini belirtin. UI bağlamı kural karşılanana kadar bu komutları/tools windows gizleyebilirsiniz.

2. Otomatik yükü sınırlamaları: otomatik yük, yalnızca kural karşılandığında paketleri

3. Geciken görevi: Belirtilen geçtikten ve kural hala karşılanana kadar yükleme gecikmesi.

   Mekanizması herhangi bir Visual Studio uzantısı tarafından kullanılıyor olabilir.

## <a name="create-a-rule-based-ui-context"></a>Bir kural tabanlı UI bağlamı oluşturur
 Yalnızca ".config" uzantılı dosyalar için geçerli bir menü komutu sunan TestPackage adlı bir uzantı olduğunu varsayalım. VS2015 önce TestPackage yüklemek için en iyi seçenek olduğu zaman <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI bağlamı etkinleştirilmediği. Yüklenen çözüm .config dosyasını bile içeremez olduğundan bu verimli değildir. Bize bakın yalnızca bir dosya açıldığında .config uzantısına sahip bir UI bağlamı etkinleştirmek için kural tabanlı UI bağlamı kullanılabilir nasıl seçilir ve bu UI bağlamı etkinleştirildiğinde TestPackage yükleyin.

1. Yeni bir Uıcontext GUID tanımlayın ve VSPackage sınıfa eklemek <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ve <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Örneğin, yeni Uıcontext varsayalım "UIContextGuid" olan eklenecek. Oluşturulan GUID (Araçlar'ı tıklatarak bir GUID oluşturabilirsiniz -> GUID Oluştur) "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B" olduğu. Ardından aşağıdakileri ekleyin, paket sınıf içinde:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Öznitelikler için aşağıdakileri ekleyin: (bu özniteliklerin ayrıntıları daha sonra verilecektir)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Bu meta veriler, yeni Uıcontext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) ve tek bir terimi, "DotConfig" başvuran bir ifade tanımlayın. Geçerli seçim etkin olan hiyerarşi, normal ifade deseniyle eşleşen bir ada sahipse, "DotConfig" terimi true olarak değerlendirilen "\\.config$" (".config" ile biter). Hata ayıklama için yararlı kuralı için isteğe bağlı bir ad (varsayılan) değerini tanımlar.

    Öznitelik değerleri daha sonra derleme zamanında oluşturulan pkgdef eklenir.

2. VSCT dosyasına TestPackage'nın komutları için uygun komutları için "DynamicVisibility" bayrak ekleyin:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT görünürlüklerini kısmında yeni Uıcontext #1'de tanımlanan GUID için uygun komutları bağlayın:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>
   </VisibilityConstraints>
   ```

4. Semboller bölümünde Uıcontext tanımını ekleyin:

   ```xml
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Şimdi, *.config dosyalar için bağlam menüsü komutları yalnızca seçili öğe Çözüm Gezgini'nde ".config" dosyasıdır ve bu komutlardan birini seçilene kadar paket yüklenmez görünür olur.

   Ardından, paket yalnızca, kendisine bekliyoruz yüklendiğini doğrulamak için bir hata ayıklayıcı kullanalım. TestPackage hata ayıklamak için:

5. Bir kesim noktası <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.

6. TestPackage oluşturun ve hata ayıklamaya başlayın.

7. Bir proje oluşturun veya açın.

8. Herhangi bir dosya uzantısı .config dışında seçin. Kesme noktası isabet değil.

9. App.Config dosyasını seçin.

   TestPackage yükler ve kesme noktasında durur.

## <a name="adding-more-rules-for-ui-context"></a>UI bağlamı için daha fazla kural ekleme
 UI bağlamı kuralları Boolean ifadeler olduğundan, bir kullanıcı Arabirimi içeriği için daha kısıtlı kuralları ekleyebilirsiniz. Örneğin, yukarıdaki UI bağlamında, kural yalnızca bir proje içeren bir çözüm ne zaman yüklendi geçerli olduğunu belirtebilirsiniz. Bu şekilde, komutları, bir ".config" dosyası açarsanız bir projenin bir parçası olarak değil bir tek başına dosya olarak görünmez.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Artık üç şartları ifade başvuruyor. İlk iki terimin "SingleProject" ve "MultipleProjects" (GUID'ler tarafından) iyi bilinen diğer UI bağlamları bakın. Üçüncü terimi, daha önce tanımladığımız kural tabanlı UI bağlamı "DotConfig" dir.

## <a name="delayed-activation"></a>Gecikmeli etkinleştirme
 Kurallar, isteğe bağlı bir "gecikmesi" olabilir. Gecikme süresini milisaniye cinsinden belirtilir. Varsa, o zaman aralığına göre geciktirileceği bir kuralın UI bağlamı devre dışı bırakma ve etkinleştirme gecikme neden olur. Kural değişikliklerini önce gecikme aralığı yedeklerseniz, hiçbir şey olmaz. Bu mekanizma "başlatma adımlar - üzerinde zamanlayıcılar güvenmek veya boşta bildirimlere kaydolma olmadan özellikle tek seferlik başlatma basamaklandırmak için" kullanılabilir.

 Örneğin, 100 milisaniye gecikme için test yük kuralınızı belirtebilirsiniz:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Terim türleri
 Terim desteklenen çeşitli türleri şunlardır:

|||
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID, bir kullanıcı Arabirimi bağlamına başvuruyor. Terimi, UI bağlamı etkin ve false Aksi durumda olduğunda true olur.|
|HierSingleSelectionName:\<deseni >|Terim Seçimi etkin hiyerarşideki tek bir öğedir ve seçilen öğenin adı "deseni" tarafından verilen .net normal ifadeyle eşleşen olduğunda true olur.|
|UserSettingsStoreQuery:\<sorgu >|"sorgu", sıfır olmayan bir değerde hesaplanmalıdır kullanıcı ayarları deposuna tam yolunu temsil eder. Sorgu, "koleksiyonu" ve "propertyName" en son eğik çizgi ayrılır.|
|ConfigSettingsStoreQuery:\<sorgu >|"sorgu", sıfır olmayan bir değerde hesaplanmalıdır yapılandırma ayarları deposuna tam yolunu temsil eder. Sorgu, "koleksiyonu" ve "propertyName" en son eğik çizgi ayrılır.|
|ActiveProjectFlavor:\<projectTypeGuid >|Seçili olan projeye markdown'lar her terimi true (toplu olarak) ve GUID belirli proje türüyle eşleşen bir özellik vardır.|
|ActiveEditorContentType:\<contentType >|Seçili belgeyi belirtilen içerik türü metin düzenleyiciyle olduğunda terimi true olur.|
|ActiveProjectCapability:\<ifadesi >|Etkin proje özellikleri sağlanan ifade eşleştiğinde true bir terimdir. VB gibi bir ifade olabilir &#124; CSharp|
|SolutionHasProjectCapability:\<ifadesi >|Yukarıdaki benzer; ancak terimi olduğunda true ifade ile eşleşen tüm yüklenen proje çözümü vardır.|
|SolutionHasProjectFlavor:\<projectTypeGuid >|Her bir çözüm (toplu) özellikli proje varsa ve GUID belirli proje türüyle eşleşen bir özellik terimi true olur.|



## <a name="compatibility-with-cross-version-extension"></a>Sürümler arası uzantısı ile uyumluluk
 Tabanlı UI bağlamı Visual Studio 2015'te yeni bir özelliktir ve önceki sürümleri için unity'nin değil kuralı. Bu, Visual Studio 2013'te otomatik olarak yüklenir ve önceki olması gerekir, ancak otomatik-Visual Studio 2015'te yüklenmesini önlemek için kural tabanlı UI bağlamı yararlanabilir Visual Studio'nun birden çok sürümünü hedefleyen uzantıları/paketleri ile ilgili bir sorun oluşturur.

 Gibi paketlerin desteklemek için AutoLoadPackages girişleri kayıt defterinde girişi Visual Studio 2015'te ve üstünde olarak atlanması gerektiğini belirtmek için değer alanında bir bayrak şimdi sağlayabilirsiniz. Bu bayrak seçeneğine ekleyerek yapılabilir <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. VSPackage artık ekleyebilirsiniz **SkipWhenUIContextRulesActive** seçeneğini kendi <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> giriş yoksayılan Visual Studio 2015'te ve yukarıdaki belirtmek için özniteliği.

## <a name="extensible-ui-context-rules"></a>Genişletilebilir UI bağlamı kuralları
 Bazı durumlarda, paketleri statik UI bağlamı kurallarını kullanamazsınız. Örneğin, komut durumu, içeri aktarılan MEF sağlayıcıları tarafından desteklenen Düzenleyicisi türlere göre olacak şekilde genişletilebilirlik destekleyen bir paket olduğunu varsayalım. Komut geçerli düzen türünü destekleyen bir uzantısı varsa etkindir. Bu gibi durumlarda koşullarına bağlı olarak hangi MEF uzantıların kullanılabilir olduğunu değiştirirsiniz olduğundan paket statik bir UI bağlamı kural kullanamazsınız.

 Kural tabanlı UI bağlamı gibi paketlerin desteklemek için bir sabit kodlanmış ifadesi destek "*", katılması ile tüm aşağıdaki koşulları gösterir veya. Bu ana paket tanımlamak bilinen bir kural tabanlı UI bağlamı sağlar ve bu bağlam komut durumuna bağlayın. Daha sonra ana paket için hedeflenen herhangi bir MEF uzantısına şartlarının başka koşullar veya ana ifade etkilemeden destekler düzenleyiciler için ekleyebilirsiniz.

 Oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> belgeleri Genişletilebilir UI bağlamı kuralları sözdizimi gösterilmektedir.
