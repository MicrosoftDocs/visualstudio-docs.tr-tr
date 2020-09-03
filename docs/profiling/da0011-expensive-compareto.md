---
title: DA0011-pahalı CompareTo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 58c94e5a24eab1c638397d7b1391596e503207fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520672"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Pahalı CompareTo

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0011|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET belleği|
|İleti|CompareTo işlevleri, ucuz olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse, CompareTo işlevi karmaşıklığını azaltın.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 Türün CompareTo yöntemi pahalıdır veya bellek ayırır.

## <a name="rule-description"></a>Kural açıklaması
 CompareTo metotları etkili olmalıdır ve bellek ayırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 CompareTo yönteminin karmaşıklığını azaltın.
