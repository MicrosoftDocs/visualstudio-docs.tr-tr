---
title: 'CA1816: GC.SuppressFinalize öğesini doğru çağırın'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5c874aac5d84d45159ef7d169ab2749269fa0905
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174237"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize öğesini doğru çağırın

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategori|Microsoft. Kullanım|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Bu kural ihlalleri neden olabilir:

- Uygulaması olan bir yöntemin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> ve çağrı değil <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Uygulaması olmayan bir yöntem <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> ve çağrıları <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Çağıran bir yöntem <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> ve dışında bir şey geçirir [bu (C#)](/dotnet/csharp/language-reference/keywords/this) veya [bana (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Kural açıklaması

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Yöntemi nesnenin çöp toplama için kullanılabilir hale gelmeden önce herhangi bir zamanda kaynakları serbest kullanıcılar olanak sağlar. Varsa <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> yöntemi çağrıldığında, bu nesnenin kaynakları serbest bırakır. Bu, sonlandırma gereksiz kılar. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> çağırmalıdır <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> böylece nesnenin Sonlandırıcısı çöp toplayıcı çağrısı değil.

Yeniden uygulayın türetilen türlerle sonlandırıcılar önlemek için <xref:System.IDisposable> ve onu çağırmak için korumasız türleri sonlandırıcılar olmadan hala çağırmalıdır <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için:

- Yöntem uygulaması ise <xref:System.IDisposable.Dispose%2A>, bir çağrı ekleyin <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Yöntem uygulaması değilse <xref:System.IDisposable.Dispose%2A>, çağrısını kaldırın ya da <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> veya türün taşıma <xref:System.IDisposable.Dispose%2A> uygulaması.

- Tüm çağrıları değiştirme <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> geçirilecek [bu (C#)](/dotnet/csharp/language-reference/keywords/this) veya [bana (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Kasıtlı olarak kullanıyorsanız, yalnızca bu kuraldan bir uyarıyı bastırmak <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> diğer nesnelerin ömrünü denetlemek için. Uygulaması, bu kuraldan bir uyarıyı bastırmak yoksa <xref:System.IDisposable.Dispose%2A> çağrısı değil <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. Bu durumda, sonlandırma bastırmak başarısız olan performansı düşürür ve hiçbir avantaj sağlar.

## <a name="example-that-violates-ca1816"></a>CA1816 ihlal eden örnek

Bu kod, çağıran bir yöntemi gösterir <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, ancak geçmiyor [bu (C#)](/dotnet/csharp/language-reference/keywords/this) veya [bana (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Sonuç olarak, bu kod CA1816 kuralı ihlal ediyor.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>CA1816 karşılayan örneği

Bu örnek bir yöntem çağrıları, doğru bir şekilde gösterir <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> geçirerek [bu (C#)](/dotnet/csharp/language-reference/keywords/this) veya [bana (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>İlgili kuralları

- [CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dispose deseni](/dotnet/standard/design-guidelines/dispose-pattern)