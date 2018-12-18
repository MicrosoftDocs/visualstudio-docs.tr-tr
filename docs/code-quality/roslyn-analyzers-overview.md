---
title: Roslyn çözümleyicilerini kullanarak kod analizi
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 620f2905e2511ed403f0d25f32fa1bfc9b1eca68
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948848"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET derleyici platformu Çözümleyicileri genel bakış

Visual Studio 2017, siz yazarken, C# veya Visual Basic kod çözümleme .NET derleyici platformu Çözümleyicileri yerleşik bir kümesini içerir. Kod stili, kod kalitesini ve Bakım, kod tasarımı ve diğer sorunları çözümleyiciler arayın. Bir NuGet paketi olarak Visual Studio uzantısı ya da proje başına temelinde ek Çözümleyicileri yükleyebilirsiniz.

Kural ihlallerinin bir çözümleyici tarafından bulunması durumunda raporlanır Kod düzenleyicisinde hem de bir *dalgalı* sorunlu kod ve buna **hata listesi**.

Birçok çözümleyicisi kuralları veya *tanılama*, olması bir veya daha fazla ilişkili *kod düzeltme* sorunu düzeltmek için uygulayabilirsiniz. Visual Studio'ya her yerleşik Çözümleyicisi tanılama ilişkili kod düzeltme vardır. Kod düzeltmeleri, ampul simgesini menüde diğer türleri ile birlikte gösterilir *hızlı Eylemler*. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [yaygın hızlı Eylemler](../ide/common-quick-actions.md).

![İhlali Çözümleyicisi ve kod düzeltmenizi hızlı eylem](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Roslyn çözümleyicilerini statik kod analizi karşılaştırması

.NET derleyici Platformu ("Roslyn") Çözümleyicileri sonunda yerini alacak [statik kod analizi](../code-quality/code-analysis-for-managed-code-overview.md) yönetilen kod için. Statik kod analizi kuralları çoğunu zaten olarak Roslyn Çözümleyicisi tanılama yazıldı.

Roslyn Çözümleyicisi ihlalleri statik kod analizi kural ihlalleri gibi görünen **hata listesi**. Ayrıca, Roslyn Çözümleyicisi ihlalleri ayrıca Kod düzenleyicisinde görünmesini *squigglies* sorunlu kod altında. Dalgalı rengi bağımlı [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#rule-severity) kural. Üç ihlalleri aşağıdaki ekran görüntüsünde gösterilmektedir&mdash;bir kırmızı, yeşil bir ve bir gri:

![Kod düzenleyicisinde Squigglies](media/diagnostics-severity-colors.png)

Roslyn çözümleyicilerini etkinleştirildi ancak siz yazarken canlı, ayrıca, statik kod analizi gibi derleme zamanında kodu analiz edin! Roslyn Çözümleyicileri de tasarım zamanı etkinleştirirseniz, düzenleyicide açık olmayan kod dosyaları analizini sağlar [tam çözüm analizini](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Derleme hataları ve Uyarıları Roslyn Çözümleyicileri gelen yalnızca bir NuGet paketi olarak Çözümleyicileri yüklü olup olmadığını gösterilir.

Yalnızca aynı türdeki statik kod analizini yapar sorunları rapor Roslyn Çözümleyicileri, ancak bunların birini veya tümünü dosyası veya proje dosyasında ihlali oluşumlarını gidermenizi kolaylaştırır. Bu eylemler adlı *kod düzeltme*. Kod düzeltmeleri IDE özgüdür; Visual Studio'da, bunlar olarak uygulanan [hızlı Eylemler](../ide/quick-actions.md). Tüm Çözümleyicisi tanılama ilişkili kod düzeltme vardır.

> [!NOTE]
> Menü seçeneği **Çözümle** > **kod çözümlemeyi Çalıştır** yalnızca statik kod analizi uygular. Ayrıca, bir projenin üzerinde **Kod Analizi** özellik sayfası **derlemede kod analizini etkinleştir** ve **üretilen koddan gelen sonuçları Gizle** onay kutularını yalnızca uygulama statik kod analizi. Roslyn çözümleyicilerini üzerinde etkiye sahiptirler.

Roslyn çözümleyicilerini gelen ihlalleri ve statik kod analizi birbirinden ayırmak için **hata listesi**, bakmak **aracı** sütun. Aracı değer Çözümleyicisi derlemelerde birini eşleşip eşleşmediğini **Çözüm Gezgini**, örneğin **Microsoft.CodeQuality.Analyzers**, ihlalin Roslyn Çözümleyicisi'nden gelir. Aksi takdirde, statik kod çözümleme dışı ihlali kaynaklanır.

![Hata listesi sütunu aracı](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>NuGet paketi VSIX uzantısı karşılaştırması

.NET derleyici platformu Çözümleyicileri olabilir, her proje bir NuGet paketi veya Visual Studio genelinde üzerinden Visual Studio uzantısı olarak yüklü. Bu iki yöntemden arasındaki bazı temel davranış farkları vardır [çözümleyicilerini yükleme](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Kapsam

Visual Studio uzantısı olarak Çözümleyicileri yüklerseniz, Visual Studio'nun tüm örneklerini çözüm düzeyinde uygulanır. Tercih edilen yöntemi olan bir NuGet paketi olarak Çözümleyicileri yüklerseniz bunlar yalnızca NuGet paketini yüklendiği projesi için geçerlidir. Ekip ortamlarında kapsamın Çözümleyicileri NuGet paketleri olarak yüklü bulunan *tüm geliştiricilerin* bu proje üzerinde çalışır.

### <a name="build-errors"></a>Derleme hataları

Komut satırı aracılığıyla parçası olarak veya sürekli tümleştirme (CI) derleme dahil olmak üzere yapı zamanında uygulanan kuralları için bir NuGet paketi olarak Çözümleyicileri yükleyin. Uzantı olarak Çözümleyicileri yüklerseniz Çözümleyicisi uyarılarını ve hataları derleme raporda görünmüyor.

Aşağıdaki ekran görüntüsünde, komut satırı derleme çıktı Çözümleyicisi Kuralı ihlali içeren bir proje oluşturma gösterir:

![MSBuild çıkışıyla kuralı ihlali](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Kural önem derecesi

Visual Studio uzantısı olarak yüklenen Çözümleyicileri gelen kural önem derecesi olarak ayarlanamıyor. Yapılandırmak için [kural önem derecesi](../code-quality/use-roslyn-analyzers.md#rule-severity), bir NuGet paketi olarak çözümleyicilerini yükleme.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio'da Roslyn çözümleyicilerini yükleme](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Roslyn çözümleyicilerini Visual Studio'da kullanın](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da hızlı Eylemler](../ide/quick-actions.md)
- [Kendi Roslyn çözümleyicinizi yazma](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET derleyici Platformu SDK'sı](/dotnet/csharp/roslyn-sdk/)