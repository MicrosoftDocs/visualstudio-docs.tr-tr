---
title: 'CA2213: Atılabilen alanlar atılmalıdır'
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be06c9bf38ec360cedc858d92a84b1f89c662856
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220638"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Atılabilen alanlar atılmalıdır

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Uygulayan bir tür <xref:System.IDisposable?displayProperty=fullName> ayrıca uygulayan türler alanlar bildirir <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Alanının yöntemi çağrılmaz <xref:System.IDisposable.Dispose%2A> bildirim türü yöntemi.

## <a name="rule-description"></a>Kural açıklaması

Bir tür için kendi yönetilmeyen tüm kaynaklarını atma sorumludur. CA2213 çekleri atılabilen bir tür olup olmadığını görmek için rule (uygulayan bir diğer bir deyişle, <xref:System.IDisposable>) `T` bir alan bildirir `F` atılabilir bir türün diğer bir deyişle bir örneğini `FT`. Her bir alan için `F` başlatıcıları, kapsayan tür veya yöntemler içinde yerel olarak oluşturulan bir nesneye atanmış `T`, kural için bir çağrı bulmaya çalışır `FT.Dispose`. Kural çağrılan yöntemler arar `T.Dispose` ve daha düşük bir düzey (diğer bir deyişle, çağrılan yöntemler tarafından çağrılan yöntemler `FT.Dispose`).

> [!NOTE]
> Yerel olarak oluşturulmuş atılabilir bir nesne içeren türün yöntemlerini ve başlatıcıları içinde atanmış olan alanlar için kural CA2213 tetikler. Nesne oluşturulduğunda veya bildirim türünün dışından atanan varsa `T`, kuralı değil başlatılamıyor. Bu, kapsayan tür nesnesinin elden sorumluluğunu sahip olduğu durumlar için gürültü azaltır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için çağrı <xref:System.IDisposable.Dispose%2A> uygulayan türler alanlar üzerinde <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Kaynağı serbest bırakarak alanı tarafından tutulan için sorumlu kullanmıyorsanız veya bu kuraldan bir uyarıyı bastırmak güvenlidir çağrısı <xref:System.IDisposable.Dispose%2A> kural denetimleri daha derin arama düzeyinde gerçekleşir.

## <a name="example"></a>Örnek

Aşağıdaki kod parçacığı bir türü gösterir `TypeA` uygulayan <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Aşağıdaki kod parçacığı bir türü gösterir `TypeB` , ihlal kural CA2213 alan bildirerek `aFieldOfADisposableType` tek kullanımlık bir tür olarak (`TypeA`) ve değil çağırma <xref:System.IDisposable.Dispose%2A> alanı.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)