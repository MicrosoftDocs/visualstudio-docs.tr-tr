---
title: DA0004-yüksek işlemci kullanımı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e0ac8d8558ee73903898e920ed8174c73ea66c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548180"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Yüksek işlemci kullanımı

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0004|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemleri|İzleme<br /><br /> Örnekleme|
|İleti|İşlemci kullanımınız sürekli olarak %75 üzerinde. CPU 'ya dayalı uygulamalar için örnekleme modunu kullanmayı düşünün.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 İzleme yöntemi kullanılarak toplanmış olan profil oluşturma verilerinde yüksek işlemci (CPU) kullanımı yüksektir. Bir CPU ile bağlantılı uygulamanın profilini oluştururken örnekleme profili oluşturma yöntemini kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Bu profil oluşturma çalışması sırasında işlemci (veya işlemciler) sürekli olarak meşgul. Yüksek CPU kullanımı, CPU 'ya dayalı bir uygulamayı gösterebilir. Belgelenmiş profiller, CPU kullanımı senaryolarını araştırmak için en etkili yol değildir. Örnekleme, zaman içinde işlemci üzerinde yönergeler yürüten uygulamalar için profil oluştururken daha etkilidir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 İşlev zamanlamalarınız gerekmiyorsa veya giriş/çıkış işlemini işlemci performans sorunlarına göre anlamak için daha fazla bilgi edinmek istiyorsanız, izleme yöntemi yerine örnekleme yöntemini kullanarak uygulamanızın profilini oluşturmayı düşünün.
