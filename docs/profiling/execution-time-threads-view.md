---
title: Yürütme zamanı (iş parçacıkları görünümü) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b06532771aaa432deccb8040c7dd7e5962dd15f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764436"
---
# <a name="execution-time-threads-view"></a>Yürütme zamanı (iş parçacıkları görünümü)
İş parçacığının etkin bir sistemde mantıksal çekirdek çalışma yaparken bu kesimler iş parçacıkları görünümü zaman çizelgesi yürütme zamanı temsil eder.  
  
 İş parçacığı durumu değişiklikleri çekirdek içerik anahtarı olayları algılanır. Olay izleme için Windows (ETW) örnek yığınları her milisaniyelik yakalar. Çok kısa yeşil kesimdeki hiçbir örnek alınır mümkündür. Bu nedenle, bazı kısa yürütme kesimleri hiçbir çağrı yığını gösterebilir.  
  
 Bir yürütme kesimi tıklattığınızda eşzamanlılık görselleştiricisi tıklatın konumuna yakın örnek yığını görüntüler. Bu örnek yığını konumunu siyah bir ok tarafından gösterilen ya da üzerini zaman çizelgesi ve örnek yığını düzeltme işareti görünür **geçerli** sekmesi.  
  
 Geçerli görünümdeki tüm yürütme süresini geleneksel örnekleme profili görmek için tıklatın **yürütme** görünür zaman çizelgesi profilinde.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yürütme Profil raporu](../profiling/execution-profile-report.md)   
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)