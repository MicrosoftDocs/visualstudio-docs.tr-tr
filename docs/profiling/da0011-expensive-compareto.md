---
title: 'DA0011: Pahalı CompareTo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6137c07ac6b920234a9772764b5ad758efdb1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818854"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Pahalı CompareTo

|||  
|-|-|  
|Kural Kimliği|DA0011|  
|Kategori|.NET framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET bellek|  
|İleti|CompareTo fonksiyonları ucuz ve diğer bellek ayrılamadı. gerekir. Mümkünse CompareTo fonksiyonunun karmaşıklığını azaltın.|  
|Kural türü|Uyarı|  

## <a name="cause"></a>Sebep  
 CompareTo Yöntemi türü, pahalıdır veya bellek ayırır.  

## <a name="rule-description"></a>Kural açıklaması  
 CompareTo Yöntemi verimli olmalıdır ve bellek ayrılamadı.  

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?  
 CompareTo Yöntemi karmaşıklığını azaltın.