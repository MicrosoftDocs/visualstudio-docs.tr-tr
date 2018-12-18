---
title: GPU Etkinlik Grafiği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9dcadfdbfa52815fdd6d88f78afb88d421e203c7
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237916"
---
# <a name="gpu-activity-graph"></a>GPU Etkinlik Grafiği
Eşzamanlılık görselleştiricisi GPU etkinliği grafikte DirectX etkinlik düzeyi sistemde zaman içinde kullanılan DirectX altyapısı sayısı ölçülen görüntüler.  Grafik, hangi belirli motorları kullanılan göstermez.  Altyapının herhangi bir GPU iş işliyorsa kullanımda olarak kabul edilir.  
  
## <a name="gpu-activity-graph-colors"></a>GPU Etkinlik Grafiği renkleri  
 Yeşil DirectX motorları tüketimi geçerli işlem tarafından gösterir.  
  
 Açık gri DirectX motorları tüketimi sistem üzerinde başka işlemler tarafından gösterir. Diğer işlemler tarafından tüketilen DirectX altyapısını azaltmak için sistem üzerinde çalışan diğer işlemlerin sayısını azaltın.  
  
 Beyaz sistem kullanılmayan DirectX motorlarına kullanılabilirliğini gösterir. Daha fazla bunları yararlanma fırsatı bulabilirsiniz bu motorları işleminiz için kullanılabilir. Bazı motorları yalnızca belirli tür görevleri için kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kullanım Görünümü](../profiling/utilization-view.md)