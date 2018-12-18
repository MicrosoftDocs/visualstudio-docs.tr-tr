---
title: 'CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11359e021d5c297c0782bf95fe35997b0a1b5be5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548419"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Uygulayan bir tür <xref:System.IDisposable?displayProperty=fullName> ayrıca uygulayan bir tür tarafından devralındığında <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Türetilen türün yöntemi çağırmaz <xref:System.IDisposable.Dispose%2A> üst türü yöntemi.

## <a name="rule-description"></a>Kural açıklaması
 Bir tür atılabilen bir türden devralınırsa, çağırmalıdır <xref:System.IDisposable.Dispose%2A> yöntemi kendi içinde temel türün <xref:System.IDisposable.Dispose%2A> yöntemi. Temel tür yöntem çağırma Dispose taban türü tarafından oluşturulan tüm kaynakların serbest bırakıldığından sağlar.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için çağrı `base`.<xref:System.IDisposable.Dispose%2A> içinde <xref:System.IDisposable.Dispose%2A> yöntemi.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Varsa bu kuraldan bir uyarıyı bastırmak güvenlidir çağrısı `base`.<xref:System.IDisposable.Dispose%2A> daha ayrıntılı bir çağırma kuralı denetimleri'den oluşur.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir `TypeA` uygulayan <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir `TypeB` türünden devralan `TypeA` ve doğru bir şekilde çağıran kendi <xref:System.IDisposable.Dispose%2A> yöntemi.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)