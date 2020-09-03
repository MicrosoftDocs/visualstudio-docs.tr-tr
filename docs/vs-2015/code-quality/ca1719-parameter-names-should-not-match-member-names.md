---
title: 'CA1719: parametre adları üye adlarıyla eşleşmemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545372"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Parametre adları üye adları ile eşleşmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir üyenin adı, büyük/küçük harfe duyarsız bir karşılaştırmayla eşleşir, parametrelerinden birinin adı.

## <a name="rule-description"></a>Kural Tanımı
 Parametre adı parametrenin anlamıyla iletişim kurmalı ve üyenin adını üye anlamıyla iliştirmelidir. Bunların aynı olduğu yerlerde nadir bir tasarım olur. Aynı üye adıyla parametreyi adlandırma sezgisel değildir ve kütüphane kullanımını zorlaştırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Üye adıyla eşleşmeyen bir parametre adı seçin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yeni geliştirme için, bu kuraldan bir uyarıyı bastırmalısınız hiçbir bilinen senaryo oluşmaz. Gönderim kitaplıkları için, bu kuraldan bir uyarıyı bastırın.

## <a name="related-rules"></a>İlgili kurallar
 [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
