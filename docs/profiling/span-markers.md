---
title: Span işaretçileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37f2dd735b7deb2d4fed1232c2ba690b26a9fde0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677744"
---
# <a name="span-markers"></a>Kapsam işaretleyicileri
Aralık işaret uygulama anlamlı bir aşamasını temsil eder. Örneğin, belirli bir çalışma öğesini işleniyor zaman aralığını temsil etmek için bir aralık kullanabilirsiniz. Uzunluğu, karşılık gelen uygulaması aşaması süresince temsil eder. Bu örnekte, bir aralık eşzamanlılık görselleştiricisi içinde gösterilmiştir:  
  
 ![Eşzamanlılık görselleştiricisi de aralık bir işaret](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Eşzamanlılık görselleştiricisi'ndeki bir aralık işaretçisi  
  
## <a name="span-category"></a>Aralık kategorisi  
 Aralık işaret kategori bağlı olarak beş farklı renkler biriyle görüntülenir. Beşten fazla kategorileri varsa renkleri yinelenir. Kategori herhangi bir tamsayı olabilir. Bu örnekte, beş renkleri gösterilmiştir:  
  
 ![Farklı kategorilerdeki beş yayılma](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
İlk beş aralık kategorilerin renkleri  
  
## <a name="span-aggregation-markers"></a>Toplama işaretleyicileri  
 Bazen aralık işaretçileri bunu birbirine yakın bunlar ayrı ayrı çekilemez eşzamanlılık görselleştiricisi içinde oluşur. Bu oluştuğunda, bir gri *aralık toplama işaret* temsil olarak temel alınan yayılma gösterilir. Bu simgeler biri üzerinde işaretçiyi getirdiğinizde araç ipucu temsil edilen temel alınan yayılma sayısını görüntüler. Yayılma görüntülemek için yakınlaştırın. Tüm yakınlaştırmak ve yine de aralık toplama işaret alın, temel alınan aralık işaretçilerini görüntüleyebileceğiniz [işaretçiler raporu](../profiling/markers-report.md). Bu örnekte, aralık toplama işaret gösterilmiştir:  
  
 ![Bir toplama eşzamanlılık görselleştiricisi işaretçisi span](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Bir aralık toplama işaretçisi  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık görselleştiricisi işaretleyicileri](../profiling/concurrency-visualizer-markers.md)   
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)