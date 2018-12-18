---
title: 'CA1721: Tür adları alma metotlarıyla eşleşmemelidir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26f6e23a340ec018f766477f0bdce089a43ca3e4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549683"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Tür adları alma metotlarıyla eşleşmemelidir

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir üyenin adını 'Get' ile başlar ve aksi durumda ortak veya korumalı özellik adıyla eşleşen. Örneğin, 'GetColor' ve 'Color' adlı bir özellik adında bir yöntemi içeren bir tür, bu kuralı ihlal ediyor.

## <a name="rule-description"></a>Kural açıklaması
 Get yöntemleri ve özellikleri, açıkça işlevlerinden ayırt edilebilen adları olması gerekir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıkları için genel bir bakış sağlar. Bu tutarlılık kitaplık geliştirme yönetilen kodda uzmanlığına sahip olan kişi tarafından geliştirilmiştir müşterilerinizin size olan güvenini artırır ve yeni bir yazılım kitaplığı öğrenmek için gereken süreyi azaltır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 'Get' önekli bir metot adı eşleşmiyor adı değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

> [!NOTE]
> Bu uyarı, Iextenderprovider arabirimi uygulayarak alma yöntemini neden oluyorsa atlanabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir yöntem ve bu kuralı ihlal ediyor özelliği içerir.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1024: Uygun yerlerde özellikler kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)