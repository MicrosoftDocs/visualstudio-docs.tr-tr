---
title: "CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8c88feb35a4699770b7a05a266168e0c3ad347e4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860127"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Bir platform çağırma yöntemi tanımlanır ve .NET Framework sınıf kitaplığında eşdeğer bir işlevselliği olan bir yöntem bulunmaktadır.

## <a name="rule-description"></a>Kural açıklaması

Bir platform çağırma yöntemi kullanılarak tanımlanır ve yönetilmeyen bir DLL işlevini çağırmak için kullanılan <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği veya `Declare` Visual Basic'teki. Hatalı tanımlanmış bir platform çağırma yöntemi için çalışma zamanı özel durumları nedeniyle, parametre ve dönüş değeri veri türleri ve çağırma kuralı ve karakter gibi yanlış alan belirtimleri eşleme hatalı misnamed bir işlev gibi sorunlara neden olabilir ayarlayın. Varsa, tanımlamak ve yönetilmeyen yöntemi doğrudan çağırmanız eşdeğer yönetilen yöntemini çağırmak hataya daha basit ve daha az hata var. Platform çağırma yöntemi Çağır ele alınması gereken ek güvenlik sorunlarına da yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için yönetilmeyen işlev çağrısı yönetilen eşdeğerine çağrısı ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Önerilen değiştirme yöntemi gerekli işlevleri sağlamıyorsa bu kuraldan bir uyarıyı gizler.

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir platform kuralı ihlal yöntem tanımını çağırın. Ayrıca, platform çağrıları yöntemi çağırın ve eşdeğer Yönetilen yöntemi gösterilir.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>İlgili kuralları

- [CA1404: P/Invoke ardından hemen GetLastError çağırın](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)