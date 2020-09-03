---
title: 'CA2215: Dispose yöntemleri temel sınıf atmayı çağırmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534387"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Atma metotları taban sınıf atmayı çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Uygulayan bir tür <xref:System.IDisposable?displayProperty=fullName> , Ayrıca uygulayan bir türden devralır <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Devralan türün yöntemi <xref:System.IDisposable.Dispose%2A> üst tür yöntemini çağırmıyor.

## <a name="rule-description"></a>Kural Tanımı
 Bir tür atılabilir bir türden devralırsa, <xref:System.IDisposable.Dispose%2A> kendi yönteminin içinde temel türün yöntemini çağırmalıdır <xref:System.IDisposable.Dispose%2A> . Temel tür metodunu çağırmak, temel tür tarafından oluşturulan kaynakların serbest bırakıldığını sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için çağrısı yapın `base` .<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A>metodunda.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Çağrısı varsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir `base` .<xref:System.IDisposable.Dispose%2A> kural denetimlerinden daha derin bir çağrı düzeyinde gerçekleşir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, uygulayan bir türü gösterir `TypeA` <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `TypeB` türünden devralan `TypeA` ve metodunu doğru şekilde çağıran bir türü gösterir <xref:System.IDisposable.Dispose%2A> .

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable?displayProperty=fullName>[Dispose kriteri](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
