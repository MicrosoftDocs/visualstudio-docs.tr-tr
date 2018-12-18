---
title: C++ temel yönergeleri denetleyicilerini kullanma
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 6595e8990dece15e88e07a6c8eefabd3f543bbb7
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143469"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ temel yönergeleri denetleyicilerini kullanma
C++ temel yönergeleri yönergeleri, kuralları ve C++ uzmanlar ve tasarımcılar tarafından oluşturulan c++ kodlama hakkında en iyi taşınabilir bir kümesidir. Visual Studio, şu anda C++ için kod analizi araçlarında bir parçası olarak bu kural kümesini destekler. Ana Kılavuz denetleyicileri Visual Studio 2017'de varsayılan olarak yüklenir ve olan [Visual Studio 2015 için bir NuGet paketi olarak kullanılabilir](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>C++ temel yönergeleri proje
 Bjarne Stroustrup ve başkaları tarafından oluşturulan, C++ temel yönergeleri güvenle ve etkili bir şekilde modern C++'ı kullanarak bir kılavuz olan. Statik tür güvenliği ve kaynak güvenliği yönergeleri vurgulayın. Bunlar, kaldırın veya dil en hataya bölümlerini en aza indirmek için yollarını tanımlar ve kodunuzu daha basit hale getirme ve daha fazla yüksek performanslı, güvenilir bir biçimde önerin. Bu yönergeleri, standart C++ Foundation tarafından korunur. Daha fazla bilgi edinmek için belgelere bakın [C++ temel yönergeleri](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)ve C++ temel yönergeleri belge proje dosyaları üzerinde erişim [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>C++ temel denetimi yönergeleri kod analizini etkinleştir
 Seçerek projeniz üzerinde kod analizi etkinleştirebilirsiniz **derlemede kod analizini etkinleştir** onay kutusu **Kod Analizi** bölümünü **özellik sayfaları** için iletişim kutusu projenizi.

 ![Kod Analizi genel ayarları için özellik sayfası](media/cppcorecheck_codeanalysis_general.png)

 C++ temel denetimi kuralları bir alt kümesi çalıştıran Microsoft yerel önerilen kural kümesinde, Kod Analizi etkin olduğunda varsayılan olarak dahil edilir. Ek temel denetimi kuralları etkinleştirmek için üzerindeki açılır menüye tıklayın ve dahil etmek istediğiniz hangi kural kümeleri seçin:

 ![Ek C++ temel denetimi kuralı için açılan ayarlar](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Örnekler
 C++ temel denetimi kuralları bulabilirsiniz sorunlardan bazılarını bir örneği aşağıda verilmiştir:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Bu örnek, C++ temel denetimi kuralları bulabilirsiniz uyarıları birkaçını göstermektedir:

- C26494 olan kural Type.5: bir nesneyi her zaman başlatın.

- C26485 olan kural Bounds.3: hiçbir dizi işaretçiye azalma gerçekleştirmeyin.

- C26481 olan kural Bounds.1: işaretçi aritmetiği kullanmayın. Bunun yerine `span` kullanın.

C++ temel denetimi Kod Analizi rulesets yüklediyseniz ve bu kodu derlerken etkin ilk iki uyarıları çıktısı alınır, ancak üçüncü bastırılır. Örnek kod derleme çıktısı şöyledir:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ temel yönergeleri daha iyi ve daha güvenli kod yazmanıza yardımcı vardır. Ancak, bir kuralı ya da profili burada uygulanan olmamalıdır örneği varsa, doğrudan kodunda gizlemek kolaydır. Kullanabileceğiniz `gsl::suppress` C++ temel denetimi algılama ve bir kural aşağıdaki kod bloğu, herhangi bir ihlali raporlama tutmak için özniteliği. Belirli kurallar bastırmak için ayrı deyimler işaretleyebilirsiniz. Yazarak bile tüm sınırların profil gizleyebilirsiniz `[[gsl::suppress(bounds)]]` bir özel kural numarası dahil olmak üzere olmadan.

## <a name="supported-rule-sets"></a>Kural kümeleri desteklenir
Yeni kurallar, C++ temel yönergeleri denetleyici için eklendikçe önceden mevcut olan kod için üretilen uyarıların sayısını artırabilir. Önceden tanımlanmış kural kümeleri, hangi tür kuralların etkinleştirmek için filtre uygulamak için kullanabilirsiniz.
Çoğu kuralları için başvuru konularındaki altında [denetleyin Visual Studio C++ temel başvuru](code-analysis-for-cpp-corecheck.md).

Visual Studio 2017'den itibaren sürüm 15.3, desteklenen kural kümesi şunlardır:
- **Sahip işaretçisi kuralları** zorunlu [kaynak yönetimi denetler ilgili sahibine<T> C++ temel yönergeleri'ndeki](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Const kuralları** zorunlu [C++ temel yönergeleri'ndeki const ile ilgili denetimleri](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Ham işaretçi kuralları** zorunlu [kaynak yönetimi, C++ temel yönergeleri'ndeki ilgili ham işaretçiler denetler](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Benzersiz işaretçi kuralları** zorunlu [kaynak yönetimi denetler C++ temel yönergeleri'ndeki ilgili benzersiz işaretçi semantiğine sahip türlerle](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Sınır kuralları** zorunlu [sınırların profili C++ temel yönergeleri](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Kural türü** zorunlu [yazın C++ temel yönergeleri profili](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 sürüm 15.5**:

- **Sınıf kuralları** özel üye işlevleri ve sanal belirtimlerine uygun kullanımını üzerinde odaklanın bazı kurallar. İçin önerilen denetimler kümesini budur [sınıflar ve sınıf Hiyerarşiler](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Eşzamanlılık kuralları** hatalı bildirilmiş guard nesnelerini yakalıyor tek bir kural. Daha fazla bilgi için [yönergeleri için eşzamanlılık ilgili](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Bildirim kuralları** birkaç kurallardan [yönergeleri arabirimleri](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) nasıl genel değişkenler hangi odaklanmak bildirilir.
- **İşlev kuralları** ile kullanmaya başlamasına yardımcı olan iki denetimleri `noexcept` tanımlayıcısı. Bir parçası için yönergeler [Temizle işlevi tasarım ve uygulama](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Paylaşılan işaretçi kuralları** bir parçası olarak [kaynak yönetimi](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) yönergeleri zorlama ekledik birkaç kural paylaşılan işaretçileri belirli işlevlere geçirilen veya yerel olarak kullanılır.
- **Stil kurallarını** kullanımını engeller bir basit ancak önemli onay [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Bu, kodlama stili ve ifadelerin ve deyimlerin C++'ta kullanmak geliştirme, ilk adımıdır.

**Visual Studio 2017 sürüm 15.6**:

- **Aritmetik kuralları** aritmetik algılamak için kurallar [taşma](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [imzalı imzasız işlemleri](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) ve [bit işleme](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Uyarıları yalnızca bir veya birkaç gruplarının sınırlandırmayı seçebilirsiniz. **Yerel Minimum** ve **yerel önerilen** kural kümeleri PREfast diğer denetimleri ek olarak, C++ temel denetimi kuralları içerir. Kural kümeleri, Proje Özellikleri iletişim kutusunu açın kullanılabilir görmek için seçin **kod Analysis\General**, açılır menüde açın **kural kümeleri** birleşik giriş kutusu ve çekme **birden çok kural kümesi seçin** . Visual Studio'da kural kümeleri kullanma hakkında daha fazla bilgi için bkz. [Kod Analizi kurallarını gruplandırmak için kural kümeleri kullanma](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makrolar

C++ temel yönergeleri denetleyici uyarıları kod tüm kategorileri gösterme daha kolay hale getirmek makroları tanımlar bir üstbilgi dosyası ile birlikte gelir:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Bu makrolar için kural kümeleri karşılık gelir ve uyarı numaralarının boşlukla ayrılmış listesini genişletin. Uygun pragma yapıları kullanarak, bir proje için ilginç etkin kural kümesini veya kodun bir bölümünü yapılandırabilirsiniz. Aşağıdaki örnekte, Kod Analizi yalnızca sabit değiştiriciler eksik hakkında sizi uyarır:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Öznitelikler

Microsoft Visual C++ derleyicisi özniteliği bastırmak için GSL bir sınırlı destek vardır. İfadesi ve bir işlev içinde blok ifadeleri uyarıları bastırmak için kullanılabilir.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Komut satırı seçeneklerini kullanarak analizi gizleme

#Pragmas yerine bir proje veya tek bir dosya için uyarıları bastırmak için dosyanın özellik sayfasında komut satırı seçeneklerini kullanabilirsiniz. Örneğin, uyarıyı devre dışı bırakmak için bir dosya için 26400:

1. Dosyaya sağ **Çözüm Gezgini**

2. Seçin **özellikleri | C / C ++ | Komut satırı**

3. İçinde **ek seçenekler** penceresinde ekleme `/wd26400`.

Komut satırı seçeneği bir dosya için tüm kod analizi belirterek geçici olarak devre dışı bırakmak için kullanabileceğiniz `/analyze-`. Bu uyarıyı üretir *D9025 geçersiz kılma '/ analyze' ile ' / analyze-'*, Kod Analizi daha sonra yeniden etkinleştirmeniz anımsatır.

## <a name="corecheck_per_file"></a> C++ temel yönergeleri denetleyici belirli proje dosyaları üzerinde etkinleştirme

Bazen iş odaklı Kod Analizi ve yine de Visual Studio IDE kullanın yararlı olabilir. Aşağıdaki örnek senaryoyu büyük projeler için derleme zamandan tasarruf edin ve sonuçları filtrelemek için daha kolay hale getirmek için kullanılabilir:

1. Komut kabuğu'nda ayarlayın `esp.extension` ve `esp.annotationbuildlevel` ortam değişkenleri.
2. Bu değişkenler devralmak için komut kabuğu'ndan Visual Studio'yu başlatın.
3. Projenize yükleyin ve özelliklerini açın.
4. Kod analizini etkinleştir, uygun bir kural kümesi seç, ancak kod analizi uzantıları etkinleştirmeyin.
5. C++ temel yönergeleri Denetleyici ile analiz edin ve özelliklerini açmak istediğiniz dosyaya gidin.
6. Seçin **C / C ++ \Command satırı seçenekleri** ekleyin `/analyze:plugin EspXEngine.dll`
7. Önceden derlenmiş üst bilgi kullanımını devre dışı (**C / C ++ \Precompiled üstbilgileri**). Bunun gerekli olmasının nedeni uzantıları altyapısı Ön derlenmiş üstbilgi (PCH); iç bilgilerini okuma girişiminde bulunabilir PCH varsayılan proje seçenekleri ile derlenmişse uyumlu olmaz.
8. Projeyi yeniden derleyin. Ortak PREFast denetimleri, tüm dosyalar üzerinde çalıştırmanız gerekir. C++ temel yönergeleri denetleyici varsayılan olarak etkin olmadığından, yalnızca onu kullanmak üzere yapılandırılmış dosya üzerinde çalıştırmanız gerekir.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio dışında C++ temel yönergeleri denetleyici kullanma

İçinde otomatik yapılara, C++ temel yönergeleri denetimi kullanabilirsiniz.

### <a name="msbuild"></a>MSBuild
 Yerel Kod Analizi denetleyicisi (PREfast), özel MSBuild tarafından MSBuild ortamına tümleşiktir. Proje özellikleri etkinleştirmek için kullanın ve (hangi PREfast üzerinde göre) C++ temel yönergeleri denetleyici ekleyin:

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Bu özellikler Microsoft.Cpp.targets dosyasının içeri aktarmadan önce eklediğinizden emin olun. Özel kural kümeleri seçin veya bir özel kural kümesi oluşturma veya PREfast diğer denetimleri içeren varsayılan kural kümesi kullanın.

C++ temel denetleyici olarak aynı yaklaşımı kullanarak üzerinde yalnızca belirtilen dosyaları çalıştırıp çalıştıramayacağını [daha önce açıklanan](#corecheck_per_file), ancak MSBuild dosyalarını kullanarak. Ortam değişkenlerini kullanarak ayarlayabilirsiniz `BuildMacro` öğesi:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Proje dosyasını değiştirmek istemiyorsanız, özellikleri komut satırında geçirebilirsiniz:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>MSBuild dışındaki projeleri

Msbuild'i temel içermez bir yapı sistemi kullanıyorsanız Denetleyicisi'ni yine de çalıştırabilirsiniz, ancak kod analizi altyapısı yapılandırması ile bazı iç işlevleri hakkında bilgi edinmek gerekir. Bu iç işlevleri gelecekte desteklenmesi garanti edilmez.

Birkaç ortam değişkenlerini ayarladıktan ve uygun komut satırı seçenekleri için derleyici kullanmak zorunda. Sahip olmadığınız derleyici için belirli yollar için arama yapın, dizinleri, vb. dahil "yerel Araçlar komut istemi" ortamı altında çalışacak şekilde daha iyidir.

1. **Ortam değişkenleri**
   - `set esp.extensions=cppcorecheck.dll` Bu, C++ temel yönergeleri modülünü yüklemek için altyapı bildirir.
   - `set esp.annotationbuildlevel=ignore` SAL ek açıklamalarını işleme mantığı, devre dışı bırakır. Ek açıklamalar, Kod Analizi C++ temel yönergeleri denetleyici etkilemez, ancak bunların işlenmesi Sürüyor (bazen uzun bir süre). Bu ayar isteğe bağlıdır ancak uygulanması önemle önerilir.
   - `set caexcludepath=%include%` Standart üstbilgilerinde yangın uyarılar devre dışı bırakmanızı öneririz. Örneğin, projenizdeki ortak üst bilgileri yolu burada daha yollarını ekleyebilirsiniz.
2. **Komut satırı seçenekleri**
   - `/analyze`  Kod analizini etkinleştirir (Ayrıca kullanmayı / analyze: yalnızca ve / analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Bu seçenek, Kod Analizi uzantıları altyapısı PREfast yükler. Bu altyapısı, buna karşılık, C++ temel yönergeleri denetleyici yükler.

## <a name="use-the-guideline-support-library"></a>Kılavuzu destek kitaplığını kullanma
 Yönerge destek kitaplığı, temel yönergeleri izlemenize yardımcı olmak için tasarlanmıştır. GSL hataya yapıları ile daha güvenli alternatifler değiştirmenizi sağlayan tanımlarını içerir. Örneğin, değiştirebileceğiniz bir `T*, length` parametrelerle çiftinin `span<T>` türü. GSL kullanılabilir [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Kaynakları görüntülemek, yorum yapmak veya katkıda bulunan kitaplık açık kaynaklı olduğundan. Proje şu yolda bulunabilir: [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a> Visual Studio 2015 projelerinde C++ temel denetimi kuralları kullanma

Visual Studio 2015 kullanıyorsanız, C++ temel denetimi Kod Analizi kural kümeleri varsayılan olarak yüklü değil. C++ temel denetimi kod çözümleme araçları Visual Studio 2015'te etkinleştirmeden önce bazı ek adımlar gerçekleştirmeniz gerekir. Microsoft, bir Nuget paketi kullanarak Visual Studio 2015 projeleri için destek sağlar. Paket Microsoft.CppCoreCheck olarak adlandırılır ve adresten edinilebilir [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Bu paket, yüklü en az Visual Studio 2015 güncelleştirme 1 ile olması gerekir.

Paket, başka bir paket bağımlılık olarak, bir yalnızca üstbilgi yönerge desteği kitaplığı (GSL) de yükler. GSL GitHub üzerinde de kullanılabilir [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

Kod Analizi kuralları yüklenen şekli nedeniyle, Visual Studio 2015 içinde kontrol etmek istediğiniz her C++ projesi içine Microsoft.CppCoreCheck NuGet paketini yüklemeniz gerekir.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Projenizi Visual Studio 2015'te Microsoft.CppCoreCheck paketi eklemek için

1. İçinde **Çözüm Gezgini**, pakete eklemek istediğiniz çözümü projenizin bağlam menüsünü açmak için sağ tıklayın. Seçin **NuGet paketlerini Yönet** açmak için **NuGet Paket Yöneticisi**.

2. İçinde **NuGet Paket Yöneticisi** penceresinde, Microsoft.CppCoreCheck arayın.

    ![Nuget Paket Yöneticisi penceresi CppCoreCheck paket gösterir](../code-quality/media/cppcorecheck_nuget_window.png)

3. Microsoft.CppCoreCheck paketi seçin ve ardından **yükleme** düğmesini kuralları projenize ekleyin.

   Bir ek MSBuild NuGet paketini ekler *.targets* projeniz üzerinde kod analizini etkinleştirdiğinizde, çağrılan projenize bir dosya. Bu *.targets* dosyası Visual Studio kod analizi aracı için ek uzantı olarak C++ temel denetimi kuralları ekler. Paket yüklendikten sonra özellik sayfaları iletişim kutusu etkinleştirme veya devre dışı bırakılmış ve Deneysel kuralları kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio C++ temel denetimi başvurusu](code-analysis-for-cpp-corecheck.md)