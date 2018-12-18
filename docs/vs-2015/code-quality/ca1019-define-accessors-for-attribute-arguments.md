---
title: 'CA1019: öznitelik bağımsız değişkenleri için erişimcileri tanımlayın | Microsoft Docs'
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
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff0329c5c9d565685d4e5c0ff950b31dea3299f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854898"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Oluşturucusunda, karşılık gelen özelliklere sahip olmayan bağımsız değişkenler özniteliği tanımlar.

## <a name="rule-description"></a>Kural Tanımı
 Öznitelikler özniteliği işaretlediğinizde özelleştirilen zorunlu bağımsız değişkenleri tanımlayabilir. Ayrıca bunlar konum parametreleri olarak öznitelik yapıcısına verildiğinden duruma bağlı bağımsız değişkenler olarak da bilinirler. Zorunlu her bağımsız değişken için bağımsız değişkenin değeri yürütme zamanından alınması gerektiğinden öznitelik ilgili salt okunur özelliği de sağlamalıdır. Bu kural her Oluşturucu parametresi için karşılık gelen özelliği tanımladığınız denetler.

 Öznitelikler adlandırılmış bağımsız değişkenler olarak bilinen duruma bağlı bağımsız değişkenler olarak da tanımlanabilir. Bu bağımsız öznitelik oluşturucular ad tarafından sağlanır ve karşılık gelen bir okuma/yazma özelliğine sahip olmalıdır.

 Ancak farklı büyük/küçük harf, kullanması gereken zorunlu ve isteğe bağlı bağımsız değişkenler, karşılık gelen özelliklere ve oluşturucu parametresi için aynı adı. Özelliklerini kullanma Pascal casing ve parametreleri kullanmak camel casing.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için bir sahip olmayan her Oluşturucu parametresi salt okunur bir özellik ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Alınabilir olması zorunlu bağımsız değişkenin değeri istemiyorsanız bu kuraldan bir uyarıyı gizler.

## <a name="custom-attributes-example"></a>Özel öznitelikler örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, zorunlu (konumsal) parametresini tanımlama iki öznitelikleri gösterir. Öznitelik ilk uygulanması hatalı tanımlanmış. İkinci doğru uygulamasıdır.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Konumsal ve adlandırılmış bağımsız değişkenler

### <a name="description"></a>Açıklama
 Kitaplığınızı kullanan Tüketiciler, hangi bağımsız değişkenleri için öznitelik zorunludur ve hangi bağımsız değişkenleri isteğe bağlı olduğu için temizlemek konumsal ve adlandırılmış bağımsız değişkenler olun.

 Aşağıdaki örnek, adlandırılmış hem konumsal bağımsız değişkenlere sahip bir öznitelik uygulanışı gösterilmektedir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Açıklamalar
 Aşağıdaki örnek, iki özellik için özel bir öznitelik uygulama gösterilmiştir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1813: Korumasız özniteliklerden kaçının](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



