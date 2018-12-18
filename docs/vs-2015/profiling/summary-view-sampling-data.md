---
title: Özet görünümü - örnekleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e470cee87a2d83f72df369d79ac337fce5412ed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775244"
---
# <a name="summary-view---sampling-data"></a>Özet Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özet görünümü, bir profil oluşturma çalışmasında en pahalı performans işlevleri hakkında bilgi görüntüler. Rapor listeler ve bildirim bağlantıları açıklamasını dahil olmak üzere daha fazla bilgi için bkz. [özeti görünümünü](../profiling/summary-view.md).  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Zaman Çizelgesi grafiği  
 Özet görünümü zaman çizelgesi grafikte profil oluşturma gerçekleşen zaman içinde oluşturulan uygulamanın işlemci (CPU) kullanım yüzdesini gösterir. Seçili zaman aralığı için görünüme filtre uygulamak için zaman çizelgesi Grafiği'ni kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Özet zaman çizelgesinden rapor görünümlerini filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Etkin yol  
 **Etkin yolu** çoğu örnek toplandı yürütme yolunu görüntüler. İşlev için işlev ayrıntıları görüntülemek için bir işlev tıklayabilirsiniz. İşlevi için diğer görünümleri görüntülemek için işlev sağ tıklayın ve sonra listeden bir görünümü tıklatın.  
  
 **Etkin yolu** her işlevine yönelik olarak aşağıdaki verileri içerir:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlevin adı.|  
|**Kapsamlı örnek yüzdesi**|Bu işlev veya bu işlev tarafından çağrılan bir işlev yürütülürken gerçekleşen tüm örneklerin yüzdesi.|  
|**Dışlamalı örnek yüzdesi**|İşlev işlev gövdesinde kod yürütülürken gerçekleşen tüm örneklerin yüzdesi. Bu işlev tarafından çağırılan işlevlerdeki toplanan örnekler dahil edilmez.|  
  
## <a name="functions-doing-most-individual-work"></a>En bireysel işleri yapan işlevler  
 **İşlevleri en bireysel işleri yapan** en yüksek sayıda profil oluşturma çalışması içinde dışlamalı örnek işlevleri görüntüler. Özel bir örnek, örnek toplandığında, kendi kod işlevi yürütülüyorsa bir işleve atanır. Örnek toplandığında işlevi başka bir işlevi çağırıyorsa, özel bir örnek için bir işlev atanmadı. Dışlamalı örnek çok sayıda önemli zaman işlevde harcanan gösterir.  
  
 İşlev için işlev ayrıntıları görüntülemek için bir işlev tıklayabilirsiniz. İçin işlev sağ işlevi için diğer görünümleri görüntülemek ve sonra listeden bir görünümü tıklatın.  
  
 **En bireysel işleri yapan işlevler** her işlevine yönelik olarak aşağıdaki verileri içerir:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlevin adı.|  
|**Dışlamalı örnek yüzdesi**|İşlev kendi işlev gövdesindeki kod yürütülürken, toplanmış olan profil oluşturma, tüm örneklerin yüzdesi. Bu işlevi çağıran işlevler yürütülürken toplanan örnekler yüzdeyi dışlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özet görünümü](../profiling/summary-view-dotnet-memory-data.md)   
 [Özet Görünümü](../profiling/summary-view-instrumentation-data.md)



