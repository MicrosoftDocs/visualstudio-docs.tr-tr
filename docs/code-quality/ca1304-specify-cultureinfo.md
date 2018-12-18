---
title: 'CA1304: CultureInfo belirtme'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe02dd66b523e6ee82c5e1a2051f3a68839957d4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546203"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo belirtme

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Yöntem veya Oluşturucu kabul eden aşırı yüklenmiş bir üyeyi çağıran bir <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> parametresi ve yöntem veya Oluşturucu alan aşırı yüklemesini çağırmaz <xref:System.Globalization.CultureInfo> parametresi. Bu kural aşağıdaki yöntemlere yapılan çağrılar yok sayar:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Kural açıklaması

Olduğunda bir <xref:System.Globalization.CultureInfo> veya <xref:System.IFormatProvider?displayProperty=nameWithType> nesnesi sağlanmadı, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir. Ayrıca, .NET Framework üyeleri varsayılan kültür seçin ve biçimlendirme, kodunuz için doğru olmayabilir varsayımlar dayanır. Kod senaryolarınız için beklendiği gibi çalıştığından emin olmak için aşağıdaki kılavuzlara göre kültüre özgü bilgileri vermeniz gerekir:

- Değeri kullanıcıya görüntülenir, geçerli kültür kullanın. Bkz: <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Diğer bir deyişle, bir dosya ya da veritabanı, kalıcı bir değeri depolanan ve yazılım tarafından erişilen, sabit kültür kullanın. Bkz: <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Hedef değerin bilmiyorsanız, veri tüketici sahip veya sağlayıcıyı kültür.

Varsayılan davranışı, aşırı yüklü üye gereksinimleriniz için uygun olsa bile, böylece kendi belge ve daha kolay tutulan kodunuzu kültüre özgü aşırı açıkça çağırmak daha iyidir.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> yalnızca bir örneğini kullanarak yerelleştirilmiş kaynakları almak için kullanılan <xref:System.Resources.ResourceManager?displayProperty=nameWithType> sınıfı.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için alan aşırı yüklemesini kullanın. bir <xref:System.Globalization.CultureInfo> bağımsız değişken.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Varsayılan kültürü doğru seçimdir belirli olduğunda ve kod bakımı önemli geliştirme önceliği olmadığı bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example-showing-how-to-fix-violations"></a>İhlaller nasıl düzeltilir gösteren örnek

Aşağıdaki örnekte, `BadMethod` iki bu kural ihlalleri neden olur. `GoodMethod` Sabit kültür için geçirerek ilk ihlali düzeltir <xref:System.String.Compare%2A?displayProperty=nameWithType>ve geçerli kültürü için geçirerek ikinci ihlali düzeltir <xref:System.String.ToLower%2A?displayProperty=nameWithType> çünkü `string3` kullanıcıya görüntülenir.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Biçimlendirilmiş çıktı örneği gösterme

Aşağıdaki örnek, varsayılan olarak geçerli kültürü etkisini gösterir <xref:System.IFormatProvider> tarafından seçilen <xref:System.DateTime> türü.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>İlgili kuralları

- [CA1305: IFormatProvider belirtin](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Ayrıca bkz.

- [CultureInfo sınıfını kullanma](/dotnet/standard/globalization-localization/globalization#Cultures)