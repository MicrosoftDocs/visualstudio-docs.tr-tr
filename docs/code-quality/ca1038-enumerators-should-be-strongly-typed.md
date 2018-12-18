---
title: 'CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22cc84a0cdc8d4fdb86f6890ae0ebd25eb65beb8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545495"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür uygulayan <xref:System.Collections.IEnumerator?displayProperty=fullName> kesin türü belirtilmiş sürümünü sağlamaz, ancak <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> özelliği. Bu kurala aşağıdaki türlerden türetilmiş türleri şunlardır:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Kural açıklaması
 Bu kural gerektirir <xref:System.Collections.IEnumerator> de türü kesin belirlenmiş bir sürümünü sağlamak için uygulamaları <xref:System.Collections.IEnumerator.Current%2A> özelliği böylece kullanıcıların arabirim tarafından sağlanan işlevselliği kullandığınızda güçlü tür için dönen değer atama gerekmez. Bu kural, türün uyguladığı varsayar <xref:System.Collections.IEnumerator> değerinden daha güçlü bir türün örneklerinin bir koleksiyonunu içeren <xref:System.Object>.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için arabirim özelliği açıkça uygulama (olarak bildirin `IEnumerator.Current`). Olarak bildirilen özelliğinin genel bir türü kesin belirlenmiş sürümü ekleme `Current`, ve bu türü kesin belirlenmiş bir nesne döndürür.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bir ikili ağaç gibi bir nesne tabanlı koleksiyon ile kullanmak için bir nesne tabanlı Numaralandırıcı uyguladığınızda bu kuraldan bir uyarıyı gizler. Yeni koleksiyon genişleten türler kesin türü belirtilmiş Numaralandırıcı tanımlayın ve kesin türü belirtilmiş özelliği kullanıma sunun.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, türü kesin belirlenmiş uygulamak için doğru şekilde gösterir. <xref:System.Collections.IEnumerator> türü.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>