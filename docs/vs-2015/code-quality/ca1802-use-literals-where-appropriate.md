---
title: 'CA1802: Uygun yerlerde sabitleri kullan | Microsoft Docs'
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
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 25b9c521d55b16cef885c50138bff84c3000e1b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940092"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Uygun Yerlerde Sabitleri Kullan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir alana bildirilen `static` ve `readonly` (`Shared` ve `ReadOnly` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ve derleme zamanında hesaplanabilen bir değer ile başlatılır.

## <a name="rule-description"></a>Kural Tanımı
 Değerini bir `static``readonly` bildirim türü statik Oluşturucusu çağrıldığında, alanı çalışma zamanında hesaplanır. Varsa `static``readonly` alan bildirildiği ve derleyici alanı başlatmak için bir statik Oluşturucu yayan bir statik Oluşturucu açıkça bildirilmedi başlatılır.

 Değerini bir `const` alan derleme zamanında hesaplanır ve için karşılaştırıldığında çalışma zamanı performansını artıran meta verilerde depolanan bir `static``readonly` alan.

 Hedeflenen alana atanan değer derleme zamanında hesaplanabilir olduğundan, bildirime değiştirme bir `const` çalışma zamanında derleme zaman yerine değeri hesaplanan alanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için yerine `static` ve `readonly` değiştiricilerini `const` değiştiricisi.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans bir sorun değilse bu kuraldan bir uyarıyı bastırmak veya kuralı devre dışı bırakmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir `UseReadOnly`, kuralı ve bir tür ihlal `UseConstant`, bu kural karşılar.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]



