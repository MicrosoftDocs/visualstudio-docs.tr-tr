---
title: Bakım Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb985a6482b76b79604ce58f85e7f8cf3e83e97c
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509906"
---
# <a name="maintainability-warnings"></a>Bakım uyarıları

Bakımsız uyarılar kitaplığı ve uygulama bakımını destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Açıklama |
|-----------|-----------------------------------|
| [CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501.md) | Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. |
| [CA1502: Aşırı karmaşıklıktan kaçının](../code-quality/ca1502.md) | Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer. |
| [CA1505: Bakımı yapılamayan kodlardan kaçının](../code-quality/ca1505.md) | Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir. |
| [CA1506: Aşırı sınıf bağlantısından kaçının](../code-quality/ca1506.md) | Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer. |
| [CA1507: Dize yerine nameof kullanma](../code-quality/ca1507.md) | Bir dize sabit değeri, bir ifadenin kullanılabileceği bir bağımsız değişken olarak kullanılır `nameof` . |
| [CA1508: Ölü koşullu kodlardan kaçının](../code-quality/ca1508.md) | Bir yöntemde, her zaman çalışma zamanında olarak değerlendirilen koşullu kod bulunur `true` `false` . Bu `false` , koşulun dalındaki ölü koda yol açar. |
| [CA1509: Kod ölçümleri yapılandırma dosyasında geçersiz girdi](../code-quality/ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) ve [CA1506](ca1506.md)gibi kod ölçüm kuralları, geçersiz bir girişi olan adlı bir yapılandırma dosyası sağladı `CodeMetricsConfig.txt` . |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodun ölçüm karmaşıklığı ve Bakımma](../code-quality/code-metrics-values.md)
