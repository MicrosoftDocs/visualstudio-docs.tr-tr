---
title: Özet görünümü - izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 606ba5ebe7c485adb33fbcfa6884ad5e625d821e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677058"
---
# <a name="summary-view---instrumentation-data"></a>Özet görünümü - izleme verileri
Özet görünümü, bir profil oluşturma çalışmasında en pahalı performans işlevleri hakkında bilgi görüntüler. Rapor listeler ve bildirim bağlantıları açıklamasını dahil olmak üzere daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Zaman Çizelgesi grafiği  
 Özet görünümü zaman çizelgesi grafikte, profili oluşturulan uygulamanın profil oluşturma gerçekleşen zaman tarafından işlemci (CPU) kullanımı gösterir. Seçili zaman aralığı için görünüme filtre uygulamak için zaman çizelgesi Grafiği'ni kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Özet zaman çizelgesinden rapor görünümlerini filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Etkin yol  
 **Etkin yolu** en çok zaman harcanan yürütme yolunu görüntüler. İşlev için işlev ayrıntıları görüntülemek için bir işlev tıklayabilirsiniz. İçin işlev sağ işlevi için diğer görünümleri görüntülemek ve sonra listeden bir görünümü tıklatın.  
  
 **Etkin yolu** her işlevine yönelik olarak aşağıdaki verileri içerir:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlevin adı.|  
|**Geçen kapsamlı süre yüzdesi**|İşlevi, işlev gövdesinde ve onu çağıran işlevler kodu yürütürken harcanan profil oluşturma verilerinin tüm süre yüzdesi.|  
|**Geçen dışlamalı süre yüzdesi**|Tüm profil oluşturma verilerinin işlevi, işlev gövdesinde kod çalıştırırken harcadığı süre yüzdesi. İşlev çağrılan işlevlerde geçen süre dahil değildir.|  
  
## <a name="functions-with-most-individual-work"></a>En bireysel işlerle İşlevler  
 Çoğu zaman kodu yürütürken işlevinin gövdesi ve onu çağıran işlevlerini tüketilen işlevlerin listesi.  
  
 **En bireysel işleri işlevleriyle** her işlevine yönelik olarak aşağıdaki verileri içerir:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlevin adı.|  
|**Dışlamalı süre yüzdesi**|Tüm profil oluşturma verilerinin işlevi, işlev gövdesinde kod çalıştırırken harcadığı süre yüzdesi. İşlev çağrılan işlevlerde geçen süre dahil değildir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Özet görünümü - örnekleme verileri](../profiling/summary-view-sampling-data.md)   
 [Özet görünümü - .NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)