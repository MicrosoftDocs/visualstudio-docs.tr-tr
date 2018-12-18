---
title: Bayrak işaretleyicileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f924089ef31e2b452419b107788357060a4c6bb6
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237997"
---
# <a name="flag-markers"></a>Bayrak işaretleyicileri
Bayrak işaret anlık bir uygulama sürede oluşan bir şeyi temsil eder. Bir bayrak pek çok uygulama olayları temsil edebilir. Örneğin, bir bayrak belirli iş öğesini zaman zamanlandığı veya ne zaman bir özel durum oluştu gösterebilirsiniz. Görev paralel kitaplığı gibi çalışma zamanları bayrakları de oluşturabilirsiniz.  
  
## <a name="flag-importance"></a>Bayrak önem derecesi  
 Bayrakları önemine bağlı olarak farklı boyutlarda görüntülenir. Herhangi bir işaret gibi düşük, normal, yüksek veya kritik önem olabilir.  Bu çizim önem düzeyini işaretçilerini görünümünü gösterir:  
  
 ![Düşük, Normal, yüksek ve kritik önem işaretçileri](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Bayrak önemini gösteren işaretçileri  
  
## <a name="flag-category"></a>Bayrak kategorisi  
 Bir bayrak kategorisinin bağlı olarak beş farklı renk birinde görüntülenir. Beşten fazla kategorileri varsa renkleri yeniden kullanılır. Renk seçemezsiniz. Herhangi bir işaret gibi herhangi bir tamsayı kategori olabilir. Sonraki çizim ilk beş kategorileri için renkleri gösterir.  
  
 ![Kategori işaretlerinin beş renk](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Kategoriler gösteren işaretçileri  
  
## <a name="alerts"></a>Uyarılar  
 Bir uyarı, bir özel durum gibi bir kritik uygulama olay temsil eden bir kırmızı renkli bayrak belirtir.  Bir uyarı şöyledir:  
  
 ![Eşzamanlılık görselleştiricisi uyarı işaret](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Bir uyarı işaretçisi  
  
## <a name="aggregation-flags"></a>Toplama bayrakları  
 Bazen bayrakları bunu başka yakın bunlar ayrı ayrı çekilemez eşzamanlılık görselleştiricisi içinde oluşur. Bu oluştuğunda, bir gri *toplama bayrağı* temsil temel bayrakları gösterilir. Bu simgeleri birinde işaretçiyi getirdiğinizde, araç ipucu temsil edilen temel bayrakları sayısını görüntüler. Bayrakları görüntülemek için Yakınlaştır. Bu süreç boyunca tüm yakınlaştırmak ve hala bir toplama bayrağını alma, temel alınan bayrakları görüntüleyebilirsiniz [işaretçiler raporu](../profiling/markers-report.md).  
  
 Toplama bayrakları farklı boyutlarda çizilir. Toplama en önemli bayrağı önem düzeyini boyutuna bağlıdır. Aşağıdaki çizimde, artan düzende önem toplama bayrakları gösterir.  
  
 ![Toplama bayrakları gösteren dört önem düzeylerini](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Önem düzeyine göre toplama bayrakları  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık görselleştiricisi işaretleyicileri](../profiling/concurrency-visualizer-markers.md)   
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)