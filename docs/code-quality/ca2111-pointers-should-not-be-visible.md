---
title: 'CA2111: İşaretçiler görünür olmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a08d15ec491bb78c2d9398c8e689015c9523a3c1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546830"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: İşaretçiler görünür olmamalıdır

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir <xref:System.IntPtr?displayProperty=fullName> veya <xref:System.UIntPtr?displayProperty=fullName> alanı salt okunur değildir.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.IntPtr> ve <xref:System.UIntPtr> işaretçi türleri, yönetilmeyen bellek erişmek için kullanılır. Bir işaretçi özel, içsel veya salt okunur durumda değilse, kötü amaçlı kod işaretçinin, potansiyel olarak bellekte rastgele konumlara erişmesine izin vermek veya uygulama ya da sistem hatalarına neden değerini değiştirebilirsiniz.

 İşaretçi alan içeren tür güvenli erişim yapmak istiyorsanız, bkz. [CA2112: güvenli türler alanları kullanıma](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 İşaretçi salt okunur, iç veya özel hale getirerek güvenli hale getirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 İşaretçi değeri temel kullanmayın, bu kuraldan bir uyarıyı gizler.

## <a name="example"></a>Örnek
 Aşağıdaki kod, ihlal ve kural karşılamak işaretçileri gösterir. Özel olmayan işaretçileri de kuralı ihlal bildirimi [CA1051: görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>