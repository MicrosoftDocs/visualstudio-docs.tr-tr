---
title: 'CA2211: Sabit olmayan alanlar görünür olmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e40065351342ab49b86b21bb525b45ce78c6028
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550556"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Sabit olmayan alanlar görünür olmamalıdır

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ne de salt okunur bir ortak veya korumalı statik alan sabit değil.

## <a name="rule-description"></a>Kural açıklaması
 Ne sabitler, ne de salt okunur olan statik alanlar güvenli iş parçacığı değildir. Böyle bir alana erişim dikkatli bir şekilde denetlenebilir ve sınıf nesnesi erişimi eşitlemek için Gelişmiş programlama tekniklerini gerektirir. Bu zor becerileri öğrenin ve ana ve böyle bir nesnenin test kendine özgü zorlukları paylaşılmamasını olduğundan statik alanları en iyi değişmez verileri depolamak için kullanılır. Bu kural, kitaplıkları için geçerlidir; uygulamaların herhangi bir alan kullanıma sunmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için statik alan sabit veya salt okunur yapın. Bu mümkün değilse, temel alan iş parçacığı açısından güvenli erişimi yöneten bir iş parçacığı açısından güvenli özelliği gibi alternatif bir mekanizma kullanılacak türünü yeniden tasarlayın. Kilit çakışması ve kilitlenmeler gibi sorunları kitaplığı davranışı ve performansı etkileyebilir farkında olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bir uygulama geliştiriyorsanız bu kuraldan bir uyarıyı bastırmak ve bu nedenle statik alanı içeren tür erişimi üzerinde tam denetime sahip güvenlidir. Kitaplık tasarımcılar bu kuraldan bir uyarıyı bastırmak değil; Sabit olmayan statik alanlar kullanarak doğru şekilde kullanmak için geliştiricilere yönelik zor kitaplığı kullanarak yapabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir tür gösterir.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]