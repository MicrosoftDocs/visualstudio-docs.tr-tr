---
title: Roslyn çözümleyicilerini yapılandırma ve kullanma
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 47dc7d38a2ae9b842891d2e36aebd9b009297cbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817047"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Yapılandırma ve Roslyn çözümleyicisi kuralları kullanma

.NET derleyici Platformu ("Roslyn") çözümleyicisi kuralları veya *tanılama*, siz yazarken, C# veya Visual Basic kodunu çözümlemek. Her tanı projeniz için geçersiz kılınabilir bir varsayılan önem derecesi ve gizleme durumu vardır. Bu makale, kural kümeleri kullanma ve gizleme ihlalleri, ayar kural önem derecesi kapsar.

## <a name="analyzers-in-solution-explorer"></a>Çözüm Gezgini'nde çözümleyiciler

Çözümleyici tanılamadan özelleştirmesini çoğunu yapabileceğiniz **Çözüm Gezgini**. Varsa, [çözümleyicilerini yükleme](../code-quality/install-roslyn-analyzers.md) bir NuGet paketi olarak bir **Çözümleyicileri** düğümü altında görünür **başvuruları** veya **bağımlılıkları** düğümü **Çözüm Gezgini**. Genişletirseniz **Çözümleyicileri**ve çözümleyici bütünleştirilmiş kodlarının birini genişletin, derlemedeki tüm tanılama görürsünüz.

![Çözüm Gezgininde çözümleyiciler](media/analyzers-expanded-in-solution-explorer.png)

Varsayılan önem derecesi ve açıklama dahil olmak üzere, bir tanılama özelliklerini görüntüleyebilirsiniz **özellikleri** penceresi. Özelliklerini görüntülemek için kuralı sağ tıklatın ve **özellikleri**, kuralı seçin ve sonra basın **Alt**+**Enter**.

![Özellikler penceresindeki tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Bir tanılama için çevrimiçi belgeleri görmek için tanı üzerinde sağ tıklayıp **Yardımı Görüntüle**.

Her tanı yanındaki simge **Çözüm Gezgini** kural Düzenleyicisi'nde açtığınızda kümesi içinde gördüğünüz simgeler karşılık gelir:

- bir daire içinde "i" belirten bir [önem derecesi](#rule-severity) , **bilgileri**
- "!" bir üçgen gösteren bir [önem derecesi](#rule-severity) , **Uyarısı**
- bir daire "x" belirten bir [önem derecesi](#rule-severity) , **hata**
- açık renkli arka plan üzerinde bir daire içinde "i" belirten bir [önem derecesi](#rule-severity) , **gizli**
- aşağıyı gösteren ok bir daire içinde tanılama bastırılır gösterir

![Çözüm Gezgini'nde tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Kural kümeleri

A [kural kümesi](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) bireysel tanılama için önem derecesi ve gizleme durumunu depolayan bir XML dosyasıdır. Tek bir proje için kural kümeleri uygulamak ve bir proje birden çok kural kümesi olabilir. Etkin kural Düzenleyicisi'nde kümesi görüntülemek için sağ **Çözümleyicileri** düğümünde **Çözüm Gezgini** seçip **açık etkin kural kümesi**. Bu kural eriştiğiniz ilk kez verilirse, adlı bir dosya  *\<projectname > .ruleset* projeye eklenir ve görünür **Çözüm Gezgini**.

> [!NOTE]
> Kural kümeleri (ikili) statik kod analizi hem Roslyn çözümleyicisi kuralları içerir.

Etkin kural için bir proje üzerinde kümesi değiştirebilirsiniz **Kod Analizi** bir projenin özelliklerini sekmesi. Kural kümesi seçin **bu kural kümesini Çalıştır** aşağı açılan listesi. Kümeden kuralı da açabilirsiniz **Kod Analizi** seçerek özellik sayfası **açın**.

## <a name="rule-severity"></a>Kural önem derecesi

Önem derecesi Çözümleyicisi kuralları yapılandırabilirsiniz veya *tanılama*ise, [çözümleyicilerini yükleme](../code-quality/install-roslyn-analyzers.md) bir NuGet paketi olarak. Aşağıdaki tablo önem derecesi seçenekleri tanılama için gösterir:

|Önem Derecesi|Derleme zamanı davranışı|Düzenleyici davranışı|
|-|-|-|
|Hata|İhlalleri görünür olarak *hataları* içinde **hata listesi** ve komut satırı derleme çıkışı ve derlemeler başarısız olmasına neden olur.|Kod sorunlu altı çizili bir kırmızı dalgalı ve kaydırma çubuğundaki küçük kırmızı kutu olarak işaretlenmiş.|
|Uyarı|İhlalleri görünür olarak *uyarıları* içinde **hata listesi** ve komut satırı derleme çıkışı, ancak derleme başarısız olmasına neden olmaz.|Sorunlu kod içeren bir yeşil dalgalı ve kaydırma çubuğundaki küçük yeşil kutu işaretli altı çizili olduğundan.|
|Bilgi|İhlalleri görünür olarak *iletileri* içinde **hata listesi**ve hiçbir komut satırı derleme çıktı.|Kod sorunlu altı çizili ile dalgalı ve kaydırma çubuğundaki gri küçük Kutu işaretli bir gri olur.|
|Hidden|Non-kullanıcıya görünür.|Non-kullanıcıya görünür. Tanılama için IDE tanılama altyapısı, ancak bildirilir.|
|Yok.|Tamamen gizlendi.|Tamamen gizlendi.|

Ayrıca, "bir uyarı kuralının önem derecesi olarak ayarlayıp sıfırlayabilirsiniz" **varsayılan**. Her tanılama görülebilir bir varsayılan önem derecesine sahip **özellikleri** penceresi.

Aşağıdaki ekran görüntüsünde, Kod düzenleyicisinde, üç farklı önem dereceleri ile üç farklı tanılama ihlallerini gösterir. Dalgalı yanı sıra küçük kaydırma çubuğunun sağ taraftaki kutuya rengini dikkat edin.

![Kod Düzenleyicisi'nde hata, uyarı ve bilgi ihlali](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde görünürler aynı üç ihlallerini gösterir **hata listesi**:

![Hata listesinde hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

Bir kuraldan önemi değiştirebilirsiniz **Çözüm Gezgini**, veya içinde  *\<projectname > .ruleset* kuraldaöneminideğiştirdiktensonraçözümedosyası **Çözüm Gezgini**.

![Çözüm Gezgini'nde kural kümesi dosyası](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Çözüm Gezgini'nden kural önem derecesi ayarlamak için

1. İçinde **Çözüm Gezgini**, genişletme **başvuruları** > **Çözümleyicileri** (**bağımlılıkları**  >  **Çözümleyicileri** .NET Core projeleri için).

1. Önem derecesi için ayarlamak istediğiniz kuralı içeren derleme genişletin.

1. Sağ tıklatın ve kural **kural kümesi önem derecesini ayarlayın**. Açılan menüde, önem derecesi seçeneklerden birini seçin.

   Kural önem derecesi etkin kural kümesi dosyasına kaydedilir.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Kural kümesi için dosya kuralında önem ayarlama

1. Açık kural dosyasını çift tıklayarak kümesi **Çözüm Gezgini**u seçerek **açık etkin kural kümesi** sağ tıklama menüsünde **Çözümleyicileri** düğümünü veya seçerek **Açık** üzerinde **Kod Analizi** projenin özellik sayfası.

1. Kuralı, derlemeyi içeren genişleterek göz atın.

1. İçinde **eylem** sütununda açılan listesini açmak için bir değer seçin ve listeden istediğiniz önem derecesini seçin.

   ![Kural kümesi dosyası düzenleyicide Aç](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>İhlallerini gösterme

Kural ihlallerinin bastırmak için birden çok yolu vardır:

- Tüm geçerli ihlal gizlemek için seçin **Çözümle** > **kod analizini Çalıştır ve etkin sorunlar bastır** menü çubuğundaki. Bu bazen "taban çizgisi oluşturma" adlandırılır.

- Bir tanılama işlemince bastırmak için **Çözüm Gezgini**, önemine kümesine **hiçbiri**.

- Kural kümesi Düzenleyici'den bir tanılama bastırmak için adının yanındaki kutuyu'seçeneğinin işaretini kaldırın veya ayarlayın **eylem** için **hiçbiri**.

- Kod düzenleyicisinden bir tanılama bastırmak için tuşuna basın ve ihlali ile kod satırının imleci yerleştirin. **Ctrl**+**.** açmak için **hızlı Eylemler** menüsü. Seçin **CAxxxx bastır** > **kaynağındaki** veya **CAxxxx bastır** > **gizleme dosyasında**.

   ![Hızlı Eylemler menüsünden tanılama Gizle](media/suppress-diagnostic-from-editor.png)

- Bir tanılama işlemince bastırmak için **hata listesi**, bkz: [hata Listesi'ndeki ihlallerini gösterme](#suppress-violations-from-the-error-list).

### <a name="suppress-violations-from-the-error-list"></a>Hata listesinde ihlallerini gösterme

Bir veya daha çok tanılamadan gizleyebilirsiniz **hata listesi** bastırmak için istediklerinizi seçerek ve ardından sağ tıklayarak ve seçerek **bastır** > **içinde kaynak**  veya **bastır** > **gizleme dosyasında**.

- Seçerseniz **içinde kaynak**, **Değişiklikleri Önizle** iletişim kutusu açılır ve C# önizlemesini [#pragma Uyarısı](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) veya Visual Basic [#DisableUyarısı](/dotnet/visual-basic/language-reference/directives/directives) kaynak koduna eklenen yönergesi.

   ![#Pragma uyarısı kod dosyasına ekleme Önizleme](media/pragma-warning-preview.png)

- Seçerseniz **gizleme dosyası içinde**, **Değişiklikleri Önizle** iletişim kutusu açılır ve önizlemesini <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliği genel dosyasına eklenir.

   ![SuppressMessage özniteliğini gizleme dosyasına ekleme Önizleme](media/preview-changes-in-suppression-file.png)

İçinde **Değişiklikleri Önizle** iletişim kutusunda **Uygula**.

**Hata listesi** Tanılama veya ihlalleri, hem Canlı kod analizi ve yapı kuralı görüntüler. Derleme tanılama eski olduğundan, ve ihlali gidermek için kodu düzenlenmiş, ancak henüz yeniden, örneğin, bu Tanılama'ya başlatmayı önleyemez **hata listesi**. Ancak, tanılama Canlı analysis veya IntelliSense, her zaman geçerli kaynaklarıyla güncel olduğundan ve gelen gizlenebilir **hata listesi**. Gizleme seçeneğini sağ tıklayın veya bağlam menüsünde devre dışıysa, çünkü bir veya daha fazla tanılama Seçiminizdeki yapı olasıdır. Derleme tanılama seçimden hariç tutmak için geçiş **hata listesi** kaynak filtresinden **derleme + IntelliSense** için **yalnızca IntelliSense**. Ardından daha önce açıklandığı gibi yarayan istediğiniz Tanılama'yı seçin.

![Visual Studio hata listesi kaynak filtresi](media/error-list-filter.png)

> [!NOTE]
> NuGet Çözümleyicileri, sahip olan bir projeyi bir başvuru eklerken bir .NET Core projesinde bu Çözümleyicileri otomatik olarak bağımlı projenin çok eklenir. Örneğin bağımlı proje bir birim test projesi ise, bu davranışı devre dışı bırakmak için NuGet paketini private olarak işaretlemek *.csproj* veya *.vbproj* başvurulan projenin dosya:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="command-line-usage"></a>Komut satırı kullanımı

Komut satırında projenizi yapılandırdığınızda, aşağıdaki koşullar karşılandığında kural ihlalleri oluşturma çıktısında görüntülenir:

- Çözümleyiciler, bir VSIX uzantısı değil de, bir Nuget paketi olarak yüklenir.

- Bir veya daha fazla kural projenin kodda ihlal.

- [Önem derecesi](#rule-severity) ihlal edilen kuralını ayarlandığından **uyarı**, bu durumda ihlalleri, derleme başarısız olmasına neden olmaz veya **hata**, bu durumda ihlalleri derleme başarısız olmasına neden.

Kural ihlallerinin gösterilip gösterilmeyeceğini yapı çıkış ayrıntı etkilemez. Bile **sessiz** ayrıntı düzeyi, kural ihlalleri oluşturma çıktısında görüntülenir.

> [!TIP]
> Statik Kod Analizi ile komut satırı çalıştırma için alışkın değilseniz *FxCopCmd.exe* veya msbuild ile **RunCodeAnalysis** bayrak, Roslyn çözümleyicileriyle Bunu yapmak nasıl aşağıda verilmiştir.

Msbuild kullanarak proje oluşturduğunuzda komut satırında Çözümleyicisi ihlalleri görmek için şunun gibi bir komut çalıştırın:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Aşağıdaki görüntüde Çözümleyicisi Kuralı ihlali içeren bir proje oluşturma komut satırı derleme çıktı gösterilmektedir:

![MSBuild çıkışıyla kuralı ihlali](media/command-line-build-analyzers.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Roslyn çözümleyicilerini Visual Studio'da genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Roslyn Çözümleyicisi hata bildirme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümeleri kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod çözümleme uyarılarını bastırma](../code-quality/in-source-suppression-overview.md)