---
title: 'CA2104: Salt okunur kesilebilir başvuru türleri bildirmeyin'
ms.date: 11/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 13f1c4f19349d94cb7dedfd22a82dc86b6f33b5b
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967096"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Salt okunur kesilebilir başvuru türleri bildirmeyin

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bölünemez|

> [!NOTE]
> Kural CA2104 kullanımdan kalkmıştır ve Visual Studio'nun gelecekteki bir sürümde kaldırılacak.

## <a name="cause"></a>Sebep

Dışarıdan görünen bir tür, kesilebilir başvuru türü olan dışarıdan görünen bir salt okunur alan içerir.

## <a name="rule-description"></a>Kural açıklaması

Kesilebilir tür, örnek verileri değiştirilebilen bir türdür. <xref:System.Text.StringBuilder?displayProperty=fullName> Sınıfı kesilebilir başvuru türünde bir örnek verilmiştir. Sınıfının bir örneğini değerini değiştirebilir üye içeriyor. Bir değişmez başvuru türü örneğidir <xref:System.String?displayProperty=fullName> sınıfı. Değeri, örneği oluşturulduktan sonra hiçbir zaman değiştirebilirsiniz.

Salt okunur değiştiricisi ([salt okunur](/dotnet/csharp/language-reference/keywords/readonly) içinde C#, [salt okunur](/dotnet/visual-basic/language-reference/modifiers/readonly) Visual Basic ve [const](/cpp/cpp/const-cpp) C++'ta) bir başvuru türü üzerinde alan (veya C++'ta işaretçiyi) alanından engeller farklı bir başvuru türü örneği tarafından değiştiriliyor. Ancak, değiştiricisi başvuru türünü değiştirme alanının örnek verilerini engellemez.

Bu kural yanlışlıkla bir tür için bir ihlali gösteren, aslında sabittir. Bu durumda, uyarının gösterilmemesi güvenlidir.

Salt okunur dizi alanları bu kurala ancak bunun yerine ihlalini neden [CA2105: dizi alanları okunamadı yalnızca](../code-quality/ca2105-array-fields-should-not-be-read-only.md) kuralı.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için salt okunur değiştiricisi kaldırın veya bir değişiklik kabul edilebilir ise, alan bir sabit türüyle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Alan türü sabit ise bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bu kural ihlalini neden olan bir alan bildirimi gösterilmektedir:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]