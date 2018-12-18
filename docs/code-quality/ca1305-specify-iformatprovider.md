---
title: 'CA1305: IFormatProvider belirtme'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 05e2efde1be3430f95b00edbe8da8f952efad758
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174312"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider belirtme

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Yöntem veya Oluşturucu kabul eden aşırı yüklemelere sahip bir veya daha fazla üye çağıran bir <xref:System.IFormatProvider?displayProperty=fullName> parametresi ve yöntem veya Oluşturucu alan aşırı yüklemesini çağırmaz <xref:System.IFormatProvider> parametresi.

Bu kural yoksayılıyor olarak belgelenmiş olan .NET Framework yöntemlere yapılan çağrılar yoksayar <xref:System.IFormatProvider> parametresi. Kural ayrıca, aşağıdaki yöntemlerden yok sayar:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Kural açıklaması

Olduğunda bir <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> veya <xref:System.IFormatProvider> nesnesi sağlanmadı, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir. Ayrıca, .NET Framework üyeleri varsayılan kültür seçin ve biçimlendirme, kodunuz için doğru olmayabilir varsayımlar dayanır. Kod senaryolarınız için beklendiği gibi çalıştığından emin olmak için aşağıdaki kılavuzlara göre kültüre özgü bilgileri vermeniz gerekir:

- Değeri kullanıcıya görüntülenir, geçerli kültür kullanın. Bkz: <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Bir değeri depolanan ve (bir dosyadan veya veritabanından kalıcı) yazılım tarafından erişilen, sabit kültür kullanın. Bkz: <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Hedef değerin bilmiyorsanız, veri tüketici sahip veya sağlayıcıyı kültür.

Varsayılan davranışı, aşırı yüklü üye gereksinimleriniz için uygun olsa bile, böylece kendi belge ve daha kolay tutulan kodunuzu kültüre özgü aşırı açıkça çağırmak daha iyidir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için alan aşırı yüklemesini kullanın. bir <xref:System.IFormatProvider> bağımsız değişken. Veya, bir [C# ilişkilendirilmiş dize](/dotnet/csharp/tutorials/string-interpolation) ve geçirin <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> yöntemi.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Varsayılan biçimi doğru seçimdir belirli olduğunda ve kod bakımı önemli geliştirme önceliği olmadığı bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek

Aşağıdaki kodda, `example1` dize CA1305 kuralı ihlal ediyor. `example2` Dizesi geçirerek CA1305 kural karşılayan <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, uygulayan <xref:System.IFormatProvider>, <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. `example3` Dize bir araya alınmış dizeye geçirerek CA1305 kural karşılayan <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>İlgili kuralları

- [CA1304: CultureInfo belirtin](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Ayrıca bkz.

- [CultureInfo sınıfını kullanma](/dotnet/standard/globalization-localization/globalization#Cultures)