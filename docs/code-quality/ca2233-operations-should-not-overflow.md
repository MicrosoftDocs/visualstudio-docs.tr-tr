---
title: 'CA2233: İşlemler taşmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 73c0e616eb527a2213c77cdae00c42635d49b130
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938910"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: İşlemler taşmamalıdır

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Bir yöntem, bir aritmetik işlemi gerçekleştirir ve önceden işlenen taşmayı engellemek için doğrulamaz.

## <a name="rule-description"></a>Kural açıklaması

İşlemin sonucu dahil veri türleri için olası değerler aralığının dışında olduğundan emin olmak için önce işlenenleri doğrulamadan aritmetik işlemler gerçekleştirme. Yürütme bağlamı ve söz konusu veri türlerine bağlı olarak, aritmetik taşma ya da neden olabilir bir <xref:System.OverflowException?displayProperty=fullName> ya da sonucun en önemli bitleri atılır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için işlem gerçekleştirmeden önce işlenenleri doğrulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Olası değerler işlenenlerin aritmetik işlem taşma hiçbir zaman neden olacaksa, bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example-of-a-violation"></a>Bir ihlali örneği

Aşağıdaki örnekte bir yöntem, bu kuralı ihlal eden bir tamsayı yönetir. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] gerektirir **Kaldır** tamsayı taşma seçeneği bu harekete geçirmek devre dışı.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Bu örnekte yöntemi iletilmezse <xref:System.Int32.MinValue?displayProperty=fullName>, işlem yetersiz kalması gerekir. Bu, atılması sonucun en önemli bite neden olur. Aşağıdaki kod nasıl gerçekleştirildiğini gösterir.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Çıktı:

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Giriş parametresi doğrulama ile düzeltin

Aşağıdaki örnek, önceki ihlali Girişi değerini doğrulayarak düzeltir.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>İşaretli bir blok ile düzeltin

Aşağıdaki örnek, önceki ihlali işlemi işaretli bir blok içinde sarmalama tarafından düzeltir. İşlemi bir taşma neden olursa bir <xref:System.OverflowException?displayProperty=fullName> oluşturulur.

İşaretli bloklar içinde desteklenmiyor [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aritmetik Taşma ve Alttaşmayı açma işaretli

İşaretli aritmetik taşma ve alttaşmayı C# üzerinde kapatırsanız, her bir tamsayı işleminin işaretli bir blok içinde kaydırma eşdeğerdir.

Açmak için aritmetik taşma ve alttaşmayı C# dilinde kullanıma:

1.  İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve seçin **özellikleri**.

2.  Seçin **derleme** sekmesine **Gelişmiş**.

3.  Seçin **aritmetik taşma ve alttaşmayı denetle** tıklatıp **Tamam**.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OverflowException?displayProperty=fullName>
- [C# İşleçleri](/dotnet/csharp/language-reference/operators/index)
- [İşaretli ve İşaretsiz](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)