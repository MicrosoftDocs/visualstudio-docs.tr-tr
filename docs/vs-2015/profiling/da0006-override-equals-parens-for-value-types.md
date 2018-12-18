---
title: 'DA0006: Değer türleri için üzerine yaz | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a60bc533ccc826b09e288e7d8ca934702f0443e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768307"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Değer türleri için Eşittir()'lerin üzerine yaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0006 |  
| Kategori |. NET Framework kullanım |  
| Profiiling yöntemleri | Örnekleme |  
| İleti | Equals ve eşitlik işleci değer türleri üzerinde geçersiz kılın. |  
| İleti türü | Uyarı |  
  
## <a name="cause"></a>Sebep  
 Profil oluşturma verilerinin önemli bir kısmı çağrılarıdır Equals yöntemini veya bir genel değer türü eşitlik işleçleri. Daha verimli bir yöntem uygulamayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Değer türleri için eşittir'ın devralınmış uygulaması kullanan <xref:System.Reflection> kitaplığı ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals uygulamalıdır. İşleç aşırı yüklemesi programlama dilini destekler, ayrıca eşitlik ve eşitsizlik işleci bir uygulama sağlamalıdır.  
  
 Equals ve eşitlik işleçleri geçersiz kılma hakkında daha fazla bilgi için bkz. [uygulama Equals ve eşitlik operatörünün (==) için yönergeler](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Equals ve eşitlik işleçleri uygulama örneği için bkz: kod çözümleme kural [CA1815: geçersiz kılma eşittir ve işleç değer türleri üzerinde](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)



