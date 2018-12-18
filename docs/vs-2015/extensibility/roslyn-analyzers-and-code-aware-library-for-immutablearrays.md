---
title: Roslyn Çözümleyicileri ve kod algılayan kitaplık Immutablearray'ler için | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4c5b7f145438d6c61ae58a18176d2dae579b128
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348549"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>ImmutableArray’ler için Roslyn Çözümleyicileri ve Kod Algılayan Kitaplık
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.NET derleyici platformu](https://github.com/dotnet/roslyn) ("Roslyn") kullanan kod kitaplıkları oluşturmanıza yardımcı olur. Bir kod algılayan kitaplık en iyi şekilde veya hatalarını önlemek için kullanabileceğiniz işlevsellik ve kitaplığı kullanmanıza yardımcı olması için (Roslyn Çözümleyicileri) araçları sağlar. Bu konuda kullanırken sık karşılaşılan hataları yakalamak için gerçek dünya Roslyn çözümleyicinizi oluşturma gösterilmektedir [NIB: Sabit koleksiyonlar](http://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet paketi. Örnek ayrıca çözümleyici tarafından bulunan bir kodu sorun için bir kod düzeltme sağlamak nasıl gösterir. Kullanıcılar, Visual Studio ampul UI içinde kod düzeltmeleri görmek ve bir düzeltme kod için otomatik olarak uygulanabilir.

## <a name="getting-started"></a>Başlarken
Bu örneği oluşturmak için gerekenler:

- Visual Studio 2015 (bir Express sürüm değil) veya sonraki bir sürümü. Ücretsiz kullanabileceğiniz [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Ayrıca, aynı zamanda SDK'yı yüklemek için ortak Araçlar altında Visual Studio genişletilebilirlik araçları Visual Studio'yu yüklerken denetleyebilirsiniz. Zaten Visual Studio yüklü değilse, ayrıca bu SDK'sı ana menüye gidip yükleyebileceğiniz **dosya &#124; yeni &#124;proje...** , C# sol gezinti bölmesinde seçerek ve sonra Extensibility seçme. Seçeneğini belirlediğinizde "**Visual Studio genişletilebilirlik Araçları'nı yükleme**" içerik haritası proje şablonu, ister indirmenizi ve SDK'sını yükleyin.

- [.NET derleyici Platformu ("Roslyn") SDK'sı](http://aka.ms/roslynsdktemplates). Ayrıca, ana menüsüne giderek bu SDK'sını yükleyebilirsiniz **dosya &#124; yeni &#124; proje...** seçip **C#** sol gezinti bölmesinde ve açıp **genişletilebilirlik**. Seçeneğini belirlediğinizde "**.NET derleyici Platformu SDK'sını indirin**" içerik haritası proje şablonu, ister indirmenizi ve SDK'sını yükleyin. Bu SDK'sı içerir [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Hangi kod model türleri şekil bu son derece kullanışlı araç yardımcı Çözümleyicisi'nde göz önünde bulundurmanız gerekenler. Çözümleyici altyapısı çağrıları kodunuzla belirli kod model türleri, kodunuzun yalnızca gerekli olduğunda yürütür ve yalnızca ilgili kodunu analiz etme üzerinde odaklanabilirsiniz.

## <a name="whats-the-problem"></a>Sorun nedir?
Imagine Immutablearray ile bir kitaplığı belirtin (örneğin, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) destekler. C# geliştiricilerin .NET dizileri deneyimiyle ilgili bulunmaktadır. Ancak, uygulamada kullanılan Immutablearray'ler ve iyileştirme tekniklerini yapısı nedeniyle, C# Geliştirici intuitions bozuk kod yazmak kitaplığınızın kullanıcılar aşağıda açıklandığı gibi neden. Ayrıca, kullanıcılar kendi hataları çalışma zamanı için Visual Studio .NET ile kullanılırlar kalite deneyimi olmayan kadar görmez.

Kullanıcılar, aşağıdaki gibi kod yazma ile ilgili bilgi sahibi olduğunuz:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

C# geliştiricilerin çok oturum sonraki kod satırlarını doldurmak için boş bir dizi oluşturma ve koleksiyon Başlatıcısı sözdizimi kullanılarak sahibisiniz. Ancak, aynı yazma bir Immutablearray kodunu çalışma zamanında kilitleniyor:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

Immutablearray uygulaması'nın temel alınan veri depolama sarmak için bir yapı kullanarak nedeniyle ilk hatasıdır. Yapılar, parametresiz oluşturucu olması gerekir böylece `default(T)` ifadeleri, tüm yapıları döndürebilir sıfır ya da boş üyeleri. Kod ne zaman eriştiği `b1.Length`, Immutablearray yapıda hiçbir temel alınan depolama dizisi olduğundan çalışma zamanında null bir başvuru hata yoktur. Boş bir Immutablearray oluşturmak için doğru yoldur `ImmutableArray<int>.Empty`.

 Koleksiyon başlatıcıları hatasıyla ImmutableArray.Add yöntemi her çağırdığında yeni örnekleri döndürüldüğünden gerçekleşir. Yeni bir öğe eklediğinizde Immutablearray'ler hiçbir zaman, çünkü bu değişiklik, (Bu, performansı artırmak için depolama önceden var olan bir Immutablearray ile paylaşabilir) yeni bir Immutablearray nesnesi geri alın. Çünkü `b2` çağırmadan önce ilk Immutablearray işaret `Add()` beş kez `b2` Immutablearray varsayılandır. Uzunluğu üzerinde ayrıca kilitlenme null ile çağırılıyor başvuru hatası. Kullanmak için el ile Ekle çağırma olmayan bir Immutablearray başlatmak için doğru şekilde `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>İlgili söz dizimi düğüm türleri, çözümleyici tetiklemek için bulma
Çözümleyici oluşturmaya başlamak için öncelikle SyntaxNode ne tür, aramak için gereken her şekil.   Başlat menüsünde Syntax Visualizer **görünümü &#124; diğer Windows &#124; Roslyn Syntax Visualizer**.

Düzenleyici giriş işaretini bildiren satıra Yerleştir `b1`. Söz dizimi görselleştiricisi gösterir bulunduğunuz göreceğiniz bir `LocalDeclarationStatement` sözdizimi ağacı düğümü. Bu düğüme sahip bir `VariableDeclaration`, sırayla sahip olduğu bir `VariableDeclarator`, sırayla sahip olduğu bir `EqualsValueClause`, son olarak bir `ObjectCreationExpression`. Düğümleri Syntax Visualizer ağacında tıkladığınızda, bu düğüm tarafından temsil edilen kod göstermek için söz dizimi düzenleyici penceresinde vurgular. C# dilbilgisi içinde kullanılan adları SyntaxNode alt türlerinin adlarını eşleştirin.

## <a name="creating-the-analyzer-project"></a>Çözümleyici projesi oluşturma
Ana menüden **dosya &#124; yeni &#124; proje...** . İçinde **yeni proje** iletişim altında **C#** projeleri sol gezinti çubuğundaki genişletilebilirlik seçin ve sağ bölmede seçin **Çözümleyicisi kod düzeltmesi ile** proje şablonu. Bir ad girin ve iletişim kutusunda onaylayın.

Şablonu DiagnosticAnalyzer.cs dosyasını açar. Bu düzenleyici arabellek sekmesini seçin. Bu dosya bir çözümleyici sınıfı vardır (oluşturulmuş proje adından verdiğiniz), türetilen `DiagnosticAnalyzer` (Roslyn API türü). Yeni sınıfınıza sahip bir `DiagnosticAnalyzerAttribute` , çözümleyici bildirmek için C# dilini ilgili derleyici bulur ve yükler, çözümleyici.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# kodunda'i hedefleyen Visual Basic kullanarak bir çözümleyici uygulayabilir ve bunun tersi de geçerlidir. Çözümleyicisi, bir dil veya her ikisini de hedefler seçmek için DiagnosticAnalyzerAttribute daha önemlidir. Ayrıntılı Modelleme Dili gerektiren daha karmaşık Çözümleyicileri yalnızca tek bir dil hedefleyebilirsiniz. Çözümleyici Örneğin, yalnızca tür adları veya ortak üye adlarını denetler, Visual Basic ve C# arasında Roslyn sunar ortak dil modelini kullanmanız mümkün olabilir. Örneğin, bir sınıf uyguladığını FxCop uyarır <xref:System.Runtime.Serialization.ISerializable>, ancak sınıf olmayan <xref:System.SerializableAttribute> özniteliği dilden bağımsızdır ve Visual Basic ve C# kodu için çalışır.

## <a name="initalizing-the-analyzer"></a>Initalizing Çözümleyicisi
Aşağı biraz kaydırın `DiagnosticAnalyzer` görmek için sınıf `Initialize` yöntemi. Bir çözümleyici etkinleştirirken, derleyici bu yöntemi çağırır. Yöntem alır bir `AnalysisContext` bağlam bilgileri edinin ve olayları çözümlemek istediğiniz kod türleri için geri aramaları kaydetme, çözümleyici sağlayan nesne.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Bu bağlamda yöntemi ve türü"." yeni bir satır Aç Bir IntelliSense tamamlanma listesini görmek için. Tamamlanma listesine dâhil kullanabileceğiniz birçok gördüğünüz `Register…` çeşitli olayları işlemek için yöntemleri. Örneğin, ilk öğe `RegisterCodeBlockAction`, kodunuz, genellikle kod kaşlı ayraçlar arasında olan bir blok için geri çağrı. Bir bloğu için kaydetme de geri kodunuza bir alan, bir öznitelik için belirtilen değer ya da isteğe bağlı bir parametre değeri için Başlatıcı çağırır.

Başka bir örnek olarak `RegisterCompilationStartAction`, kodunuzun pek çok konuma durumu toplamak, ihtiyacınız olduğunda yararlıdır bir derleme, başlangıcında geri çağrıları. Bir veri yapısı varsayalım, tüm sembolleri kullanıldığında, toplanacak oluşturabilir ve, çözümleyici geri bazı sözdizimi veya sembol, her çağrıldığında data yapınız her konum hakkında bilgileri kaydedebilirsiniz. Derleme bitiş nedeniyle geri adlandırılırlar, kaydettiğiniz, örneğin, hangi simgelerin kodu kullanan her rapor için tüm konumlarda çözümleyebilirsiniz `using` deyimi.

Kullanarak **Syntax Visualizer**, derleyici bir ObjectCreationExpression işlediğinde çağrılacak istediğiniz öğrendiniz. Geri çağırma ' ayarlamak için şu kodu kullanın:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Sözdizimi düğümü ve filtre yalnızca nesne oluşturma sözdizimi düğümleri için kaydolun. Kural gereği, bir lambda Çözümleyicileri durum bilgisiz tutmanıza yardımcı olan Eylemler, kaydolurken çözümleyici yazarlarının kullanın. Visual Studio özelliği kullanabileceğiniz **kullanımından Oluştur** oluşturmak için `AnalyzeObjectCreation` yöntemi. Bu bağlam parametresi doğru türde sizin için çok oluşturur.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Kullanıcılar, Analyzer'ın özelliklerini ayarlama
Visual STUDİO'da uygun şekilde, çözümleyici gösterilir böylece arayın ve kod, çözümleyici tanımlamak için aşağıdaki satırı değiştirin:

```csharp
internal const string Category = "Naming";
```

Değişiklik `"Naming"` için `"API Guidance"`.

Sonrakini Bul ve Resources.resx dosyasını kullanarak proje açın **Çözüm Gezgini**. Bir açıklama Çözümleyicisi, başlık, vb. için koyabilirsiniz. Tüm bu değeri değiştirebilirsiniz `“Don’t use ImmutableArray<T> constructor”` şimdilik. Dize, dize bağımsız değişken biçimlendirme koyabilirsiniz ({0}, {1}, vs.) ve üzeri çağırdığınızda `Diagnostic.Create()`, geçirilecek bağımsız değişkenleri params dizisi sağlayabilirsiniz.

## <a name="analyzing-an-object-creation-expression"></a>Bir nesne oluşturma ifadesi analiz etme
`AnalyzeObjectCreation` Yöntemi farklı türde bir kod Çözümleyicisi framework tarafından sağlanan bağlamı alır. Başlatma yöntemin `AnalysisContext` , çözümleyici ayarlamak için eylem geri çağırmaları kaydetmenize olanak sağlar. `SyntaxNodeAnalysisContext`, Örneğin, bir `CancellationToken` , geçici olarak geçirebilirsiniz. Bir kullanıcı bir düzenleyicide yazarak başlarsa, Roslyn kaydedin ve performansı artırmak için çalışan çözümleyiciler iptal eder. Başka bir örnek olarak, bu bağlam nesnesi oluşturma sözdizimi düğümü döndüren bir düğüm özelliği vardır.

Sözdizimi düğümü eylemi filtre türü varsayabilirsiniz düğüm alın:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Visual Studio, ilk kez Çözümleyicisi ile başlatılıyor
Oluşturma ve yürütme, Çözümleyicisi Visual Studio'yu başlatın (basın **F5**). Başlangıç projesi olmadığından **Çözüm Gezgini** kodunuzu ve bir VSIX kod yapılarınızı çalıştırma, VSIX projesi ve ardından Visual Studio, VSIX yüklü ile başlatır. Bu şekilde Visual Studio'yu başlatın, böylece Visual Studio ana kullanımınız, test örnekleri tarafından Çözümleyicileri oluşturulurken etkilenmez bir ayrı bir kayıt defteri kovanı ile başlatır. Bu şekilde başlatma ilk kez Visual Studio birkaç başlatmalar olduğunda, ilk Visual Studio yüklendikten sonra başlatılan için benzer yapar.

 Bir konsol projesi oluşturun ve ardından konsol uygulamaları Main yönteminiz dizi kodu girin:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

İle kod satırlarını `ImmutableArray` değişmez NuGet paketini alın ve eklemeniz gerekir çünkü dalgalı çizgiler sahip bir `using` kodunuzda deyimi. İçinde proje düğümüne sağ işaretçi düğmesine basın **Çözüm Gezgini** ve **NuGet paketlerini Yönet...** . NuGet Yöneticisi'nde, arama kutusuna "Genellikle" ve "Gt;System.Collections.Immutable" öğesini seçin ("Microsoft.Bcl.Immutable" seçmeyin) sol bölmesinde ve sağ bölmede yükle düğmesine basın. Paket yüklenirken, projenizin başvurularına bir başvuru ekler.

Altında kırmızı dalgalı çizgiler görmeye `ImmutableArray`, bu nedenle bu tanımlayıcı ve tuşuna giriş işaretini koyun **CTRL +.** önerilen düzeltme menüyü getirin ve uygun eklemek (nokta) `using` deyimi.

**Tümünü Kaydet ve Kapat** devam etmek için temiz bir duruma yerleştirmek için Visual Studio'yu Şimdi ikinci örneğini.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Düzenle ve devam et çözümleyicisini kullanarak tamamlama
Visual Studio'nun ilk örnekte, başında bir kesme noktası ayarlayın, `AnalyzeObjectCreation` tuşuna basarak yöntemi **F9** kelimeyi ilk satırdaki ile.

Çözümleyicisi ile yeniden başlatma **F5**ve Visual Studio'nun ikinci örneğini son kez oluşturduğunuz konsol uygulamanızı yeniden açın.

Roslyn derleyici bir nesne oluşturma ifadesi gördünüz ve, çözümleyicisine adlı kesme noktasında Visual Studio'nun ilk örneğine döndürür.

**Nesne oluşturma düğümü alın.** Ayarlar satırı üzerinden adımla `objectCreation` tuşuna basarak değişken **F10**hem de **komut penceresi** ifade `“objectCreation.ToString()”`. Değişkenin işaret sözdizimi düğümü kod olduğunu gördüğünüz `"new ImmutableArray<int>()"`, yalnızca aradıklarınızı.

**Immutablearray alma\<T > türü nesne.** Oluşturulan türü Immutablearray olup olmadığını denetlemek gerekir. İlk olarak, bu tür temsil eden nesnesini alın. Tam olarak doğru tür olması ve ToString() dizeden kendisiyle karşılaştırmayın emin olmak için anlam modeli kullanarak türlerini denetleyin. Aşağıdaki işlev sonunda kod satırını girin:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Genel türler backquotes (') sahip meta veriler ve genel parametre sayısı, belirlediğiniz. Görmezsiniz nedenle "... Immutablearray\<T > "meta veri adı.

Anlam modeli, semboller, veri akışı, değişken ömrü, vb. hakkında sorular sormak olanak tanıyan üzerindeki pek yararlı sahiptir. Roslyn söz dizimi düğümleri anlam modeli çeşitli mühendislik nedenlerle (modelleme hatalı kod, vb. performans.) ayırır. Doğru karşılaştırma için başvurular yer alan bilgileri aramak için derleme modelini kullanmanız gerekir.

Sarı yürütme işaretçisi Düzenleyicisi penceresinin sol tarafında sürükleyebilirsiniz. Ayarlar satırının adede kadar sürükleyin `objectCreation` değişkeni ve, yeni bir satır kod kullanarak üzerinden adımla **F10**. Değişkenin fare işaretçisini, `immutableArrayOfType`, gördüğünüz biz türünü tam anlamsal modelde bulunamadı.

**Nesne oluşturma ifadenin türü alın.** "Type" Bu makalede birkaç yöntemle kullanılır, ancak bu "Yeni Foo" olup olmadığını anlamına gelir. ifade, Foo modelinin almanız gereken. Immutablearray olup olmadığını görmek için nesne oluşturma ifadesi türü almanız gereken\<T > türü. Anlam modeli, nesne oluşturma ifadesinde tür simgesi (Immutablearray) için Sembol bilgilerini almak için yeniden kullanın. Aşağıdaki işlev sonunda kod satırını girin:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Çözümleyici eksik veya yanlış Düzenleyici arabellekler kodumuzda işliyoruz gerektiğinden (örneğin, eksik bir `using` deyimi), için denetlemelisiniz `symbolInfo` olan `null`. Analizi tamamlamak için Sembol bilgilerini nesneden adlandırılmış tür (INamedTypeSymbol) almanız gerekir.

**Türleri karşılaştırın.** Açık genel tür ki aradığınız t yoktur ve kod olarak gir somut bir genel tür olduğundan, ne tür (açık genel tür) oluşturulan için Sembol bilgilerini sorgulamak ve bu sonuç ile Karşılaştır `immutableArrayOfTType`. Yönteminin sonuna aşağıdaki girin:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Tanılama raporu.** Tanı raporlama oldukça kolaydır. Initialize yöntemi önce tanımlanan proje şablonu, sizin için oluşturulan kural kullanırsınız. Bu durumda kod bir hata olduğundan değiştirmek için kural başlatılan satırın değiştirebilirsiniz `DiagnosticSeverity.Warning` (yeşil dalgalı çizgi) ile `DiagnosticSeverity.Error` (kırmızı dalgalı çizgi). İzlenecek yol başlangıcı yakınında düzenlediğiniz kaynaklardan gelen kuralı geri kalanı başlatır. Ayrıca, nesne oluşturma expresssion'ın tür belirtimi'nın konumudur dalgalı oku için konum rapor gerekir. Bu kodu girin `if` engelle:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

İşlevinizi (belki de farklı bir şekilde biçimlendirilmiştir) şöyle görünmelidir:

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Kesme noktası Çözümleyicisi bkz (ve Visual Studio'nun ilk örneğine döndüren Durdur böylece) kaldırın. Yürütme işaretçisi yöntemi ve ENTER tuşuna başlangıcına kadar sürükleyin **F5** yürütme devam etmek için. Visual Studio'nun ikinci örneğine geçiş yaptığınızda, derleyici kodu yeniden inceleyin başlatılır ve, çözümleyicisine çağırır. Bir dalgalı çizgi altında gördüğünüz `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Kod sorunu için "Kod düzeltmesi" ekleme
Başlamadan önce Visual Studio'nun ikinci örneğini kapatın ve Visual Studio'nun (burada Çözümleyicisi geliştiriyorsunuz) ilk örneğinde hata ayıklamasını durdurun.

**Yeni bir sınıf ekleyin.** Çözüm Gezgini'nde, proje düğümü üzerinde (işaretçi sağ düğme) kısayol menüsünü kullanın ve yeni bir öğe eklemek seçin. Adlı bir sınıf ekleyin `BuildCodeFixProvider`. Bu sınıfın türetilmesi gerekir `CodeFixProvider`, ve kullanması gereken **CTRL +.** (nokta) doğru ekler kod düzeltme çağrılacak `using` deyimi. Bu sınıf ayrıca ile Açıklama gerekir `ExportCodeFixProvider` özniteliği ve eklemeniz gerekir bir `using` çözmek için deyimi `LanguageNames` sabit listesi. Aşağıdaki kodda ile bir sınıf dosyası olması gerekir:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Saplama kullanıma üyeler türetilmiş.** Artık, düzenleyici giriş işaretini bir tanımlayıcıda yerleştirin `CodeFixProvider` basın **CTRL +.** (Bu Özet temel sınıf uygulamasını kullanıma saptama için nokta). Bu özellik ve yöntem sizin için oluşturur.

**Özelliğini uygulayın.** Doldurun `FixableDiagnosticIds` özelliğin `get` gövdesi aşağıdaki kod ile:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn tanılama bir araya getirir ve yalnızca dizelerdir bu tanımlayıcıları eşleştirerek giderir. Proje şablonu tanılama kimliği sizin için oluşturulan ve değiştirmek ücretsizdir. Özellik kodda, yalnızca Çözümleyicisi sınıftan Kimliğini döndürür.

**RegisterCodeFixAsync yöntem bir bağlamı alır.** Bağlam bir kod düzeltmesi için birden çok tanılama uygulayabilir veya bir kod satırının birden fazla sorun olabilir çünkü önemlidir. "Bağlam" yazarsanız, yöntemin gövdesinde, IntelliSense tamamlama listesinin yararlı olan bazı üyeleri gösterir. Düzeltme iptal ister bir şeyler görmek için kontrol eden CancellationToken üye yok. Çok sayıda kullanışlı üyelerinin ve proje ve çözüm modeli nesneleri alabilmenizi sağlar belge üyesi yok. Başlangıç aralık bir üye yoktur ve ne zaman tanılama rapor kod konumu sonuna belirtilir.

**Oluşturma yöntemi, zaman uyumsuz olması.** Yapmanız gereken ilk şey olacak şekilde oluşturulan yöntem bildiriminde düzeltme olduğu bir `async` yöntemi. Bir soyut sınıf uygulamasını saptamaların için kod düzeltmesi içermez `async` anahtar sözcüğü döner olsa bile bir `Task`.

**Sözdizimi ağacının kökü alın.** Yeni bir söz dizimi ağacı değişikliklerle üretmek için ihtiyacınız olan kod değiştirmek için kod düzeltmenizi sağlar. Gereksinim duyduğunuz `Document` çağrılacak bağlamından `GetSyntaxRootAsync`. Dosyayı diskten alma, ayrıştırma ve bunun için Roslyn kod modeli oluşturma da dahil ederek söz dizimi ağacı almak için bilinmeyen iş olduğundan bir zaman uyumsuz yöntem budur. Visual Studio kullanıcı arabirimini kullanarak hangi bu süre boyunca, hızlı yanıt veren olmalıdır `async` sağlar. Yönteminde kod satırı aşağıdaki satırla değiştirin:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Sorunu düğümü bulunamıyor.** Bağlamın yayılma, ancak kodu değiştirmek zorunda olmayabilir bulduğunuz düğüm geçirmeniz. Bildirilen Tanılama, yalnızca aralık türü tanımlayıcısı (dalgalı çizgi nereye ait) için sağlanan, ancak tüm nesne oluşturma ifadesi değerini değiştirmeniz de dahil olmak üzere `new` keywoard başında ve sonunda parantezler. Aşağıdaki kod, yönteminize ekleyin (ve **CTRL +.** eklemek için bir `using` bildirimi `ObjectCreationExpressionSyntax`):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Ampul kullanıcı Arabirimi için kod düzeltmenizi kaydedin.** Kod düzeltmenizi kaydettiğinizde Roslyn UI Visual Studio ampul otomatik olarak yararlanmanıza imkan sağlar. Son kullanıcıların görebileceği kullanabilecekleri **CTRL +.** (nokta), çözümleyici squiggles bozuk olduğunda `ImmutableArray<T>` Oluşturucu kullanın. Bir sorun oluştuğunda, kod düzeltme sağlayıcısı yalnızca yürütüldüğünden, aradığınız nesne oluşturma ifadesi olması kabul edilebilir. Bağlam parametresinden sonuna aşağıdaki kodu ekleyerek yeni bir kod düzeltmesi kaydedebilirsiniz `RegisterCodeFixAsync` yöntemi:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Düzenleyici giriş işaretini bir tanımlayıcıda yerleştirmek gereken `CodeAction`, ardından **CTRL +.** uygun eklemek için (nokta) `using` bu tür için bildirimi.

Ardından, düzenleyici giriş işaretini yerleştirebilirsiniz `ChangeToImmutableArrayEmpty` tanımlayıcısı ve kullanım **CTRL +.** Bu metot taslağı yeniden oluşturmak için.

Eklediğiniz son Bu kod parçacığı geçirerek kod düzeltme kaydeder. bir `CodeAction` ve tanılama kimliği türüne ilişkin sorun bulundu. Bu örnekte, yoktur yalnızca biri için bu kod sağlayan tanılama kodu düzeltir tanılama kimlikleri dizinin ilk öğesi geçirmeniz yeterlidir. Oluştururken `CodeAction`, ampul UI kod düzeltme açıklaması kullanacağı metni geçirin. Ayrıca, bir CancellationToken alır ve yeni bir belge döndüren bir işlev de geçirin. Yeni belge çağırır düzeltilmiş kodunuzu içeren yeni bir sözdizimi ağacına sahip `ImmutableArray.Empty`. Bu kod parçacığı bir lambda kullanır, bu nesne yaratımı düğüm ve belge bağlamı'nın üzerinden kapatabilirsiniz.

**Yeni bir söz dizimi ağacı oluşturun.** İçinde `ChangeToImmutableArrayEmpty` yöntemi, saptama daha önce oluşturulan kod satırını girin: `ImmutableArray<int>.Empty;`. Söz dizimi görselleştiricisi araç penceresi yeniden görüntülerseniz, bu sözdizimi, SimpleMemberAccessExpression düğüm görebilirsiniz. Bu yöntem oluşturmak ve yeni bir belgede döndürmek gerekli olmasıdır.

İlk değişiklik `ChangeToImmutableArrayEmpty` eklemektir `async` önce `Task<Document>` çünkü kod oluşturucuları olmalıdır zaman uyumsuz yöntemin varsayamazsınız.

Aşağıdaki kod ile birlikte gövdede yönteminiz aşağıdaki gibi görünür, böylece doldurun:

```csharp

private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Düzenleyici giriş işaretini yerleştirmek ihtiyacınız olacak `SyntaxGenerator` tanımlayıcısı ve kullanım **CTRL +.** uygun eklemek için (nokta) `using` bu tür için bildirimi.

Bu kod `SyntaxGenerator`, yeni kod oluşturmak için çok yararlı bir tür olduğu. Bu belge için bir oluşturucuyu alma kodu sorun olduğunda `ChangeToImmutableArrayEmpty` çağrıları `MemberAccessExpression`istiyoruz erişmek için üye olan bir tür geçirme ve üyenin adını bir dize olarak geçirerek.

Ardından, yöntem belgesinin kök getirir ve kod genel durumda rastgele iş içerebildiğinden, bu çağrı bekler ve iptal belirtecini geçirir. Roslyn kod modelleri değişmez bir .NET dizeyle çalışmak gibidir; dize güncelleştirdiğinizde, yeni bir dize nesnesi iade alma. Çağırdığınızda `ReplaceNode`, yeni bir kök düğümü ulaşırsınız. Sözdizimi ağacı çoğunu (sabit olduğundan) paylaşılır, ancak `objectCreation` düğümü ile değiştirilir `memberAccess` söz dizimi ağacı kök kadar tüm üst düğümleri yanı sıra, düğüm.

## <a name="trying-your-code-fix"></a>Kod düzeltmenizi çalışıyor
Artık basabilirsiniz **F5** , Çözümleyicisi Visual Studio ikinci bir örneğini yürütmek için. Önceden kullanmış olduğunuz konsol projesi açın. Artık, yeni nesne oluşturma ifadesi için olduğu görünür ampul görmelisiniz `ImmutableArray<int>`. Basarsanız **CTRL +.** (Dönem), kodunuzu düzeltin ardından görür ve bir ampul kullanıcı Arabirimi otomatik olarak oluşturulan kodu fark önizlemede görürsünüz. Roslyn sizin için oluşturur.

Pro İpucu: Visual Studio'nun ikinci örneğini başlatabilir ve kod düzeltmenizi ampul görmüyorsanız, Visual Studio bileşen önbelleği temizlemek gerekebilir. Önbelleği temizleniyor, Visual Studio, en son bileşenini ardından seçmeniz gerekir, böylece bileşenleri yeniden incelemek için Visual Studio zorlar. İlk olarak, Visual Studio ikinci örneğini kapatın. Ardından Windows Gezgini'nde, kullanıcı dizinine gidin (c:\users\\< UserID\>) ve AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\. Bu dizinde ComponentModelCache alt dizini silin. "14" değişiklikleri sürümü ile Visual Studio sürümü.

## <a name="talk-video-and-finish-code-project"></a>Konuşma Video ve son kod projesi
Bu örnekte, ele alınan ve geliştirilmiş görebilirsiniz daha ayrıntılı olarak [bu konuşmada](http://channel9.msdn.com/events/Build/2015/3-725). Konuşma çalışma Çözümleyicisi gösterir ve oluşturma sürecinde size yol gösterir.

Tüm tamamlanan kodu gördüğünüz [burada](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Alt klasörleri DoNotUseImmutableArrayCollectionInitializer ve DoNotUseImmutableArrayCtor sorunları ve kullanıcı Arabirimi Visual Studio ampul içinde görünen kod düzeltmeleri uygulayan bir C# dosyası bulmak için bir C# dosyasına sahiptir. Unutmayın, tamamlanan kodu sahip Immutablearray getirilirken önlemek için biraz daha fazla soyutlama\<T > nesnesi tekrar tekrar yazın. İç içe geçmiş kayıtlı eylemleri kullanılabilir bir bağlamda tür nesnesi kaydetmek için kullandığı her alt işlemleri (nesne oluşturma analiz ve toplama başlatmalar analiz) yürütün.

## <a name="see-also"></a>Ayrıca Bkz.
[\\\Build 2015 konuşma](http://channel9.msdn.com/events/Build/2015/3-725)
[tamamlanan kodu github'da](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[çeşitli örnekler github'da Çözümleyicileri üç tür gruplandırılmış](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
 [GitHub OSS sitesindeki diğer docs](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
[Roslyn Çözümleyicileri github'da ile uygulanan FxCop kuralı](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)

