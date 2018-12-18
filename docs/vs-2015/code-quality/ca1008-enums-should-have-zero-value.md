---
title: 'CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır | Microsoft Docs'
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
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 69e60b0f2ee8106b04507722f1b3094e1bbdbbc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874832"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Eklemek için istendiğinde bölünemez - bir **hiçbiri** bayrağı olmayan bir sabit listesi değeri. Yeniden adlandırmakta ya da tüm sabit listesi değerleri kaldırmak isteyip istemediğiniz sorulduğunda - kesiliyor.|

## <a name="cause"></a>Sebep
 Numaralandırmaya uygulanan bir olmadan <xref:System.FlagsAttribute?displayProperty=fullName> ; sıfır veya bir uygulanmış olan bir numaralandırma değeri olan bir üye tanımlamıyor <xref:System.FlagsAttribute> bir üyeyi tanımlayan bir değeri sıfır olan ancak adını 'None' değil veya sıfır değerli birden çok sabit listesi tanımlar Üyeler.

## <a name="rule-description"></a>Kural Tanımı
 Diğer değer türleri gibi başlatılmamış bir numaralandırmanın varsayılan değeri sıfırdır. Flags−attributed olmayan numaralandırma, böylece varsayılan değer geçerli bir numaralandırma değeri sıfır değerine sahip bir üye tanımlamanız gerekir. Uygunsa, üye 'None' olarak adlandırın. Aksi takdirde, sıfır en sık kullanılan bir üyeye atayın. Değerin ilk sabit listesi üyesi bildiriminde ayarlanmazsa varsayılan olarak, değeri sıfır olduğuna dikkat edin.

 Sahip bir sabit listesi varsa <xref:System.FlagsAttribute> uygulanan bir sıfır değerli üyeyi tanımlayan adı numaralandırmada hiçbir değer ayarlandığını göstermek için ' None' olmalıdır. Aykırı kullanımını başka bir amaç için sıfır değerli bir üyeyi kullanarak <xref:System.FlagsAttribute> içeren ve ve veya bit düzeyinde işleçler üyesiyle gereksiz. Bu, yalnızca bir üyenin değeri sıfır atanması anlamına gelir. Birden çok üye varsa sıfır değerli bayrakları yazarından bir numaralandırmada ortaya Not `Enum.ToString()` sıfır olmayan üyeler için hatalı sonuçlar verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Flags−attributed olmayan numaralandırmalar için bu kural ihlalini düzeltmek için sıfır değerine sahip bir üye tanımlayın. Bu bir hataya neden olmayan değişikliktir. Sıfır değerli bir üyeyi tanımlayan bayraklar öznitelikli numaralandırmalar bu üye 'None' olarak adlandırın ve sıfır değerine sahip herhangi bir üye silin; bir değişiklik budur.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk bayrakları öznitelikli numaralandırmalar dışında bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kural karşılayan iki sabit listeleri ve bir numaralandırma gösterir `BadTraceOptions`, bu kuralı ihlal ediyor.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Numaralandırma değerlerini 'Ayrılmış' olarak adlandırmayın](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Numaralandırma depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Enum?displayProperty=fullName>



