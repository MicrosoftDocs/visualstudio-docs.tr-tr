---
title: 'CA1039: Listelerin türü kesin olarak belirlenmiştir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 961052d778551818942977b4d8895b85e96091d6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551827"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listelerin türü kesin olarak belirlenmiştir

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Ortak veya korumalı tür uygular <xref:System.Collections.IList?displayProperty=fullName> ancak bir veya daha fazlasını için türü kesin belirlenmiş bir yöntem sağlamaz:

- IList.Item

- IList.Add

- IList.Contains

- IList.IndexOf

- IList.Insert

- IList.Remove

## <a name="rule-description"></a>Kural açıklaması

Bu kural gerektirir <xref:System.Collections.IList> kesin sağlamak için uygulamaları yazılan üyeleri, böylece kullanıcılar bağımsız değişkenleri atamaları gerekli değildir <xref:System.Object?displayProperty=fullName> arabirim tarafından sağlanan işlevselliği kullandığı zaman yazın. <xref:System.Collections.IList> Arabirimi dizin tarafından erişilebilen bir nesne koleksiyonları tarafından uygulanır. Bu kural, türün uyguladığı varsayar <xref:System.Collections.IList> değerinden daha güçlü bir türün örneklerinin bir koleksiyonunu yönetir <xref:System.Object>.

<xref:System.Collections.IList> uygulayan <xref:System.Collections.ICollection?displayProperty=fullName> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimleri. Uygularsanız <xref:System.Collections.IList>, gerekli türü kesin belirlenmiş üyeler için sağlamanız gereken <xref:System.Collections.ICollection>. Koleksiyondaki nesneleri genişletirseniz <xref:System.ValueType?displayProperty=fullName>, türü kesin belirlenmiş bir üye için sağlamanız gereken <xref:System.Collections.IEnumerable.GetEnumerator%2A> performans düşüşünü önlemek için kutulama tarafından neden; koleksiyon nesnelerini bir başvuru türü olduğunda bu zorunlu değildir.

Bu kurala uygun için arabirim üyelerini açıkça InterfaceName.InterfaceMemberName, formun gibi adları kullanarak uygulama <xref:System.Collections.IList.Add%2A>. Açık arabirim üyeleri arabirim tarafından bildirilen veri türlerini kullanın. Arabirim üye adı gibi kullanarak türü kesin belirlenmiş üyeler uygulama `Add`. Türü kesin belirlenmiş üyeler genel olarak bildirmek ve parametreleri bildirmek ve dönüş değerleri koleksiyon tarafından yönetilen sağlam türünde olması. Tanımlayıcı türleri gibi daha zayıf türlerine değiştirin <xref:System.Object> ve <xref:System.Array> arabirim tarafından bildirilir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için açıkça uygulama <xref:System.Collections.IList> üyeleri ve daha önce not aldığınız üyeler için türü kesin belirlenmiş alternatifler sağlar. Doğru uygulayan kodu için <xref:System.Collections.IList> gerekli sağlar ve arabirim türü kesin belirlenmiş üyeler, aşağıdaki örnekte bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Yeni nesne tabanlı bir koleksiyon, burada yeni koleksiyon genişleten türler güçlü tür belirlemek bağlantılı liste gibi uyguladığınızda bu kuraldan bir uyarıyı gizler. Bu türler, bu kurala uygun ve türü kesin belirlenmiş üyeler kullanıma sunar.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, türü `YourType` genişletir <xref:System.Collections.CollectionBase?displayProperty=fullName>, tüm kesin türde koleksiyonlar gibi. <xref:System.Collections.CollectionBase> Açık uygulamasını sağlar <xref:System.Collections.IList> arabirimi. Bu nedenle, yalnızca türü kesin belirlenmiş üyeler için sağlamanız gereken <xref:System.Collections.IList> ve <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>