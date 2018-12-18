---
title: 'CA2233: İşlemler değil overflow | Microsoft Docs'
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
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f6690f6577d936757ae3bbe8b725b4434b6bee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836664"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: İşlemler taşmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir yöntem, bir aritmetik işlemi gerçekleştirir ve önceden işlenen taşmayı engellemek için doğrulamaz.

## <a name="rule-description"></a>Kural Tanımı
 Aritmetik işlemler işleminin sonucu dahil veri türleri için olası değerler aralığının dışında olduğundan emin olmak için önce işlenenleri doğrulamadan gerçekleştirilmemelidir. Yürütme bağlamı ve söz konusu veri türlerine bağlı olarak, aritmetik taşma ya da neden olabilir bir <xref:System.OverflowException?displayProperty=fullName> ya da sonucun en önemli bitleri atılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için işlem gerçekleştirmeden önce işlenenleri doğrulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Olası değerler işlenenlerin aritmetik işlem taşma hiçbir zaman neden olacaksa, bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example-of-a-violation"></a>Bir ihlali örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnekte bir yöntem, bu kuralı ihlal eden bir tamsayı yönetir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] gerektirir **Kaldır** tamsayı taşma seçeneği bu harekete geçirmek devre dışı.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Açıklamalar
 Bu örnekte yöntemi iletilmezse <xref:System.Int32.MinValue?displayProperty=fullName>, işlem yetersiz kalması gerekir. Bu, atılması sonucun en önemli bite neden olur. Aşağıdaki kod nasıl gerçekleştirildiğini gösterir.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Çıkış

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Giriş parametresi doğrulama ile düzeltin

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, önceki ihlali Girişi değerini doğrulayarak düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>İşaretli bir blok ile düzeltin

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, önceki ihlali işlemi işaretli bir blok içinde sarmalama tarafından düzeltir. İşlemi bir taşma neden olursa bir <xref:System.OverflowException?displayProperty=fullName> oluşturulur.

 İşaretli blok içinde desteklenmeyen Not [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Aritmetik Taşma ve Alttaşmayı açma işaretli
 İşaretli aritmetik taşma ve alttaşmayı C# üzerinde kapatırsanız, her bir tamsayı işleminin işaretli bir blok içinde kaydırma eşdeğerdir.

 **İşaretli aritmetik taşma ve alttaşmayı C# ' ta açılıp açılmayacağı**

1.  İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve seçin **özellikleri**.

2.  Seçin **derleme** sekmesine **Gelişmiş**.

3.  Seçin **aritmetik taşma ve alttaşmayı denetle** tıklatıp **Tamam**.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.OverflowException?displayProperty=fullName> [C# işleçleri](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked ve Unchecked](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)



