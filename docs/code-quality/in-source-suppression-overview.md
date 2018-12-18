---
title: Kod çözümleme uyarılarını bastırma
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 1e90de7acf13ca28a20a35aa3ad3e70f58780279
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513052"
---
# <a name="suppress-code-analysis-warnings"></a>Kod çözümleme uyarılarını bastırma

Genellikle, bir uyarı geçerli olmadığını göstermek kullanışlıdır. Bu, kod gözden geçirildi ve uyarı gizlenebilir takım üyeleri gösterir. Kaynak gizleme (ISS) kullanan <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> bir uyarıyı bastırmak için özniteliği. Öznitelik, uyarıyı oluşturan kod kesimi yakın yerleştirilebilir. Ekleyebileceğiniz <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğini kaynak dosyaya, yazarak veya kısayol menüsünden bir uyarı kullanabilirsiniz **hata listesi** otomatik olarak eklemek için.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Yalnızca derleme zamanında code_analysıs derleme simge tanımlanmışsa, yönetilen kod derlemenizin IL meta verilerde bulunan conditional özniteliği bir özniteliktir.

C + +/ CLI, CA makroları\_BASTIR\_ileti veya CA\_genel\_öznitelik eklemek için üst bilgi dosyasının SUPPRESS_MESSAGE.

> [!NOTE]
> Kaynak gizlemeleri yayın derlemelerinde kaynak gizleme meta verileri yanlışlıkla sevkiyat önlemek için kullanmamanız gerekir. Ayrıca, kaynak gizleme işleme maliyetini nedeniyle, uygulamanızın performansı düşebilir.

> [!NOTE]
> Bir projeyi Visual Studio 2017'ye geçirirseniz, birden çok sayıda kod çözümleme uyarıları karşılaştığı. Bu uyarılar geldiğini [Roslyn Çözümleyicileri](roslyn-analyzers-overview.md). Uyarıları gidermek hazır değilseniz, bunların tümünün seçerek gizleyebilirsiniz **Çözümle** > **kod analizini Çalıştır ve etkin sorunlar bastır**.
>
> ![Kod Analizi çalıştırmak ve Visual Studio sorunları Gizle](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage özniteliği

Seçeneğini belirlediğinizde **bastır** bir kod analizi uyarı bağlamı veya sağ tıklama menüsünden **hata listesi**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliği, kodunuzda veya projenin genel gizlemeyi eklenir dosya.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Özniteliği şu biçime sahiptir:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Öznitelik özelliklerini içerir:

- **Kategori** -kategori kural tanımlanır. Kod Analizi kural kategorileri hakkında daha fazla bilgi için bkz: [yönetilen kod uyarıları](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Checkıd** -kural tanımlayıcısı. Hem bir kural tanımlayıcısı için kısa ve uzun ad desteği içerir. CAXXXX kısa adıdır; uzun CAXXXX:FriendlyTypeName adıdır.

- **Gerekçe** -iletisini engelleme nedenini belge için kullanılan metin.

- **MessageID** -bir sorun için her iletinin benzersiz tanımlayıcısı.

- **Kapsam** -hedef üzerinde uyarı engellenir. Hedef belirtilmemişse, özniteliğin hedef ayarlanır. Desteklenen kapsamları aşağıdakileri içerir:

    - Modül

    - Ad Alanı

    - Kaynak

    - Tür

    - Üye

- **Hedef** - üzerinde uyarı engellenir hedef belirtmek için kullanılan tanımlayıcı bir. Tam öğe adı içermelidir.

## <a name="suppressmessage-usage"></a>SuppressMessage kullanımı

Kod çözümleme uyarıları hangi düzeyde gizlenir <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliği uygulanır. Örneğin, öznitelik, derleme, modül, tür, üye veya parametre düzeyinde uygulanabilir. Bunun amacı, sıkı bir şekilde kod gizleme bilgileri eşleştiği ihlalin gerçekleştiği sağlamaktır.

Kural kategorisi ve kural adı isteğe bağlı okunabilir bir temsilini içeren bir kural tanımlayıcısı genel formu gizleme içerir. Örneğin:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Kaynak gizleme meta veriler en aza indirmek için katı Performans nedeniyle varsa, kural adı atlanmış olabilir. Kural kategorisi ve kural kimliği birlikte yeterince benzersiz kural tanımlayıcısı oluşturur. Örneğin:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Kural adı atlama bakım nedeniyle önerilmez.

## <a name="suppress-selective-violations-within-a-method-body"></a>Bir yöntem gövdesi içindeki seçmeli ihlallerini gösterme

Gizleme öznitelikler, bir yönteme uygulanabilir, ancak bir yöntem gövdesinde eklenemiyor. Yani eklerseniz, belirli bir kural tüm ihlalleri gizlenen <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğini yöntemine.

Bazı durumlarda, böylece sonraki kodu Kod Analizi kural dışında otomatik olarak muaf değil ihlali, örneğin belirli bir örneğini gizlemek isteyebilirsiniz. Belirli kod analizi kuralları kullanarak bunu izin `MessageId` özelliği <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliği. Genel olarak, belirli sembol (bir yerel değişken veya parametre) saygı üzerinde ihlalleri eski kuralları `MessageId` özelliği. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) böyle bir kural örneğidir. Ancak, eski kuralları ihlalleri yürütülebilir kodu (sembolü olmayan) değil dikkate `MessageId` özelliği. Ayrıca, .NET derleyici Platformu ("Roslyn") Çözümleyicileri saygı `MessageId` özelliği.

Bir kural belirli bir sembol ihlalini bastırmak için sembol adını belirtin. `MessageId` özelliği <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliği. Aşağıdaki örnek, iki ihlalleri koduyla gösterir [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;biri `name` değişkeni, diğeri de `age` değişkeni. Yalnızca ihlali için `age` sembol geçersiz kılınır.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Oluşturulan kod

Yönetilen kod derleyicileri ve bazı üçüncü taraf araçları hızlı kod geliştirme kolaylaştırmak için kod oluşturur. Kaynak dosyalarında görünür, derleyicinin ürettiği kodu ile işaretlenmiş genellikle `GeneratedCodeAttribute` özniteliği.

Kod Analizi uyarıları ve hataları üretilen kod için engellenip engellenmeyeceğini seçebilirsiniz. Bu tür uyarılar ve hatalar gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: üretilen kod için uyarıları bastır](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Kod Analizi yoksayar `GeneratedCodeAttribute` zaman uygulandığı bütünleştirilmiş tamamını veya tek bir parametre.

## <a name="global-level-suppressions"></a>Genel düzeyi gizlemelerinin

Yönetilen kod analizi aracı inceler `SuppressMessage` derleme, modül, tür, üye veya parametre düzeyinde uygulanan öznitelikler. Ayrıca, kaynakları ve ad alanlarına karşı ihlalleri tetikler. İhlalleri genel düzeyde uygulanması gerekir ve kapsamına ve hedef. Örneğin, aşağıdaki ileti bir ad alanı ihlali engeller:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Ad alanı kapsamında bir uyarıyla gizlediğinizde, ad karşı uyarı bastırır. Ad alanı içindeki türleri karşı uyarı engellemez.

Açık bir kapsam belirterek herhangi bir gizleme ifade edilebilir. Bu gizlemeleri genel düzeyde bulunmalıdır. Bir tür tasarlayarak üye düzeyinde gizleme belirtemezsiniz.

Genel düzeyi gizlemelerinin açıkça sağlanan kullanıcının kaynağa eşlenmiyor derleyicinin ürettiği kodu başvuran iletilerinin gösterilmemesini tek yoludur. Örneğin, aşağıdaki kod bir ihlali derleyici yayılan bir oluşturucu karşı engeller:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` her zaman tam öğe adı içerir.

## <a name="global-suppression-file"></a>Küresel bir gizleme dosyası

Küresel bir gizleme dosyası genel düzeyi gizlemelerinin ya da bir hedef belirtmeyin gizlemeleri gizlemeleri tutar. Örneğin, derleme düzeyi ihlalleri gizlemeleri bu dosyada depolanır. Ayrıca, proje düzeyi ayarları bir formun arkasındaki kod için kullanılabilir olmadığından bazı ASP.NET gizlemeleri bu dosyada depolanır. Küresel bir gizleme dosyası oluşturulur ve projeniz için seçtiğiniz ilk kez eklendi **proje gizleme dosyası** seçeneği **bastır** komutunu **hata listesi**penceresi.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.CodeAnalysis>
- [Roslyn çözümleyicilerini kullanın](../code-quality/use-roslyn-analyzers.md)