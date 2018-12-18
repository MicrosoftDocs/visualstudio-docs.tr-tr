---
title: 'CA1802: Uygun Yerlerde Sabitleri Kullan'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 13cfc8b090d289173975b0ef2ee55562955de0c8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548757"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Uygun Yerlerde Sabitleri Kullan

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir alana bildirilen `static` ve `readonly` (`Shared` ve `ReadOnly` içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ve derleme zamanında hesaplanabilen bir değer ile başlatılır.

## <a name="rule-description"></a>Kural açıklaması
 Değerini bir `static``readonly` bildirim türü statik Oluşturucusu çağrıldığında, alanı çalışma zamanında hesaplanır. Varsa `static``readonly` alan bildirildiği ve derleyici alanı başlatmak için bir statik Oluşturucu yayan bir statik Oluşturucu açıkça bildirilmedi başlatılır.

 Değerini bir `const` alan derleme zamanında hesaplanır ve için karşılaştırıldığında çalışma zamanı performansını artıran meta verilerde depolanan bir `static``readonly` alan.

 Hedeflenen alana atanan değer derleme zamanında hesaplanabilir olduğundan, bildirime değiştirme bir `const` çalışma zamanında derleme zaman yerine değeri hesaplanan alanın.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için yerine `static` ve `readonly` değiştiricilerini `const` değiştiricisi.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Performans bir sorun değilse bu kuraldan bir uyarıyı bastırmak veya kuralı devre dışı bırakmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir `UseReadOnly`, kuralı ve bir tür ihlal `UseConstant`, bu kural karşılar.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]