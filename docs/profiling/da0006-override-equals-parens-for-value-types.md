---
title: 'DA0006: Değer türleri için üzerine yaz | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ab011487f33438091eb963c9ea4a7e1d1c80ec4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856281"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Değer türleri için Eşittir()'lerin üzerine yaz

|||  
|-|-|  
|Kural Kimliği|DA0006|  
|Kategori|.NET framework kullanımı|  
|Profiiling yöntemleri|Örnekleme|  
|İleti|Equals ve eşitlik işleci değer türleri üzerinde geçersiz kılar.|  
|İleti türü|Uyarı|  

## <a name="cause"></a>Sebep  
 Profil oluşturma verilerinin önemli bir kısmı çağrılarıdır Equals yöntemini veya bir genel değer türü eşitlik işleçleri. Daha verimli bir yöntem uygulamayı düşünün.  

## <a name="rule-description"></a>Kural açıklaması  
 Değer türleri için eşittir'ın devralınmış uygulaması kullanan <xref:System.Reflection> kitaplığı ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals uygulamalıdır. İşleç aşırı yüklemesi programlama dilini destekler, ayrıca eşitlik ve eşitsizlik işleci bir uygulama sağlamalıdır.  

 Equals ve eşitlik işleçleri geçersiz kılma hakkında daha fazla bilgi için bkz. [uygulama Equals ve eşitlik operatörünün (==) için yönergeler](http://go.microsoft.com/fwlink/?LinkId=177818).  

## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Equals ve eşitlik işleçleri uygulama örneği için bkz: kod çözümleme kural [CA1815: geçersiz kılma eşittir ve işleç değer türleri üzerinde](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)