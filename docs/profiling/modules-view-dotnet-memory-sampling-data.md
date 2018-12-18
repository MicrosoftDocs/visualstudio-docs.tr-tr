---
title: Modüller görünümü - .NET bellek örnekleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c5cbae58aeaa1164aab6c254f62e0959da02d31c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257679"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modüller görünümü - .NET bellek örnekleme verileri
.NET bellek ayırma verilerinin örnekleme yöntemini kullanarak toplanan modülleri görünümü bellek verileri profil Çalıştır yürütüldü modülleri göre gruplandırır. Her modül hiyerarşik bir köküdür. Modül işlevleri modülü düğümünün altında listelenir.  
  
 Kaynak dosya satır numaralarını bellek deyimlerinin işlevi düğümünün altında listelenen ve ayırma işlemini yönergeleri adreslerini satır düğümünün altında listelenir. (Bunlar dahil) ve özel değerler her zaman satır verileri ve yönerge verileri için aynıdır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Modül, işlev, satır numarası veya yönerge adresi adı.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|Modül yolu.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Kapsayıcı ayırmaları**|-Bir işlev için işlev tarafından oluşturulan nesneleri toplam sayısı. Bu işlev tarafından adı veriliyordu işlevlerinde oluşturulan nesneleri içerir.<br />-Bir modül için en az bir işlev modülünden ayrılan bir profil oluşturma çalıştırma nesnelerin sayısı yürütülmekte olan. Modül işlevleri tarafından adı veriliyordu işlevlerinde oluşturulan nesneleri içerir.<br />-Bir satır veya yönerge, toplam satırı veya yönerge tarafından ayrılan nesne sayısı için.|  
|**Kapsayıcı ayırmaları %**|Profil çalışmasını ayrılan tüm nesneleri yüzdesi modülü, işlev, satır veya yönerge dahil ayrılmasını yoktu.|  
|**Özel ayırmaları**|-Geçerli işlev, işlev kodunu işlev gövdesi yürütülürken oluşturulan nesneleri sayısı için (diğer bir deyişle, ne zaman işlevi çağrı yığını üstünde olduğu). Sayı, bu işlev tarafından adı veriliyordu işlevlerinde oluşturulan nesneleri içermez.<br />-Bir modül için özel ayırmaları modülündeki işlevlerin toplamı.<br />-Bir satır veya yönerge, bu satırı veya yönerge tarafından oluşturulan nesneleri toplam sayısı için.|  
|**Özel ayırmaları %**|Profil çalışmasını ayrılan tüm nesneleri yüzdesi modülü, işlev, satır veya yönerge özel ayrılmasını yoktu.|  
|**Kapsayıcı bayt**|-Bir işlev için işlev tarafından ayrılan bayt sayısı. Bu işlev tarafından adı veriliyordu işlevlerinde ayrılan bayt sayısını içerir.<br />-Bir modül için profil oluşturma çalıştırılmasıyla ayrılan en az bir işlev modülünden ayrılan bayt sayısı yürütülmekte olan. Modül işlevleri tarafından adı veriliyordu tüm işlevlerinde oluşturulan nesneleri içerir.<br />-Bir satır veya yönerge, çizgi veya yönerge tarafından oluşturulan nesneleri toplam sayısı için.|  
|**Kapsayıcı bayt %**|Profil çalışmasını ayrılan tüm bayt yüzdesi modülü, işlev, satır veya yönerge dahil bayt yoktu.|  
|**Özel bayt sayısı**|-Bir işlev için toplam işlev tarafından ayrılan bayt sayısı. Sayı ayrılan bayt bu işlev tarafından adı veriliyordu işlevleri içermez.<br />-Bir modül için modülündeki işlevler tarafından ayrılan özel bayt toplamını.<br />-Bir satır veya yönerge, bu satırı veya yönerge tarafından ayrılan nesneleri toplam sayısı için.|  
|**Özel bayt %**|Profil çalışmasını ayrılan tüm bayt yüzdesi modülü, işlev, satır veya yönerge özel bayt yoktu.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Modüller görünümü - izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller görünümü](../profiling/modules-view-sampling-data.md)   
 [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)