---
title: 'CA1815: Geçersiz kılma eşittir ve işleç değer türlerinde | Microsoft Docs'
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
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3868e5e1e78fd5640e9a2b55b133a9c6e0b47816
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912610"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Değer türlerinde eşittir ve işleç eşitliklerinin üzerine yaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Genel değer türü geçersiz <xref:System.Object.Equals%2A?displayProperty=fullName>, veya eşitlik operatörünün (==) uygulamıyor. Bu kural, sabit listeleri denetlemez.

## <a name="rule-description"></a>Kural Tanımı
 Değer türleri için ' ın devralınmış uygulaması <xref:System.Object.Equals%2A> Reflection kitaplığını kullanır ve tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Karşılaştırma ya da sıralama örnekleri için kullanıcıların ya da tablo anahtarlarını karma olarak kullandığınız, değer türünüz uygulamalıdır <xref:System.Object.Equals%2A>. İşleç aşırı yüklemesi programlama dilini destekler, ayrıca eşitlik ve eşitsizlik işleci bir uygulama sağlamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için bir uygulamasını sağlamak <xref:System.Object.Equals%2A>. Mümkünse, eşitlik işlecini uygular.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Değer türü örneklerini birbirine karşılaştırılmayacak varsa bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example-of-a-violation"></a>Bir ihlali örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek bu kuralı ihlal eden bir yapı (değer türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>İlişkin bir örnek için düzeltme

### <a name="description"></a>Açıklama
 Aşağıdaki örnek önceki ihlali geçersiz kılarak düzeltmeleri <xref:System.ValueType.Equals%2A?displayProperty=fullName> ve eşitlik işleçleri (==,! =).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Object.Equals%2A?displayProperty=fullName>



