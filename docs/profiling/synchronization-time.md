---
title: Eşitleme zamanı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67f63f292a20e21a00f733dd1190521fd573b98b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861182"
---
# <a name="synchronization-time"></a>Eşitleme saati
Bu segmentlerde faaliyet zaman çizelgesi, eşitleme sınıflandırılmış bir kez engelleme ile ilişkilidir. Bir iş parçacığı eşitlemede engellendi olarak işaretlendiğinde, bunlardan birini gösterilir:  
  
- İş parçacığının yürütülmesini iyi bilinen bir iş parçacığı eşitleme API çağrısında gibi neden olmuş olabilir `EnterCriticalSection()` veya `WaitForSingleObject()`.  
  
- API eşleştirme algoritmasını tamamen kapsamlı olamaz ve eşitleme, ilkel engelleyen bir temel çekirdek ulaştığından çağrısında bir çerçeve yığın çünkü sonunda bu nedenle diğer kategorilere eşleştirilebilir bazı API'leri de görünebilir Bu kategoriyi eşlendi.  
  
  Bir iş parçacığı engelleme olayı temel nedenini anlamak için engelleme çağrı yığınları ve profil raporlarını dikkatle inceleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İş Parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)