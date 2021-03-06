---
title: DA0006-değer türleri için Equals () öğesini geçersiz kıl | Microsoft Docs
description: Eşittir yöntemine veya bir ortak değer türünün eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir orandır.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6f8399dbe43c20a8c888ac4e4bac9ec8b03e9610
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466147"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Değer türleri için Equals() üzerine yazın

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0006|
|Kategori|.NET Framework kullanımı|
|Profikenme yöntemleri|Örnekleme|
|İleti|Değer türlerinde Equals ve eşitlik işlecini geçersiz kılın.|
|Messge türü|Uyarı|

## <a name="cause"></a>Nedeni
 Eşittir yöntemine veya bir ortak değer türünün eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir orandır. Daha verimli bir yöntem uygulamayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Değer türleri için, eşittir devralınan uygulama kitaplığı kullanır ve bu <xref:System.Reflection> türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıların örnekleri karşılaştırmasını veya sıralamasını veya onları karma tablo anahtarları olarak kullanmasını bekleliyorsanız, değer türü eşittir değerini uygulamalıdır. Programlama diliniz işleç aşırı yüklemesini destekliyorsa eşitlik ve eşitsizlik işleçleri de bir uygulama sağlamalısınız.

 Eşit ve eşitlik operatörlerinin nasıl geçersiz kılındığı hakkında daha fazla bilgi için bkz. [Equals ve eşitlik işleci (= =) uygulamak Için yönergeler](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Eşittir ve eşitlik işleçlerini uygulamayla ilgili bir örnek için, bkz. kod analizi kuralı [CA1815: geçersiz kılma Equals ve değer türlerinde işleç eşittir](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)
