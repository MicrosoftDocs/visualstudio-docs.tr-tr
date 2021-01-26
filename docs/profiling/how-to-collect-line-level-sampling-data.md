---
title: Line-Level örnekleme verilerini toplayın | Microsoft Docs
description: Profiler 'ın satır düzeyi örnekleme, büyük miktarlarda işlemci süresi kullanan kodu nasıl açığa çıkartabilecek hakkında bilgi edinin. Hem yönetilen hem de yerel kodla birlikte çalışarak.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3a760980b16fab17fed7180b0bc74e0271c61e1d
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801068"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Nasıl yapılır: satır düzeyi örnekleme verileri toplama
Satır düzeyinde örnekleme, profil oluşturucunun, yüksek ayrıcalıklı örneklere sahip bir işlev gibi, işlemcinin yoğun bir işlev kodunda nerede bir süre harcadığını belirlemede kullandığı bir işlemdir.

## <a name="overview"></a>Genel Bakış
 Satır düzeyi örnekleme için, profil oluşturucu program çağrı yığınını belirlenen aralıklarda yönlendirir ve bu sonuçları toplar. Bu sonuçlar, örnek çekilirken işlemcinin hangi talimatları yürüttüğünü gösterir. Dışlamalı örneklerle ilgili toplanan veriler daha sonra kod satırlarını ve yönerge işaretçisini (IP) belirlemek için çözümlenir.

 Satır düzeyi örnekleme, yönetilen ve yerel kod için de kullanılır. Bu verileri görüntüleyen performans raporları, satırlar görünümü ve modüller görünümünü içerir.

 Yerel kod için karakter başlangıç/bitiş bilgileri kullanılamıyor. Çok satırlı deyimler için, satır başlangıç bilgileri yerel kod için kullanılamaz; yalnızca satır sonu bilgileri kullanılabilir.

### <a name="available-data"></a>Kullanılabilir veriler
 Kullanılabilir satır düzeyi örnekleme verileri aşağıdaki bilgileri içerir:

- İşlev adı.

- İşlev adresi.

- Satır başlangıcı-örneklenmiş kodun satır numarası.

- Satır bitiş bitiş kaynak satır numarası. Tek bir program ifadesinin birden çok kaynak kodu satırını yaydığı durumlar dışında, bu genellikle "satır başlangıcı" verileriyle aynıdır.

- Karakter başlangıcı-toplu Örneğin başlangıç sütunu. Tek bir satır birden çok program deyimi içerdiğinde bu genellikle 0 ' dır.

- Toplu örneğin karakter bitiş bitiş sütunu.

- Toplama örneğinin alındığı IP adresi (yalnızca IP görünümü).

  **Modüller** görünümünde, bir işlevde satır düzeyi istatistikleri varsa, istatistikler her bir işlevin altına yuvalanır. Bunlara ek olarak, her satırın altında iç içe geçmiş IP düzeyi istatistikler sunulur.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Yönetilen kod için satır düzeyinde örnekleme kapatma
 Varsayılan olarak, satır düzeyi örnekleme açıktır. Aşağıdaki komutlardan birini kullanarak, yönetilen kod için satır düzeyi veri toplamayı kapatabilirsiniz:

- Profil oluşturmadan önce **VSPerfCLREnv/samplelineoff** yazın. Bu, hem uygulamaları hem de hizmetleri etkiler.

     veya

- Bir uygulamayı başlatırken **VSPerfCmd/LineOff \<other arguments>** yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
