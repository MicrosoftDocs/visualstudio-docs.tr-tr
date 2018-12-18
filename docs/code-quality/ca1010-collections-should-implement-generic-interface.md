---
title: 'CA1010: Koleksiyonlar genel arabirim uygulamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5264292e6dc1e8cf86a64d41dc15154d836a8444
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915288"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Koleksiyonlar genel arabirim uygulamalıdır

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir türün uyguladığı <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirim ancak uygulamıyor <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> arabirimi ve içeren derleme hedefleri [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Bu kural uygulayan türler yoksayar <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Kural açıklaması
 Bir koleksiyon kullanılabilirliğini genişletmek için genel koleksiyon arabirimlerinden birini uygulayın. Ardından koleksiyonu, aşağıdaki gibi genel koleksiyon türlerini doldurmak için kullanılabilir:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için aşağıdaki genel koleksiyon arabirimlerinden birini uygulayın:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan bir uyarıyı bastırmak güvenlidir; Ancak, koleksiyonu daha sınırlı kullanım olacaktır.

## <a name="example-violation"></a>Örnek ihlali

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, genel olmayan türeyen bir sınıf (başvuru türü) gösterir. `CollectionBase` sınıfını, bu kuralı ihlal ediyor.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Açıklamalar
 Bu ihlal ihlalini düzeltmek için genel arabirimi uygulayan ya da temel sınıfı zaten gibi hem genel hem de genel olmayan arabirimleri uygulayan bir türe çeviremezsiniz `Collection<T>` sınıfı.

## <a name="fix-by-base-class-change"></a>Temel sınıf değişiklikten Düzelt

### <a name="description"></a>Açıklama
 Aşağıdaki örnek genel olmayan koleksiyonu temel sınıfını değiştirerek ihlali giderir `CollectionBase` genel sınıfa `Collection<T>` (`Collection(Of T)` içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) sınıfı.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Açıklamalar
 Zaten yayımlanmış bir sınıfın temel sınıf değiştirme, varolan tüketicilerde bozucu değişiklik olarak kabul edilir.

## <a name="fix-by-interface-implementation"></a>Arabirimi uygulama tarafından Düzelt

### <a name="description"></a>Açıklama
 Aşağıdaki örnek bu genel arabirimler uygulayarak ihlali giderir: `IEnumerable<T>`, `ICollection<T>`, ve `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, ve `IList(Of T)` içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca bkz.
 [Genel Türler](/dotnet/csharp/programming-guide/generics/index)