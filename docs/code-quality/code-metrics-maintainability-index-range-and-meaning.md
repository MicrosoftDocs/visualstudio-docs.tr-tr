---
title: Kod ölçümleri-Bakımdışı dizin aralığı ve anlamı
ms.date: 1/8/2021
description: Visual Studio 'da kod ölçümleri için bakım dizini Aralık ölçümü hakkında bilgi edinin.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa825b439b75606da136635d5816ac3e19ea8392
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860470"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Kod ölçümleri-Bakımdışı dizin aralığı ve anlamı

Soru: bakımma dizini 0 ile 100 arasında olacak şekilde sıfırlandı. Bu nasıl ve neden tamamlandı?

İlk olarak ölçüm şu şekilde hesaplanır: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

Bu formülün kullanımı, 171 ' den sınırlandırılmamış negatif bir sayıya kadar derecelendirçalıştığını belirtir.  Kodu 0 ' a katdığından, kod bakımı oldukça zordur ve kod arasındaki fark 0 ve bazı negatif bir değer yararlı değildir.  Negatif sayıların azalan kullanışlılığı ve ölçüyü mümkün olduğunca net bir şekilde korumak için, 0 veya daha az dizini 0 olarak kabul etmeye karar verdik ve sonra 171 veya daha az aralığı 0 ile 100 arasında olacak şekilde yeniden temellendirtik. Bu nedenle, kullandığımız formül:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Bunlara ek olarak, eşiklerle koruyucu olduğuna karar verdik.  Bunun yerine, Dizin kırmızı gösterilirse, kodla ilgili bir sorun olduğunu yüksek ölçüde güvenle söyliyoruz.  Bu, aşağıdaki eşikleri vermiştir:

Eşikler için bu 0-100 Aralık 80-20 ' i kesintiye uğramaya karar verdik ve yalnızca şüpheli kod işaretlendi. Aşağıdaki eşikleri kullandık:

- 0-9 = kırmızı
- 10-19 = sarı
- 20-100 = yeşil
