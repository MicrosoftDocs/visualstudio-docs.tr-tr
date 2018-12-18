---
title: 'CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4cbb4c6ea167dd06328c3cce513f42cdfcf3c7a1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546424"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Ortak tür eşitlik işlecini uygular, ancak geçersiz <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Kural açıklaması

Eşitlik işleci işlevselliğini erişmeye sözdizimsel olarak kullanışlı bir yol olması amaçlanmıştır <xref:System.Object.Equals%2A> yöntemi. Eşitlik işleci uygularsanız, mantıksal olarak aynı olmalıdır <xref:System.Object.Equals%2A>.

Kodunuzu bu kuralı ihlal ediyorsa C# derleyicisinin bir uyarı verir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için eşitlik işlecini uygulamasını kaldırmak, ya da geçersiz kılma <xref:System.Object.Equals%2A> ve iki yöntem dönüş değerlerine sahip. Eşitlik işleci tutarsız davranışa sebep değil, uygulaması sağlayarak ihlali düzeltebilirsiniz <xref:System.Object.Equals%2A> çağrılarının <xref:System.Object.Equals%2A> yöntemi temel sınıf.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Eşitlik işleci'nın devralınmış uygulaması aynı değer döndürürse bu kuraldan bir uyarıyı bastırmak güvenlidir <xref:System.Object.Equals%2A>. Bu makaledeki örneklerde, güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak bir tür içerir.

## <a name="examples-of-inconsistent-equality-definitions"></a>Tutarsız eşitlik tanımları örnekleri

Aşağıdaki örnek, bir tür eşitlik tutarsız tanımlarını içeren gösterir. `BadPoint` Eşitlik anlamını eşitlik işlecini bir özel uygulanışı sağlayarak değişir, ancak geçersiz <xref:System.Object.Equals%2A> böylece aynı şekilde davranır.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Aşağıdaki kod, davranışı testleri `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

Aşağıdaki örnek, teknik olarak bu kuralı ihlal ediyor, ancak tutarlı bir şekilde davranmaz bir tür gösterir.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Aşağıdaki kod, davranışı testleri `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Sınıf örneği

Aşağıdaki örnek bu kuralı ihlal eden bir sınıf (başvuru türü) gösterir.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Aşağıdaki örnek, geçersiz kılarak ihlali düzeltmeleri <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Yapısı örneği

Aşağıdaki örnek bu kuralı ihlal eden bir yapısı (değer türü) gösterilmektedir:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Aşağıdaki örnek, geçersiz kılarak ihlali düzeltmeleri <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>İlgili kuralları

[CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)