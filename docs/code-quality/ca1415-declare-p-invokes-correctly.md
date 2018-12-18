---
title: "CA1415: P-Invoke'ları doğru bildirin"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f95c3e68190acbd53c4b75ceb81abf2885d15bce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922633"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invoke'ları doğru bildirin

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|P/Invoke, parametre bildirirse bölünemez - derlemenin dışından görülemez. P/Invoke parametresi bildiren derlemesi dışında görülebilir, - kesiliyor.|

## <a name="cause"></a>Sebep
 Bir platform çağırma yöntemi hatalı bildirilmiş.

## <a name="rule-description"></a>Kural açıklaması
 Bir platform yöntemi erişimleri yönetilmeyen kod çağırmak ve tarafından tanımlanan `Declare` anahtar sözcüğünü [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Bu kural için platform çağırma işaretçiniz bir ÇAKIŞAN yapı parametresine Win32 işlevlerini hedef yöntem bildirimleri ve yönetilen bir işaretçi değil. şu anda görünür bir <xref:System.Threading.NativeOverlapped?displayProperty=fullName> yapısı.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için doğru platform bildirin yöntemi çağır.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte gösterildiği platform çağırma kuralı ihlal ediyor ve kural karşılamak yöntemler.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.
 [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)