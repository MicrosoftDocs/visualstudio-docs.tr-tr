---
title: 'CA2220: Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c814324ac21017acf6a0182f7807b0a0878c8aca
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551213"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Geçersiz kılan bir tür <xref:System.Object.Finalize%2A?displayProperty=fullName> arama <xref:System.Object.Finalize%2A> temel sınıfındaki yöntemi.

## <a name="rule-description"></a>Kural açıklaması

Sonlandırılma, devralma hiyerarşisi aracılığıyla gönderilmelidir. Bunu sağlamak için kendi temel sınıf türleri çağırmalıdır <xref:System.Object.Finalize%2A> yönteminden kendi içinde <xref:System.Object.Finalize%2A> yöntemi. C# derleyicisi, temel sınıf Sonlandırıcı çağrısını otomatik olarak ekler.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için temel türün çağrı <xref:System.Object.Finalize%2A> yönteminden, <xref:System.Object.Finalize%2A> yöntemi.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu kuraldan uyarıyı bastırmayın. Ortak dil çalışma zamanını hedefleyen bazı derleyiciler, Microsoft Ara diline (MSIL) temel türün Sonlandırıcısı için bir çağrı ekleyin. Bu kuraldan bir uyarıyı bildirilirse, derleyici arama eklemez ve kod eklemeniz gerekir.

## <a name="example"></a>Örnek

Aşağıdaki Visual Basic örnek, bir tür gösterir `TypeB` doğru çağrılarının <xref:System.Object.Finalize%2A> temel sınıfındaki yöntemi.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)