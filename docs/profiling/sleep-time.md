---
title: Bekleme süresi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94b1695eb36aa8f55847c21a14d72357d51a405
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677721"
---
# <a name="sleep-time"></a>Bekleme süresi
Bu segmentlerde faaliyet zaman çizelgesi uyku kategorilere ayrılır engelleme zamanı ile ilişkilidir. Uyku kategori, bir iş parçacığı, mantıksal çekirdek gönüllü verdiği ve herhangi bir çalışma yapılması anlamına gelir. Bu süre boyunca, bir iş parçacığı eşzamanlılık görselleştiricisi uyku sayılıyor bir API'de engellendi. API'leri gibi `Sleep()` ve `SwitchToThread()` bu gruba girer.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İş Parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)