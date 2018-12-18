---
title: 'CA1018: Öznitelikleri AttributeUsageAttribute ile işaretleyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a54dd39746364d6908f440ac77d7a2b8bbfdbcf6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547626"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Öznitelikleri AttributeUsageAttribute ile işaretleyin

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> Özniteliği özel özniteliği mevcut değil.

## <a name="rule-description"></a>Kural açıklaması
 Özel öznitelik tanımladığınızda, kullanarak işaretlemek <xref:System.AttributeUsageAttribute> özel öznitelik kaynak kodunun nerede uygulanabilir belirtmek için. Bir özniteliğin anlamı ve amaçlanan kullanımı, kodun içinde onun varolan konumunu tanımlar. Örneğin, kimin tutmaktan ve her tür kitaplığında geliştirme sorumludur ve sorumluluk her zaman tür düzeyinde atanan kişi tanımlayan bir öznitelik tanımlayabilir. Bu durumda, derleyiciler, sınıflar, numaralandırmalar ve arabirimler özniteliğini etkinleştirmeniz gerekir, ancak yöntemler, olaylar veya özellikler etkinleştirmemelisiniz. Kuruluş politikaları ve yordamları, öznitelik derlemelerini etkin olmadığını dikte.

 <xref:System.AttributeTargets?displayProperty=fullName> Numaralandırması için özel bir öznitelik belirtebilirsiniz hedefleri tanımlar. Atlarsanız <xref:System.AttributeUsageAttribute>, özel bir öznitelik tarafından tanımlandığı gibi tüm hedefler için geçerli olacağı `All` değerini <xref:System.AttributeTargets> sabit listesi.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için kullanarak özniteliği için hedefleri belirtin <xref:System.AttributeUsageAttribute>. Aşağıdaki örnekte bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 İleti hariç yerine bu kural ihlalini düzeltmek. Inherits özniteliği bile <xref:System.AttributeUsageAttribute>, öznitelik kod bakımı basitleştirmek için mevcut olmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki öznitelikleri tanımlar. `BadCodeMaintainerAttribute` yanlış atlar <xref:System.AttributeUsageAttribute> deyimi ve `GoodCodeMaintainerAttribute` doğru Bu bölümde daha önce açıklanan özniteliğini uygular. Unutmayın özelliği `DeveloperName` tasarım kuralı tarafından gerekli [CA1019: öznitelik bağımsız değişkenleri için erişimcileri tanımlayın](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) ve bütünlük açısından dahil edilmiştir.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Korumasız özniteliklerden kaçının](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](/dotnet/standard/design-guidelines/attributes)