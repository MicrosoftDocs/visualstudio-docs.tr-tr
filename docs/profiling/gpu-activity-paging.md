---
title: GPU etkinliği (disk belleği) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b8b682c47844a9bc88afdce4a532b1188746a85
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238039"
---
# <a name="gpu-activity-paging"></a>GPU Etkinliği (Disk Belleği)
**GPU etkinliği (disk belleği)** üzerinde kesim **iş parçacığı** sekmesinde temsil kez zaman GPU işleme disk belleği istekleri.  Bir segment uzunluğu GPU doğrudan bellek erişimi (DMA) disk belleği paket işliyordu süreyi temsil eder. Genellikle, disk belleği paketleri CPU ve GPU'ya arasında bellek aktarımı ile ilişkilendirilmiş.  
  
 Seçtiğinizde, bir GPU disk belleği segment, rapor üzerinde **geçerli** sekmesini işlenmiş DMA paket hakkındaki bilgileri görüntüler. Bu, beklenen süre miktarını DirectX altyapısı, DMA paket gönderilen işlem ve paket işlemek için gerekli olan zamanı ile ilişkili donanım sıranın içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kullanım Görünümü](../profiling/utilization-view.md)