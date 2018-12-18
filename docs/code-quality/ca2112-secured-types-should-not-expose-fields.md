---
title: 'CA2112: Güvenli türler alanları açığa çıkarmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 538c7ac89643c168086d6bdcb514d88295e482dc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548367"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Güvenli türler alanları açığa çıkarmamalıdır

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür ortak alanları içerir ve tarafından güvenli hale getirilen bir [bağlantı talepleri](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Kural açıklaması
 Bağlantı talebi tarafından güvenli türde bir örnek kod erişimi varsa, kod türün alanlarına erişmek için bağlantı talebine sahip değildir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için alanları ortak olmayan ve ortak özellik veya alan verisi döndüren yöntemler ekleyin. LinkDemand güvenlik denetimleri türlerinde türün özellikleri ve yöntemleri erişimi koruyun. Ancak, kod erişim güvenliği alanlar için geçerli değildir.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Hem güvenlik sorunlarını ve iyi bir tasarım, ortak alanları özel hale getirerek ihlalleri düzeltmeniz gerekir. Alanın güvenli kalması gereken bilgi tutmazsa bu kuraldan bir uyarıyı gözardı edebileceğini ve alanın içeriklerine güvenmeyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir kitaplık türü oluşur (`SecuredTypeWithFields`) güvenli olmayan alanlarla bir tür (`Distributor`) kitaplığı türün örneğini oluşturabilir ve hatalı geçişleri örnekleri türleri için bunları oluşturma iznine sahip değil ve uygulama kodu Bu tür güvenliğini iznine sahip değil olsa bile bir örneğin alanları okuyabilirsiniz.

 Aşağıdaki kitaplık kodu kuralı ihlal ediyor.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Örnek 1
 Uygulama koruyan güvenli tür bağlantı isteği nedeniyle bir örneği oluşturulamıyor. Aşağıdaki sınıf güvenli türünün bir örneği elde etmek için uygulamayı etkinleştirir.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Örnek 2
 Aşağıdaki uygulama nasıl güvenli bir türün yöntemlerini erişim izni kod kendi alanlarına erişebilir gösterilmektedir.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>İlgili kuralları

- [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı talepleri](/dotnet/framework/misc/link-demands)
- [Veri ve Modelleme](/dotnet/framework/data/index)