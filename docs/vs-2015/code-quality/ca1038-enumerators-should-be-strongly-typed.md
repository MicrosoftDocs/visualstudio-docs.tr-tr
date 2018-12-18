---
title: 'CA1038: Numaralandırıcıların türü kesin | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aafd89a068a57ef1eb89584441195e1ece8b8f52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899077"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür uygulayan <xref:System.Collections.IEnumerator?displayProperty=fullName> kesin türü belirtilmiş sürümünü sağlamaz, ancak <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> özelliği. Bu kurala aşağıdaki türlerden türetilmiş türleri şunlardır:

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 Bu kural gerektirir <xref:System.Collections.IEnumerator> de türü kesin belirlenmiş bir sürümünü sağlamak için uygulamaları <xref:System.Collections.IEnumerator.Current%2A> özelliği böylece kullanıcıların arabirim tarafından sağlanan işlevselliği kullandığınızda güçlü tür için dönen değer atama gerekmez. Bu kural, türün uyguladığı varsayar <xref:System.Collections.IEnumerator> değerinden daha güçlü bir türün örneklerinin bir koleksiyonunu içeren <xref:System.Object>.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için arabirim özelliği açıkça uygulama (olarak bildirin `IEnumerator.Current`). Olarak bildirilen özelliğinin genel bir türü kesin belirlenmiş sürümü ekleme `Current`, ve bu türü kesin belirlenmiş bir nesne döndürür.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir ikili ağaç gibi bir nesne tabanlı koleksiyon ile kullanmak için bir nesne tabanlı Numaralandırıcı uyguladığınızda bu kuraldan bir uyarıyı gizler. Yeni koleksiyon genişleten türler kesin türü belirtilmiş Numaralandırıcı tanımlayın ve kesin türü belirtilmiş özelliği kullanıma sunun.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, türü kesin belirlenmiş uygulamak için doğru şekilde gösterir. <xref:System.Collections.IEnumerator> türü.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Collections.IEnumerator?displayProperty=fullName><xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



