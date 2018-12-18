---
title: 'CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 60c5e6e93c8ededc7d08d3b917f8066148f133f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551801"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Eklemek için istendiğinde bölünemez - bir **hiçbiri** bayrağı olmayan bir sabit listesi değeri. Yeniden adlandırmakta ya da tüm sabit listesi değerleri kaldırmak isteyip istemediğiniz sorulduğunda - kesiliyor.|

## <a name="cause"></a>Sebep

Numaralandırmaya uygulanan bir olmadan <xref:System.FlagsAttribute?displayProperty=fullName> ; sıfır veya bir uygulanmış olan bir numaralandırma değeri olan bir üye tanımlamıyor <xref:System.FlagsAttribute> bir üyeyi tanımlayan bir değeri sıfır olan ancak adını 'None' değil veya sıfır değerli birden çok sabit listesi tanımlar Üyeler.

## <a name="rule-description"></a>Kural açıklaması

Diğer değer türleri gibi başlatılmamış bir numaralandırmanın varsayılan değeri sıfırdır. Bayrakları öznitelikli sabit listesi, böylece varsayılan değer geçerli bir numaralandırma değeri sıfır değerine sahip bir üye tanımlamanız gerekir. Uygunsa, üye 'None' olarak adlandırın. Aksi takdirde, sıfır en sık kullanılan bir üyeye atayın. Değerin ilk sabit listesi üyesi bildiriminde ayarlanmazsa varsayılan olarak, değeri sıfırdır.

Sahip bir sabit listesi varsa <xref:System.FlagsAttribute> uygulanan bir sıfır değerli üyeyi tanımlayan adı numaralandırmada hiçbir değer ayarlandığını göstermek için ' None' olmalıdır. Aykırı kullanımını başka bir amaç için sıfır değerli bir üyeyi kullanarak <xref:System.FlagsAttribute> içeren ve ve veya bit düzeyinde işleçler üyesiyle gereksiz. Bu, yalnızca bir üyenin değeri sıfır atanması anlamına gelir. Sıfır değerine sahip birden çok üye bayrakları öznitelikli numaralandırmada, gerçekleşirse `Enum.ToString()` sıfır olmayan üyeler için hatalı sonuçlar verir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Numaralandırma bayraklarını öznitelikli için bu kural ihlalini düzeltmek için sıfır değerine sahip bir üye tanımlayın. Bu bir hataya neden olmayan değişikliktir. Sıfır değerli bir üyeyi tanımlayan bayraklar öznitelikli numaralandırmalar bu üye 'None' olarak adlandırın ve sıfır değerine sahip herhangi bir üye silin; bir değişiklik budur.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Daha önce sevk bayrakları öznitelikli numaralandırmalar dışında bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kural karşılayan iki sabit listeleri ve bir numaralandırma gösterir `BadTraceOptions`, bu kuralı ihlal ediyor.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>İlgili kuralları

- [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Numaralandırma değerlerini 'Ayrılmış' olarak adlandırmayın](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Numaralandırma depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum?displayProperty=fullName>