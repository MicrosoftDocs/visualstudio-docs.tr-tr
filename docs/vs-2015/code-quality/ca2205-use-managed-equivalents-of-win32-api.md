---
title: "CA2205: Win32 API'sının eşdeğerleri yönetilen kullan | Microsoft Docs"
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
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba23b176ed4f2120f4675611567955bdaf652153
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907475"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir platform çağırma yöntemi tanımlanır ve eşdeğer bir işlevselliği olan bir yöntem bulunmaktadır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sınıf kitaplığı.

## <a name="rule-description"></a>Kural Tanımı
 Bir platform çağırma yöntemi kullanılarak tanımlanır ve yönetilmeyen bir DLL işlevini çağırmak için kullanılan <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği veya `Declare` Visual Basic'teki. Hatalı tanımlanmış bir platform çağırma yöntemi için çalışma zamanı özel durumları nedeniyle, parametre ve dönüş değeri veri türleri ve çağırma kuralı ve karakter gibi yanlış alan belirtimleri eşleme hatalı misnamed bir işlev gibi sorunlara neden olabilir ayarlayın. Varsa, daha basit ve daha az hataya tanımlayın ve yönetilmeyen yöntemi doğrudan çağırmanız eşdeğer yönetilen yöntemini çağırmak genelde olduğu. Platform çağırma yöntemi Çağır ele alınması gereken ek güvenlik sorunlarına da yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için yönetilmeyen işlev çağrısı yönetilen eşdeğerine çağrısı ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Önerilen değiştirme yöntemi gerekli işlevleri sağlamıyorsa bu kuraldan bir uyarıyı gizler.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte gösterildiği bir platform kuralı ihlal yöntem tanımını çağırın. Ayrıca, platform çağrıları yöntemi çağırın ve eşdeğer Yönetilen yöntemi gösterilir.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1404: P/Invoke ardından hemen GetLastError çağırın](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



