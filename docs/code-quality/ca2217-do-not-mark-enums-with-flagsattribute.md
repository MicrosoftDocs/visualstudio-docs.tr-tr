---
title: 'CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12cc5f9fc58ac533d118b693587cf807f44b288f
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031650"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Olmayan sonu|

## <a name="cause"></a>Sebep

Dışarıdan görünür numaralandırma işaretlenmiş <xref:System.FlagsAttribute>ve onu bir veya iki ya da başka bir birleşimini tabanların olmayan daha fazla değer sabit değerleri tanımlı.

## <a name="rule-description"></a>Kural açıklaması

Bir numaralandırma olmalıdır <xref:System.FlagsAttribute> yalnızca sabit listesinde tanımlanan her değerin iki ya da bir birleşimini gücünü ise mevcut tanımlı değerler.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Bu kural ihlal düzeltmek için kaldırmak <xref:System.FlagsAttribute> gelen numaralandırması.

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Bu kuraldan uyarıyı bastırmayın.

## <a name="example-that-should-not-have-the-attribute"></a>Öznitelik olmaması gereken örnek

Aşağıdaki örnek, bir numaralandırma gösterir `Color`, 3 değeri içerir. 3 iki ya da değerlere herhangi bir birleşimini gücünü değil. `Color` Numaralandırması ile işaretlenmelidir döndürmemelidir <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Özniteliği olmalıdır örnek

Aşağıdaki örnek, bir numaralandırma gösterir `Days`, ile işaretlenen gereksinimlerini karşılayan <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>İlgili kuralları

[CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.FlagsAttribute?displayProperty=fullName>
