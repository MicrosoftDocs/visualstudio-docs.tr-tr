---
title: 'CA2211: Sabit olmayan alanlar görünür olmamalıdır | Microsoft Docs'
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
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 62c3ee28a3b7cbb9bef864483e254dda5f63bfae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894260"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Sabit olmayan alanlar görünür olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ne de salt okunur bir ortak veya korumalı statik alan sabit değil.

## <a name="rule-description"></a>Kural Tanımı
 Ne sabitler, ne de salt okunur olan statik alanlar güvenli iş parçacığı değildir. Böyle bir alana erişim dikkatli bir şekilde denetlenebilir ve sınıf nesnesi erişimi eşitlemek için Gelişmiş programlama tekniklerini gerektirir. Bu zor becerileri öğrenin ve ana ve böyle bir nesnenin test kendine özgü zorlukları paylaşılmamasını olduğundan statik alanları en iyi değişmez verileri depolamak için kullanılır. Bu kural, kitaplıkları için geçerlidir; uygulamaların herhangi bir alan kullanıma sunmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için statik alan sabit veya salt okunur yapın. Bu mümkün değilse, temel alan iş parçacığı açısından güvenli erişimi yöneten bir iş parçacığı açısından güvenli özelliği gibi alternatif bir mekanizma kullanılacak türünü yeniden tasarlayın. Kilit çakışması ve kilitlenmeler gibi sorunları kitaplığı davranışı ve performansı etkileyebilir farkında olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir uygulama geliştiriyorsanız bu kuraldan bir uyarıyı bastırmak ve bu nedenle statik alanı içeren tür erişimi üzerinde tam denetime sahip güvenlidir. Kitaplık tasarımcılar bu kuraldan bir uyarıyı bastırmak değil; Sabit olmayan statik alanlar kullanarak doğru şekilde kullanmak için geliştiricilere yönelik zor kitaplığı kullanarak yapabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir tür gösterir.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



