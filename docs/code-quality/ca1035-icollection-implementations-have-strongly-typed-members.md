---
title: 'CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bcf5218f41a11d50b6cc3f36767190cce5deab1b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545534"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür uygulayan <xref:System.Collections.ICollection?displayProperty=fullName> için türü kesin belirlenmiş bir yöntem sağlamaz ancak <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Kesin türü belirtilmiş sürümünü <xref:System.Collections.ICollection.CopyTo%2A> sahip olamaz ve iki parametre kabul etmesi gereken bir <xref:System.Array?displayProperty=fullName> veya bir dizi <xref:System.Object?displayProperty=fullName> ilk parametre olarak.

## <a name="rule-description"></a>Kural açıklaması
 Bu kural gerektirir <xref:System.Collections.ICollection> kesin sağlamak için uygulamaları, böylece kullanıcılar bağımsız değişkenleri atamaları gerekli değildir üyeleri yazılan <xref:System.Object> arabirim tarafından sağlanan işlevselliği kullandığı zaman yazın. Bu kural, türün uyguladığı varsayar <xref:System.Collections.ICollection> yoksa, bu nedenle daha güçlü bir türün örneklerinin bir koleksiyonunu yönetmek için <xref:System.Object>.

 <xref:System.Collections.ICollection> uygulayan <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimi. Koleksiyondaki nesneleri genişletirseniz <xref:System.ValueType?displayProperty=fullName>, türü kesin belirlenmiş bir üye için sağlamanız gereken <xref:System.Collections.IEnumerable.GetEnumerator%2A> kutulama tarafından neden olan performans düşüklüğü önlemek için. Koleksiyon nesneler bir başvuru türü olmadığında bu gerekli değildir.

 Bir arabirim üyesi türü kesin belirlenmiş bir sürümünü uygulamak için arabirim üyelerini açıkça biçiminde adlarını kullanarak uygulama `InterfaceName.InterfaceMemberName`, gibi <xref:System.Collections.ICollection.CopyTo%2A>. Açık arabirim üyeleri arabirim tarafından bildirilen veri türlerini kullanın. Arabirim üye adı gibi kullanarak türü kesin belirlenmiş üyeler uygulama <xref:System.Collections.ICollection.CopyTo%2A>. Türü kesin belirlenmiş üyeler genel olarak bildirmek ve parametreleri bildirmek ve dönüş değerleri koleksiyon tarafından yönetilen sağlam türünde olması. Tanımlayıcı türleri gibi daha zayıf türlerine değiştirin <xref:System.Object> ve <xref:System.Array> arabirim tarafından bildirilir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için arabirim üyesini açıkça uygulama (olarak bildirin <xref:System.Collections.ICollection.CopyTo%2A>). Olarak bildirilen genel bir türü kesin belirlenmiş üye ekleme `CopyTo`, ve onu bir türü kesin belirlenmiş diziye ilk parametre olarak geçirmesine sahip.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Yeni nesne tabanlı bir koleksiyon, burada yeni koleksiyon genişleten türler güçlü tür belirlemek bir ikili ağaç gibi uygularsanız, bu kuraldan bir uyarıyı gizler. Bu türler, bu kurala uygun ve türü kesin belirlenmiş üyeler kullanıma sunar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, uygulama doğru şekilde gösterir. <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>