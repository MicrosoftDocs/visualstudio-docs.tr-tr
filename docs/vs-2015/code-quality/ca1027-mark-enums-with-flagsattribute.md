---
title: 'CA1027: Numaralandırmaları FlagsAttribute ile işaretle | Microsoft Docs'
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
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8cebc05fa58c589f07beed70ab222d31bc8553a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879226"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Numaralandırmaları FlagsAttribute ile işaretle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Ortak bir numaralandırma değerlerini iki powers veya numaralandırmada tanımlanan diğer değerleri birleşimlerini ve <xref:System.FlagsAttribute?displayProperty=fullName> özniteliği mevcut değil. Hatalı pozitif sonuçları azaltmak için bu kuralı ihlal bitişik değerlere sahip sabit listeleri için raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Uygulama <xref:System.FlagsAttribute> anlamsız atayamayacağına birleştirilebilir, bir sabit listesi. Örneğin, bir uygulamada hangi günün kaynaklar kullanılabilir izler haftanın günlerini numaralandırması göz önünde bulundurun. Her kaynak kullanılabilirliğini sahip numaralandırma kullanılarak kodlanır <xref:System.FlagsAttribute> yoksa, herhangi bir birleşimini gün gösterilebileceği. Öznitelik olmadan, yalnızca haftanın bir gününü temsil edilebilir.

 Combinable numaralandırmalar depolama alanları için tek tek numaralandırma değerlerinin bit alanına grupları olarak kabul edilir. Bu nedenle, bu tür alanlar olarak da adlandırılır *bit alanları*. Numaralandırma değerlerinin bit alanı depolama birleştirmek için koşullu Boole işleçlerini kullanın. Bir bit alanı, belirli bir sabit listesi değeri mevcut olup olmadığını belirlemek için test etmek için Boolean mantıksal işleçleri kullanın. Bir bit alanı birleşik numaralandırma değerlerinin doğru şekilde depolanıp numaralandırmada tanımlanan her bir değeri ikinin üssü olmalıdır. Bu olmadığı sürece, Boolean mantıksal işleçler alanında depolanan tek bir sabit listesi değerlerini ayıklamak mümkün olmayacaktır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için ekleme <xref:System.FlagsAttribute> için sabit listesi.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Numaralandırma değerlerinin combinable olmasını istemiyorsanız bu kuraldan bir uyarıyı gizler.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `DaysEnumNeedsFlags` kullanma gereksinimleri karşılayan bir sabit listesidir <xref:System.FlagsAttribute>, yok ancak. `ColorEnumShouldNotHaveFlag` Numaralandırma iki powers değerler yok, ancak yanlış belirtir <xref:System.FlagsAttribute>. Bu kuralı ihlal ediyor [CA2217: numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName>



