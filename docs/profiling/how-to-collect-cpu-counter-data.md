---
title: 'Nasıl yapılır: CPU sayaç verileri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d5bb2d554ee67a4a2c83decba017e9a1f0fe1e9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813915"
---
# <a name="how-to-collect-cpu-counter-data"></a>Nasıl yapılır: CPU sayaç verileri toplama

CPU olay sayaç donanıma özgü performans verilerini toplamak için kullanılır. Bu makalede, yöntemi profil oluşturma Araçları'nı kullandığınızda, olay sayacı verilerini toplama işlemini göstermektedir.

İki tür CPU sayaç olaylarını gerçekleşir:

- Taşınabilir olayları - bağımsız olarak belirli CPU toplanabilir CPU olayları.

- Platform olayları - belirli bir CPU'ya bağlı CPU olayları'nı tıklatın.

  Taşınabilir olayları yönergeleri Çekildi ve olmayan durdurulamaz döngüleri gibi genel olayları, CPU arabellek olayları, dallanma olayları ve L2 önbellek olayları içerir. Kullanılabilir platformu olay sayaç işlemci üreticisi tarafından belirlenir.

  Olayların kategorilerini taşınabilir ve platform sayaçları arasında paylaşılabilir. Örneğin, aşağıdaki veri kategorileri için her iki tür sık ortaktır:

- Bellek olayları.

- Ön uç etkinlikleri.

- Dal etkinlikleri.

  İki şekilde profil oluşturucu performans sayacı verilerini toplayabilirsiniz:

- Ölçümlü izlemeyle profil, bir veya daha fazla sayaçlarından veri toplayın.

- Örnekleme tarafından profil, bir sayaç olay örnekleme aralığı belirtin. Daha fazla bilgi için [nasıl yapılır: örnekleme olayları seçme](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Ölçümlü izlemeyle profil, CPU performans sayacı verilerini toplamak için

1. Performans oturum **özellik sayfaları**, tıklayın **CPU sayaçları.**

2. Seçin **CPU sayaçlarını Topla** onay kutusu.

3. Genişletin **ulaşılabilir performans sayaçları** toplamak istediğiniz örnek olaylar bulana kadar ağaç.

4. Toplamak istediğiniz her olay, olay seçin ve ardından olaya eklemek için sağ oka tıklayın **sayaçları seçildi** listesi.

    > [!NOTE]
    > **Ulaşılabilir performans sayaçları** yalnızca seçerseniz etkin **toplamak CPU sayaçları** onay kutusu.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
[Performans oturumu özellikleri](../profiling/performance-session-properties.md)  
[CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)  
[Nasıl yapılır: Örnekleme olayları seçme](../profiling/how-to-choose-sampling-events.md)