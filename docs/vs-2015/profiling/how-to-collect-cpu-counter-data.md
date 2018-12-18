---
title: 'Nasıl yapılır: CPU sayaç verileri toplama | Microsoft Docs'
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
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46ade222b6032baca17afe37d72dd6e5657ae1c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763393"
---
# <a name="how-to-collect-cpu-counter-data"></a>Nasıl yapılır: CPU Sayaç Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CPU olay sayaç donanıma özgü performans verilerini toplamak için kullanılır. Bu konuda yöntemi profil oluşturma Araçları'nı kullandığınızda olay sayacı verilerini nasıl toplayacağınızı gösterilmektedir.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  İki tür CPU sayaç olaylarını gerçekleşir:  
  
- Taşınabilir olayları - bağımsız olarak belirli CPU toplanabilir CPU olayları.  
  
- Platform olayları - belirli bir CPU'ya bağlı CPU olayları'nı tıklatın.  
  
  Taşınabilir olayları yönergeleri Çekildi ve olmayan durdurulamaz döngüleri gibi genel olayları, CPU arabellek olayları, dallanma olayları ve L2 önbellek olayları içerir. Kullanılabilir platformu olay sayaç işlemci üreticisi tarafından belirlenir.  
  
  Olayların kategorilerini taşınabilir ve platform sayaçları arasında paylaşılabilir. Örneğin, aşağıdaki veri kategorileri için her iki tür sık ortaktır:  
  
- Bellek olayları.  
  
- Ön uç etkinlikleri.  
  
- Dal etkinlikleri.  
  
  Profiler iki yolla performans sayacı verilerini toplayabilirsiniz:  
  
- Ölçümlü izlemeyle profil, bir veya daha fazla sayaçlarından veri toplayın.  
  
- Örnekleme tarafından profil, bir sayaç olay örnekleme aralığı belirtin. Daha fazla bilgi için [nasıl yapılır: örnekleme olayları seçin](../profiling/how-to-choose-sampling-events.md).  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Ölçümlü izlemeyle profil, CPU performans sayacı verilerini toplamak için  
  
1.  Performans oturum **özellik sayfaları**, tıklayın **CPU sayaçları.**  
  
2.  Seçin **CPU sayaçlarını Topla** onay kutusu.  
  
3.  Genişletin **ulaşılabilir performans sayaçları** toplamak istediğiniz örnek olaylar bulana kadar ağaç.  
  
4.  Toplamak istediğiniz her olay, olay seçin ve ardından olaya eklemek için sağ oka tıklayın **sayaçları seçildi** listesi.  
  
    > [!NOTE]
    >  **Ulaşılabilir performans sayaçları** yalnızca seçerseniz etkin **toplamak CPU sayaçları** onay kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Performans oturum özellikleri](../profiling/performance-session-properties.md)   
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)   
 [Nasıl Yapılır: Örnekleme Olayları Seçme](../profiling/how-to-choose-sampling-events.md)



