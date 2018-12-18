---
title: 'CA1502: Aşırı karmaşıklıktan kaçının'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfa12a2a1ade8d32c5518660c46ce79bc997d776
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819309"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Aşırı karmaşıklıktan kaçının

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategori|Microsoft.Maintainability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Bir yönteme bir aşırı döngüzel karmaşıklığına sahip.

## <a name="rule-description"></a>Kural açıklaması

*Döngüsel karmaşıklık* sayısı ve karmaşıklığı koşullu dalları tarafından belirlenir yöntemi giden doğrusal bağımsız yolların sayısını ölçer. Düşük döngüzel karmaşıklığına genellikle anlamak, test etme ve korumak kolay bir yöntemi gösterir. Döngüsel karmaşıklık yönteminin denetim akışı grafikten hesaplanır ve aşağıda verilmiştir:

Döngüsel karmaşıklık kenarlar - düğüm sayısını + 1 sayısı =

mantıksal dal noktası ve bir uç düğüm burada temsil eder, düğümler arasında bir satırı temsil eder.

Döngüsel karmaşıklık 25'ten fazla olduğunda kuralı ihlal bildirir.

Kod ölçümleri hakkında daha fazla bilgi [ölçüm karmaşıklığı ve yönetilen kod bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için döngüsel karmaşıklığı azaltmak için yöntemi yeniden düzenleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Karmaşık bir kolayca azaltılamaz ve anlaşılması, test ve korumak kolay bir yöntemdir bu kuraldan bir uyarıyı bastırmak güvenlidir. Özellikle, bir büyük içeren bir yöntem `switch` (`Select` içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) deyimi dışlama için aday olduğunu. Kod tabanı geç geliştirme döngüsü ya da beklenmeyen bir çalışma zamanı davranışını daha önce sevk edilen kodda değişiklik giriş kodu yeniden düzenlemeye bakım avantajlarını gölgede bırakabilir destabilizing riskini.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Döngüsel karmaşıklık nasıl hesaplanır

Döngüsel karmaşıklık 1 aşağıdaki ekleyerek hesaplanır:

- Dal sayısıyla (gibi `if`, `while`, ve `do`)

- Sayısı `case` deyimlerinde bir `switch`

## <a name="example"></a>Örnek

Aşağıdaki örnekler, değişen döngüsel karmaşıklık içeren yöntemleri gösterir.

**Döngüsel karmaşıklık 1**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>Örnek

**Döngüsel karmaşıklık 2**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>Örnek

**Döngüsel karmaşıklık 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Örnek

**Döngüsel karmaşıklık 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>İlgili kuralları

[CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)