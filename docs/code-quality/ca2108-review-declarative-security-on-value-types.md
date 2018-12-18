---
title: 'CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2d76a0ecf6a2eeac677475eb25efe495129c213
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548523"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Ortak veya korunan değer türü tarafından güvenliği sağlanan bir [veri ve modelleme](/dotnet/framework/data/index) veya [bağlantı talepleri](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Kural açıklaması

Değer türleri ayrılan ve diğer oluşturucular yürütmeden önce kendi varsayılan oluşturucu tarafından başlatılır. Bir değer türü, isteğe bağlı ya da LinkDemand tarafından güvenlik altına alınır ve arayan güvenlik denetimi, herhangi bir oluşturucu dışında uygun izinlere sahip değil'de varsayılan başarısız olur ve bir güvenlik özel durumu oluşturulur. Değer türü serbest değil; kendi varsayılan oluşturucu tarafından ayarlanmış durumda kalır. Değer türü örneğini geçirir bir çağıranın oluşturun veya örnek erişim izni olduğunu varsaymayın.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Güvenlik denetimi türünden kaldırın ve onun yerine kullanmak yöntem düzeyi güvenlik denetimleri sürece bu kural ihlalini düzeltmek olamaz. Bu şekilde ihlali düzeltme değer türü örneklerini alma gelen yetersiz izinlerle çağıranlar engellemez. Bir değer türü örneği, varsayılan durumunda, hassas bilgileri kullanıma sunmuyor ve zararlı bir biçimde kullanılamaz emin olmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Herhangi bir çağıranın varsayılan durumuna içinde değer türüne örneklerini güvenlik tehdit taşıyor olmadan elde bu kuraldan bir uyarıyı gösterilmemesini sağlayabilirsiniz.

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek bu kuralı ihlal eden bir değer türü içeren bir kitaplık gösterir. `StructureManager` Türü, değer türü örneğini geçirir bir çağıranın oluşturun veya örnek erişim izni olduğunu varsayar.

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>Örnek 2

Aşağıdaki uygulama kitaplığın zayıflık gösterir.

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı talepleri](/dotnet/framework/misc/link-demands)
- [Veri ve Modelleme](/dotnet/framework/data/index)
