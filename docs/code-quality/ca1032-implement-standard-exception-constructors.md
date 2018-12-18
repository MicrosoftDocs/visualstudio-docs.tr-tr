---
title: 'CA1032: Standart özel durum oluşturucuları uygulayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6cd6922cae5e2d182a279e2d1637a19f8572468
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454758"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standart özel durum oluşturucuları uygulayın

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Bir tür genişletir <xref:System.Exception?displayProperty=fullName> tüm gerekli oluşturucuları bildirme değil ancak.

## <a name="rule-description"></a>Kural açıklaması

Özel durum türleri, aşağıdaki üç oluşturucular uygulamanız gerekir:

- Ortak NewException()

- Ortak NewException(string)

- Ortak NewException (dize, özel durum)

Eski FxCop statik kod analizi olarak çalıştırıyorsanız ek olarak, için değil [Roslyn tabanlı FxCop çözümleyiciler](../code-quality/roslyn-analyzers-overview.md), dördüncü bir oluşturucu yokluğu aynı zamanda bir ihlali oluşturur:

- korumalı veya özel NewException (SerializationInfo, StreamingContext)

Yapıcıların tüm ayarlamasını sağlamaktaki başarısızlık, istisnalarla başa çıkmayı zorlaştırabilir. Örneğin, imzası Oluşturucusu `NewException(string, Exception)` tarafından diğer özel durumlar nedeniyle özel durum oluşturmak için kullanılır. Bu oluşturucu, oluşturabilir ve bir örneğini hangi yönetilen kod böyle bir durumda yapmalısınız olan bir iç (iç içe) özel içeriyor, özel durum atar.

İlk üç özel durum oluşturucuları kurala göre ortak. Dördüncü Oluşturucusu korumasız sınıflardaki korumalı ve korumalı sınıflar, özel ' dir. Daha fazla bilgi için bkz: [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Bu kural ihlal düzeltmek için eksik oluşturucular özel durumu ekleyin ve doğru erişilebilirlik sahip olduğunuzdan emin olun.

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Genel oluşturucular için farklı erişim düzeyi kullanarak ihlaline neden olduğunda bir uyarı bu kuraldan bastırmak güvenlidir. Ayrıca, için gizlemek kesebilirsiniz `NewException(SerializationInfo, StreamingContext)` taşınabilir sınıf kitaplığı (PCL) oluşturuluyorsa Oluşturucusu.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bu kural ihlal eden bir özel durum türünü ve doğru şekilde uygulanan bir özel durum türü içerir.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

[CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)