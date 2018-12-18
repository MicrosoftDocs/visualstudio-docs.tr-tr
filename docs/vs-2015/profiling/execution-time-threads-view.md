---
title: Yürütme zamanı (iş parçacıkları görünümü) | Microsoft Docs
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
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89dd600976e151c377db8ebb2c0e67935c23e006
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789869"
---
# <a name="execution-time-threads-view"></a>Yürütme Zamanı (İş Parçacıkları Görünümü)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş parçacığı etkin bir sistemde bir mantıksal çekirdek çalışmaları yaparken bu segmentlerde faaliyet iş parçacıkları görünümü zaman çizelgesi yürütme zamanı temsil eder.  
  
 İş parçacığı durumu değişiklikleri çekirdek bağlam anahtar olayları algılanır. Olay izleme için Windows (ETW), her bir milisaniyeden kısa örnek yığınları yakalar. Çok kısa yeşil Segmentte hiç örnek alındıktan mümkündür. Bu nedenle, bazı kısa yürütme kesimlerinin hiçbir çağrı yığını gösterebilir.  
  
 Yürütme bölütü tıkladığınızda, Concurrency Visualizer tıklayarak konumuna yakın bir örnek yığını görüntüler. Bu örnek yığın konumunu siyah bir okla gösterilen ya da giriş işaretini bir zaman çizelgesi ve örnek yığını üzerinde görünür **geçerli** sekmesi.  
  
 Geçerli görünümdeki tüm yürütme kesimlerinin geleneksel örnekleme profil görmek için tıklayın **yürütme** görünür zaman çizelgesi profili içinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme Profil raporu](../profiling/execution-profile-report.md)   
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)



