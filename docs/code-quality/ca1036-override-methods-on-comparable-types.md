---
title: 'CA1036: Karşılaştırılabilir türlerde geçersiz kılma yöntemleri'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed69ba759d63ba27114bc097ac1fd9ccbe424edd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547744"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Karşılaştırılabilir türlerde geçersiz kılma yöntemleri

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür uygulayan <xref:System.IComparable?displayProperty=fullName> arabirim ve geçersiz <xref:System.Object.Equals%2A?displayProperty=fullName> veya dile özgü işleci eşitlik, eşitsizlik durumu olabilir, daha az aşırı değil-daha küçük veya büyük-daha. Türü arabiriminin bir uygulamasını devralırsa kuralı ihlal raporlamaz.

## <a name="rule-description"></a>Kural açıklaması

Özel sıralama düzenini tanımlamak türleri uygulayan <xref:System.IComparable> arabirimi. <xref:System.IComparable.CompareTo%2A> Yöntem türü iki örneği için doğru sıralama düzenini belirten bir tamsayı değeri döndürür. Bu kural, bir sıralama düzeni kümesi türlerini tanımlar. Gelir bir sıralama düzeni ayarı olağan anlamını eşitlik, eşitsizlik durumu olabilir, daha az-daha küçük ve büyük-daha geçerli değildir. Bir uygulamasını sağlaması zaman <xref:System.IComparable>, genellikle gerekir ayrıca geçersiz <xref:System.Object.Equals%2A> ile tutarlı olan değerler döndürür, böylece <xref:System.IComparable.CompareTo%2A>. Kılarsanız <xref:System.Object.Equals%2A> ve Kodladığınız İşleç aşırı yüklemeleri destekler bir dilde tutarlı işleçleri de sağlamalıdır <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için geçersiz kılın <xref:System.Object.Equals%2A>. İşleç aşırı yüklemesi programlama dilini destekler, aşağıdaki işleçleri sağlayın:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

C# içinde bu işleçler temsil etmek için kullanılan belirteçleri aşağıda belirtilmiştir:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Visual Basic ile olduğu gibi İşleç aşırı yüklemesi, işleçler ve programlama dilini eksik ihlali neden olduğu CA1036 desteklemiyor kuraldan bir uyarıyı bastırmak güvenlidir. Op_Equality işleçleri uygulamaya karar verirseniz, uygulama bağlamında mantıklı dışında eşitlik işleçlerde tetiklendiğinde için bu kuraldan bir uyarıyı bastırmak güvenlidir. Her zaman ancak op_Equality gerekir ve Object.equals'ı geçersiz kılarsanız == işleci.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru uygulayan bir tür içerir <xref:System.IComparable>. Kod açıklamaları için ilgili çeşitli kuralları karşılayan yöntemleri tanımlamak <xref:System.Object.Equals%2A> ve <xref:System.IComparable> arabirimi.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama davranışını testleri <xref:System.IComparable> daha önce gösterilen uygulama.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Eşitlik İşleçleri](/dotnet/standard/design-guidelines/equality-operators)