---
title: 'CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2e095c862edc5d7b68e1a6c55ada90a425b7e64f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550459"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Oluşturucusunda, karşılık gelen özelliklere sahip olmayan bağımsız değişkenler özniteliği tanımlar.

## <a name="rule-description"></a>Kural açıklaması
 Öznitelikler özniteliği işaretlediğinizde özelleştirilen zorunlu bağımsız değişkenleri tanımlayabilir. Ayrıca bunlar konum parametreleri olarak öznitelik yapıcısına verildiğinden duruma bağlı bağımsız değişkenler olarak da bilinirler. Zorunlu her bağımsız değişken için bağımsız değişkenin değeri yürütme zamanından alınması gerektiğinden öznitelik ilgili salt okunur özelliği de sağlamalıdır. Bu kural her Oluşturucu parametresi için karşılık gelen özelliği tanımladığınız denetler.

 Öznitelikler adlandırılmış bağımsız değişkenler olarak bilinen duruma bağlı bağımsız değişkenler olarak da tanımlanabilir. Bu bağımsız öznitelik oluşturucular ad tarafından sağlanır ve karşılık gelen bir okuma/yazma özelliğine sahip olmalıdır.

 Ancak farklı büyük/küçük harf, kullanması gereken zorunlu ve isteğe bağlı bağımsız değişkenler, karşılık gelen özelliklere ve oluşturucu parametresi için aynı adı. Özelliklerini kullanma Pascal casing ve parametreleri kullanmak camel casing.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için bir sahip olmayan her Oluşturucu parametresi salt okunur bir özellik ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Alınabilir olması zorunlu bağımsız değişkenin değeri istemiyorsanız bu kuraldan bir uyarıyı gizler.

## <a name="custom-attributes-example"></a>Özel öznitelikler örneği

Aşağıdaki örnek, zorunlu (konumsal) parametresini tanımlama iki öznitelikleri gösterir. Öznitelik ilk uygulanması hatalı tanımlanmış. İkinci doğru uygulamasıdır.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Konumsal ve adlandırılmış bağımsız değişkenler

Konumsal ve adlandırılmış bağımsız değişkenler Temizle kitaplığınızı kullanan Tüketiciler, hangi bağımsız değişkenleri için öznitelik zorunludur ve hangi bağımsız değişkenleri isteğe bağlı olduğu için kolaylaştırır.

Aşağıdaki örnek, adlandırılmış hem konumsal bağımsız değişkenlere sahip bir öznitelik uygulanışı gösterilmektedir:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

Aşağıdaki örnek, iki özellik için özel bir öznitelik uygulama gösterilmektedir:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1813: Korumasız özniteliklerden kaçının](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Ayrıca bkz.
 [Öznitelikler](/dotnet/standard/design-guidelines/attributes)