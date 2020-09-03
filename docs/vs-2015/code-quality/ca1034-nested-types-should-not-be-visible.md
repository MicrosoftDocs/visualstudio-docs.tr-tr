---
title: 'CA1034: Iç Içe türler görünür olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04a982c993ffbb04a3e7600dfb93a00e80727b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542174"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: İç içe türler görünür olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir tür, dışarıdan görünen bir tür bildirimi içerir. İç içe geçmiş numaralandırmalar ve korumalı türler bu kuraldan muaf tutulur.

## <a name="rule-description"></a>Kural Tanımı
 İç içe bir tür, başka bir türün kapsamı içinde belirtilen bir türdür. İç içe türler, kapsayan türün özel uygulama ayrıntılarını kapsüllemek için faydalıdır. Bu amaçla kullanılan, iç içe türün dışarıdan görünür olmaması gerekir.

 Mantıksal gruplandırma için dışarıdan görünebilir iç içe türler kullanmayın veya ad çakışmalarını önleyin; Bunun yerine ad alanlarını kullanın.

 İç içe türler, bazı programcılar açıkça anlaşılmayan üye erişilebilirliği kavramını içerir.

 Korumalı türler, Gelişmiş özelleştirme senaryolarında alt sınıflarda ve iç içe türler için kullanılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İç içe geçmiş türün dışarıdan görünür olmasını düşünmüyorsanız, türün erişilebilirliğini değiştirin. Aksi takdirde, iç içe türü üst öğesinden kaldırın. İç içe geçme amacı iç içe türü sınıflandırıdıysanız, bunun yerine hiyerarşiyi oluşturmak için bir ad alanı kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
